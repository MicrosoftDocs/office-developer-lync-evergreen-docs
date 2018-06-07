---
title: PortRange (QuickStart)
TOCTitle: PortRange (QuickStart)
ms:assetid: 50620ffb-d04f-474b-bba5-68965ee89026
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454815(v=office.15)
ms:contentKeyID: 57103642
ms.date: 07/25/2014
mtps_version: v=office.15
---

# PortRange (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Description  
Features  
Prerequisites  
Running the sample  

Sample name: PortRange

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AudioVideoCall\\PortRange

## Description

The application places an audio/video call to the designated target, after initializing platform and endpoints. It then uses **AudioVideoSettings** to change the port range to be used by the media stack at run time. After successfully placing the audio/video call, the application prints the content of the change to the console, and then exits, performing normal platform shutdown.

## Features

  - Subscribing to a change in flow properties and dealing with being put on hold.

  - Basic audio/video call placement.

  - **AudioVideoFlow** handling and control.

  - Changing the configuration of an active **AudioVideoFlow**.

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two users capable of sending and receiving audio calls.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Replace the credentials in the variables at the beginning of the code sample with the credentials and server of the users from your Lync Server 2013 topology.

2.  Substitute the address of the called user in the code example with the address of a valid, currently signed-in user capable of receiving audio calls.

3.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

