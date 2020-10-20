Check docker images on the local repository
`docker images`{{execute}}

Let's create a little image for running an Apache Web Server

1 -Create an “index.html” with your “Hello Techedge!”

`echo "Hello Techedge!" > index.html`{{execute}}

2 -Create a “Dockerfile” from the Apache image 

`nano Dockefile` {{execute}}

Copy and paste the following into a file named Dockerfile

`FROM httpd:2.4`
`COPY ./index.html /usr/local/apache2/htdocs/`

3- Build the image by the docker file

`docker build -t my-apache2 .`



