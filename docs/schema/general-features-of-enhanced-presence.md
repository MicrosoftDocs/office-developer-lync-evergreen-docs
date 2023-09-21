---
title: General features of Enhanced Presence
TOCTitle: General features
ms:assetid: c5fd4776-1b16-4118-b4a3-ca3df698dd0e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454616(v=office.15)
ms:contentKeyID: 57093344
ms.date: 07/24/2014
mtps_version: v=office.15
---

# General features of Enhanced Presence

Learn how to use Unified Communications Enhanced Presence Schemas in a Microsoft Lync Server 2013 deployment.


**Applies to:** Lync 2013 | Lync Server 2013

Lync Server 2013 includes a general presence publication and presence subscription framework that the clients can use for the user to share the enhanced presence data with others. In this process, a unified communications client determines how enhanced presence data is used in a particular application, because the semantics of enhanced presence data is application-specific.

Microsoft Lync 2013 is a unified communication client that defines the enhance presence data model that is specified by the enhance presence schemas. For information about the enhanced presence data model, see [Lync-defined Enhanced Presence category instance elements](lync-defined-enhanced-presence-category-instance-elements.md).

Other unified communications clients can use and extend the Lync 2013-supported presence features. Alternatively, they can define and implement their own custom presence features. The first kind of application is tied to Lync 2013 and it leverages the enhanced presence features that are included with Lync 2013 by automating a running Lync 2013 instance. The second kind of application may be a Lync 2013-like client with application-specific requirements and behaviors. They may or may not interoperate with Lync 2013.

This section is a general overview of the enhanced presence subsystem and provides programming guidance to enable custom presence features in a Lync Server 2013 deployment. Code examples that are based on Microsoft Unified Communications Managed API (UCMA) 4.0 are used to demonstrate enhanced presence features. For information about Lync 2013-specific presence features, see [Lync-specific features of Enhanced Presence](lync-specific-features-of-enhanced-presence.md).

## In this section

  - [Introducing Enhanced Presence](introducing-enhanced-presence.md)  
    Overview of enhanced presence that is supported by Lync Server 2013 and Lync 2013, including the data model, infrastructure, and programming interfaces.

  - [Enhanced Presence data](enhanced-presence-data.md)  
    Describes an XML-based data type system, known as presence categories, to represent enhanced presence data.

  - [Programming with Enhanced Presence](programming-with-enhanced-presence.md)  
    Overview of the enhanced presence publication mechanism that is supported by Lync Server 2013, including access control using containers, multiple point of presence (MPOP) using aggregation, and general methodology of presence publication with UCMA.

  - [Publishing Enhanced Presence](publishing-enhanced-presence.md)  
    Describes the general programming patterns used to publish enhanced presence with UCMA.

  - [Receiving Enhanced Presence](receiving-enhanced-presence.md)  
    Describes the general programming patterns for enhanced presence subscription and query with UCMA.

  - [Managing self-published contact lists](managing-self-published-contact-lists.md)  
    Describes how an application can use the enhanced presence infrastructure to maintain a contact list for the user and to cache server-provisioned data and other application data.

  - [Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)  
    Describes how to receive in-band provisioning data.

## See also

#### Concepts

[Lync-specific features of Enhanced Presence](lync-specific-features-of-enhanced-presence.md)

[Get started with Enhanced Presence](get-started-with-enhanced-presence.md)

#### Other resources

[Lync Videos on Channel9](http://channel9.msdn.com/tags/lync)

