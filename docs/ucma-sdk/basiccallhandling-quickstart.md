---
title: BasicCallHandling (QuickStart)
TOCTitle: BasicCallHandling (QuickStart)
ms:assetid: c989d841-a7e8-4896-8dd0-479ac75bd571
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466144(v=office.15)
ms:contentKeyID: 57103475
ms.date: 07/25/2014
mtps_version: v=office.15
---

# BasicCallHandling (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013



Sample name: BasicCallHandling

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\BasicCallHandling

## Description

The application initializes the platform to start listening on behalf of a user, accepts the first incoming instant messaging call, and then terminates the call. This is followed by tearing down the conversation, and then the platform. The application prints logging data to the console, and then quits, shutting down the platform normally. Note that the sample does not send a response to the instant message that it receives.

## Features

  - Basic Call placement

  - Handling of an incoming instant messaging call

  - Call and Conversation cleanup and use

  - Call termination on an established call

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two users capable of sending and receiving audio calls.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you'll be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

3.  Log in to a client (Microsoft Lync 2013) using the second user's credentials and send an instant message to the user whose credentials the endpoint is using.

