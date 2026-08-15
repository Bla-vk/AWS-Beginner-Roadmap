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

### 5. [Creating a Private Subnet](./Creating%20a%20Private%20Subnet)
Built a dedicated private subnet within an existing VPC and gave it its own route table, separate from the VPC's main route table, to prevent any path to the internet gateway. Replaced the default Network ACL, which allows all traffic by default, with a custom deny-all NACL as a zero-trust baseline, requiring every port and protocol to be explicitly declared rather than open by default.

**Skills:** Private subnets, route table design, Network ACLs, zero-trust security baseline

### 6. [Launching VPC Resources](./Launching%20VPC%20Resources)
Deployed a public EC2 instance into a custom VPC's public subnet with a dedicated public Security Group, and a private EC2 instance into the private subnet with a Security Group scoped to only accept SSH traffic originating from the public instance. Set up SSH key pairs for secure instance access, and used the AWS "VPC and more" quick-create feature to provision an entire VPC topology, including subnets, route tables, and NAT gateways, in minutes while meeting high-availability standards across Availability Zones.

**Skills:** EC2 deployment, SSH key pairs, tiered Security Groups, NAT gateways, high-availability subnet design

### 7. [Testing VPC Connectivity](./Testing%20VPC%20Connectivity)
Tested and troubleshot connectivity between EC2 instances in public and private subnets, using EC2 Instance Connect, ping, and curl to diagnose issues. Resolved a blocked SSH connection by adding a missing Security Group inbound rule, and restored instance-to-instance connectivity by adding the correct Network ACL and Security Group rules for ICMP traffic.

**Skills:** Network troubleshooting, EC2 Instance Connect, Security Groups, Network ACLs, ping/curl diagnostics

---

## 🧠 What this roadmap covers end to end

- **Networking:** VPC design, CIDR blocks, public/private subnets, Internet Gateways, NAT gateways, route tables
- **Security:** Security Groups, Network ACLs, zero-trust private subnet design, least-privilege IAM policy design
- **Compute:** EC2 deployment, SSH key pairs, instance-to-instance connectivity
- **Storage:** S3 static website hosting, bucket policies, ACLs
- **Tooling:** AWS Console, AWS CLI, AWS CloudShell, IAM Policy Simulator, EC2 Global View, EC2 Instance Connect, ping/curl

---

## 🛠️ Tech Stack

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon VPC](https://img.shields.io/badge/Amazon%20VPC-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=flat&logo=amazons3&logoColor=white)
![AWS IAM](https://img.shields.io/badge/AWS%20IAM-DD344C?style=flat&logo=amazoniam&logoColor=white)

---

More projects, including software development work, are on my [profile](https://github.com/Bla-vk).
