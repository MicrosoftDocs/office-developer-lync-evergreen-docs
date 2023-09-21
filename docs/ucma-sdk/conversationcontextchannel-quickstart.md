---
title: ConversationContextChannel (QuickStart)
TOCTitle: ConversationContextChannel (QuickStart)
ms:assetid: 629b6197-eb45-4810-99fe-66bd44881d21
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454821(v=office.15)
ms:contentKeyID: 57103671
ms.date: 07/25/2014
mtps_version: v=office.15
---

# ConversationContextChannel (QuickStart)


**Applies to**: Lync 2013



Sample name: ConversationContextChannel

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\ConversationContextChannel

## Description

The application initializes the platform to start listening on behalf of a user, accepts the first incoming instant messaging call, and then terminates the call. This is followed by tearing down the conversation, and then the platform. The application prints logging data to the console, and then quits, shutting down the platform normally. Note that the sample does not send a response to the instant message that it receives.

## Features

  - [ConversationContextChannel](https://msdn.microsoft.com/library/hh161849\(v=office.15\)) establishment

  - Sending context data to the remote user on the **ConversationContextChannel** instance

  - Receiving context data from the remote user on the **ConversationContextChannel** instance

## Prerequisites

  - Microsoft Lync Server 2013.

  - A Lync user who is logged on to Lync Server 2013.

  - Microsoft Lync 2013 SDK installed on the computer where a user is signed on to Lync.

  - Two users capable of sending and receiving audio calls.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you'll be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

3.  Log on to a client (Microsoft Lync 2013) using the second user's credentials.

4.  Open the project in Visual Studio, and press **F5**.

## See also

#### Concepts

[Contextual communication](contextual-communication.md)

[Conversation context channel](conversation-context-channel.md)

#### Other resources

[Register contextual conversation packages\_Retired](https://msdn.microsoft.com/library/gg253680\(v=office.15\))

