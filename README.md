# 0. Project Definition
The aim is to deploy a user registration and login gateway upon which applications may be built. A total of 14 microservices will be deployed, and a network built so that they may commmunicate with each other as needed. The services will be built using docker, then deployed and connected. This will be done initially using docker-compose and, once it has been verified that the app is working, then kuberneties.
# 1. Architecture
![Diagram](https://github.com/Assad-Zahieer/BobsProject/blob/master/Architecture.jpg)
figure 1.0 Services architecture
# 2. Steps
What follows is a brief guide to how the project was carried out.
## 2.1 Docker
Docker images were built by first creating a Dockerfile for each service and then running docker build. This was done by cloning the services from github and then building using the appropriate Dockerfile. An example of this (Dockerfile) can be seen here: https://github.com/Assad-Zahieer/login-deployment/tree/master/account-service
All services and client images are built from node. Clients are built by implimenting the npm run serve endpoint, and services with  node src/app/js. The primary function of these images is to allow easier access and faster deployment of the services.

## 2.2 Docker-compose
A docker-compose file was created to join-up the services and expose the gateway to the internet. This file can be seen in `https://github.com/Assad-Zahieer/login-deployment/blob/master/docker-compose.yaml`
It should be noted that the structure of this file corresponds to the Architecture (figure 1.0). Each numbered service on the diagram depends upon service with numbers greater than it. Therefore by deploying the services backwards (from 6) and ensuring that each corresponding number depends on the previous (e.g. 5 depends on 6, 4 on 5 etc.) We can ensure that all services are started up in the correct order. 
Once all services were deployed, they were tested by going to the IP address of the VM, creating a user, verifying it, and loging in. The images were then pushed to docker hub: `docker-compose push` this works because the container names (in the yaml) are in the following format docker-hub-username/repository-name.

## 2.3 Kuberneties

