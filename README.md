# AWS Beginner Roadmap ☁️

Hands-on AWS projects focused on the services and practices that cloud teams use day to day: VPC networking, IAM and security, S3 and CloudFront, Aurora and DynamoDB, serverless, Kubernetes on EKS, and CI/CD.

Most projects follow NextWork guided project formats. For each one I documented what I built, the problems I hit, and how I fixed them. Every folder is a self-contained project with its own write-up. This page lists the projects most relevant to cloud and DevOps roles.

**Beyond the guided projects:** [AWS Dev Environment with Terraform](https://github.com/Bla-vk/terraform-aws-dev-environment) is an independent project where I rebuilt a VPC and EC2 setup as code and bootstrapped Docker with `user_data`.

---

## Contents

1. [Networking and VPC](#1-networking-and-vpc)
2. [Identity, Security and Monitoring](#2-identity-security-and-monitoring)
3. [Storage and Content Delivery](#3-storage-and-content-delivery)
4. [Databases](#4-databases)
5. [Serverless and Three-Tier Architecture](#5-serverless-and-three-tier-architecture)
6. [Containers and Kubernetes (Amazon EKS)](#6-containers-and-kubernetes-amazon-eks)
7. [CI/CD and Infrastructure as Code](#7-cicd-and-infrastructure-as-code)

---

## 1. Networking and VPC

Core cloud networking: designing a VPC, controlling traffic, connecting networks and monitoring them.

| Project | What I built | Key skills |
|---|---|---|
| [Building a Virtual Private Cloud](./04-Building%20a%20Virtual%20Private%20Cloud) | Custom VPC with a CIDR block, public subnet and Internet Gateway, built in the console and again with the AWS CLI in CloudShell. | VPC, CIDR design, subnetting, Internet Gateway, AWS CLI |
| [VPC Traffic Flow and Security](./05-VPC%20Traffic%20Flow%20and%20Security) | Route tables, Security Groups and Network ACLs to control traffic, plus a second-region deployment monitored with EC2 Global View. | Route tables, Security Groups, NACLs, multi-region |
| [Creating a Private Subnet](./06-Creating%20a%20Private%20Subnet) | Private subnet with its own route table and a custom deny-all Network ACL as a zero-trust baseline. | Private subnets, route tables, NACLs |
| [Launching VPC Resources](./07-Launching%20VPC%20resources) | Public and private EC2 instances in a custom VPC with tiered Security Groups, SSH key pairs and NAT gateways across Availability Zones. | EC2, NAT gateway, SSH, high availability |
| [VPC Peering](./09-VPC%20Peering) | Two isolated VPCs connected privately with a peering connection and route tables, verified with a cross-VPC ping after fixing a Security Group rule. | VPC peering, routing, Elastic IP |
| [VPC Monitoring with Flow Logs](./10-VPC%20Monitoring%20with%20Flow%20Logs) | VPC Flow Logs delivered to CloudWatch through an IAM role, analysed with Logs Insights, including a top-10 traffic query. | Flow Logs, CloudWatch Logs Insights, IAM roles |
| [VPC Endpoints](./12-VPC%20Endpoints) | S3 Gateway Endpoint moving traffic off the public internet, locked down with an endpoint policy and a bucket policy, with allow and deny behaviour tested. | VPC endpoints, S3 bucket policies, private connectivity |

## 2. Identity, Security and Monitoring

Least privilege, encryption, secrets handling and alerting.

| Project | What I built | Key skills |
|---|---|---|
| [Cloud Security with AWS IAM](./03-Cloud%20Security%20with%20AWS%20IAM) | Tag-based least-privilege JSON policy, IAM users and groups, tested with a restricted user and the IAM Policy Simulator. | IAM, policy authoring, least privilege, Policy Simulator |
| [Encrypt Data with AWS KMS](./17-Encrypt%20Data%20with%20AWS%20KMS) | Symmetric KMS key used to encrypt a DynamoDB table, with key access tested through IAM user policies. | KMS, encryption at rest, key policies, DynamoDB |
| [Secure Secrets with Secrets Manager](./19-%20Secure%20Secrets%20with%20Secret%20Manager) | Replaced hardcoded AWS credentials in a sample app with Secrets Manager, and used an interactive Git rebase to remove secrets from commit history. | Secrets Manager, credential hygiene, Git history cleanup |
| [Build a Security Monitoring System](./20-Build%20a%20Security%20Monitoring%20System) | CloudTrail logging to S3, a CloudWatch filter and alarm, and SNS email alerts for access to a secret, including troubleshooting a missing alert. | CloudTrail, CloudWatch, SNS, alerting |

## 3. Storage and Content Delivery

Hosting and delivering content from S3.

| Project | What I built | Key skills |
|---|---|---|
| [Host a Website on S3](./02-Host%20a%20website%20on%20S3) | Static website on S3, with a 403 error fixed through object ACLs and a bucket policy that blocks deleting the site's index file. | S3 static hosting, bucket policies, ACLs |
| [Website Delivery with CloudFront](./21-Website%20Delivery%20with%20CloudFront) | Website served through CloudFront from a private S3 bucket using Origin Access Control, with load time compared against direct S3 hosting. | CloudFront, Origin Access Control, S3, CDN |

## 4. Databases

Relational and NoSQL data on AWS.

| Project | What I built | Key skills |
|---|---|---|
| [Aurora Database with EC2](./13-Aurora%20Database%20with%20EC2) | Managed Amazon Aurora cluster alongside an EC2 instance, with the reasoning behind Aurora's writer and replica architecture. | Aurora, high availability, EC2 |
| [Connect a Web App to Aurora](./14-Connect%20a%20Web%20App%20with%20Aurora) | Apache and PHP app on EC2 reading and writing employee records in Aurora, verified through the UI and direct SQL queries. | Aurora, MySQL, Apache/PHP, SQL |
| [Load Data into DynamoDB](./15-Load%20Data%20into%20DynamoDB) | DynamoDB tables created and loaded through the AWS CLI, with partition and sort keys and capacity settings. | DynamoDB, NoSQL modelling, AWS CLI |
| [Query Data with DynamoDB](./16-Query%20Data%20with%20DynamoDB) | Key-based queries and a multi-table transactional write that keeps related records consistent. | DynamoDB queries, transactions |

## 5. Serverless and Three-Tier Architecture

Building an application without managing servers.

| Project | What I built | Key skills |
|---|---|---|
| [APIs with Lambda and API Gateway](./22-API%27s%20with%20Lambda%20%2B%20API%27s%20Gateway) | REST API on API Gateway backed by a Lambda function that looks up user data in DynamoDB by user ID. | Lambda, API Gateway, REST APIs |
| [Fetch Data with AWS Lambda](./23-Fetch%20Data%20with%20AWS%20Lambda) | Lambda function reading from a DynamoDB table, with a custom inline IAM policy written from scratch. | Lambda, DynamoDB, IAM execution roles |
| [Build a Three-Tier Web App](./24-Build%20a%20Three-Tier%20Web%20App) | End-to-end app: S3 and CloudFront for presentation, Lambda and API Gateway for logic, DynamoDB for data, including a CORS and 403 issue traced to a URL typo. | S3, CloudFront, Lambda, API Gateway, DynamoDB, CORS |

## 6. Containers and Kubernetes (Amazon EKS)

Running containerised workloads on Kubernetes.

| Project | What I built | Key skills |
|---|---|---|
| [Launch a Kubernetes Cluster](./25-Launch%20a%20Kubernetes%20Cluster) | EKS cluster and node group created with eksctl (CloudFormation behind the scenes), including fixing a missing install and IAM permission errors. | EKS, eksctl, CloudFormation, IAM access entries |
| [Set Up a Kubernetes Deployment](./26-Set%20up%20Kubernetes%20Deployment) | Backend code built into a Docker image and pushed to Amazon ECR, ready for Kubernetes to pull. | Docker, Amazon ECR, EKS |
| [Create Kubernetes Manifests](./27-Create%20Kubernetes%20Manifests) | Deployment and Service manifests describing how Kubernetes runs the containerised backend. | Kubernetes manifests, Deployments, Services |
| [Deploy a Backend with Kubernetes](./28-Deploy%20Backend%20with%20Kubernetes) | Containerised backend deployed to the EKS cluster with kubectl from manifests and an ECR image. | kubectl, EKS, ECR, container deployment |

## 7. CI/CD and Infrastructure as Code

Automating build, test and deployment, and defining infrastructure in code.

| Project | What I built | Key skills |
|---|---|---|
| [Secure Packages with CodeArtifact](./31-Secure%20Packages%20with%20CodeArtifact) | CodeArtifact domain and repository with Maven Central as upstream, Maven connected, and IAM permissions for the build instance. | CodeArtifact, Maven, IAM |
| [Continuous Integration with CodeBuild](./32-Continuous%20Integration%20with%20CodeBuild) | Automated build and test with CodeBuild using buildspec.yml and a test script, connected to GitHub through a GitHub App. | CodeBuild, buildspec, CodeConnections |
| [Deploy a Web App with CodeDeploy](./33-Deploy%20a%20Webapp%20with%20CodeDeploy) | Automated deployment with appspec.yml and deployment scripts into an environment created with CloudFormation, including recovery from a failed deployment. | CodeDeploy, appspec, CloudFormation |
| [Build a CI/CD Pipeline with AWS](./34-Build%20a%20CICD%20pipeline%20with%20AWS) | CodePipeline connecting GitHub, CodeBuild and CodeDeploy so a code push updates the live app, with rollback and webhooks. | CodePipeline, CI/CD stages, rollbacks |
| [Create an S3 Bucket with Terraform](./40-Create%20an%20S3%20Bucket%20with%20Terraform) | Introduction to Terraform: provider plugins, state and lock files, and an S3 bucket provisioned from configuration. | Terraform, Infrastructure as Code, S3 |

---

## What this roadmap covers

- **Networking:** VPC design, CIDR blocks, public and private subnets, Internet and NAT gateways, route tables, VPC peering, VPC endpoints, Flow Logs
- **Security:** IAM least privilege, Security Groups, Network ACLs, KMS encryption, Secrets Manager, CloudTrail, CloudWatch alarms and SNS alerts
- **Compute:** EC2, Lambda, API Gateway, Amazon EKS with Docker, ECR and kubectl
- **Storage and delivery:** S3 static hosting, bucket policies, CloudFront with Origin Access Control
- **Databases:** Amazon Aurora (MySQL) and DynamoDB, including transactions
- **DevOps:** CodeArtifact, CodeBuild, CodeDeploy, CodePipeline, CloudFormation
- **Infrastructure as Code:** Terraform fundamentals here, plus a full VPC and EC2 build in the [Terraform project](https://github.com/Bla-vk/terraform-aws-dev-environment)
- **Tooling:** AWS Console, AWS CLI, CloudShell, eksctl, kubectl, Docker, Git and GitHub

---

## 🛠️ Tech Stack

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon VPC](https://img.shields.io/badge/Amazon%20VPC-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=flat&logo=amazons3&logoColor=white)
![AWS IAM](https://img.shields.io/badge/AWS%20IAM-DD344C?style=flat&logo=amazoniam&logoColor=white)
![Amazon Aurora](https://img.shields.io/badge/Amazon%20Aurora-527FFF?style=flat&logo=amazonrds&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-4053D6?style=flat&logo=amazondynamodb&logoColor=white)
![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=flat&logo=awslambda&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=flat&logo=terraform&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)

---

More projects, including software development work, are on my [profile](https://github.com/Bla-vk).
