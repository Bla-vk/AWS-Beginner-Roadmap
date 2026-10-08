<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Save User Info with a Lex Chatbot

**Project Link:** [View Project](https://nextwork.ai/projects/19e304aa-a759-5670-97ff-e3e1c45436eb)

**Author:** Precious Awoyemi  
**Email:** pawoyemi@gmail.com

---

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_505be5b8)

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a service for building conversational interfaces into applications using voice and text. It is useful because it lets you create intelligent chatbots that understand natural language, automate customer service, and improve the user experience by remembering context during a conversation.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to store user information in an output context tag, set up a FollowupCheckBalance intent, and enable context carryover to that intent. This allows the chatbot to remember user details, like their birthday, from earlier in the conversation, so it doesn't have to ask for them again.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how easy it is to change how long the bot remembers a conversation.

### This project took me...

This project took me an Hour.

## Context Tags

Context tags are labels that track the state of a conversation, such as which topic or intent is currently active. They carry relevant information forward between turns, so the user doesn't have to repeat details they have already provided.

There are two types of context tags:

Output context tag: This tells the chatbot to save certain details once an intent is fulfilled, so other intents later in the conversation can use them. For example, the account type collected during BalanceCheck can be saved and reused.

Input context tag: This checks whether a specific context is active before an intent can be triggered. For example, FollowupCheckBalance requires the context created by BalanceCheck. If that context is active, the stored details, such as the user's date of birth, are already available, so the chatbot doesn't need to ask for them again.

I created a context tag called 'contextCheckBalance'. This context tag was created in the intent 'CheckBalance'. This tag stores information about the user's birthday.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_97dc2351)

## FollowUpCheckBalance

I created a new intent called FollowupCheckBalance to handle follow-up questions about account balances without asking the user for their birthday again. It does this by using the contextCheckBalance context, which carries the date of birth collected in the earlier CheckBalance intent into the follow-up intent.

This intent is connected to the CheckBalance intent I created earlier because it uses the context contextCheckBalance to carry over the user's date of birth. CheckBalance sets this context as an output context, and this intent accepts it as an input context. As a result, users can ask follow-up questions about their account balance without being asked for their date of birth again.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_12345678)

## Input Context Tag

I created an input context, contextCheckBalance, that the CheckBalance intent sets as an output context once the user's date of birth has been collected. The FollowupCheckBalance intent uses it as an input context, so it can reuse that date of birth instead of asking for it again.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_c4fc89af)

## The final result!

To see context tags and follow-up intents in action, I first tried to trigger the FollowupCheckBalance intent without invoking CheckBalance. Then I triggered CheckBalance first, followed by FollowupCheckBalance.

If I had tried to trigger the FollowupCheckBalance intent without setting up any context first, it would not have worked. The intent's input context, contextCheckBalance, would not have been active, so Lex would not have matched my request to the intent. Without that context, the intent also would not have had the user's date of birth, which was captured earlier and carried over through the context.

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_505be5b8)

## Managing context expiry

An extension for this project is to manage the context expiry for contextCheckBalance, which controls how long the bot keeps that context active. You can set it by the number of conversation turns or by a length of time, and once either limit is reached, the context expires and the bot no longer uses it. By default, a context lasts for 5 turns or 90 seconds, whichever comes first.

I updated my bot's context expiry to 1 turn or 5 seconds. For my end users, this means they can ask a follow up bank balance request only once, and only within 5 seconds of the previous response.

A longer context expiry window is helpful when we want the bot to remember a user's information across a longer conversation or after pauses in it. A shorter context expiry window is helpful when we want a more secure conversation, especially when sensitive data is involved

![Image](https://nextwork.ai/determined_olive_loyal_guava/uploads/19e304aa-a759-5670-97ff-e3e1c45436eb_81b763822)

---

*Built with [NextWork](https://nextwork.ai) - [View this project](https://nextwork.ai/projects/19e304aa-a759-5670-97ff-e3e1c45436eb)*
