﻿---
title: CallTransferBasic (QuickStart)
TOCTitle: CallTransferBasic (QuickStart)
ms:assetid: 5a4b0a5a-4db1-45be-b9a7-c899066faaf0
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454816(v=office.15)
ms:contentKeyID: 57103650
ms.date: 07/25/2014
mtps_version: v=office.15
---

# CallTransferBasic (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

 

Sample name: CallTransferBasic

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\CallTransferBasic

## Description

This sample involves communication between three users: a transferor, a transferee, and a transfer target. The sample logs in as the transferor, who is the user who receives an incoming audio-video call from the transferee, logged in to Microsoft Lync 2013.The transferor accepts the call from the transferee, and initiates a transfer to the transfer target. This sample demonstrates the ATTENDED transfer-type; hence after the transfer completes, the initial incoming call is disconnected.

The user can choose between attended or unattended transfers by changing the transfer-type in the code.

The difference between attended and unattended transfer is that unattended transfers begin the transfer (send the REFER to the caller) and terminate the initial call on receipt of the transfer request response (202-Reply) from the caller. Attended transfers, on the other hand, wait to terminate the call until the transfer either succeeds or fails. The application prints logging to the console, and then quits, shutting down the platform normally.

## Features

  - Call transfer, and established call activities

  - Basic call placement

  - Basic incoming audio/video call use

  - **AudioVideoFlow** handling and control

## Prerequisites

  - Microsoft Lync Server 2013.

  - Three users capable of making and receiving audio calls.

  - The credentials for each user, and a client (such as Lync 2013) capable of signing in to Lync Server 2013.

  - A currently logged-in user on Lync 2013, using one of the three users above, that will initiate the call sequence.

## Running the sample

1.  Supply the user credentials in the accompanying app.config file, or you'll be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

3.  Make a voice call to the user whose credentials the endpoint is using.

