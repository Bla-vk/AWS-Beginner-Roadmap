<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy Backend with Kubernetes

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-eks4)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Deploy Backend with Kubernetes

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks4_6cfb382f2)

---

## Introducing Today's Project!

In this project, I will set up the backend of an app for deployment using kubernetes.

### Tools and concepts

I used Amazon EKS, kubectl, Docker, eksctl, ECR, and GitHub to deploy the backend application. Key concepts I worked with include using manifest files, building container images, and pushing them to a container registry.

### Project reflection

This project took me approximately 60 minutes. 

---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. The cluster's role in this deployment is to act as the control centre for orchestrating all the containers that will run the application I want to deploy. Its control plane makes the scheduling and management decisions, while its worker nodes actually run the containers.

### Backend code

I retrieved the backend code by cloning a team member's GitHub repository to get a local copy. Pulling the code is essential to this deployment because I need local access to it in order to build a container image, which is what Kubernetes will actually deploy, not the raw code itself.

### Container image

Once I cloned the backend code, I built a container image because Kubernetes requires applications to be packaged this way. Without an image, it would be difficult for Kubernetes to deploy the application.

I also pushed the container image to a container registry, which is a storage space for container images. ECR facilitates scaling for my deployment because Kubernetes can easily pull whatever is the latest image in the repository on demand.

---

## Manifest files

Kubernetes manifests are set of instructions that tells Kubernetes how to run your app. Manifests are helpful because Kubernetes uses it to know what your app needs, like which containers to run, how many copies to create, and how much memory to allocate. 

A Deployment manifest defines a Deployment resource, which manages the creation and lifecycle of Pods running my containers across the nodes in my Kubernetes cluster. The container image URL in my Deployment manifest tells Kubernetes where to pull my image from, in this case, my ECR repository.

A Service resource exposes a set of Pods as a stable network endpoint, routing traffic to them based on matching labels with my Deployment. My Service manifest sets up a Service that exposes my backend application on port 8080 within the EKS cluster.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks4_b01876554)

---

## Backend Deployment!

To deploy my backend application, I applied the manifest files I created. Applying a manifest file means giving Kubernetes a YAML definition of the desired state for resources, In this case, Deployment and Service which Kubernetes then creates to deploy and expose my application.

### kubectl

kubectl is the command-line tool for interacting with Kubernetes resources (like Deployment or Service resources) once the cluster is up and running. I need this tool to deploy the application by creating the Deployment and Service resources. I can't use eksctl for this job, since that tool is meant for creating and managing the cluster infrastructure itself, not the resources running inside it

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks4_6cfb382f2)

---

## Verifying Deployment

My extension for this project was to use the EKS console to verify my deployment. To do this, I had to set up IAM access, since I didn't have access to see my cluster's nodes by default. I resolved this by running the eksctl create iamidentitymapping command to map my IAM identity to the cluster's RBAC permissions

Once I gained access to my cluster's nodes, I discovered pods running inside each node. Pods are the smallest deployable unit in Kubernetes and represent a bundle of one or more containers. Containers within the same pod share networking and storage resources, which makes communication between them efficient.

The EKS console shows the events for each Pod, where I could see the container image being pulled and used to create a new container running the backend application. This confirmed that the deployment was successful and the backend was deployed.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks4_3b391f873)

---

---
