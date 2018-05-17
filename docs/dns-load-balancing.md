---
title: DNS load balancing
TOCTitle: DNS load balancing
ms:assetid: c9a63210-ada3-4a93-aa57-4fdbe0a95dc2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465931(v=office.15)
ms:contentKeyID: 57102425
ms.date: 07/25/2014
mtps_version: v=office.15
---

# DNS load balancing


_**Applies to:** Lync 2013 | Lync Server 2013_

In Microsoft Unified Communications Managed API 4.0 provides inherent support for DNS-based load balancing. When multiple connections are made to a pool that can resolve to multiple IP addresses, connections can be distributed across multiple available servers. If a server instance is offline, the platform can detect this state, and will disable attempts to connect to the offline server instance for ten minutes. This is assumed to be the approximate minimum amount of time required for a server (Microsoft Lync Server 2013 or application) to stop and start, update, and be restored. The ability to perform DNS-based load balancing is helpful for building scalable applications. An application can take advantage of this functionality with no additional code. For more information, see [General application activation](general-application-activation.md).

