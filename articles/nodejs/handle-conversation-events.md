---
title: Handle user and conversation events  | Microsoft Docs
description: Learn how your conversational application (bot) can handle events such as a user joining a conversation or adding a bot to their contacts list.
keywords: bot framework, user events, handle conversation updates, join conversation, add to contacts, greet users, conversationUpdate, contactRelationUpdate
author: DeniseMak
manager: rstand
ms.topic: article
ms.prod: bot-framework

ms.date: 02/24/2017
ms.reviewer:
#ROBOTS: Index
---
<!-- This topic is about handling conversation update events, conversationUpdate and contactRelationUpdate
The title is "Greet users" because typically, you'll greet the users or do other first-run activities when a user joins a conversation -->

# Greet users who join a conversation or add your bot to their contacts using the Bot Builder SDK for Node.js

<!--
> [!div class="op_single_selector"]
> * [.NET](~/dotnet/howto-save-user-data.md)
> * [Node.js](~/nodejs/save-user-data.md)
>
-->



This article demonstrates how your bot can handle events such as a user joining a conversation or adding a bot to their contacts list. 

 <!-- todo: Session and Converstaion and PrivateConversation --> 

## Greeting a user on conversation join
The Bot Framework provides the conversationUpdate event for notifying your bot when a user joins or leaves a conversation.

Your bot can greet the user or perform other first-run activities when a user joins the conversation. 

<!-- TODO: Reference code in snippet repository -->
[!include[conversationUpdate sample Node.js](~/includes/snippet-code-node-contactrelationupdate-1.md)]

## Acknowledge add to contacts list

The contactRelationUpdate event notifies your bot that a user has added you to their contacts list.


[!include[contactRelationUpdate sample Node.js](~/includes/snippet-code-node-contactrelationupdate-1.md)]

## Add a first-run dialog

Neither the conversationUpdate nor the contactRelationUpdate event are supported by all channels. See the documentation for each channel to determine whether the channel provides these events.
A more universal way to greet a user who joins a conversation is to add a first-run dialog.

In the following example we’ve added a function that triggers the dialog anytime we’ve never seen a user before. 
You can customize the way an action is triggered by providing an [onFindAction][onFindAction] handler for your action. 

[!include[first-run sample Node.js](~/includes/snippet-code-node-first-run-dialog-1.md)]


You can also customize what an action does after its been triggered by providing an [onSelectAction][onSelectAction] handler. 
For trigger actions you can provide an [onInterrupted][onInterrupted] handler to intercept an interruption before it occurs. 

## Next steps

To learn more, see:

> [!NOTE]
> To do: Add links to other articles.


<!-- TODO: UPDATE LINKS TO POINT TO NEW REFERENCE -->
[onFindAction]: https://docs.botframework.com/en-us/node/builder/chat-reference/interfaces/_botbuilder_d_.itriggeractionoptions#onfindaction
[onSelectAction]: https://docs.botframework.com/en-us/node/builder/chat-reference/interfaces/_botbuilder_d_.itriggeractionoptions#onselectaction
[onInterrupted]: https://docs.botframework.com/en-us/node/builder/chat-reference/interfaces/_botbuilder_d_.itriggeractionoptions#oninterrupted

[SendTyping]: https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.session#sendtyping
[IMessage]: http://docs.botframework.com/en-us/node/builder/chat-reference/interfaces/_botbuilder_d_.imessage
[ChatConnector]:https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.chatconnector.html
[session_userData]:https://docs.botframework.com/en-us/node/builder/chat-reference/classes/_botbuilder_d_.session.html#userdata