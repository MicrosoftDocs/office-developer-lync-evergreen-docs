---
title: CallTransferSupervised (QuickStart)
TOCTitle: CallTransferSupervised (QuickStart)
ms:assetid: 9c755cf5-c4ff-467c-bc6c-6b704755ba2e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454819(v=office.15)
ms:contentKeyID: 57103669
ms.date: 07/25/2014
mtps_version: v=office.15
---

# CallTransferSupervised (QuickStart)


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Description  
Features  
Prerequisites  
Running the sample  

Sample name: CallTransferSupervised

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\CallTransferSupervised

## Description

The application represents three users, referred to in this description as transferee, transferor, and transfer target. The transferor places audio calls to both transferee and transfer target. After the calls are accepted and connect successfully, the transferor executes a supervised transfer from transferee to the transfer target. In doing so, the original calls that the transferor had with the transferee and transfer target are terminated, and a new call directly between transferee and transfer target is established. The transferor then drops out of the communication. The application prints log messages to the console, and then quits, shutting down the platform normally.

## Features

  - Call transfer and established call activities

  - Basic call placement

  - Basic incoming audio/video call use

  - **AudioVideoFlow** handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Three users, enabled to use the Lync Server 2013.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you will be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio, and then press **F5**.

