<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-security)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a logically isolated section of the AWS Cloud where you can launch resources in a virtual network that you define and it is useful because it provides security, maintain control over IP addresses, internet gateways and security groups.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create VPC, subnets, internet gateways and also security groups, network ACLs for security.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how long and detailed it was, i thought i will be done in an hour but it took longer, had to take time to understand each steps and VPC features.

### This project took me...

This project took me approximately 2 hours.

---

## Route tables

Route tables are essential rule sets within an Amazon VPC that dictate network traffic flow. They map out the exact path the destination and the next hop so your resources can seamlessly reach other subnets or the internet.



Route tables are needed to make a subnet public because merely attaching an Internet Gateway to a VPC is not enough; you must explicitly define a route mapping external traffic (0.0.0.0/0) to that gateway so resources can successfully communicate over the internet.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Routes are defined by their destination and target, which mean the destination specifies the desired IP range (like 0.0.0.0/0 for the internet), while the target identifies the specific resource, such as a gateway or peering connection, that receives it.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 and a target of the Internet gateway attached to my VPC.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are stateful, instance level firewalls designed to govern the flow of ingress and egress traffic for AWS assets. They filter network connections using specific ports, protocols, and IP CIDR ranges, ensuring your cloud resources remain isolated from unauthorized access without sacrificing necessary operational connectivity.

### Inbound vs Outbound rules

Inbound rules are configurable policies that dictate the incoming traffic permitted to reach a resource based on its origin IP, protocol, and port. I configured an inbound rule permitting HTTP traffic (TCP port 80) from any source address (0.0.0.0/0).

Outbound rules are network policies governing the transmission of data leaving a specific resource. By default, my security group's outbound rule default state permits all traffic to any IPv4 (0.0.0.0/0) or IPv6 (::/0) destination, guaranteeing unrestricted outward communication capabilities.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are like digital security guards assigned to individual subnets within your Amazon VPC. They use a strict, numbered list of allow and deny rules checking IP addresses, ports, and protocols to control traffic flow and provide an additional layer of security alongside security groups.

### Security groups vs. network ACLs

The difference between a security group and a Network ACL is that they operate at fundamentally different scopes and states. Security groups protect individual resources (like EC2 instances) using only "allow" rules, while Network ACLs protect entire subnets using both "allow" and "deny" rules. Security groups are stateful (automatically permitting return traffic), whereas Network ACLs are stateless (requiring separate rules for inbound and outbound traffic).

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will permit all IPv4 and IPv6 traffic. Associated subnet resources can communicate freely until you restrict access with custom entries.

In contrast, a custom Network ACL's inbound and outbound rules are automatically set to a strict deny-all state. Administrators must manually configure allow rules to permit any specific communication to and from the associated subnet.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

I created additional VPC resources including a VPC, Internet gateway and Security group. Instead of my usual region, I used eu central 1 - Frankfurt. Teams would use multiple regions to improve application availability, reduce latency for users in different locations, support disaster recovery, and also meet data residency or compliance requirements.

EC2 Global View is a tool where you can find EC2 and VPC resources across all AWS regions from a dashboard. I could even narrow down my search by AWS region, resource type or resource ID.  Without EC2 Global View, you'd have to manually switch between different AWS region to locate and manage resources.

Now that I've learnt about EC2 Global View, I'd use it again to locate, monitor and manage all EC2 and VPC resources accross all regions. It is useful for auditing infrastructure, troubleshooting and managing multiple region deployments without manually switching between regions.



![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-security_b03ea6162)

---

---
