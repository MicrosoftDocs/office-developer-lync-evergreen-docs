---
title: SpeechSynthesisConnector (QuickStart)
TOCTitle: SpeechSynthesisConnector (QuickStart)
ms:assetid: e1d13515-e5e7-4a1a-8a0b-845419d2a708
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466132(v=office.15)
ms:contentKeyID: 57103429
ms.date: 07/25/2014
mtps_version: v=office.15
---

# SpeechSynthesisConnector (QuickStart)


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Description  
Features  
Prerequisites  
Running the sample  

Sample name: BasicCallHandling

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AudioVideoCall\\

## Description

The application initializes the platform to start listening on behalf of a user, accepts the first incoming instant messaging call, and then ends the call. The application then tears down the call, conversation, and platform. The application prints log results to the console, and then exits, performing normal platform shutdown.


> [!WARNING]
> <P>The application runs indefinitely in an idle state until it is called.</P>



## Features

  - Call and conversation cleanup and use

  - Proper call termination on an established call

  - Basic incoming call handling

  - Basic instant messaging incoming call usage

  - **AudioVideoFlow** handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two users capable of sending and receiving audio calls.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Replace the credentials in the variables at the beginning of the code sample with the credentials and server of the users from your topology.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

3.  Send an instant message to the user whose credentials the endpoint is using.

