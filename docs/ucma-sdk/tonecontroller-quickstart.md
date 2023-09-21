﻿---
title: ToneController (QuickStart)
TOCTitle: ToneController (QuickStart)
ms:assetid: 2497ed23-a5b4-43dd-96ab-9287beabd3bd
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466135(v=office.15)
ms:contentKeyID: 57103442
ms.date: 07/25/2014
mtps_version: v=office.15
---

# ToneController (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

 

Sample name: ToneController

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AudioVideoCall\\ToneController

## Description

The application places an audio/video call to the designated target, after initializing platform and endpoints. After the call is connected, the application waits for the **AudioVideoFlow** to become active (when the value of its **State** property is **Active**), and then attaches a **ToneController** and registers a handler for an event that is raised when a DTMF tones or Fax tones are received. For each tone that is received, the application replies by sending the same tone back to the remote endpoint. Zero and a fax tone will shut down the platform and close the demo.

## Features

- Basic audio/video call placement

- Platform an endpoint initialization

- **AudioVideoFlow** handling and control.

- Attaching an **AudioVideoFlow** to a **ToneController**.

- Using **ToneController** to receive DTMF or Fax tones from the remote side.

- Sending tones.

## Prerequisites

- Microsoft Lync Server 2013.

- Two users capable of sending and receiving audio calls.

- The credentials for each user, and a client capable of signing in to Lync Server 2013.

- A client signed in to Lync Server 2013.

## Running the sample

1.  Replace the credentials in the variables at the beginning of the code sample with the credentials and server of the users from your Lync Server 2013 topology.

2.  Substitute the address of the called user in the code sample with the address of a valid, currently signed-in user capable of receiving audio calls.

3.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

