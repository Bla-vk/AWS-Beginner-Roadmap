<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Endpoints

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-endpoints)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## VPC Endpoints

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_09bcaa8a)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) provides a logically isolated network environment within AWS for deploying computing resources. It grants administrators comprehensive control over the network architecture, including IP address allocation via CIDR blocks, subnet segmentation, internet access, and traffic security policies

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to run an EC2 instance and configure both S3 and VPC endpoint policies, transitioning bucket access from a public internet route to a secure, private endpoint.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the number of policies, the endpoint policy and bucket policies.

### This project took me...

This project took me approximately 2 hours.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will create a VPC from scratch, launch an EC2 instance and set up an S3 bucket.

### Step 2 - Connect to EC2 instance

In this step, I will connect directly to my EC2 instance.

### Step 3 - Set up access keys

In this step, I will create Access keys, because it will give my EC2 instance access to my AWS environment.

### Step 4 - Interact with S3 bucket

In this step, I will get my EC2 instance to access my S3 bucket.

---

## Architecture set up

I started my project by creating a VPC and launching an EC2 instance in the VPC.

I also set up a general purpose S3 bucket and uploaded 2 files as objects.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_4334d777)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured the AWS CLI using the AWS Access key ID, Secret Access Key, Default region name, and Output format.

Access keys are credentials for your applications and other servers used to authenticate requests into AWS services.

Secret access keys are like passwords that pair with your access key ID (username) to access AWS services.

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use IAM Roles with least priviledged principle attached directly to the EC2 instance.

---

## Connecting to my S3 bucket

The command I ran was aws s3 ls.This command is used to list the S3 buckets in the AWS account.

The terminal responded with a list of available S3 buckets. This indicated that the access keys I set up worked.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_4334d778)

---

## Connecting to my S3 bucket

I also tested the command s3 ls s3://nextwork-vpc-project-precious, which returned a list of stored objects uploaded earlier.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command sudo touch /tmp/network.txt. This command creates an empty text file in a temporary directory of the Linux inctance.

The second command I ran was aws s3 cp /tmp/nextwork.txt s3://nextwork-vpc-project-precious This command will copy and upload the newly created file into the specified S3 bucket.

The third command I ran was aws s3 ls s3://nextwork-vpc-project-precious, which validated that the file was successfully uploaded.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_3e1e79a2)

---

## In the second part of my project...

### Step 5 - Set up a Gateway

In this step, I will create a endpoint. This is to setup a way for VPC to communicate directly with the S3.

### Step 6 - Bucket policies

In this step i will limit my S3 bucket access's to only traffic from my endpoint.



### Step 7 - Update route tables

In this step, I will test my VPC endpoint and troubleshoot any connectivity issue.

### Step 8 - Validate endpoint conection

In this step, I will test my VPC endpoint set up again and restrict the VPC's acccess to my AWS environment.



---

## Setting up a Gateway

I set up an S3 Gateway, which is a dedicated endpoint that modifies VPC route tables to keep S3 and DynamoDB traffic entirely off the public internet.

### What are endpoints?

An endpoint is a service that allows private connection between VPC and other AWS services without the use for public internet.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_09bcaa8a)

---

## Bucket policies

A bucket policy is an IAM policy that dictates access permissions for an S3 bucket, specifying exactly who can use it and what actions are allowed.

My bucket policy will block all external access, ensuring the S3 bucket is reachable exclusively through my specific VPC endpoint.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_7316a13d)

---

## Bucket policies

Right after saving my bucket policy, my S3 bucket page showed 'denied access' warnings. This was because the policy denies all traffic not routed through the VPC endpoint, immediately preventing console access.

I also had to update my route table because the EC2 instance's traffic still attempts to reach S3 through the public internet instead of the new endpoint.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_4ec7821f)

---

## Route table updates

To update my route table, I accessed the VPC Endpoints console and used "Manage route tables" to attach the endpoint directly to my public subnet's routing configuration.

After updating my public subnet's route table, my terminal could return the list of objects in the S3 bucket, confirming the private route works.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_d116818e)

---

## Endpoint policies

An endpoint policy is an IAM document attached directly to the VPC endpoint to restrict which AWS resources are accessible via that link.

I updated my endpoint's policy by changing the Effect from "Allow" to "Deny. I could see the effect of this right away, because running the aws s3 ls command immediately returned an "Access Denied" error, proving the endpoint gate was closed.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-endpoints_3e1e79a3)

---

---
