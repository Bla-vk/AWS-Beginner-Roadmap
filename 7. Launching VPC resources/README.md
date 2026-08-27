<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-ec2)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Launching VPC Resources

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated network. It is useful because it lets you launch AWS resources like virtual servers and databases into a secure, custom network where you control IP address ranges, subnets, route tables, and network ACLs.

### How I used Amazon VPC in this project

I used Amazon VPC to deploy compute resources EC2 instances, secure them wit specific security groups. I also practices setting up a new network in minutes.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the creation of two different VPCs with the same IPV4 CIDR (IP range), and aslo create an entire network in minutes

### This project took me...

This project took me approximately 90 minutes.

---

## Setting Up Direct VM Access

Directly accessing a virtual machine means securely connecting to its operating system to handle configurations, inspect logs, and perform advanced troubleshooting beyond what the AWS Management Console allows.

### SSH is a key method for directly accessing a VM

SSH traffic means secure, encrypted communication over TCP port 22 that safely delivers commands and credentials between a client and remote server, effectively protecting against network sniffing and man-in-the-middle attacks.

### To enable direct access, I set up key pairs

Key pairs are asymmetric cryptographic credentials used to authenticate an SSH connection. SSH key pairs provide secure login using two linked keys: a public key stored on the EC2 instance and a private key kept safely on your device. During connection, the server confirms your identity by testing whether your computer holds the matching private key.

A private key's file format means the specific way cryptographic data is encoded and saved for SSH clients to read. My private key's file format was .pem (Privacy-Enhanced Mail), the widely supported standard for managing cryptographic keys on Unix/Linux systems.

---

## Launching a public server

I had to change my EC2 instance's networking settings by bypassing the default AWS VPC and launching it directly into my custom NextWork VPC. I placed it in the NextWork Public Subnet and attached the NextWork Public Security Group to ensure it received a public IP and the correct firewall rules.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because it operates in a different trust tier than the public server.

My private server's security group's source is he NextWork Public Security Group, which means the private instance will only accept incoming SSH connections if the traffic originates from an EC2 instance that holds that specific public security group.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC! This time, I chose the "VPC and more" feature to instantly generate the entire network topology, automating the creation of subnets, route tables, and gateways for much faster provisioning.

A VPC resource map is an interactive AWS Console visualizer that displays live connections between network components, instantly showing how subnets link to route tables and route traffic through Internet or NAT Gateways.

My new VPC has a CIDR block of 10.0.0.0/16. It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC because AWS VPCs are isolated, standalone network environments. As long as  i don't attempt to connect them, the overlapping IP ranges will never conflict.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options: 0 or 2. This was because the AWS setup automatically applies High Availability (HA) standards, distributing resources across multiple Availability Zones so your system remains resilient and accessible even if a data center fails.

The set up page also offered to create NAT gateways, which are managed public subnet devices that enable private instances to access the internet while blocking unsolicited inbound connections.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-ec2_8ee57662)

---

---
