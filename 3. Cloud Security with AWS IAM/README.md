<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-iam)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate Cloud security with AWS by using the AWS Identity and Access Management (IAM). I'm doing this project to learn about clound security and the use of EC2 instances.

### Tools and concepts

Services I used were EC2 and AWS IAM. Key concepts I learnt include IAM users, Policy role, user groups, account aliases, launching instances, tagging instances, log-in as another user, policy simulator and JSON policy.

### Project reflection

This project took me approximately 1 hour. The most challenging part was learning to use the policy simulator. It was most rewarding to see the IAM policy in action when the intern tried to delete the production instance.

---

## Tags

### What I did in this step

In this step, I will launch two EC2 instances because i need to increase Nextwork's computing power to match increased traffic to the website.

### Understanding tags

Tags are organizational tools that lets us label our resources. It helps with grouping resources, cost allocation and applying policies to all resourses of the same tag.

### My tag configuration

The tag I’ve used on my EC2 instances is called Environment. The value I’ve assigned for my instances are production and development.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will use IAM policies to control the access level of a new intern, because they should have access to the development environment but not the production environment.

### Understanding IAM policies

IAM Policies are rules that determine who can do what in our AWS account.

### The policy I set up

For this project, I’ve set up a policy using JSON. i'm using policy to control who has access to production or environment instances.

### Policy effect

I’ve created a policy that allows the policy holder to have permissions to do anything they want to any instance tagged with development, can also see information related to any instance but denied access to deleting or creating tags.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy means whether the policy is allowing or denying actions which is the effect and what the policy holder can or cannot do which is the action and the AWS resources thst the policy relates to that is the resource.

---

## My JSON Policy

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will set up an account alias which is a nickname for an AWS account console login. This is because an account alias makes it simpler for our user to login.

### Understanding account aliases

An account alias is simply a nickname for our AWS account instead of a long account id,  we can now reference our account alias instead.

### Setting up my account alias

Creating an account alias took me 20 secs. Now, my new AWS console sign-in URL uses the alias instead of my account id.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I will set up IAM user and IAM user groups because IAM users are logins for people that want access to our AWS account while user groups are folders to manage users with the same level of access.

### Understanding user groups

IAM user groups are folders that collect IAM users so that you can apply permission settings at the group level.

### Attaching policies to user groups

I attached the policy I created to this user group, which means any user created inside the group will automatically get the permissions attached to IAM policy.

### Understanding IAM users

IAM users are people that have access and can login to your AWS account.

---

## Logging in as an IAM User

### Sharing sign-in details

The first way is to email sign-in instructions to the user while the second way is to download he csv file with the sign-in details inside.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that our user is denied access to panels on the main AWS console dashboard. This was because i only set up permission to EC2 development instance so the intern wont have access to anything else.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will log-in to AWS as the intern and test access to the production and development access, because we want to make sure our intern dosen't have the ability to do anything that can affect our production environment.

### Testing policy actions

I tested my JSON IAM policy by trying to stop the development and production instances.

### Stopping the production instance

When I tried to stop the production instance, i was met with an error. This was because our production instance is tagged with a production label which is not included in the permission policy, interns are only allowed to work on the development instance.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, the instance state change to stopping and then stopped. This was because the permission policy allows the intern to stop the development instances.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my project, I'm going to test the permission policy in a safer and more controlled way using a tool called IAM policy simulator. I'm doing this because having to stop instances and log-in to AWS account as other user is a bit disruptive.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is tool that simulates actions and test permission settings by defining a specific user/role/group and the action to test for. It's useful for saving time when testing permission settings, no need to log-in to another use to stop resources.

### How I used the simulator

I set up a simulation for the development user group has permission to stop instances or delete tags. The results were denied for both so i had to adjust the scope of the EC2 instances to the ones tagged with development, permission was allowed once applied.

![Image](http://nextwork.ai/determined_olive_loyal_guava/uploads/aws-security-iam_069d8a621)

---

---
