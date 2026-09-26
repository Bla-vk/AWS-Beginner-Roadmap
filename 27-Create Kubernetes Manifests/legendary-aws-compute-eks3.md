<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create Kubernetes Manifests

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-eks3)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Create Kubernetes Manifests

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks3_b01876555)

---

## Introducing Today's Project!

In this project, I'll set up manifest files since they're a core part of the Kubernetes deployment process. Manifest files tell Kubernetes exactly how to deploy my containerized application.

### Tools and concepts

I used Amazon EKS, eksctl, Git, Docker, and ECR to create a Kubernetes cluster and build the container image for the backend of an app I deployed. Key concepts I worked with include using manifest files, along with Deployments and Services, to get the app ready for Kubernetes deployment.

### Project reflection

I chose to do this project today to understand Kubernetes deployment on AWS. 

This project took me approximately an hour.The most challenging part was understanding and breaking down the deployment manifest.

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. The steps I took included attaching an IAM role with the necessary permissions to my EC2 instance and installing the eksctl command line tool. I then created the cluster using the eksctl create cluster command.

### Backend code

I retrieved the backend that I plan to deploy by cloning a team members GitHub repository. Backend is the brain of an application. It's where your app processes user requests and stores and retrieves data.

### Container image

Once I cloned the backend code, I built a container image, since Kubernetes requires applications to be packaged as container images before they can be deployed. I used Docker to build the image of my backend.

I also pushed the container image to a container registry, since this helps establish a single source of truth for the latest version of my image. To push it to ECR, I ran the push commands, which included tagging the image with the ECR repository URI(Uniform Resource Identifier) before uploading it.

---

## Manifest files

Kubernetes manifests are set of instructions that tells Kubernetes how to run your app. Manifests are helpful because they setup and manage your apps automatically. Without manifest you'd have to manually configure each container every time you deploy, which would be confusing, error-prone, and hard to repeat.

A Kubernetes Deployment manages multiple identical copies of the same containerized backend. The container image URL in my Deployment manifest tells Kubernetes which specific container image to pull and run for each replica, while other settings like ports, environment variables, and resource limits are defined separately within the container spec.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks3_b01876554)

---

## Service Manifest

A Kubernetes Service exposes the application to network traffic. You need a Service manifest to tell Kubernetes to create or update that traffic controller. In it, you specify a selector to determine which pods receive the traffic, a type to determine how that traffic reaches the service (e.g., internally within the cluster or externally via a load balancer), and the ports it listens on and forwards to.

My Service manifest sets type: NodePort, which opens a port on every node's IP for external traffic to reach the cluster. That traffic is then routed to the Service's port (8080), which forwards it to targetPort 8080 on the container running the application.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks3_b01876555)

---

## Deployment Manifest

Annotating the Deployment manifest helped me understand the ins and outs of each command, since I broke down and explained each line individually, along with how it relates to the other commands around it

A notable line in the Deployment manifest is the number of replicas, which specifies how many copies of my app I'd like running across the cluster. Pods are relevant here because there's a 1:1 relationship (3 replicas means 3 Pods) which is enforced by the Deployment.

One part of the Deployment manifest I still want to understand better is the namespace field, since it's not yet clear to me what it means, how it affects the Deployment, or how it's used as metadata.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks3_6aae73e71)

---

---
