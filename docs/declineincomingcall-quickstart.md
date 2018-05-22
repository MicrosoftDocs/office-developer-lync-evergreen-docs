---
title: DeclineIncomingCall (QuickStart)
TOCTitle: DeclineIncomingCall (QuickStart)
ms:assetid: 72db6c20-e348-489d-bf98-160d72329a4d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454825(v=office.15)
ms:contentKeyID: 57103684
ms.date: 07/25/2014
mtps_version: v=office.15
---

# DeclineIncomingCall (QuickStart)


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Description  
Features  
Prerequisites  
Running the sample  

Sample name: DeclineIncomingCall

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\DeclineIncomingCall

## Description

The application initializes the platform to start listening on behalf of a user, rejects the first incoming instant messaging call, and then tears down the call, conversation, and platform. The application then quits.

The sample expects a user logged on to a client (such as Microsoft Lync 2013) to send an instant message to the user who is logged on to the sample application.

## Features

  - Call and conversation cleanup and use

  - Handling of incoming instant messages

  - [InstantMessagingFlow](https://msdn.microsoft.com/en-us/library/hh383312\(v=office.15\)) handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two users, enabled to use Lync Server 2013.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you will be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

3.  Send an instant message to the user whose credentials the endpoint is using.

