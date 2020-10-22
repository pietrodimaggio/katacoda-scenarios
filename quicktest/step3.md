1 -If not already started start minikube

`minikube start`{{execute}}

2- Create the persistent volume and the persistent volume claim 

`kubectl apply -f https://k8s.io/examples/application/mysql/mysql-pv.yaml`{{execute}}

3- Create the MySql deployment linked to the previous volume claim

`kubectl apply -f https://k8s.io/examples/application/mysql/mysql-deployment.yaml`{{execute}}

4- Check if the MySql pod is running
`kubectl get pods`{{execute}}

5- Open a connection my mysql client (type exit when finished)
`kubectl run -it --rm --image=mysql:5.6 --restart=Never mysql-client -- mysql -h mysql -ppassword`{{execute}}

Type in mysql shell

`CREATE DATABASE mydb;`{{execute}}

this will create a db instance

6- Find the MySql pod and delete by the command 

kubectl delete pod ***mysql_pod-id**


After that the pod lost all its local resources and will be recreate automatically from Kubernetes
`kubectl get pods`{{execute}}

7- Open a connection my mysql client to check if the database mydb is still there(type exit when finished)
`kubectl run -it --rm --image=mysql:5.6 --restart=Never mysql-client -- mysql -h mysql -ppassword`{{execute}}

Type into the mysql shell for listing the active databases

`SHOW DATABASES;`{{execute}}