## Learning DevOps 
### Base Project
This was a demo app - developing with Docker:
ALL CREDITS GO TO THE [DOCKER TUTORIAL](https://www.youtube.com/watch?v=3c-iBn73dDE) by TechWorld with Nana
A docker tutorial that teaches how to use docker to create 3 containers (nodejs app, mongodb, mongo-express) that are connected to one another using docker-compose.

### What I built on top of this
#### Kubernetes (Minikube)
> 1. Created a k8 cluster for 3 different services: nodejs app, mongodb, mongo-express 
> 2. Learned how to tag docker images and push them to AWS ECR
- Challenges
> 1. Figuring out the connection of the nodejs app to the mongodb by changing some lines in the base code
---
#### Webhook for jenkins server (ec2) to "kinda" build the app whenever theres changes in the repo
- ec2 instance
> 1. Created a ec2 linux instance using AWS console
> 2. Putty for SSH connection to instance's shell
> 3. Installed jenkins and other dependencies (java-openjdk, git)
> 4. Started jenkins server 
> 5. Connect to jenkins by using <ec2_dns>:8080  
- Webhook
> 1. Created github webhook for a pipeline
> 2. Created github webhook for multibranch pipepline (the use of multibranch pipeline trigger token plug-in  
- Challenges
> 1. Very simple step but I forgot that I have to install git for the to run builds using Jenkinfiles in github
---
#### Pushing docker image of node application to ecr
- AWS credentials
> 1. Easily configured using the CloudBees AWS credentials plug-in  
- Docker on EC2 instance
> 1. Installed docker using yum  
- Challenges
> 1. Giving permission to use docker for jenkins
> 2. Jenkinsfile wrapper (withDockerRegistry) - RMB to use the pipeline syntax helper
---
#### Deploying containers on ECS using Jenkins with (docker compose + ECS integration in agent's shell)
[https://docs.docker.com/cloud/ecs-integration/](https://docs.docker.com/cloud/ecs-integration/)
> 1. download latest docker compose
> 2. create a docker ecs context
> 3. "docker compose up" after switching context
- Challenges
> 1. Spent quite a long time trying to figure out how to upgrade docker compose.
> 2. Docker compose up still giving permissions errors after I attached the policy to my IAM user according to the above link.
