<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Kubernetes Deployment

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-eks2)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Set Up Kubernetes Deployment

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks2_45e6c3de5)

---

## Introducing Today's Project!

In this project, I'll prepare an app's backend for deployment with Kubernetes. Since Kubernetes requires apps to be containerized and packaged as a container image before deployment, this project will focus on building that container image.

### Tools and concepts

I used Amazon EKS, Git, Docker, and Amazon ECR to prepare a backend app for deployment with Kubernetes. Key steps included setting up an EKS cluster, cloning the code from GitHub, and building and pushing a Docker image to Amazon ECR.

### Project reflection

This project took me approximately 50 minutes. The most challenging part was troubleshooting the errors I encountered along the way and working through them to find solutions.

Something new that I learnt from this experience was just how many tasks can be performed directly from the EC2 instance terminal.

---

## What I'm deploying

To set up today's project, I launched a Kubernetes cluster. Steps I took to do this included launching an EC2 instance to act as my admin machine, installing eksctl on it, attaching an IAM role with AdministratorAccess so it had the necessary permissions, and then running an eksctl command to create the cluster.

### I'm deploying an app's backend

Next, I retrieved the backend that I plan to deploy. An app's backend means the brain of an application. It's where your app processes user requests and stores and retrieves data. I retrieved backend code by cloning it from a Github repository.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks2_1ebb86c71)

---

## Building a container image

Once I cloned the backend code, my next step is to build a container image of the backend. This is because a container image bundles your app’s code, libraries, and settings into a single file. Kubernetes pulls that image to start identical containers, which are live copies of your app. I haven't prepared a container image yet, just raw code.

When I tried to build a Docker image of the backend, I ran into a permissions error because Docker requires root privileges or membership in the docker group to access its socket. Since ec2-user wasn't added to the docker group, it couldn't talk to the Docker engine directly even though ec2-user does have sudo access. I resolved this by adding ec2-user to the docker group.

To solve the permissions error, I added ec2-user to the docker group. This group is created when Docker is installed, and membership grants a user access to it, allowing them to run Docker commands (like docker build) without needing sudo.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks2_45e6c3de5)

---

## Container Registry

I'm using Amazon ECR in this project to store my container image. ECR is a good choice for the job because it's an AWS service, which lets Elastic Kubernetes Service (EKS) deploy my container image with minimal authentication setup.

Container registries like Amazon ECR are pretty handy for Kubernetes deployments  because i get to keep my tagged images in one place as the "source of truth." Once permissions are set up, Kubernetes just pulls whatever image it needs automatically, so no manual downloading or copying files around.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks2_l2m3n4o5)

---

## EXTRA: Backend Explained

After reviewing the app's backend code, I learned that the application serves a dual role: it consumes data from an external API, and through app.py, it also exposes its own API endpoint so external clients can access our services.

### Unpacking three key backend files

The requirements.txt file lists all the dependencies and libraries that every container needs to install when the container is created.

The Dockerfile gives Docker step-by-step instructions on how to build an image for the backend. Key commands include the COPY command, which copies the requirements.txt file into the image so its listed packages can be installed, and the RUN command, which executes pip install -r requirements.txt to actually install those dependencies. The CMD instruction then specifies the default command that automatically runs when a container starts from that image.

The app.py file is structured around three main parts: setting up the app and defining its routes, fetching the requested data, and sending back a response formatted as JSON.

---

---
