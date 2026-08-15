<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Testing VPC Connectivity

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-connectivity)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Testing VPC Connectivity

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-connectivity_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon Virtual Private Cloud (VPC) is a foundational AWS service that lets you carve out a logically isolated, private section of the public AWS cloud. It essentially acts as your own virtual data center, allowing you to launch AWS resources into a virtual network that you design and control.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to test internet connectivity, establish communication between instances in public and private subnets, and troubleshoot routing issues by configuring inbound and outbound rules.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the active troubleshooting involved in connect the instances together.

### This project took me...

This project took me Approximately 1 hour.

---

## Connecting to an EC2 Instance

Connectivity means how well different parts of your network talk to each other and with external networks. Connectivity is how data flows smoothly across your network, powering everything from simple web hosting on the Internet to complex operations.

My first connectivity test was whether I could connect to EC2 instance public server.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-connectivity_88727bef)

---

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is a way to use SSH instance connect which lets you securely connect to your EC2 instances directly on the AWS management console.

My first attempt at getting direct access to my public server resulted in an error, because the security group had no rule to allow SSH traffic to go through the public EC2 instance.

I fixed this error by adding a new inbound rule to the security group, which allowed the SSH traffic to go through the public EC2 instance.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-connectivity_1cbb1b88)

---

## Connectivity Between Servers

Ping is a common diagnostic tool that checks if your system can successfully reach another device on the network. I used ping to test the connectivity between the two EC2 instances(Nextwork public server and Nextwork private server).

The ping command I ran was - ping 10.0.1.250. Which is the IPV4 address of the EC2 NextWork Private Server.

The first ping returned a single line response. This meant that your Public Server has sent out a ping message and is awaiting response.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-connectivity_defghijk)

---

## Troubleshooting Connectivity

I troubleshooted this by updating the Network ACL and Security Group, as both initially denied all traffic. Specifically, I added an inbound NACL rule for all ICMP IPv4 traffic and a Security Group rule allowing ICMP traffic from the public EC2's Security Group. This configuration enables the public instance's traffic to successfully enter the private subnet and reach the private EC2.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-connectivity_4a9e8014)

---

## Connectivity to the Internet

Curl is a command line utility used to exchange data with a server. While ping simply confirms whether a host is reachable and measures round trip time, curl allows you to test connectivity while actively pulling or pushing data across the internet.

I used curl to test the connectivity between the Public server EC2 instance and the Internet..

### Ping vs Curl

Ping and curl are different because ping simply performs basic reachability and latency checks while curl allows you to not only verify network connectivity but also actively upload or download data from remote servers.

---

## Connectivity to the Internet

I ran the curl command - curl learn.nextwork.org which returned a response with the webpage details of learn.nextwork.org.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-connectivity_8ee57662)

---

---
