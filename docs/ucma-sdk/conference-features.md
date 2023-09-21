---
title: Conference features
TOCTitle: Conference features
ms:assetid: 73465dfc-ab21-4659-bb4f-f806079e3309
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465958(v=office.15)
ms:contentKeyID: 57102449
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Conference features


**Applies to:** Lync 2013 | Lync Server 2013

The topics in this section summarize the most important new or changed conferencing features in Microsoft Unified Communications Managed API 4.0. These features can be divided into three broad areas:

  - Conferencing infrastructure

  - Conference scheduling

  - Joining the conference and the in-conference experience

## Conferencing infrastructure

To learn how UCMA 4.0 Conferencing API works, it's essential to first understand the underlying infrastructure. All conferences are scheduled by the use of a Microsoft Lync Server 2013 Front End Focus Factory and stored in the User Services database. The Focus stands for the central point of conferencing command and control. It runs on every instance of a Lync Server 2013 Front End. The Multipoint Conferencing Units (MCUs) for chat, application, and desktop sharing, or data collaboration usually run on the Front End, although the Audio Video MCU runs on a separate server role of the Lync Server 2013 architecture. The MCU Factory is responsible for allocating MCUs to an activated Conference and monitoring their health. The following illustration shows a typical conferencing topology.

Microsoft Lync Server 2010 conferencing topology

  
![Conference Topology](images/Dn465958.UCMA_ConfTopology(Office.15).jpg "Conference Topology")

The following illustration shows a logical view of Lync Server 2013, together with the protocols that are used.

Logical view of Microsoft Lync Server 2010 Conferencing and protocols

  
![Conference logical topology](images/Dn465958.UCMA_ConfLogicalTopology(Office.15).jpg "Conference logical topology")

## In this section

  - [Pre-meeting: conference scheduling](pre-meeting-conference-scheduling.md)

  - [In-meeting: during the conference](in-meeting-during-the-conference.md)

