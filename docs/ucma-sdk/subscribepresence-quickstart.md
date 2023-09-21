---
title: SubscribePresence (QuickStart)
TOCTitle: SubscribePresence (QuickStart)
ms:assetid: 0d48b640-c58c-442a-9e13-2ff1d9dc5397
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454835(v=office.15)
ms:contentKeyID: 57103769
ms.date: 07/25/2014
mtps_version: v=office.15
---

# SubscribePresence (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

  

Sample name: SubscribePresence

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\SubscribePresence

## Description

The application initializes the platform and endpoint and subscribes to the presence of a target user. Throughout the process, the application listens for incoming notifications from a user logged on to Microsoft Lync 2013 and reflects the updated state of that user in the console.

## Features

  - Presence subscription

  - Monitoring of presence-related notifications

## Prerequisites

  - Microsoft Lync Server 2013.

  - Two users, enabled to use Lync Server 2013.

  - The credentials for each user, and a client capable of signing in to Lync Server 2013.

  - A client signed in to Lync Server 2013.

## Running the sample

1.  Supply the configuration settings to be used by the sample in the accompanying App.config file, you'll be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

3.  Change the presence of the user logged on to Lync 2013, and see the presence change in the console.

