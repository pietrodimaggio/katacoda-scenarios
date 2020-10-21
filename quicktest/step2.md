1 -Start minikube

`minikube start`{{execute}}

2 -Create a nginix deployment

`kubectl apply -f https://raw.githubusercontent.com/kubernetes/website/master/content/en/examples/controllers/nginx-deployment.yaml`{{execute}}

3 - See the pods creating

`kubectl get pods`{{execute}}

4- See the deployment state
`kubectl get deployments`{{execute}}



5- Expose your nginx by LoadBalancer. Now the nginx pod instances run inside the cluster on port 80 and are not reachable from the outside.
Create a service LoadBalancer to expose the nginx pool.
`kubectl expose deployment nginx-deployment --type=LoadBalancer`{{execute}}

Now the Kubernetes service nginx-deployment is balancing request on the pods instances


6- Check your service LoadBalancer by
`kubectl get service`{{execute}}

You'll get something like the following:


NAME               TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE

kubernetes         ClusterIP      10.96.0.1       <none>        443/TCP        41m

nginx-deployment   LoadBalancer   10.106.21.178   <pending>     80:30944/TCP   10s

Find the port after the 80:XXXXX 
Click on "+" at the top of the shell and "select port to view on host1"
Enter port XXXXX, if all is fine you'll see the welcome page

7-Clean up
`kubectl delete service nginx-deployment`{{execute}}
`kubectl delete deployment nginx-deployment`{{execute}}