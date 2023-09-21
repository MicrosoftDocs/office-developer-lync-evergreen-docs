﻿---
title: AVFlow-Mute (QuickStart)
TOCTitle: AVFlow-Mute (QuickStart)
ms:assetid: 1d213bf7-9044-44cb-90dd-a54cd10a0f69
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466146(v=office.15)
ms:contentKeyID: 57103606
ms.date: 07/25/2014
mtps_version: v=office.15
---

# AVFlow-Mute (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

 

Sample name: AVFlow-Mute

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AudioVideoCall\\AVFlow-Mute

## Description

The application places an audio/video call to the designated target, after initializing platform and endpoints. After the call is connected, the application waits until the **State** property on the **AudioVideoFlow** changes to **Active**, and then the application mutes the call.

A moment later, the application unmutes the call. The application prints the step-by-step actions it performs to the console, and then exits, performing normal platform shutdown.

## Features

  - Mute control on an **AudioVideoFlow**

  - Basic audio/video call placement

  - **AudioVideoFlow** handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two users capable of sending and receiving voice calls.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Replace the credentials in the variables at the beginning of the code sample with the credentials and server of the users from your Lync Server 2013 topology.

2.  Substitute the address of the called user in the code sample with the address of a valid, currently signed-in user capable of receiving audio calls.

3.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

