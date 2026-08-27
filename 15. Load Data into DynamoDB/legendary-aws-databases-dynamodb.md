<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Load Data into DynamoDB

**Project Link:** [View Project](http://nextwork.ai/projects/aws-databases-dynamodb)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Load Data into a DynamoDB Table

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-dynamodb_b481c730)

---

## Introducing Today's Project!

### What is Amazon DynamoDB?

Amazon DynamoDB is a fully managed, serverless NoSQL database service provided by AWS that stores data in key-value and document formats. It delivers consistent, single-digit millisecond response times regardless of how large the database grows or how many requests are made.

### How I used Amazon DynamoDB in this project

I used Amazon DynamoDB in today’s project to create tables, load data using AWS CloudShell, view and update items.

### One thing I didn't expect in this project was...

One thing I didn’t expect in this project was the sheer ease of using AWS CloudShell, which made DynamoDB CLI execution and table management incredibly straightforward.

### This project took me...

This project took me an hour.

---

## Create a DynamoDB table

DynamoDB tables organize data using items (rows) and attributes (columns), uniquely indexing each record via a primary key that comprises a partition key and an optional sort key for sophisticated data retrieval.

An attribute is a single field within a DynamoDB item, equivalent to a column, that holds data like strings or numbers to structure an item.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-dynamodb_a3cefee0)

---

## Read and Write Capacity

Read capacity units (RCUs) and write capacity units (WCUs) are throughput allocation metrics in Amazon DynamoDB; RCUs quantify a table's strongly consistent read capacity per second, whereas WCUs regulate its write capacity.

Amazon DynamoDB's Free Tier covers 25 RCUs, 25 WCUs, and 25GB of storage per month. I turned off auto scaling because i want to control the Read and Write capacity to better understand how throughput affects performance and cost.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-dynamodb_ef47dd8f)

---

## Using CLI and CloudShell

AWS CloudShell is an AWS console based, preconfigured command line environment that lets you securely manage AWS resources using the AWS CLI(Command Line Interface), without needing to install locally.



AWS CLI is a command-line tool used to manage AWS resources and automate operations directly from your terminal or CloudShell.

I ran a CLI command in AWS CloudShell that created four tables which are, ContentCatalog (Id), Forum (Name), Post (ForumName, Subject), and Comment (Id, CommentDateTime).

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-dynamodb_81e0258b)

---

## Loading Data with CLI

I ran a CLI command in AWS CloudShell that loaded all the data into the DynamoDB tables previously created.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-dynamodb_791c600b)

---

## Observing Item Attributes

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-dynamodb_b481c731)

I checked a ContentCatalog item, which had the following attributes: Id, Authors, ContentType, Difficulty, Price, ProjectCategory, Published, and Title, all of which outline the essential project details stored within the DynamoDB table.

I checked another ContentCatalog item, which had a different set of attributes: Id, ContentType, Price, Services, Title, URL, and VideoType for a video resource, unlike an earlier DynamoDB project item that featured Authors, Price, and Published.

---

## Benefits of DynamoDB

A benefit of DynamoDB over relational databases is flexibility, because it enables individual items to maintain distinct attribute sets, bypassing the rigid column constraints mandated by relational systems.

Another benefit over relational databases is speed, because DynamoDB leverages partition keys for instant item lookups, bypassing the slow full table scans of relational systems..

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-dynamodb_b481c730)

---

---
