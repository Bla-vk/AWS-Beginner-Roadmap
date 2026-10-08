<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Add Custom Slots to a Lex Chatbot

**Project Link:** [View Project](https://nextwork.ai/projects/9b23ef35-9a36-5a21-9a3c-cfa3d61a0e2b)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/9b23ef35-9a36-5a21-9a3c-cfa3d61a0e2b_c4fc89af)

## Introducing Today's Project!

In today's project, I used Amazon Lex to enhance my BankerBot by adding slots to the CheckBalance intent. This allowed the chatbot to collect specific details from the user, such as accountType and dateOfBirth, more efficiently, which improved the conversational flow and the overall user experience.

### What is Amazon Lex?

Amazon Lex is an AWS service for building conversational interfaces into applications using voice and text. It is useful because it lets you define intents, which are the different actions a user might want to perform, so a single chatbot can handle a variety of related requests. This helps you create chatbots that can understand user input, fulfill requests, and respond in a natural, conversational way.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how much creativity goes into designing the ways a chatbot can interact with users.

### This project took me...

This project took me about 75 minutes including creating the chatbot from scratch.

## Slots

Slots are the pieces of information a chatbot needs to fulfill a user's request. Think of them as the blanks in a form that must be filled in before the request can be completed.

By adding custom slots in utterances, my chatbot's users can specify account types like savings, checking, or credit, which are values I defined in a custom slot type.

In this project, I created a custom slot type in Amazon Lex that defines the account types my BankerBot can recognize: Checking, Savings, and Credit. I set the slot type to restrict its values, so the bot only accepts these valid options when a user asks for an account balance.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/9b23ef35-9a36-5a21-9a3c-cfa3d61a0e2b_97dc2351)

## Connecting slots with intents

This slot type uses restricted slot values, which means your Amazon Lex chatbot will only accept the values you define, along with any synonyms you add. As a result, BankerBot will only recognize 'Checking', 'Savings', and 'Credit' as valid account types, and it won't expand beyond that list to accept other, potentially irrelevant, values.

I associated my custom slot with CheckBalance, which is the new intent I created to handle requests from users who want to check their bank account balance. I then assigned a custom slot type to the accountType slot, so the intent can collect the information needed to process a balance inquiry, such as the accountType and dateOfBirth, from the user.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/9b23ef35-9a36-5a21-9a3c-cfa3d61a0e2b_c4fc89af)

## Slot values in utterances

I included slot values in some of the utterances (i.e., sample user inputs) by adding {accountType} directly into the phrasing. This lets Amazon Lex recognize and capture the accountType slot from the user's initial input when they provide it, so the bot doesn't need to ask a follow-up question. For example, with an utterance like "What's the balance in my {accountType} account?", the bot can pick up the account type straight from a request like "What's the balance in my savings account?"

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/9b23ef35-9a36-5a21-9a3c-cfa3d61a0e2b_505be5b8)

## Handling failures in slot values

I added variations to the dateOfBirth slot prompt, such as 'Sorry, that wasn't clear to me. What's your date of birth?' and 'Hmm, didn't work, try sharing it in this format MM/DD/YYYY'. These variations give the bot a range of ways to ask the same question, and Amazon Lex will randomly choose one of them each time it prompts the user for this slot. This makes the conversation feel more natural and less repetitive.

I also used failure responses to handle invalid user inputs, such as a birthdate in the wrong format. I also changed the default slot prompt so it explicitly asks for a birthdate, since the bot uses it to verify the user's identity.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/9b23ef35-9a36-5a21-9a3c-cfa3d61a0e2b_a028bc8d2)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/9b23ef35-9a36-5a21-9a3c-cfa3d61a0e2b)*
