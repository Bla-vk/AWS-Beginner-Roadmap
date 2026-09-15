<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# APIs with Lambda + API Gateway

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-api)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-api_c9d0e1f2)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build an API without having to manage traditional servers. I'm doing this project to learn how to build APIs using API gateway and connect AWS Lambda to it. I will also be diving into the logic tier, which is all about my app's backend. This is where i'll write and run the code that translates user actions to applications functionality.

### Tools and concepts

Services I used were AWS Lambda, API Gateway. Key concepts I learnt include Lambda functions, API's,  API resources and endpoints, API documentation.

### Project reflection

This project took me about an hour to complete. The most rewarding part was gaining a clear understanding of how APIs work, along with the distinctions between an API, an API gateway, and API resources/endpoints.

Today, I chose to work on this project to learn how to build an API without managing traditional servers. Which is an essential step in understanding how to set up serverless architecture and manage APIs on AWS.

---

## Lambda functions

AWS Lambda is a service that lets you run code without needing to manage any computers/servers . I'm using Lambda in this project to run code only when i need it to avoid paying for idle time.

The code I added to my function will set up a Lambda function that retrieves data from a DynamoDB table. It looks for specific user data based on a 'userId' and returns the data. If there is an error, it returns an error message.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-api_a1b2c3d5)

---

## API Gateway

APIs are ways for different software systems to talk to each other. It's like a messenger that carries requests and responses between systems. There are different types of APIs, like REST, HTTP and, WebSocket. My API is a REST API.

Amazon API Gateway is an AWS service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale. I'm using API Gateway in this project to create an API that carries requests from a user's browser to my Lambda function.

When a user makes a request, it's received by the API gateway, which acts as the front door and passes it along to the Lambda function for handling. Lambda then processes it and returns the response back through the API gateway to the user.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-api_m3n4o5p6)

---

## API Resources and Methods

An API is made up of resources, which are individual endpoints within your API that handle different parts of its functionality.

Each resource consists of methods, which are actions you can perform on a resource. Examples are GET, ANY, DELETE, POST e.t.c

I created a GET function for the /users resource. When the  GET method is called, API Gateway will pass the request to the lambda function. When the function runs, Lambda will retrieve user data in a DynamoDB table.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-api_c9d0e1f2)

---

## API Deployment

When you deploy an API, you deploy it to a specific stage. A stage is a snapshot of your API at a specific point in time. I deployed to "New stage" with a Stage name of 'prod'.

To visit my API, I copied the Invoke URL on the prod stage page and access it on a new browser tab. The API displayed an error because i haven't set up my DynamoDB table yet.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-api_3ethryj2)

---

## API Documentation

For my project's extension, I am writing API documentation because a good documentation is crusial for developers to understand how to use the API correctly and efficiently. It is a detailed description of my API's functionality, including endpoints, parameters, and responses. You can do this in the API Gateway console, and select the documentation option under the section dedicated to the API created.

Once I prepared my documentation, I can publish it to the Stage name "prod" . You have to publish your API to a specific stage because it makes sure that your documentation is consistent with the API version deployed to that stage. This means i can write different versions of documentation across different stages of my API lifecycle.

My published and downloaded documentation showed me API's version, title, date created and many more.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-api_z9a0b1c2)

---

---
