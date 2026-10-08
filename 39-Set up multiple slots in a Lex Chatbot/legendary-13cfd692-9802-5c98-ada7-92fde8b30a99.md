<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Multiple Slots in a Lex Chatbot

**Project Link:** [View Project](https://nextwork.ai/projects/13cfd692-9802-5c98-ada7-92fde8b30a99)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/13cfd692-9802-5c98-ada7-92fde8b30a99_67890123)

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a service for building conversational interfaces into any application using voice and text. It is useful because it lets you create chatbots that understand natural language, automate customer service, and improve user experience by carrying context from one step of a conversation to the next.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to configure multiple slots that share a single slot type, add a confirmation prompt, and refine my chatbot's conversation flow using the visual conversation builder.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was that CloudFormation can deploy a chatbot from code. After deploying, I hit a Lambda permissions error that stopped the chatbot from invoking the function, which I fixed by adding a resource-based policy statement granting the bot aliases invoke access.

### This project took me...

This project took me 3 hours. I built the bot in one go with 4 intents and added conversation logic using the visual builder. I then deleted the bot and recreated it from scratch using CloudFormation.

## TransferFunds

An intent I created for my chatbot was TransferFunds, which lets users move money between their bank accounts. It uses three slots: sourceAccountType and targetAccountType, which share the same slot type, and transferAmount. The intent also includes a confirmation prompt that asks users to verify the transaction details before the transfer goes ahead.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/13cfd692-9802-5c98-ada7-92fde8b30a99_67890123)

## Using multiple slots

For this intent, I had to use the same slot type twice. This is because I was transferring money from one account to another, so I needed to collect two account types: the source account and the destination account. Both slots use the custom slot type "accountType", but each has its own unique slot name, such as "sourceAccountType" and "targetAccountType".

I also learnt how to create confirmation prompts, which are messages that ask the user to confirm or decline before the bot carries out an intent. In this case, the intent was transferring money from one account to another.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/13cfd692-9802-5c98-ada7-92fde8b30a99_97dc2351)

## Exploring Lex features

Lex also has a special conversation flow feature that lets you visualize and edit the logical flow of an intent as you build your bot.

You can also build an intent using the visual builder. The visual builder lets you see the conversation flow of an intent as a diagram, and you can edit that flow directly on the canvas, adding or changing steps such as prompts, slots, and conditional branches, if you prefer a more visual way of working.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/13cfd692-9802-5c98-ada7-92fde8b30a99_12345678)

## AWS CloudFormation

AWS CloudFormation is a service that gives you an easy way to create and set up AWS resources. It is an infrastructure as code service, meaning you write a template file that describes all the resources you want and their dependencies. You can then use that template to create, update, and delete the entire stack of resources together, instead of managing each resource individually.

I used CloudFormation to deploy the Lex bot I defined in my template, including all the intents and slots needed for BankerBot.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/13cfd692-9802-5c98-ada7-92fde8b30a99_c4fc89af)

## The final result!

Re-building my bot with CloudFormation took me a few minutes to deploy.

There was an error after I deployed my bot! The error was that the Lambda function's permissions were misconfigured, so the chatbot couldn't invoke the function and never received a response. I fixed this by adding a resource-based policy statement to the Lambda function that grants the bot's alias permission to invoke it.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/13cfd692-9802-5c98-ada7-92fde8b30a99_505be5b8)

## Using the visual builder

Using the visual builder, I added a condition that checks whether the user wants to see their balance after a transfer is completed. For an end user, this means they can keep chatting with BankerBot and trigger other intents based on what they need, without having to start a new conversation.

The new Get slot value card will trigger once the transfer is complete. This card will capture whether the user wants to check their account balance.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/13cfd692-9802-5c98-ada7-92fde8b30a99_9cac15cd4)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/13cfd692-9802-5c98-ada7-92fde8b30a99)*
