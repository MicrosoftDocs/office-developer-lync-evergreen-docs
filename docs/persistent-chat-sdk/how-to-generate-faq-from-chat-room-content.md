---
title: 'How to: Generate FAQ from chat room content'
TOCTitle: 'How to: Generate FAQ from chat room content'
ms:assetid: 7ab3447d-dc47-4bc6-afab-2cf6a93b277b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465893(v=office.15)
ms:contentKeyID: 57101346
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Generate FAQ from chat room content

Learn how to create a FAQ by using Persistent Chat room data and the Microsoft Lync Server 2013 Persistent Chat API.


**Applies to:** Lync 2013 | Lync Server 2013

Imagine a collaborative project involving multiple teams. The project manager can request to have a chat room set up for the team members to discuss issues related to the project. New members to the project are expected to come to the chat room to ask questions and find answers to get started with the project. Existing members can use the chat room to discuss any issues related to the project and to share their thoughts and results. When the product is delivered, the Persisted Chat messages can be used to create the initial list of Frequently Asked Questions about the project and the FAQ list can be posted on the project’s or product’s home page. After the product release, the chat room can be used for any further questions and answers from the public at large. The FAQ list can be updated periodically or as needed to include new questions and answers.

To construct a FAQ list this way, the chat messages must be retrieved from a chat room. The Lync Server 2013 Persistent Chat API can be used to accomplish this. The process involves connecting the application to a Persistent Chat server, establishing a session with the chat room, and submitting a query to receive the results. This part can be done using the Lync Server 2013 Persistent Chat API. The other part of the process involves parsing, analyzing, and classifying the retrieved chat messages into correlated questions and answers ordered by a certain frequency measure. This part is independent of the Lync Server 2013 Persistent Chat API and can be thought of a part of another business application. Altogether, this scenario serves as an example of integrating the Lync Server 2013 Persistent Chat API into a business application.

Programmatically, the implementation of the Lync Server 2013 Persistent Chat API part of the application can proceed as shown in the following workflow:

1.  Connect to the Microsoft Lync Server 2013 on a [UserEndpoint](https://msdn.microsoft.com/en-us/library/hh348819\(v=office.15\)) or an [ApplicationEndpoint](https://msdn.microsoft.com/en-us/library/hh384825\(v=office.15\))

2.  Connect to the Microsoft Lync Server 2013 Persistent Chat on a [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)).

3.  Instantiate a [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) on the connected [PersistentChatEndpoint](https://msdn.microsoft.com/en-us/library/jj267567\(v=office.15\)).

4.  Establish the [ChatRoomSession](https://msdn.microsoft.com/en-us/library/jj265925\(v=office.15\)) by calling [BeginJoin(Uri, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267599\(v=office.15\)) join the specified chat room.

5.  Query chat history of the joined chat room by calling [BeginQueryChatHistory(ChatHistoryQueryOptions, AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj267612\(v=office.15\)).

6.  Parse the returned collection of **ChatHistoryResults** to retrieve chat messages.

When the entire chat message collection is retrieved, it can be fed into a separate process or thread for natural language processing to extract questions and their matching answers. Some statistical analysis can then be performed to determine which questions will be shown in the final FAQ list.

## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

