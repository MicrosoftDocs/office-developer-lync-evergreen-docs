﻿---
title: Platform and endpoints
TOCTitle: Platform and endpoints
ms:assetid: de5868bc-9ac7-4f88-b700-a2efce8d531e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466045(v=office.15)
ms:contentKeyID: 57103038
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Platform and endpoints


**Applies to:** Lync 2013 | Lync Server 2013

The [CollaborationPlatform](https://msdn.microsoft.com/library/hh385176\(v=office.15\)) class provides connection management, message dispatching, and other services to endpoints. An application creates an instance of the **CollaborationPlatform** class to take advantage of the Microsoft Unified Communications Managed API 4.0 infrastructure. An application developer can use one of the constructors in this class to create a server platform, from which an application server can be created. Another constructor can be used to create an auto-provisioned application server platform, and a third constructor in this class can be used to create a client platform, on which a number of user endpoints can be created.

The following illustration shows the principal classes that represent the two platform types and the three endpoint types.

![UCMA platform and endpoint classes](images/Dn466045.UCMA-Platform-Endpoint(Office.15).jpg "UCMA platform and endpoint classes")

## In this section

  - [Client platforms](client-platforms.md)

  - [Server platforms](server-platforms.md)

  - [User endpoints and application endpoints](user-endpoints-and-application-endpoints.md)

  - [Incoming message dispatching](incoming-message-dispatching.md)

  - [Trusted applications](trusted-applications.md)

  - [Trusted domains and SIP gateways](trusted-domains-and-sip-gateways.md)

