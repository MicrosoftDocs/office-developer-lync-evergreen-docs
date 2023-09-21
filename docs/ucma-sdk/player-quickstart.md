﻿---
title: Player (QuickStart)
TOCTitle: Player (QuickStart)
ms:assetid: 479967c3-7fc8-4884-83f7-ea92c9893026
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454813(v=office.15)
ms:contentKeyID: 57103636
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Player (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

 

Sample name: Player

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AudioVideoCall\\Player

## Description

The application initializes the platform and places a call to the specified user, plays a WMA file, pauses and then resumes playing the file, and then stops. The application then tears down the player, file source, and platform. The application prints logging log results to the console, and then exits, performing normal platform shutdown.

## Features

  - Call and conversation cleanup and use

  - Basic call placement

  - Basic **Player** and **WmaFileSource** usage

## Prerequisites

  - Microsoft Lync Server 2013.

  - One user capable of receiving audio calls.

  - The credentials for the user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Replace the credentials in the variables at the beginning of the code sample with the credentials and server of the users from your topology.

2.  Substitute the address of the called user in the code sample with the address of a valid, currently signed-in user capable of receiving audio calls.

3.  Open the project in Microsoft Visual Studio, and then press **F5**.

