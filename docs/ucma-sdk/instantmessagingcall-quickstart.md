---
title: InstantMessagingCall (QuickStart)
TOCTitle: InstantMessagingCall (QuickStart)
ms:assetid: 76574248-8d00-4c66-aad5-a5df2f9f7607
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454827(v=office.15)
ms:contentKeyID: 57103703
ms.date: 07/25/2014
mtps_version: v=office.15
---

# InstantMessagingCall (QuickStart)


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Description  
Features  
Prerequisites  
Running the sample  

Sample name: InstantMessagingCall

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\InstantMessagingCall

## Description

The application initializes the platform, and logs in on behalf of a user. The sample then sends an instant message, consisting of the text "Hello World", to another user who is logged on to a client such as Microsoft Lync 2013. The sample echoes instant messages sent by the user logged in to Lync 2013. When the user logged on to Lync 2013 responds with a message that consists of the text 'bye', or closes the instant messaging window, the sample shuts down the platform and exits.

## Features

  - Call and conversation cleanup and usage

  - Basic call placement

  - Instant messaging message usage, including replying to incoming messages

  - [InstantMessagingFlow](https://msdn.microsoft.com/en-us/library/hh383312\(v=office.15\)) handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two enabled to use Lync Server 2013.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you will be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

3.  The sample sends a "Hello World" message to the called party.

4.  Log on as the called party in Lync 2013 and send an instant message to the user the sample is logged in as.

5.  Terminate the sample by sending a message with the text "bye" to the user that the sample is logged in as.

