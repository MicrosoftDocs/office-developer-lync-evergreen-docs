---
title: 'How to: Publish a chat message digest through email'
TOCTitle: 'How to: Publish a chat message digest through email'
ms:assetid: 19c47a43-b1cf-4039-990a-bd003bc4b1f6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465901(v=office.15)
ms:contentKeyID: 57101379
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Publish a chat message digest through email

Learn how the Microsoft Lync Server 2013 Persistent Chat API and Exchange Web Services (EWS) Managed API is used to create the Persistent Chat message digest. The digest is used in the Microsoft Outlook inbox for each Persistent Chat room member.


_**Applies to:** Lync 2013 | Lync Server 2013_

In a forum, it is customary to provide message digest as a mechanism to notify the participants of newly posted messages to the forum even when the participants are not online. The message digest can be in the form of complete listing of messages or some type of summaries. It can be delivered to the email accounts of the members of the forum as soon as new messages are posted or on a fixed schedule.

The Microsoft Lync Server 2013 Persistent Chat API and Exchange Web Services (EWS) Managed API can be used to provide the digest of Persistent Chat messages to the Outlook Inboxes of the members of a chat room. The simplest case would involve sending newly posted messages to the chat room members’ Outlook Inboxes as soon as they are posted.

## Send chat message digest to Outlook inbox instantly

This scenario includes the following programming tasks:

1.  Connect to Persistent Chat Server on a [UserEndpoint](https://msdn.microsoft.com/en-us/library/hh348819\(v=office.15\))-based [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)).

2.  Select a chat room and retrieve all the members of the room.

3.  Establish a chat room session and register to receive [ChatMessageReceived](https://msdn.microsoft.com/en-us/library/jj266375\(v=office.15\)) events.

4.  In the [ChatMessageReceived](https://msdn.microsoft.com/en-us/library/jj266375\(v=office.15\)) event handler, send the parsed message to the Outlook Inboxes of the chat room members using EWS.

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

