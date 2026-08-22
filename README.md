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

### 6. [Launching VPC Resources](./Launching%20VPC%20resources)
Deployed a public EC2 instance into a custom VPC's public subnet with a dedicated public Security Group, and a private EC2 instance into the private subnet with a Security Group scoped to only accept SSH traffic originating from the public instance. Set up SSH key pairs for secure instance access, and used the AWS "VPC and more" quick-create feature to provision an entire VPC topology, including subnets, route tables, and NAT gateways, in minutes while meeting high-availability standards across Availability Zones.

**Skills:** EC2 deployment, SSH key pairs, tiered Security Groups, NAT gateways, high-availability subnet design

### 7. [Testing VPC Connectivity](./Testing%20VPC%20connectivity)
Tested and troubleshot connectivity between EC2 instances in public and private subnets, using EC2 Instance Connect, ping, and curl to diagnose issues. Resolved a blocked SSH connection by adding a missing Security Group inbound rule, and restored instance-to-instance connectivity by adding the correct Network ACL and Security Group rules for ICMP traffic.

**Skills:** Network troubleshooting, EC2 Instance Connect, Security Groups, Network ACLs, ping/curl diagnostics

### 8. [VPC Peering](./VPC%20Peering)
Peered two isolated VPCs (NextWork-1 and NextWork-2) so their EC2 instances could communicate privately over the AWS backbone instead of the public internet, configuring unique CIDR blocks, a peering connection, and updated route tables on both sides. Resolved an EC2 Instance Connect failure caused by disabled auto-assign public IPs by attaching an Elastic IP, then validated the peering connection with a successful cross-VPC ping test after updating a security group to allow inbound ICMP traffic from the peer's CIDR block.

**Skills:** VPC peering, route table configuration, Elastic IP addresses, EC2 Instance Connect, cross-VPC security group rules

### 9. [VPC Monitoring with Flow Logs](./VPC%20Monitoring%20with%20Flow%20Logs)
Set up VPC Flow Logs to capture all inbound and outbound traffic across a two-VPC peered network, creating an IAM role and custom trust policy to grant Flow Logs permission to publish to CloudWatch. Diagnosed a failed ping test by tracing it to a missing peering connection, resolved it by configuring the peering connection and route tables, then used CloudWatch Logs Insights to query flow log data, including a top-10 byte-transfer analysis by source and destination IP.

**Skills:** VPC Flow Logs, CloudWatch, Logs Insights, IAM roles and trust policies, network traffic analysis

### 10. [Access S3 from a VPC](./Access%20S3%20from%20a%20VPC)
Launched an EC2 instance into a custom VPC and configured it to interact with an S3 bucket using the AWS CLI, setting up access keys (access key ID, secret access key, region, and output format) to authenticate the instance. Ran CLI commands to list buckets, list bucket contents, and upload a new file, validating each step's success, while noting that an IAM role with least-privilege permissions is the recommended best practice over long-lived access keys.

**Skills:** AWS CLI, IAM access keys, S3 bucket operations, EC2-to-S3 connectivity, least-privilege best practices

### 11. [VPC Endpoints](./VPC%20Endpoints)
Set up an S3 Gateway Endpoint to move an EC2 instance's S3 traffic off the public internet and onto the AWS private network, updating the public subnet's route table to direct S3-bound traffic through the endpoint. Layered a bucket policy blocking all access not routed through the specific VPC endpoint with an endpoint policy controlling which resources the endpoint could reach, then validated both allow and deny behavior by toggling the endpoint policy's Effect and confirming S3 CLI access succeeded or failed accordingly.

**Skills:** VPC Gateway Endpoints, S3 bucket policies, endpoint policies, private AWS service connectivity, access control validation

---

## 🧠 What this roadmap covers end to end

- **Networking:** VPC design, CIDR blocks, public/private subnets, Internet Gateways, NAT gateways, route tables, VPC peering, VPC endpoints
- **Security:** Security Groups, Network ACLs, zero-trust private subnet design, least-privilege IAM policy design, bucket and endpoint policies
- **Compute:** EC2 deployment, SSH key pairs, instance-to-instance connectivity
- **Storage:** S3 static website hosting, bucket policies, ACLs, private S3 access via VPC endpoints
- **Observability:** VPC Flow Logs, CloudWatch, Logs Insights queries
- **Tooling:** AWS Console, AWS CLI, AWS CloudShell, IAM Policy Simulator, EC2 Global View, EC2 Instance Connect, ping/curl

---

## 🛠️ Tech Stack

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon VPC](https://img.shields.io/badge/Amazon%20VPC-232F3E?style=flat&logo=amazonaws&logoColor=white)
![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=flat&logo=amazons3&logoColor=white)
![AWS IAM](https://img.shields.io/badge/AWS%20IAM-DD344C?style=flat&logo=amazoniam&logoColor=white)

---

More projects, including software development work, are on my [profile](https://github.com/Bla-vk).
