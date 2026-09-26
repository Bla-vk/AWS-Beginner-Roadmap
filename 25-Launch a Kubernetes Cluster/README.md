<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launch a Kubernetes Cluster

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-eks1)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Launch a Kubernetes Cluster

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks1_e5f6g7h8)

---

## Introducing Today's Project!

In this project, I will deploy my first Kubernetes cluster using Amazon EKS, learning what it does and why people love it along the way. This is because EKS is AWS' service for deploying Kubernetes clusters in the cloud

### What is Amazon EKS?

### One thing I didn't expect

### This project took me...

---

## What is Kubernetes?

Kubernetes is a container orchestration platform, It makes sure all your containers are running where they should, scales containers automatically to meet demand levels, and even restarts containers if something crashes. Companies and developers use Kubernetes to to deploy and manage large-scale containerized applications.

I used eksctl from the command line to create a Kubernetes cluster, specifying the cluster name, node group name, node size, AWS region, and EC2 instance type as part of the cluster configuration.


I initially encountered two errors while using `eksctl`. The first occurred because `eksctl` had not yet been installed, while the second was caused by my EC2 instance not having the necessary permissions to access my AWS account and services.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks1_ff9bfc221)

---

## eksctl and CloudFormation

CloudFormation was used to provision my EKS cluster because eksctl relies on CloudFormation behind the scenes when executing the eksctl create command. It also provisioned the required VPC resources, as deploying the EKS cluster into the default VPC could lead to compatibility and permission related issues.

There was also a separate CloudFormation stack for the node group. The key difference is that a Kubernetes cluster represents the entire Kubernetes environment, including the control plane, whereas a node group is simply a collection of EC2 instances that run workloads within the cluster.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks1_w3e4r5t6)

---

## The EKS console

I had to create an IAM access entry in order to authorize my IAM principal to query the cluster's Kubernetes API and view the nodes in my new node group (without it, `kubectl` would return an "Unauthorized" error). An access entry maps an IAM principal user or role to Kubernetes RBAC permissions, and EKS managed access policies (like `AmazonEKSViewPolicy`) determine what that principal can actually do inside the cluster. I set this up using the Access Entries page within the EKS management console.

It took at least 10 minutes to create my cluster. Since I'll be creating this same cluster again in the next project of this series, I think the overall process could be sped up by using infrastructure-as-code templates like Terraform or CloudFormation, and by scripting dependency installation ahead of time, so I spend less manual effort and reduce the chance of missed steps.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks1_e5f6g7h8)

---

## EXTRA: Deleting nodes

Did you know you can find your EKS cluster's nodes in Amazon EC2? This is because when you create nodes in a Kubernetes cluster on AWS, each node is actually an EC2 instance.

Desired size means the number of nodes you want running in your node group. Mininum and maximum sizes are helpful for maintaining app high availability at all times.

When I deleted my EC2 instances, they were instantly relaunched. This is because EKS managed node groups are backed by an EC2 Auto Scaling Group, which automatically detects that the instance count dropped below the desired capacity and launches replacement instances to restore it. Kubernetes then schedules pods onto the new nodes once they join the cluster.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-eks1_q7r8s9t0)

---

---
