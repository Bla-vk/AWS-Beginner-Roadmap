<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Peering

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-peering)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## VPC Peering

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-peering_88727bef)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a private, dedicated virtual network within your AWS account that functions much like a traditional on-premises data center and it is useful because it gives complete control over your AWS networking environment.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to peer two isolated networks (NextWork-1 and NextWork-2), configuring route tables and security groups so EC2 instances could communicate privately without using the public internet.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the EC2 Instance Connect connection failure caused by disabling auto-assign public IPs, which prevented my instance from acquiring a public IPv4 address.

### This project took me...

This project took me an hour to complete.

---

## In the first part of my project...

### Step 1 - Set up my VPC

In this step, I will create two VPCs which are (NextWork-1 and NextWork-2) using the VPC and more wizard because we need distinct, isolated network environments with unique IPv4 CIDR blocks to prevent IP conflict and prepare for a secure VPC peering connection.

### Step 2 - Create a Peering Connection

In this step, I will setup a connection link between the two VPCs, ecause they need to successfully communicate with eachother.

### Step 3 - Update Route Tables

In this step, I will set up a way for traffic coming fromVPC 1 to get to VPC 2 and vis versa because it is needed for traffic in my VPCs.

### Step 4 - Launch EC2 Instances

In this step, I will launch an EC2 instance in each VPC. because i can use them to test VPC peering connection later.

---

## Multi-VPC Architecture

I started my project by launching two separate VPCs (NextWork-1 and NextWork-2) using the VPC and more wizard, creating 1 public subnet and 0 private subnets in each VPC.

The CIDR blocks for VPCs 1 and 2 are 10.1.0.0/16 and 10.2.0.0/16. They have to be unique because overlapping IPv4 CIDR blocks would cause routing conflicts and prevent the VPCs from successfully communicating with each other.

### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as AWS seamlessly manages them through EC2 Instance Connect, eliminating the need to repeat the manual configuration steps covered in previous projects.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-peering_11111111)

---

## VPC Peering

A VPC peering connection is a private link between two Virtual Private Clouds that routes IPv4 or IPv6 traffic, allowing resources to communicate seamlessly as a single network without exposing data to the public internet.

VPCs would use peering connections to securely exchange data between separate networks via private IPs, keeping all traffic entirely on the AWS backbone instead of the public internet.

The difference between a Requester and an Accepter in a peering connection is the Requester initiates the network link, while the Accepter is responsible for receiving and approving the request to make it operational.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-peering_1cbb1b88)

---

## Updating route tables

After accepting a peering connection, my VPCs' route tables need to be updated because explicit routing rules must be established to direct traffic between the two isolated networks.

My VPCs' new routes have a destination of other VPC's CIDR block (10.2.0.0/16 for VPC 1 and 10.1.0.0/16 for VPC 2). The routes' target was the VPC peering connection (VPC 1 <> VPC 2).

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-peering_4a9e8014)

---

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

In this step, I will use EC2 Instance Connect to connect to my first EC2 instance and fix a connection error.

### Step 6 - Connect to EC2 Instance 1

In this step, I will use EC2 Instance connect to connect to the first instance again and fix any error that surfaces.

### Step 7 - Test VPC Peering

In this step, I will get Instance 1 to send test messages to Instance 2 and solve any connection errors.

---

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect to securely access my first EC2 instance (Instance - NextWork VPC 1) from the browser.

I was stopped from using EC2 Instance Connect as we disabled public IPs during launch, so I attached an Elastic IP to provide the static address required for browser access

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-peering_7685490c)

---

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are static IPv4 addresses that remain assigned to your AWS account even when instances stop, allowing for consistent and persistent remote access.

Associating an Elastic IP address resolved the error because it allocated a static public IP to the EC2 instance, fulfilling the prerequisite for EC2 Instance Connect to establish a secure connection and bypassing the previous restriction

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-peering_45663498)

---

## Troubleshooting ping issues

To test VPC peering, I ran the command ping 10.2.5.222.

A successful ping test would validate my VPC peering connection because it proves the traffic can travel across the private network boundaries of the two separate VPCs using their private IP addresses.

I had to update my second EC2 instance's security group because its default rule rejects incoming ICMP pings from external networks. I added a new rule that accepts inbound ICMP - IPv4 traffic from the 10.1.0.0/16 CIDR block, ensuring the security group grants access to incoming ping requests.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-peering_7a29d352)

---

---
