---
title: 'How to: Create custom a Persistent Chat client'
TOCTitle: 'How to: Create custom a Persistent Chat client'
ms:assetid: 5949cdc4-560c-4a95-b84e-c00964d55aae
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465892(v=office.15)
ms:contentKeyID: 57101356
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Create custom a Persistent Chat client

Learn how to create a custom Persistent Chat client by using the Microsoft Lync Server 2013 Persistent Chat API.


**Applies to:** Lync 2013 | Lync Server 2013

A user can use Microsoft Lync 2013 as the default client to access Microsoft Lync Server 2013 Persistent Chat and to use the supported features. However, when a business application demands a custom client, the Lync Server 2013 Persistent Chat API can be used to build it. The resultant custom client can support the full feature set of the API and interoperate with Lync 2013 as well. It can be a standalone application or an add-in to another one. It's especially useful for an application to integrate features with other line-of-business applications.

## Simple custom client

In the simplest case, a custom Lync Server 2013 Persistent Chat API client can use a [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\))-based [PersistentChatEndpoint](https://msdn.microsoft.com/library/jj267567\(v=office.15\)) to connect to the Lync Server 2013 Persistent Chat. When connected, it can allow the user to search for a chat room based on certain criteria, join a selected chat room, post messages to the chat room, and receive messages from the room either in real time or on demand. The application can be synthesized using the following programming tasks as explained in [How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md):

  - [How to: Connect to a Persistent Chat server](how-to-connect-to-a-persistent-chat-server.md)

  - [How to: Browse available Persistent Chat rooms](how-to-browse-available-persistent-chat-rooms.md)

  - [How to: Join and leave a Persistent Chat room session](how-to-join-and-leave-a-persistent-chat-room-session.md)

  - [How to: Send and receive Persistent Chat messages](how-to-send-and-receive-persistent-chat-messages.md)

  - [How to: Query and view Persistent Chat history](how-to-query-and-view-persistent-chat-history.md)

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

