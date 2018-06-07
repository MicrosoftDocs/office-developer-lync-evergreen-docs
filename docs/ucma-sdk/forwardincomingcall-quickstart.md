---
title: ForwardIncomingCall (QuickStart)
TOCTitle: ForwardIncomingCall (QuickStart)
ms:assetid: 33f4303f-c3dc-47e5-b44e-3edfeb666a5e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454826(v=office.15)
ms:contentKeyID: 57103695
ms.date: 07/25/2014
mtps_version: v=office.15
---

# ForwardIncomingCall (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Description  
Features  
Prerequisites  
Running the sample  

Sample name: ForwardIncomingCall

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\ForwardIncomingCall

## Description

The application initializes the platform and logs in on behalf of a user. The sample then waits for an incoming audio-video call, and forwards the call to the designated target. After forwarding the call, the sample then terminates the call, conversation, and platform. The sample then exits.

## Features

  - Call and conversation cleanup and use

  - Call forwarding

  - [AudioVideoFlow](https://msdn.microsoft.com/en-us/library/hh383533\(v=office.15\)) handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Three users, enabled to use Lync Server 2013.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you will be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

3.  Make a voice call from the user logged in to Lync 2010 to the URI of the user whose credentials the sample is using.

