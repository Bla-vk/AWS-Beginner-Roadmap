<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Secrets with Secrets Manager

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-secretsmanager)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-secretsmanager_r7s8t9u0)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use AWS Secrets Manager to securely store and retrieve secrets.. I'm doing this project to learn a better way to store and retrieve credentials using AWS Secrets Manager.

### Tools and concepts

Services I used were. AWS Secrets Manager and GitHub. Key concepts I learnt include securely storing and accessing confidential data such as AWS credentials through Secrets Manager, along with managing and cleaning up commit history using Git and GitHub tools. I also gained experience using interactive rebasing to eliminate sensitive data, resolve merge conflicts, and make sure secrets are never exposed in version control.

### Project reflection

This project took me approximately 2 hours to complete. The most challenging part was resolving the commit conflict. It was most rewarding to see how AWS Secrets Manager works, knowing that the credentials were now stored and accessed securely, following best practices.

I chose to do this project today to improve my Git proficiency and understand how to safely handle secrets in AWS. Through it, I gained practical knowledge of securely managing sensitive credentials, preventing accidental exposure of confidential data in version control, and hands on skill in resolving merge conflicts and tidying up commit history.

---

## Hardcoding credentials

In this project, a sample web app is exposing AWS credentials publicly in its code. It is unsafe to harcode credentials because it can lead to data breaches, unauthorized access and unexpected changes to your AWS account.

I've set up the initial configuration with an AWS Access Key and AWS Secret Access Key in the config.py file. These credentials are just examples because it's easier and safer to use than real credentials that would expose your account to security risks.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-secretsmanager_j2k3l4m5)

---

## Using my own AWS credentials

As an extension for this project, I also decided to set up my virtual environment, I installed essential packages to support FastAPI development, it also supports dependencies and package management.

When I first ran the app, I ran into an error because we are using placeholder credentials which are not real AWS credentials. It gave a JSON response saying "{"error":"An error occurred (InvalidAccessKeyId)..."}", which means the AWS Access Key ID provided is not valid.

To resolve the 'InvalidAccessKeyId' error, I updated the Access Key ID, secret access key and the AWS region where my S3 bucket is present.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-secretsmanager_wghjteykut)

---

## Pushing Insecure Code to GitHub

Once I updated the web app code with credentials, I forked the repository because i wanted to make changes while still linking it to the original project. A fork is different from a clone because it creates a server side copy of a repository in my personal GitHub account, while a clone downloads a local copy of a repository to my computer's hard drive

To connect my local repository to the forked repository, I used "git remote add origin" to link the local repository with the GitHub forked one. Then I used git add and git commit to stage changes by telling Git the files to include in the next commit message. Finally, git push uploads the commit changes to the GitHub repository, which gave an error that "Push cannot contain secrets" , indicating sensitive data like API keys or passwords in my commit.

GitHub blocked my push because it detected AWS credentials in my commit. This is a good security feature because it prevents the accidental uploads of sensitive data such as, Access keys, API keys. This prevents unauthorized AWS access, protecting against security breaches, data loss, and unexpected costs.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-secretsmanager_o2p3q4r5)

---

## Secrets Manager

Secrets Manager is a service that helps you securely store and manage secrets, such as database credentials, API keys, and other sensitive information. I'm using it to store AWS access key and secret access key so they can be accessed securely by applications or services without hardcoding them. Other common use cases include storing database credentials, API tokens, and encryption keys.

Another feature in Secrets Manager is. secrets rotation, which means the process of automatically changing your secrets on a regular schedule. It's useful in situations where security best practices require frequent credential changes, such as in production environments, to reduce the risk of long term exposure from compromised credentials.

Secrets Manager provides sample code in various languages, like java. python, .Net, Go and Rust. This is helpful because it makes it easier for developers to quickly integrate the secure secret retrieval into their applications without needing to build the logic.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-secretsmanager_h2i3j4k5)

---

## Updating the web app code

I updated the config.py file to retrieve credentials from AWS Secrets Manager instead of hardcoding them. The get_secret() function will connect to Secrets Manager via the boto3 client to fetch the "aws-access-key" secret from a designated AWS region, parse its JSON structure, and subsequently extract and return essential parameters like username, password, host, and database name.

I also added code to config.py to extract individual credentials from the retrieved secret. This is important because our configuration file no longer has hardcoded credentials inside. 

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-secretsmanager_v0w1x2y3)

---

## Rebasing the repository

Git rebasing is a way to rewrite commit history by changing, reordering, or removing commits.. I used it to remove a commit that includes hardcoded AWS credential. This was necessary because it removes the git push conflict of the updated config.py file.

A merge conflict occurred during rebasing because Git could not automatically reconcile changes made to the commit i was rebasing and existing commits. I resolved the merge conflict by opening the conflicted file,  and manually choosing the correct code between the conflict markers (<<<<<<<, =======, >>>>>>>), then saving the file with the correct content.

Once the merge conflict was resolved, I verified that the hardcoded credentials were out of sight in the repository

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-secretsmanager_t5u6v7w8)

---

---
