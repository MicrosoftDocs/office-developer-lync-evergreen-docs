---
title: Managing self-published contact lists
TOCTitle: Managing self-published contact lists
ms:assetid: 0006101d-f412-48c3-936f-62a783a43151
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454628(v=office.15)
ms:contentKeyID: 57093092
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Managing self-published contact lists


_**Applies to:** Lync 2013 | Lync Server 2013_

Microsoft Lync 2013 uses the enhanced presence publication and subscription mechanism to store the user’s contact list on the server and to roam the contact list across multiple user endpoints.

In Lync 2013, a contact list is described by a collection of the contacts and groups category instances. When the user adds another user to his or her contact list, Lync 2013 publishes a contacts category instance to the user’s self-container. When a new group is created for organizing the entries in the contact list, a groups category instance is published to the container, as well. Each time when Lync 2013 starts, it retrieves the contact list from the server by subscribing to the already published contacts and groups category instances.

At the protocol level, receiving a contact list involves submitting a SUBSCRIBE request. The returned contact list does not contain any presence information of the contacts. To receive the contacts presence publications, a separate subscription must be created and maintained.

At the API level, the SIP messages are encapsulated by the API types and the associated operations are exposed as methods of the API types. This section discusses how to use Microsoft Unified Communications Managed API 4.0 to manage a contact list.

## In this section

  - [Preparing to receive a contact list](preparing-to-receive-a-contact-list.md)  

  - [Receiving contacts and groups](receiving-contacts-and-groups.md)  

  - [Maintaining contacts and groups](maintaining-contacts-and-groups.md)  

  - [Receiving contacts presence](receiving-contacts-presence.md)  

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

[Programming with Enhanced Presence](programming-with-enhanced-presence.md)

[General features of Enhanced Presence](general-features-of-enhanced-presence.md)

