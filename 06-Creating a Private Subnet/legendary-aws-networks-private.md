<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Creating a Private Subnet

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-private)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Creating a Private Subnet

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-private_afe1fdbd)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated network. It is useful because it lets you launch AWS resources like virtual servers and databases into a secure, custom network where you control IP address ranges, subnets, route tables, and network ACLs.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a private subnet, route tables and network ACLs that denys resources access to the public internet.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is that AWS automatically assigns new subnets to the VPC's default Network ACL, which permits all traffic. Failing to immediately swap this for a custom NACL creates a major security vulnerability, leaving your network open to lateral movement.

### This project took me...

This project took me approximately 1 hour.

---

## Private vs Public Subnets

The difference between public and private subnets is that a public subnet has route to an internet gateway while private subnet does not.

Having private subnets are useful because it reduces attack surfaces by placing sensitive and important resources i.e databases, APIs in private, makes them isolated from public internet access.

My private and public subnets cannot have the same ipv4 CIDR block because it overlaps. Overlapping CIDR block creates routing conflicts.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-private_afe1fdbd)

---

## A dedicated route table

By default, my private subnet is associated with the main vpc route table which was configured with the internet gateway.

I had to set up a new route table because there is need to seperate the private subnet from the main vpc route table to prevent internet access.

My private subnet's dedicated route table only has one inbound and one outbound rule that allows traffic to move seamlessly between resources in the VPC.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-private_b4b904b5)

---

## A new network ACL

By default, my private subnet is associated with the VPCs default network ACL which by default allows all inbound and outbound traffic.

I set up a dedicated network ACL for my private subnet because we do not want direct access to the internet gateway which will make it public. A dedicated private network ACL acts as a ststeless firewall.

My new network ACL has two simple rules - deny all inbound and outbound traffic. It establishes a zero trust base line which forces engineers to declare tthe required ports and protocol only.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-private_1ed2cb07)

---

---
