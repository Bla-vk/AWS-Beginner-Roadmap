# AWS Beginner Roadmap ☁️

A hands-on journey through foundational AWS services, built through structured guided projects covering networking, storage, and identity and access management.

Each folder in this repo is a self-contained project with its own write-up.

---

## 📁 Projects in this repo

### 1. [Building a Virtual Private Cloud](./Building%20a%20Virtual%20Private%20Cloud)
Built a custom Amazon VPC from scratch, including defining an IPv4 CIDR block, creating public subnets with automatic public IP assignment, and attaching an Internet Gateway for outbound connectivity. Extended the project by provisioning the same VPC, subnet, and Internet Gateway setup using the AWS CLI through CloudShell, comparing console-based and command-line infrastructure workflows.

**Skills:** Amazon VPC, CIDR block design, subnetting, Internet Gateways, AWS CLI, AWS CloudShell

### 2. [VPC Traffic Flow and Security](./VPC%20Traffic%20Flow%20and%20Security)
Configured route tables to direct internet-bound traffic to an Internet Gateway, completing the routing layer needed to make a subnet public. Set up Security Group inbound/outbound rules to control HTTP traffic at the instance level, and implemented Network ACLs as a stateless, subnet-level layer of defense alongside them. Deployed additional VPC resources in a second AWS region (Frankfurt) and used EC2 Global View to monitor resources across regions.

**Skills:** Route tables, Security Groups, Network ACLs, multi-region deployment, EC2 Global View

### 3. [Host a Website on S3](./Host%20a%20website%20on%20S3)
Deployed a static website on Amazon S3, configuring the bucket, uploading site files, and enabling static website hosting with a live public endpoint. Diagnosed a 403 Forbidden error by identifying that object-level permissions, not just bucket-level public access settings, controlled visibility, and resolved it by updating object ACLs. Extended the project with a bucket policy denying deletion of the site's index.html file, validated by confirming a blocked delete attempt.

**Skills:** Amazon S3, static website hosting, bucket policies, ACLs, permissions troubleshooting

### 4. [Cloud Security with AWS IAM](./Cloud%20Security%20with%20AWS%20IAM)
Provisioned and tagged multiple EC2 instances (production and development) and authored a JSON IAM policy restricting a simulated user to development-tagged resources only. Created IAM users, groups, and an account alias, attaching policies at the group level to enforce scoped access control. Validated the setup end to end: confirmed a restricted IAM user was denied access to the production instance while development actions succeeded, then used the IAM Policy Simulator to test and refine permission scope without disrupting live resources.

**Skills:** AWS IAM, JSON policy authoring, least-privilege access design, IAM Policy Simulator, resource tagging

---

## 🧠 What this roadmap covers end to end

- **Networking:** VPC design, CIDR blocks, public/private subnets, Internet Gateways, route tables
- **Security:** Security Groups, Network ACLs, least-privilege IAM policy design
- **Storage:** S3 static website hosting, bucket policies, ACLs
- **Tooling:** AWS Console, AWS CLI, AWS CloudShell, IAM Policy Simulator, EC2 Global View

---

## 🛠️ Tech Stack

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon VPC](https://img.shields.io/badge/Amazon%20VPC-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=flat&logo=amazons3&logoColor=white)
![AWS IAM](https://img.shields.io/badge/AWS%20IAM-DD344C?style=flat&logo=amazoniam&logoColor=white)

---

More projects, including software development work, are on my [profile](https://github.com/Bla-vk).
