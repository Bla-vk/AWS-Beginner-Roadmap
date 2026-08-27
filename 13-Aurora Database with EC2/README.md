<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Aurora Database with EC2

**Project Link:** [View Project](http://nextwork.ai/projects/aws-databases-aurora)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Connect a Web App to Amazon Aurora

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-aurora_44443546)

---

## Introducing Today's Project!

### What is Amazon Aurora?

Amazon Aurora is Amazon Aurora is a fully managed, cloud-native relational database engine that is fully compatible with MySQL and PostgreSQL and it is useful because it delivers up to 5x the throughput of standard MySQL and 3x that of standard PostgreSQL on equivalent hardware and also provides a serverless option that automatically scales database capacity up or down based on traffic demand, reducing costs for variable workloads.

### How I used Amazon Aurora in this project

In today's project, I used Amazon Aurora to deploy a relational database that stores and serves data for an EC2-hosted web application.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the vast range of specialized database engines available, extending far past standard RDBMS to include NoSQL, caching, and serverless architectures like Aurora for unique workloads.

### This project took me...

The project took me 30 minutes to complete.

---

## In the first part of my project...

### Creating an Aurora Cluster

A relational database is a type of database that organizes data into tables, which are collections of rows and columns. Kind of like an Excel spreadhsheet.

Aurora is a good choice when we have a large-scale application with peak performance and uptime. This is because Aurora databases use clusters.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-aurora_44443546)

---

## Halfway through I stopped!

I stopped creating my Aurora database because i haven't created an EC2 instance yes which is required for the project.

### Features of my EC2 instance

I created a new key pair for my EC2 instance because it serves as a cryptographic login credential (a .pem file) required to access, configure, and manage the virtual machine via SSH. it will be required later to connect to the Arora database from the EC2 Instance Connect CLI.


When I created my EC2 instance, I took particular note of the Public IPv4 DNS and the associated Key pair name (to ensure I had the correct access credentials).

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-aurora_91b9fd1g)

---

## Then I could finish setting up my database

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-aurora_1fddb0b5)

Aurora Database uses clusters because they ensure high availability and fault tolerance by grouping a write handling primary instance with multiple read replicas that share the read workload and provide automatic failover

---

---
