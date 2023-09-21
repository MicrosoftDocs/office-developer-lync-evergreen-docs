---
title: BasicAudioVideoCall (QuickStart)
TOCTitle: BasicAudioVideoCall (QuickStart)
ms:assetid: 062e5bc2-0f8b-4584-8335-f5a88beaf43e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466147(v=office.15)
ms:contentKeyID: 57103617
ms.date: 07/25/2014
mtps_version: v=office.15
---

# BasicAudioVideoCall (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

 

Sample name: BasicAudioVideoCall

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\AudioVideoCall\\BasicAudioVideoCall

Make a basic **AudioVideoCall** and perform basic flow handling.

## Description

The application places an audio/video call to the designated target, after initializing platform and endpoints. After the call is connected, the application subscribes to events that monitor basic **AudioVideoFlow** transitions and states.

The application prints log results to the console. After the call is completed, the application exits, performing normal platform shutdown.

## Features

  - Basic call placement

  - Basic use of **AudioVideoCall**

  - Basic **AudioVideoFlow** handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two users capable of sending and receiving audio calls.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013 (Microsoft Lync 2013 is the recommended client).

  - A client signed in to Lync Server 2013.

## Running the sample

1.  You may either supply the user credentials in the accompanying app.config file, or you will be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

