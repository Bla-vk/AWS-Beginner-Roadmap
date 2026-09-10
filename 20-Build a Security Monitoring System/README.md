<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Security Monitoring System

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-monitoring)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-monitoring_reghtjy)

---

## Introducing Today's Project!

In this project, I will demonstrate building a security monitoring system using logging and alerting tools. I'm doing this project to learn how to improve cloud security and monitoring, which is an essential part of cloud engineering.

### Tools and concepts

Services I used were CloudTrail, CloudWatch, SNS, IAM roles, S3 buckets and Secrets manager. Key concepts I learnt include secrets storing, CloudWatch vs CloudTrail, notifications and different kinds of endpoints, learned how to create CloudWatch filter and alarm and how to troubleshoot errors.

### Project reflection

This project took me approximately 3 hour. The most challenging part was troubleshooting why the email wasn't delivering, it was frustrating because there were no error logs to investigate, this was because the alarm was working, it was just the threshold that needed to be changed. It was most rewarding to evaluate CloudTrail alongside CloudWatch, revealing exactly when and how to deploy each service effectively.

---

## Create a Secret

Secrets Manager is an AWS security tool engineered to safeguard, manage, and retrieve sensitive assets like API keys, passwords, and database tokens. You could use Secrets Manager to safeguard your data through encryption, manage permissions via IAM policies, and lower security threats by automatically rotating credentials.

To set up for my project, I created a secret called TopSecretInfo that contains a key/value pair. This secret will be used to test access monitoring and alerting in the later steps of the project.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-monitoring_o5p6q7r8)

---

## Set Up CloudTrail

CloudTrail is a monitoring service, it records events that happened in your AWS account, like creating resources, updating a name or setting. I set up a trail to automatically collect and store logs in an S3 bucket so I can track specific events.

CloudTrail events include types like management events, data events, insight events, and network activity events.

### Read vs Write Activity

Read API activity involve querying or fetching data, such as viewing secrets or listing items. Write API activity involves modifying or creating resources, such as updating settings, adding secrets, or deleting items. For this project, we need to track Read API calls to catch anyone viewing our secret.

---

## Verifying CloudTrail

I retrieved the secret in two ways: First through the AWS Secret Manager by selecting my secret, and then clicking the “Retrieve secret value” button. Second using the AWS CloudShell and running the command "aws secretsmanager get-secret-value --secret-id "TopSecretInfo" --region eu-west-2" which displays the secret in JSON format.

To analyze my CloudTrail events, I visited the Event History tab of CloudTrail. I found two events with the GetSecretValue name, which matched the time i accessed my secret through the console and the AWS CloudShell. This tells me CloudTrail maintains detailed records of secret retrievals, providing complete visibility into the timing and method of access.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-monitoring_s8t9u0v1)

---

## CloudWatch Metrics

CloudWatch Logs is a service that helps you bring together your logs from different AWS services, including CloudTrail. It's important for monitoring because it helps with visibility, troubleshooting, and analysis of log events in near real-time.

CloudTrail's Event History is useful for tracking who did what in your AWS account,  like who created a bucket or deleted a user. While CloudWatch Logs are better for tracking what your apps and systems are doing, like error messages or performance data from your running resources.

A CloudWatch metric is a numerical representation of data points over time, used to track and analyze specific events or system performance. When setting up a metric, the metric value represents what gets recorded when our filter spots a match in the logs(1 was used to represent). Default value is used when our filter doesn't find any matches during a given time period (0 was used to represent).

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-monitoring_a9b0c1d2)

---

## CloudWatch Alarm

A CloudWatch alarm is an automated system that monitors custom metrics and reacts to specific threshold breaches across your AWS environment.. I set my CloudWatch alarm threshold to static, with the condition set to trigger whenever the "SecretIsAccessed" metric is greater than or equal to 1. so the alarm will trigger when someone fetches the secrets, instantly highlighting a security risk that demands attention.

I created an SNS topic along the way. An SNS topic is an AWS Simple Notification Service resource that acts as a communication channel for sending messages to multiple subscribers. My SNS topic is set up to  send a notification to my email whenever the CloudWatch alarm is triggered.

AWS requires email confirmation because it ensures that the recipient consents to receive notifications from the SNS topic. This helps prevent unauthorized subscriptions, spam, and unwanted messages, making sure that only verified recipients get alerted.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-monitoring_fsdghstt)

---

## Troubleshooting Notification Errors

To test my monitoring system, I retrieved the secret value again to simulate access and trigger the CloudWatch alarm. The results was the alarm detected the access event, but i did not receive any email. 

When troubleshooting the notification issues I checked CloudTrail to see if it didn't record the GetSecretValue event. Verified CloudTrail isn't sending logs to CloudWatch, which it was. Checked if CloudWatch's metric filter isn't filtering logs correctly, it filtered the logs correctly. Tested if CloudWatch's Alarm isn't triggering an action which it wasn't. I checked SNS delivery, making sure my email subscription was confirmed, and the alarm was set to notify the correct topic and recipient.

I initially didn't receive an email before because CloudWatch was configued to use the wrong threshold. The key solution was to change the threshhold from avarage to sum, this triggered the alarm and i received an email.

---

## Success!

To validate that my monitoring system can successfully detect an alarm, I checked my secrets value one more time. I received an email within 1 to 2 minutes of the event. My alarm in CloudWatch is also in alarm state.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-monitoring_ageraergearge)

---

## Comparing CloudWatch with CloudTrail Notifications

In a project extension, I configured a direct CloudTrail notification and compared it against using CloudWatch and alarms.

After enabling CloudTrail SNS notifications, my inbox was filled with multiple emails. In terms of the usefulness of these emails, I thought it is useful for security monitoring systems which creates logs that can be observed.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-monitoring_d7e8f9g0)

---

---
