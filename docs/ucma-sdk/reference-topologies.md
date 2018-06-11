---
title: Reference topologies
TOCTitle: Reference topologies
ms:assetid: db9cfb90-90dd-4319-b98f-7cc47f2f1d82
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465966(v=office.15)
ms:contentKeyID: 57102662
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Reference topologies


**Applies to:** Lync 2013 | Lync Server 2013

The ideal Microsoft Lync Server 2013 communications software topology depends on the organization’s size, the workloads that will be deployed, and preferences for high availability versus cost of investment.

The topics in this section outline three reference topologies, and provide the reasoning behind many of the decisions that drive the requirements for each topology.

## Redundant application deployment in Microsoft Lync Server 2013

In a redundant application deployment, multiple servers run instances of the same UCMA 4.0 application, as in the typical deployment shown in the following illustration. Unlike redundant application deployment in Office Communications Server 2007 R2, the Contoso application server pool no longer requires a hardware load balancer to successfully distribute traffic across all application instances. Instead, DNS-based load balancing, a system of cycling between servers based on DNS A records, serves to balance new connections.

DNS-based load balancing, from the application developer’s perspective, is primarily a matter of properly configuring the application’s host machines in DNS, provisioning the application and application pool in Lync Server 2013, and then creating the appropriate certificates, trusted service ports, and optionally contact objects or user objects in Active Directory. For more information, see [Activating a UCMA 4.0 trusted application](activating-a-ucma-4-0-trusted-application.md).

The following are the important points about load balancing in Lync Server 2013:

  - Both hardware load balancing and DNS-based load balancing are supported for application pools for Lync Server 2013.

  - Application deployment and provisioning are identical in the hardware load-balanced and DNS-load-balanced cases, except for one additional step in DNS-based load balancing. That step consists of configuring multiple A records in DNS for the application pool FQDN.

  - Application draining requires DNS-based load balancing to function.

  - DNS-based load balancing of incoming connections is necessary only for trusted server applications. Endpoints that use client credentials are rung simultaneously on an incoming call.

  - No additional application code is required to enable DNS-based load balancing, as compared to hardware load balancing.

  - An administrator deploying an application can choose either hardware load balancing or DNS-based load balancing at deployment time, but an application pool must use only one method of load balancing (either hardware or DNS-based).

  - If there are multiple Lync Server 2013 front end servers, outbound connections from UCMA 4.0 to Lync Server 2013 servers are also load balanced using either DNS-based load balancing or hardware load balancing, depending on whether the Lync Server 2013 Front End deployment uses DNS-based load balancing or hardware load balancing. Regardless of which load-balancing method is used, UCMA 4.0 should be pointed to the Lync Server 2013 Front End pool FQDN as its next hop.

## In this section

  - [Reference topology with limited high availability](reference-topology-with-limited-high-availability.md)

  - [Reference topology with high availability and a single data center](reference-topology-with-high-availability-and-a-single-data-center.md)

  - [Reference topology with high availability and multiple data center](reference-topology-with-high-availability-and-multiple-data-center.md)

