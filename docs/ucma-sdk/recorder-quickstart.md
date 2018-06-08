---
title: Recorder (QuickStart)
TOCTitle: Recorder (QuickStart)
ms:assetid: e76144e2-b8f4-47bf-8d39-4f079a376a88
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454822(v=office.15)
ms:contentKeyID: 57103673
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Recorder (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

  

Sample name: Recorder

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AudioVideoCall\\Recorder

## Description

The application initializes the platform and places a call to the specified user, records what the user says, and then tears down the platform. The application prints log results to the console, and then exits, performing normal platform shutdown.

## Features

  - Call and conversation cleanup and use

  - Basic call placement

  - Basic **Recorder** and **WmaFileSink** usage

## Prerequisites

  - Microsoft Lync Server 2013.

  - One user capable of sending and receiving audio calls.

  - The credentials for the user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Replace the credentials in the variables at the beginning of the code sample with the credentials and server of the users from your topology.

2.  Substitute the address of the called user in the code sample with the address of a valid, currently signed-in user capable of receiving audio calls.

3.  Open the project in Microsoft Visual Studio, and then press **F5**.

