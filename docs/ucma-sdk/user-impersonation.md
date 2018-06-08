---
title: User impersonation
TOCTitle: User impersonation
ms:assetid: 4d243ea7-4131-462f-a476-f41bba5dac51
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465968(v=office.15)
ms:contentKeyID: 57102530
ms.date: 07/25/2014
mtps_version: v=office.15
---

# User impersonation


**Applies to:** Lync 2013 | Lync Server 2013

In Microsoft Unified Communications Managed API 4.0 an application (specifically, an [ApplicationEndpoint](https://msdn.microsoft.com/en-us/library/hh384825\(v=office.15\)) instance) can impersonate another user.

The following illustration depicts a two-party conversation using audio. In this illustration an application (Application A) impersonates a user (User A). In this situation, the endpoint owner and the local participant of the associated conversation instance are different. Another difference between this scenario and the two previous ones is that the endpoint for Application A must be an **ApplicationEndpoint**, rather than a [UserEndpoint](https://msdn.microsoft.com/en-us/library/hh348819\(v=office.15\)).

![Two-party conversation with impersonation](images/Dn465968.Two-party-Impersonation-AV(Office.15).jpg "Two-party conversation with impersonation")

