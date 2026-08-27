<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Query Data with DynamoDB

**Project Link:** [View Project](http://nextwork.ai/projects/aws-databases-query)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Query Data with DynamoDB

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-query_733d9399)

---

## Introducing Today's Project!

### What is Amazon DynamoDB?

Amazon DynamoDB is a fully managed, serverless NoSQL database service provided by AWS that stores data in key-value and document formats. It eliminates the need to provision, patch, or manage servers. It automatically scales capacity up or down to adjust for capacity and maintain performance.

### How I used Amazon DynamoDB in this project

In today's project, I used Amazon DynamoDB to create tables, load and query data using partition and sort keys, perform transactions across two tables, and manage data using AWS CLI in CloudShell.



### One thing I didn't expect in this project was...

One thing I didn't expect in this project is DynamoDB rejecting queries missing both the partition and sort keys, highlighting its strict querying requirements. The project also shows the need to have Fundamentals down.

### This project took me...

This project took me an Hour to complete. It was a fun project.

---

## Querying DynamoDB Tables

A partition key is the unique identifier in DynamoDB that dictates an item's physical storage partition for efficient data grouping and retrieval.

A sort key is a secondary attribute combined with a partition key to group, order, and filter related DynamoDB items.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-query_d105b0b0)

---

## Limits of Using DynamoDB

I ran into an error when I queried the database. This was because I left out the partition and sort keys required for DynamoDB to locate the records.

Insights we could extract from our Comment table includes querying comments by their Id and using the CommentDateTime sort key to quickly retrieve chronological feedback for specific posts.. 

Insights we can’t easily extract from the Comment table includes finding all comments from a specific user. Since PostedBy isn't a partition key, this requires a full table scan or a new index, proving why good DynamoDB data modelling is essential.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-query_cb3e260c)

---

## Running Queries with CLI

A query I ran in CloudShell used the get-item command to retrieve the Items, Title, ContentType, and Services data from the database.

Query options I could add to my query are --projection-expression to limit returned attributes, --consistent-read to guarantee strongly consistent reads, and --return-consumed-capacity to monitor read capacity unit usage.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-query_733d9399)

---

## Transactions

A transaction is an all-or-nothing sequence of operations that must entirely succeed; if a single operation fails, no changes are saved, guaranteeing data consistency across your database tables.

I ran a transaction using DynamoDB’s transactional write operation through the AWS CLI, which allows multiple write actions to be grouped into a single request. 

This transaction did two things: it added a new comment to the Comment table and updated the Forum table by incrementing the Comments count for the "Events" item.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-databases-query_2f65f83e)

---

---
