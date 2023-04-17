# react_flask_app

# backend-api/Dockerfile
1.Use an official Python Alpine base image

2.Set the working directory in the container

3.Copy the backend files into working directory

4.Install dependencies using Alpine package manager

5.Expose the backend server port

6.Start the Gunicorn server using the app module inside the /app directory and binds it to port 5000 on all network interfaces.


# frontend-sys-stats/Dockerfile

1.Use an official Node.js base image

2.Set the working directory in the container

3.Copy the package.json and package-lock.json files into the container

4.Install dependencies for reactjs

5.Copy the frontend application code to the container

6.Build the frontend app using npm

7.Use a smaller nginx base image for serving the static files

8.Copy the built frontend app from the previous stage to the Nginx default HTML directory

9.Copy the Nginx configuration file to the container

10.Expose the port that Nginx will run on 80 port

11.Start Nginx

# Docker-Compose-file

1.Mention the docker-compose file version 

2.The backend service is built using the Dockerfile located in the ./api directory, and is configured to expose port 5000. This service is responsible for serving the API for the application.

3.The frontend service is built using the Dockerfile located in the ./sys-stats directory, and is configured to expose port 80. This service is responsible for serving the frontend of the application.

4.Start the backend service before starting the frontend service, and will ensure that the two services can communicate with each other. For this we use depends_on directive is used to specify that the frontend service depends on the backend service.

5.Docker Compose file defines a simple two-container setup for running an application with a frontend and backend, where the frontend communicates with the backend over the network. The backend service is exposed on port 5000, and the frontend service is exposed on port 80.

# Docker Desktop local

1.Install docker desktop in local

2.Start Docker daemon 

3.Install docker-compose on local

4.Go to directory where docker-compose.yml file exists and run a command docker-compose up --build it will build the images of frontend, backend and creates contianers

5.Access the application using localhost

# aws_infra

1.Install terraform and awscli in local.

2.Provisioned AWS infra using terraform.

3.Created VPC with two public subnets, an Internet Gateway, and NAT Gateway. The VPC and the subnets are tagged with a specified environment name.

4.Created ec2 instance associates an Elastic IP, provisions a security group for the EC2 instance and adds rules to it, allowing access to the instance from the internet and configuration creates a key pair for the instance, which allows connecting to it securely using SSH.

5.Written shell script to installing git, docker and docker-compose

6.User data is defined using template_file content can be used as input to an EC2 instance in AWS, for example, as a user data script that is executed when the instance launches.

7.Created hosted zone ,recordsets and attached public ip of ec2 instance in record set


# Code Change

1.In sys-stats folder under src need to change code in App.js file, have to replace localhost with public dns name in line number 23 to expose application outside.


# Build

1.Login into ec2 instance 

2.Clone the code from gitrepository

3.Navigate to the folder where code exists and run a command docker-compose up --build it will spin up application

4.Check whether the application is accessible or not through public dns name (reactjs.19091999.quest).


# Minikube

1.Install minikube, kubetcl in local using brew command in mac and start minikube

2.Check cluster is running or not.

3.Written deployment, service yaml files for frontend and backend.

4.Deployed frontend and backend services in minikube.

5.Since minikube is  single-node Kubernetes cluster on their local machine not able to create load balancer and minikube doesn't come with an ingress controller installed, have to do port forward to access application.

6.Have to port forward both frontend and backend services because by deafult reactjs nature is it will not communicate to backend in this case have to port forward backend service as well.