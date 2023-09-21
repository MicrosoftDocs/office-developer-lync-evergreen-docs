---
title: Trusted applications
TOCTitle: Trusted applications
ms:assetid: 12b41b03-6149-4e97-bc70-adaeb2aa28e3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466044(v=office.15)
ms:contentKeyID: 57103037
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Trusted applications


**Applies to:** Lync 2013 | Lync Server 2013

A typical Microsoft Unified Communications Managed API 4.0 application is trusted by Microsoft Lync Server 2013.

There are two types of trusted applications. The two types differ by the type of endpoint used:

  - Communication-enabled and collaboration-enabled applications use [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)).

  - Middle-tier client applications that emulate Microsoft Lync 2013 use [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)).

## Communication-enabled and collaboration-enabled applications

Examples include Automated Call Distributor, Instant Messaging (IM) Bot, Interactive Voice Response, Conference Bridge, and Personal Virtual Assistant.

An **ApplicationEndpoint** endpoint designates a service involving communications, possible user interactions, and collaborations. It's represented by a [Contact](https://msdn.microsoft.com/library/hh381065\(v=office.15\)) object in Active Directory. It can communicate, using IM or audio, with one or more remote parties, and can collaborate using presence (through Enhanced Presence subscription and publication). **ApplicationEndpoint** can be assigned a SIP URI and a Dialed Number Identification Service (DNIS) telephone number.

Applications that require multimodal communications or presence must register against Lync Server 2013.

**ApplicationEndpoint** is globally trusted and uses server permissions. It's highly available.

**ApplicationEndpoint** load balances communications across multiple Front End Servers.

## Middle-tier client applications

Examples include Web clients.

A **UserEndpoint** designates an Information Worker endpoint. An Information Worker is represented by a **User** object in Active Directory. A **UserEndpoint** endpoint is assigned an Address of Record (AOR) and registers against Lync Server 2013.

**UserEndpoint** is not globally trusted and cannot impersonate another user or join a conference as a trusted user.

**UserEndpoint** caches one connection that is used for all its communications and collaborations.

