---
title: BasicConferencing (QuickStart)
TOCTitle: BasicConferencing (QuickStart)
ms:assetid: 87398899-e1a8-48c4-9137-9ea2d741ac1c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466142(v=office.15)
ms:contentKeyID: 57103473
ms.date: 07/25/2014
mtps_version: v=office.15
---

# BasicConferencing (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

  

Sample name: BasicConferencing

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\BasicConferencing

## Description

The application initializes a platform and two endpoints, caller and callee, each on behalf of a different user. The caller endpoint schedules an IM conference using the conference scheduling APIs, and then both the caller and the callee join this scheduled conference. This sample also expects a third user to be logged in to a client (Microsoft Lync 2013) who will be extended an invitation to participate in the conference. This way, you can get a visual representation of the IM conference and the roster. The end result is that you have three users in an IM conference with each other.

The caller endpoint sends an IM on the conference, which all three endpoints receive. The callee endpoint always echoes all messages sent by caller endpoint. All messages sent by the caller endpoint and callee endpoint are always logged to the console. The third endpoint, logged in to Lync 2013, can terminate the conference by sending a "bye" message, which in turn shuts down the platform normally.

## Features

  - Conference scheduling and configuration

  - Joining an existing conference

  - **InstantMessagingCall** conference use

  - **InstantMessagingFlow** handling and control

## Prerequisites

  - Lync Server 2013

  - Three users capable of sending and receiving audio calls

  - The credentials for each user

  - A third user, logged in to Microsoft Lync 2013

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you will be prompted for them when you run the sample.

2.  Log-in as the third user in Lync 2013.

3.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

4.  Terminate the sample by sending a text message of "bye" from the user logged in to Lync 2013.

