<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-vpc)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build a Amazon Virtual Private Cloud (VPC). I'm doing this project to learn how to setup a VPC, public subnets and network Gateway.

### What is Amazon VPC?

### Personal reflection

---

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I will setup a VPC in AWS console.

### How VPCs work

VPCs are Virtual Private Cloud that isolate and make resources private, it helps seperate and organize your cloud. VPC gives control over how our resources are connected to the public internet.

### Why there is a default VPC in AWS accounts

There was already a default VPC in my account ever since my AWS account was created. This is because AWS sets up all resources to private and secured from day 1 of using it. AWS automatically sets up a default VPC which enables you to launch resources e.g. EC2 instances, and connect services together.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-vpc_2facf927)

### Defining IPv4 CIDR blocks

To set up my VPC, I had to define an IPv4 CIDR block, which is a way to assign a whole block of Ip addresses. It specifies the number of bits i will be using for the network and also the server host. The smaller the CIDR number, the more the IPV4 addresses possible.

---

## Subnets

### What I did in this step

In this step, I will setup a subnet inside my VPC because it will help seperate and organize how the VPC will be used.

### Creating and configuring subnets

Subnets are like different neighborhoods inside your city. There are already subnets existing in my account, one for every availability zone in my region.

### Public vs private subnets

The difference between public and private subnets are public subnets and connected to the internet while private subnets are not by default. For a subnet to be considered public, it has to be connected to a internet gateway.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-vpc_157c4219)

### Auto-assigning public IPv4 addresses

Once I created my subnet, I enabled IPV4 address. This setting makes sure that IP address and assigned automatically, so that i do not need to create one manually.

---

## Internet gateways

### What I did in this step

In this step, I will create an Internet gateway because it will give access to the internet and can connect to other servers outside of my VPC. It enables my resources to communicate beyond my private space.

### Setting up internet gateways

Internet gateways are access to the outside world. It connects your VPC to the internet.

Attaching an internet gateway to a VPC means connecting our VPC to the internet, it gives access. If I missed this step i will have no access to the internet through the internet gateway.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

### What I'm doing in this extension

In this project extension, I will make use of AWS Cloudshell to run AWS CLI commands, it will be used to setup a VPC, subnet and Internet gateway.

### Exploring CloudShell and CLI

VPC resources could also be created with CloudShell, which is is a shell in AWS management console. CLI is the command Line Interface that allows you to perform actions by running commands.

### Debugging my setup

To set up a VPC or a subnet, you can use the command aws ec2 create-subnet --vpc-id<vpc-id> --cidr-block<10.0.0.0/16>. Make sure to avoid errors by including the correct subnet that is within your VPC IP CIDR.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-vpc_9b2465411)

### Comparing CloudShell vs AWS Console

Compared to using the AWS Console, an advantage of using commands is much faster. An advantage of using the Console is that you can manually setup everything and have more control. Overall, I preferred using CLI.

---

---
