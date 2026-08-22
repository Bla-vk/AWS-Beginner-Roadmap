<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Access S3 from a VPC

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-s3)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Access S3 from a VPC

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-s3_3e1e79a2)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC provides a logically isolated network environment within AWS for deploying computing resources. It grants administrators comprehensive control over the network architecture, including IP address allocation via CIDR blocks, subnet segmentation, internet access, and traffic security policies.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to host an EC2 instance with a public subnet, created an Access key for my instance to access AWS services, and connected it to my S3 bucket with instance connect.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the need for Access keys which enables EC2 instances or other applications to get access to my AWS services.

### This project took me...

This project took me an hour.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, i will create a VPC from scratch and launch an EC2 instance into the VPC.

### Step 2 - Connect to my EC2 instance

In this step, I will connect directly into the EC2 instance by using AWS instance connect.

### Step 3 - Set up access keys

In this step, I will give my EC2 instance access to AWS services/environment.

---

## Architecture set up

I started my project by launching a VPC, then i launched an EC2 instance in the VPC.

I also set up a general purpose S3 bucket and uploaded 2 files.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-s3_4334d777)

---

## Running CLI commands

AWS CLI is a software that can be downloaded to a local computer terminal so we can access AWS account. I have access to AWS CLI because it preinstalled in EC2 instance.

The first command I ran was aws s3 ls. This command is used to list all S3 buckets the EC2 instance has access to.

The second command I ran was aws configure. This command is used to setup EC2 instance credentials to access and manage AWS services securely.


![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-s3_e7fa8776)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured the instance with access keys - ID and secret, default region and output format to login as the user  and access the AWS S3 bucket created.

Access keys are credentials for your applications and other servers to log into AWS and talk to AWS services.

Secret access keys are like passwords that pairs with access key ID(username) which is required to login and access AWS services.


### Best practice

Although I'm using access keys in this project, a best practice alternative is to use  IAM role with least privileage access permission.

---

## In the second part of my project...

### Step 4 - Set up an S3 bucket

In this step, I will launch a bucket in Amazon S3.

### Step 5 - Connecting to my S3 bucket

In this step, I will get my EC2 instance to interact with S3 bucket.

---

## Connecting to my S3 bucket

The first command I ran was aws s3 ls. This command is used to list all S3 buckets the EC2 instance has access to.

When I ran the command aws s3 ls, again, the terminal responded with a list of S3 bucket present. This indicated that the IAM credentials worked.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-s3_4334d778)

---

## Connecting to my S3 bucket

Another CLI command I ran was aws s3 ls s3://nextwork-vpc-project-precious, which returned a list of objects stored inside the bucket.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-s3_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command sudo touch /tmp/test.txt. This command creates an empty zero bytes text file in a /tmp/(temporary) directory.

The second command I ran was ws s3 cp /tmp/test.txt s3://nextwork-vpc-project-precious. This command will copy and upload the file into the S3 bucket.

The third command I ran was aws s3 ls s3://nextwork-vpc-project-precious, which validated that the transfer was successful and displays the files in the S3 bucket including the new text file.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-s3_3e1e79a2)

---

---
