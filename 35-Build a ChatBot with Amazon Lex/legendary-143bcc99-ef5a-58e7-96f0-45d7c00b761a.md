<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Chatbot with Amazon Lex

**Project Link:** [View Project](https://nextwork.ai/projects/143bcc99-ef5a-58e7-96f0-45d7c00b761a)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_505be5b8)

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate the use of Amazon Lex to build intelligent chatbots that understand natural language and help users get things done.

### What is Amazon Lex?

Amazon Lex is an AWS service for building conversational interfaces that work with both voice and text. It uses artificial intelligence, including automatic speech recognition and natural language understanding, to power chatbots and virtual assistants. It's useful for automating customer support, streamlining workflows, and integrating with other AWS services such as Lambda and Amazon Connect.

### Key tools and concepts

The service I used was Amazon Lex, which is used to build chatbots. Key concepts I learned include the FallbackIntent (the default intent that triggers when the bot doesn't understand a user's input), initial responses (the message the bot sends right after it recognizes an intent), and closing responses (the message the bot sends once the intent has been fulfilled).

### Personal reflections

One thing I didn't expect in this project was how easy it was to set up a chatbot using Amazon Lex. I had a working bot responding to test messages in just a few steps.

### Project timeline

This project took me approximately 1 hour.

## Setting up a Lex chatbot

### Approach to chatbot setup

In this step, I will create a new chatbot from scratch using Amazon Lex. This is the foundation of the project, because the bot is what will understand users' messages and respond to them.

### Chatbot creation process

I built a chatbot from scratch using Amazon Lex. Creating the bot took about 5 minutes, since I used mostly default settings.

### IAM role configuration

While creating my chatbot, I also created an IAM role with basic permissions, because Amazon Lex needs permission to call other AWS services on my behalf. Later in this project, I'll integrate Lex with a Lambda function.

### Intent classification confidence score

In terms of the intent classification confidence score, I kept the default value of 0.40. This means the bot needs to be at least 40% confident that the user's input matches one of the intents I programmed before my Banker bot responds with that intent. If the confidence falls below this threshold, the bot triggers the fallback intent instead.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_97dc2351)

## Intents

In this step, I will create a Welcome intent in BankerBot and add sample utterances, such as "Hi" and "Hello", so it can recognize greetings and respond to my users.

### Creating my first intent

An intent is the goal a user wants to accomplish when they interact with a chatbot. Examples include checking a bank account balance, booking a flight, or ordering food.

I created my first intent, WelcomeIntent, to greet users when they start a chatbot conversation with "Hello" or a similar greeting.

### Testing chatbot responses

I launched and tested my chatbot, which could respond successfully if I enter "Hello", "Hi", or "Help Me" .

## Handling unrecognized inputs

My chatbot returned the message 'Intent FallbackIntent is fulfilled' when I entered 'Good Morning' and 'How are you'. This happened because those phrases were not added to the sample utterances of any intent during setup, so the bot could not match them to an intent and fell back to the default FallbackIntent.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_505be5b8)

## Configuring FallbackIntent

In this step, I customise FallbackIntent to send user-friendly messages.

### When FallbackIntent triggers

FallbackIntent is a built-in default intent in Amazon Lex that is triggered when the bot cannot match a user's input to any of its other intents.

I configured the FallbackIntent because the default response Lex gives when it can't match a user's input is vague and unhelpful. A custom fallback message lets me tell users clearly that their request wasn't understood and guide them on what to try next.

### My FallbackIntent configuration

"To configure the FallbackIntent, I had to create a custom closing response on the intent's setup page. I used the message: 'Sorry I am having trouble understanding. Can you describe what you'd like to do in a few words?...'

I also added response variations. For an end user, this means they see different versions of my chatbot's reply to the same question. This makes the conversation feel less repetitive and more natural, like talking to a person.

## FallbackIntent with Variations

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_c4fc89af)

## Initial Responses

In this project extension, I'm going to set up initial responses, which are the greetings or confirmations my chatbot sends right after it recognizes the user's intent. I'm doing this to add variation to the bot's replies so it sounds less repetitive.

### Setting up initial responses

Initial responses are useful for telling users what to expect while their request is being processed. I've set up an initial response to acknowledge the user's request as soon as the bot recognizes their intent.

### Initial response implementation

The initial response messages I set up are "Hmmm, this is interesting...", "One moment...", and "Thinking...". For the user, these messages appear right after the chatbot recognizes what they want, while it works on a response.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/143bcc99-ef5a-58e7-96f0-45d7c00b761a_09bcb9701)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/143bcc99-ef5a-58e7-96f0-45d7c00b761a)*
