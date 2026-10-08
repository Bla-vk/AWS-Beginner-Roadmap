<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect Amazon Lex with Lambda

**Project Link:** [View Project](https://nextwork.ai/projects/05a8853b-a1e0-5be3-a93f-adeecd72e61c)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/05a8853b-a1e0-5be3-a93f-adeecd72e61c_505be5b8)

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a service for building conversational interfaces, such as chatbots, using voice and text. It is useful because it lets you define intents, which represent the different things a user might want to do, so the chatbot can recognize what each user is asking for and respond appropriately. This helps a single chatbot handle a wide variety of requests more accurately and efficiently.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to build a conversational interface (chatbot) called BankerBot. I created a WelcomeIntent, customized the built-in FallbackIntent, and built a CheckBalance intent with custom slots to collect user information. I then integrated Lex with an AWS Lambda function using a fulfillment code hook, so the chatbot could return a bank balance figure once the slots were filled.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how straightforward it would be to create and customize a bot. I was also surprised that even after adding the Lambda function to the bot's alias, I still had to enable a code hook on the specific intent, like CheckBalance. I assumed the alias connection would cover every intent, but each intent needs its own code hook enabled for the function to run and for fulfillment to work.

### This project took me...

This project took me approximately 90 minutes.

## AWS Lambda Functions

AWS Lambda lets you run code in the cloud without provisioning or managing servers. It runs your code only when triggered and scales automatically, from a few requests per day to thousands per second. You just supply your code in a supported language.

In this project, I created a Lambda function that uses a Python script to generate a random number. When a user asks the chatbot for their account balance, Amazon Lex triggers this Lambda function to run. The function picks a random number to act as a placeholder bank balance and returns it to Lex, and Lex then delivers that balance to the user in the chatbot's reply.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/05a8853b-a1e0-5be3-a93f-adeecd72e61c_97dc2351)

## Chatbot Alias

An alias in Amazon Lex acts as a pointer to a specific version of your bot. Applications and services connect to the alias instead of a fixed version, so you can point the alias to a new bot version without changing the applications themselves. This saves development time and reduces the risk of errors.

TestBotAlias is a default alias that Amazon Lex creates for your bot, intended for testing and development. It points to the draft version of your bot, so you can use it as a sandbox to confirm everything works smoothly before publishing changes to users.

To connect Lambda to my BankerBot, I opened the bot's TestBotAlias, selected English (US) in the Languages panel, and chose my Lambda function, BankingBotEnglish, as the source. I left the function version set to $LATEST and clicked Save.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/05a8853b-a1e0-5be3-a93f-adeecd72e61c_c4fc89af)

## Code Hooks

A code hook connects your chatbot to a custom Lambda function so it can perform specific tasks during a conversation. Code hooks handle more complex actions that the basic chatbot setup can't do on its own, such as validating what a user says, retrieving data from a database or API, and deciding how the conversation should continue based on what the user has already said. In short, code hooks make your chatbot more capable and useful by letting it run custom logic seamlessly while it chats.

Even though I had already connected my Lambda function to my chatbot's alias, I still had to enable code hooks. The alias connection only makes the Lambda function available to the bot. Amazon Lex still needs to be told which specific intent should invoke it, such as the CheckBalance intent, so that Lambda can handle its fulfillment.

I found the code hooks in my chatbot by opening the CheckBalance intent. From there, I scrolled down to the Fulfillment section, expanded On successful fulfillment, and selected Advanced options. This revealed the fulfillment Lambda code hook settings.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/05a8853b-a1e0-5be3-a93f-adeecd72e61c_505be5b9)

## The final result!

I've set up my chatbot to trigger Lambda and return a random dollar figure when user specifies the account they want to check.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/05a8853b-a1e0-5be3-a93f-adeecd72e61c_505be5b8)

## Customizing the Lambda function

To level up the connection between Lambda and Lex,I added randomly selected descriptions to the Lambda function's responses, so the chatbot's replies are unique and more engaging.

Now, the message my users see when they ask for their bank balance is "Hello! Your Savings account balance, tucked away in your personal treasure box, is currently $283.38". I can customise this message even further by editing the Lambda function and adding more creative descriptions

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/05a8853b-a1e0-5be3-a93f-adeecd72e61c_38b5f5691)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/05a8853b-a1e0-5be3-a93f-adeecd72e61c)*
