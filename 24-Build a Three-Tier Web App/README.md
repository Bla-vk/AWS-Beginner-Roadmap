<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Three-Tier Web App

**Project Link:** [View Project](http://nextwork.ai/projects/aws-compute-threetier)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

## Build a Three-Tier Web App

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_2b3c4d5e)

---

## Introducing Today's Project!

In this project, I will demonstrate setting up a 3-tier web app from scratch. I'm doing this project to learn how to build a scalable web app with S3, CloudFront, Lambda, API Gateway, and DynamoDB.

### Tools and concepts

The AWS services I worked with were Amazon S3, CloudFront, DynamoDB, Lambda, and API Gateway. Along the way, I learned key concepts such as how Lambda functions work, how to troubleshoot CORS errors, how to update JavaScript files with the correct API Invoke URL, and how to test that Invoke URL directly in the browser.

### Project reflection

This project took me approximately 90 minutes. The most challenging part was troubleshooting the 403 error and CORS issue, since the error message (an XML response instead of JSON) made the actual cause a small typo in the URL which was hard to spot at first. It was most rewarding to see the full stack finally connect end-to-end, watching user data flow correctly from DynamoDB through Lambda and API Gateway all the way to the browser.

I chose to do this project today to learn how to set up and troubleshoot a 3-tier web app, using S3 and CloudFront for the presentation tier, Lambda and API Gateway for the logic tier, and DynamoDB for the data tier. This is part of the foundational skills I'm building for my cloud engineering learning journey.

---

## Presentation tier

For the presentation tier, I will set up an S3 bucket to store my website's files. Upload a simple index.html file and set up CloudFront to deliver my website's content globally.

I accessed my delivered website through the CloudFront distribution's URL. This works because I configured an origin access control, which allows my S3 bucket to restrict access so that only my CloudFront distribution can reach it.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_3a4b5c6d)

---

## Logic tier

For the logic tier, I will set up a Lambda function to fetch data from a DynamoDB table and create an API Gateway REST API.

The Lambda function retrieves data by searching for a userId within DynamoDB. The function code relies on the SDK, which provides templates and libraries to locate the correct DynamoDB table and pull the requested data.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_6a7b8c9d)

---

## Data tier

For the data tier, I will set up a DynamoDB table and add user data into my table.

The partition key for my DynamoDB table is 'userId,' meaning the table uses this value to locate user data during a lookup. It then retrieves all the data or attributes associated with the item matching that ID.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_u1v2w3x4)

---

## Logic and Data tier

Once all three layers of my three-tier architecture are set up, the next step is to update my index.html file to make a request to my API Gateway endpoint and display the returned data, since the frontend currently has no logic in place to actually call the API and pass along user requests.

To test my API, I navigated to the Invoke URL for the prod stage. This let me verify that the API was functional and could successfully pull user data. Looking up userId=1 returned the corresponding user data in JSON format, confirming a working connection between the logic and data tiers

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_a112c3d5)

---

## Console Errors

The error in my distributed site was because of an issue within script.js (one of the website files I'd uploaded to S3). The file was pointing to a placeholder prod stage API URL instead of my API's actual URL

To resolve the error, I replaced the placeholder text in script.js with the API's prod stage Invoke URL. I then reuploaded it to S3, since the bucket was still holding onto the previous version (the one causing the error).

I ran into a second error after updating script.js. This turned out to be a CORS (Cross-Origin Resource Sharing) issue on the browser side, since CORS wasn't set up properly in API Gateway, the browser blocked the request coming from CloudFront.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_a1b2c3d5)

---

## Resolving CORS Errors

To resolve the CORS error, I first navigated to my API Gateway and turned on CORS for the /users resource. I then confirmed GET requests were permitted, and specified my CloudFront domain as the allowed origin for access.

I also updated my Lambda function because it needs to return CORS headers so that the browser allows my frontend to read the response from the API. Without this, the browser blocks cross-origin requests even if the backend processes them successfully. To fix this, I added Access-Control-Allow-Origin as a header in the response.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_1qthryj2)

---

## Fixed Solution

I verified my fix to the API Gateway URL by clearing the browser cache and re-testing the user data lookup on the deployed site. After a hard refresh, the correct script.js loaded and the data was successfully returned, confirming that a user request in the presentation tier can retrieve data from the data tier.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-compute-threetier_2b3c4d5e)

---

---
