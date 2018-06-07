---
title: PublishPresence (QuickStart)
TOCTitle: PublishPresence (QuickStart)
ms:assetid: d3ae55a9-9cf6-40aa-9cab-33aeceb2ae37
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454837(v=office.15)
ms:contentKeyID: 57103777
ms.date: 07/25/2014
mtps_version: v=office.15
---

# PublishPresence (QuickStart)


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Description  
Features  
Prerequisites  
Running the sample  

Sample name: PublishPresence

Sample location: %ProgramFiles%\\Microsoft UCMA 4.0\\SDK\\Core\\Sample Applications\\QuickStarts\\PublishPresence

## Description

The application initializes the platform and a user endpoint and subscribes to the sample user's presence (self-presence). The sample then publishes the user state, machine state, note, and contact card. The note is published using raw XML, while all other categories are published using strongly typed objects. The sample then deletes the presence categories that it published, terminates the endpoint, and shuts down the platform, exiting normally.

To see the categories being published, you can log on to a client (such as Microsoft Lync 2013), as the same user as the sample is using.

## Features

  - Presence publication using a grammar and strongly-typed categories.

## Prerequisites

  - Microsoft Lync Server 2013.

  - One user, enabled to use Lync Server 2013.

  - The credentials for that user.

## Running the sample

1.  Supply the configuration settings to be used by the sample in the accompanying App.config file, you will be prompted for them when you run the sample.

2.  Open the project in Microsoft Visual Studio development system, and then press **F5**.

3.  Change the presence of the user logged on to Lync 2013, and see the presence change in the console.

