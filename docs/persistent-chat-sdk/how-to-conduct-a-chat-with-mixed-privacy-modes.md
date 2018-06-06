---
title: 'How to: Conduct a chat with mixed privacy modes'
TOCTitle: 'How to: Conduct a chat with mixed privacy modes'
ms:assetid: 278b2fe3-2f83-456c-8053-c8df38f46fe6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465895(v=office.15)
ms:contentKeyID: 57101349
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Conduct a chat with mixed privacy modes

Learn how to use the Microsoft Lync Server 2013 Persistent Chat API to set up a Persistent Chat room that uses mixed privacy modes.


_**Applies to:** Lync 2013 | Lync Server 2013_

A Persistent Chat room can have a privacy setting of [Open](https://msdn.microsoft.com/en-us/library/jj267572\(v=office.15\)), [Closed](https://msdn.microsoft.com/en-us/library/jj267572\(v=office.15\)), or [Secret](https://msdn.microsoft.com/en-us/library/jj267572\(v=office.15\)). An open chat room is accessible by any users in the scope configured in the chat room parent category. A closed chat room is visible to all the users prescribed by the parent category, but only the users added to the room in the Member role can join the chat room and send or receive messages. A secret chat room is visible to and joined by the members only. In any given chat room, all the permitted users share the same privacy mode. In practice, however, it is desirable to have mixed privacy modes when a large group of participants are engaged in discussions of certain subject. For example, in a panel discussion, the panelists can interact with each other and the audience in a public way while conducting private conversations amongst themselves. The Lync Server 2013 Persistent Chat API can be used to enable such chat scenarios of mixed privacy modes.

One solution involves creating separate chat rooms of varying privacy settings and combining them together to form a single logical chat room. An open or closed chat room can be used for public discourse, while a secret chat room is used for private communications. In this case, members of the private (secret) chat room should be a subset of the public (open or closed) chat room members.

When connecting to Microsoft Lync Server 2013 Persistent Chat, the user first joins the public chat room. If the user is also a member of the related private chat room, the user must also join the private chat room. The public-only members can view and post messages in the public room, but not in the private room. The private members, however, can view messages from both the public and private rooms, but must choose to post messages in the either public or private chat room. Messages sent to the public chat room are visible to all while those sent to the private chat room are visible only to the private members.

The interactions between this kind of Lync Server 2013 Persistent Chat API application and a logical chat room of mixed privacy settings appear in figure 1. Instances of the application are represented by the rectangular shapes labeled **Public member** and **Private member**.

Figure 1. Logical chat room showing mixed privacy modes

  
![Logical chat room of mixed privacy modes](images/Dn465895.Howtoconductchatwithmixedprivacymodes_Fig01(Office.15).jpg "Logical chat room of mixed privacy modes")

Programmatically, the solution entails the following steps using the Lync Server 2013 Persistent Chat API:

  - Connect to Microsoft Lync Server 2013 Persistent Chat on a [UserEndpoint](https://msdn.microsoft.com/en-us/library/hh348819\(v=office.15\))-based [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)) instance.

  - Select and join to the public chat room for the mixed-mode chat. Register for the [ChatMessageReceived](https://msdn.microsoft.com/en-us/library/jj266375\(v=office.15\)) events to receive and display new messages posted to the chat room.

  - Optionally, get and display the chat history from the chat room.

  - Search and join to the related [Secret](https://msdn.microsoft.com/en-us/library/jj267572\(v=office.15\)) chat room. Register for the [ChatMessageReceived](https://msdn.microsoft.com/en-us/library/jj266375\(v=office.15\)) events to receive and display new messages posted to the private chat room. This step is applicable only when the user is a member of the private chat room.

  - Optionally, get and display the chat history from the private chat room. This step is applicable only when the user is a member of the private chat room.

  - To post a message, a public member can send the message to the public chat room only, whereas a private member must choose the public or private chat room to send the message.

For the application to work, the public (either open or closed) chat room and private (secret) chat room must first be created. These can be carried out by a Lync Server 2013 Persistent Chat administrator or a separate Lync Server 2013 Persistent Chat API application.

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

