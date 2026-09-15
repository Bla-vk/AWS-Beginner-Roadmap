<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Fetch Data with AWS Lambda

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-lambda)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Fetch Data with AWS Lambda

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-lambda_p9thryj2)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use a serverless AWS Lambda function to retrieve data from a DynamoDB table.. I'm doing this project to learn how to create scalable cloud solutions that handle large amounts of data efficiently.

### Tools and concepts

Services I used were Amazon DynamoDB and AWS Lambda. Among the key concepts I picked up were working with Lambda functions, inserting items into tables, testing Lambda functions, choosing the appropriate permission policies, and creating custom inline policies.

### Project reflection

This project took me approximately 40 minutes. The trickiest part was crafting my own inline policy from scratch. The most satisfying moment was watching the correct data appear after the function test ran successfully.

Today, I worked on this project to understand the data tier within a 3-tier architecture and learn how to integrate it with AWS Lambda, which serves as the logic tier.

---

## Project Setup

To set up my project, I created a database using DynamoDB with table name UserData. The partition key is userId, which is the heart of how DynamoDB organizes data.

In my DynamoDB table, I added some user data. Since DynamoDB is schemaless, the data I add can include new attributes freely, and each item can have its own unique set of attributes without affecting the others.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-lambda_a112c3d5)

### AWS Lambda

AWS Lambda is a service that lets you run code without needing to manage any computers/servers. I'm using Lambda in this project to create a function.

---

## AWS Lambda Function

My Lambda function has an execution role, which is an IAM role for your Lambda function. It defines what the function is allowed to do. By default, the role grants basic permissions for writing logs to CloudWatch.

My Lambda function retrieves data from a DynamoDB database table. The first half of the code handles the data retrieval, while the second half manages any errors that occur during the database operation, providing a tailored error message that explains exactly what went wrong.

The code uses AWS SDK, which is a set of tools that let developers build apps that interact with AWS. My code uses SDK to use pre-written functions for communicating with DynamoDB and getting data from a table.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-lambda_a1b2c3d5)

---

## Function Testing

To test whether my Lambda function works, I wrote a function test in the Test tab in the Lambda console. The test is written in JSON. If the test is successful, I'd see 'Executing function: succeeded'.

The test showed 'success' because the function executed without any code level errors (no syntax or dependency issues), but the actual response returned was an error. My Lambda function was attempting to retrieve data from DynamoDB but lacked the necessary permissions to access it.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-lambda_u1v2w3x4)

---

## Function Permissions

To fix the AccessDenied error, I'm granting my Lambda function permission to perform the GetItem action on a DynamoDB table, since GetItem is the specific action Lambda is currently blocked from performing and it's the root cause of the error.

There were four DynamoDB permission policies I could choose from, but I ruled out "AWSLambdaDynamoDBExecutionRole" and "AWSLambdaInvocation-DynamoDB" since neither includes the 'GetItem' permission."

I also didn't pick AmazonDynamoDBFullAccess or AmazonDynamoDBFullAccess_v2, since they'd grant my Lambda function excessive permissions over the table. AmazonDynamoDBReadOnlyAccess was the better option since it protects the table from unauthorized modifications via Lambda.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-lambda_3ethryj2)

---

## Final Testing and Reflection

To validate my new permission settings, I re-ran my Lambda test function, and it executed successfully, confirming that the updated permissions were correctly configured.

Web apps are a popular use case for combining Lambda and DynamoDB. For instance, I could use it to look up product details by pulling data from DynamoDB. It can also retrieve user profiles or content based on user queries within a web app.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-lambda_p9thryj2)

---

## Enahancing Security

For my project extension, I challenged myself to work with an inline policy rather than a managed one, such as AmazonDynamoDBReadOnlyAccess. This restricts our Lambda function's access to only the UserData table, making the inline policy the more secure choice.

To create the permission policy, I opted for the JSON method since it deploys faster and helps build familiarity with how it's actually done in live production/cloud environments.

When updating a Lambda funciton's permission policies, there's a risk of losing access to the resources or actions it depends on. I confirmed my Lambda function was still working by re-testing it after making the policy updates, and it performed as expected.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-lambda_1qthryj2)

---

---
