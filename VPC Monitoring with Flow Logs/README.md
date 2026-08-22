<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Monitoring with Flow Logs

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-monitoring)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## VPC Monitoring with Flow Logs

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_3e1e79a1)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a logically isolated, private network space within AWS where you deploy resources like EC2 instances, databases, and Lambda functions, giving you complete control over your IP ranges, subnet architecture, internet connectivity, and traffic flow.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create 2 VPCs, peer them and troubleshoot the peering issues. Also viewed the traffic logs on CloudWatch using VPC Flow Logs.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was it being more technical than previous projects, a lot to learn. Took me a while to complete.

### This project took me...

This project took me 2 hours to complete.

---

## In the first part of my project...

### Step 1 - Set up VPCs

In this step, I will create 2 VPCs from scratch. Network monitiring can be done with a single VPC but this is an opportunity to revise VPC Peering.

### Step 2 - Launch EC2 instances

In this step, I will launch an EC2 instance in each VPC, so i can use them to test VPC peering connection later.

### Step 3 - Set up Logs

In this step, I will set up a way to track al inbound and outbound traffic and setup a space that tracks these records.

### Step 4 - Set IAM permissions for Logs

In this step, I will give VPC Flow Logs the permission to write logs and send them to CloudWatch.

---

## Multi-VPC Architecture

I started my project by launching 2 VPCs with 1 Availability zone each and a public subnet.

The CIDR blocks for VPCs 1 and 2 are 10.1.0.0/16 and 10.2.0.0/16. They have to be unique because they distinguish two different networks and ensures resources don't overlap.

### I also launched EC2 instances in each subnet

My EC2 instances' security groups allow All ICMP IPv4 traffic. This is because we need to test the connection between each VPCs and also from any internet source. 

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_e7fa8775)

---

## Logs

Logs serve as a comprehensive record of all VPC instance activity, detailing every allowed or rejected action, the identity of the user, the timestamp, and the final outcome. 

Log groups are AWS folders used to group logs from the same source, and though they are strictly region-specific, CloudWatch dashboards allow for cross-region aggregation.

### I also set up a flow log for VPC 1

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_e8398869)

---

## IAM Policy and Roles

I created an IAM policy because VPC Flow Logs doesn't have the permission to write logs and send them to CloudWatch yet. So i needed to give VPC Flow Logs the permission to do so by using IAM roles and policies.

I also created an IAM role because services like VPC Flow Logs require one to obtain the necessary permissions to record and publish log data.

A custom trust policy is like a guardrail specifying who can assume an IAM role, unlike standard IAM policies that define which actions a user or service can perform.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_4334d777)

---

## In the second part of my project...

### Step 5 - Ping testing and troubleshooting

In this step, I will get EC2 instance 1 to send test messages to instance 2.

### Step 6 - Set up a peering connection

In this step, I will setup a connection link between the 2 VPCS by creating a peering connection and configure route tables.

### Step 7 - Analyze flow logs

In this step, I will review and analyse the flow logs recorded about VPC 1's public subnet.

---

## Connectivity troubleshooting

My first ping test between my EC2 instances had no replies, which means there is a problem with security group or Network ACLs rules.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_99d4ba42)

I could receive ping replies if I ran the ping test using the other instance's public IP address, which means ICMP traffic is allowed by the public(internet) traffic.

---

## Connectivity troubleshooting

Looking at VPC 1's route table, I identified that the ping test with Instance 2's private address failed because no peering connection was setup between both instances.

### To solve this, I set up a peering connection between my VPCs

I also updated both VPCs' route tables so that the traffic bound for the other VPC can be directed to the peering connection .

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_7316a13d)

---

## Connectivity troubleshooting

I received ping replies from Instance 2's private IP address! This means the peering connection was successful.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_4ec7821f)

---

## Analyzing flow logs

Flow logs tell us about the source and destination, the size of data packet sent and the action that took place (ACCEPT/REJECT) within the flow log.

For example, the flow log I've captured tells us that instance 2 could not communicate with instance 1 and was rejected.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_d116818e)

---

## Logs Insights

Logs Insights is a CloudWatch feature that lets you query, filter, and analyze log data to troubleshoot issues and analyze network traffic patterns.

I ran the query "Top 10 byte transfers by source and destination IP addresses". This query analyzes the flow logs collected on EC2 Instances and it returns the top 10 pairs of IP addresses based on the amount of data transferred between them.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-networks-monitoring_3e1e79a1)

---

---
