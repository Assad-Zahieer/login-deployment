# 0. Project Definition
The aim is to deploy a user registration and login gateway upon which applications may be built. A total of 14 microservices will be deployed, and a network built so that they may commmunicate with each other as needed. The services will be built using docker, then deployed and connected. This will be done initially using docker-compose and, once it has been verified that the app is working, then kuberneties.
# 1. Architecture
![Diagram](https://github.com/Assad-Zahieer/BobsProject/blob/master/Architecture.jpg)
# 2. Steps
What follows is a brief guide to how the project was carried out.
## 2.1 Docker
Docker images were built by first creating a Dockerfile for each service and then running docker build. This was done by first cloning each service from github. Example: `https://github.com/Assad-Zahieer/session-token-service.git` and then building using the appropriate Dockerfile. An example of this can be seen in the afformentioned link.

## 2.2 Docker-compose
A docker-compose file was created to join-up the services and expose the gateway to the internet. This file can be seen in `https://github.com/Assad-Zahieer/BobsProject/blob/master/Architecture.jpg`
This was then tested by going to the IP address of the VM, creating a user, and loging in. The images were then pushed to docker hub.

## 2.3 Kuberneties

