---
title: Get started with Enhanced Presence
TOCTitle: Get started
ms:assetid: 65a43945-0be1-4e6e-ade2-e14957dd0ff0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454615(v=office.15)
ms:contentKeyID: 57092864
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Get started with Enhanced Presence

This section discusses enhanced presence in Microsoft Lync Server 2013 deployments.


_**Applies to:** Lync 2013 | Lync Server 2013_

A unified communications application establishes real-time communication between users and identifies the presence of each user. A typical unified communications application publishes presence data to specify availability, activities and supported device capabilities, calendar data, contact information, and other user information. It also needs to support presence subscription for the user to discover the presence information published by other users. Such presence information allows the users to determine when and how to contact each other.

Enhanced presence, as supported in a Lync Server 2013 deployment, lets an application developer include any information as part of the presence. It also provides a flexible mechanism for the application developer to publish the presence information in a way that the user controls what presence data is published, who can access the publications, and how much information a subscriber may receive. It does so with a flexible data model to represent many types of presence information, which is also supported by a robust access control mechanism for publishing, subscribing to and querying the enhanced presence.

In a Lync Server 2013 deployment, the enhanced presence schemas are exposed to third-party application developers through various APIs, including Microsoft Unified Communications Managed API 4.0 and Microsoft Lync 2013 SDK. With these APIs, presence data can be created, parsed, and manipulated by using supported API objects instead of the raw XML-blobs. In Lync SDK, all the supported presence data is encapsulated. However, UCMA might require the application to explicitly construct or parse some presence data as XML blobs. This is especially true when the application must handle custom presence data.

## In this section

  - [Enhanced Presence application scenarios](enhanced-presence-application-scenarios.md)  
    Describes application scenarios that are used to demonstrate general presence functionality.

  - [General features of Enhanced Presence](general-features-of-enhanced-presence.md)  
    Overview of the enhanced presence publication mechanism that is supported by Lync Server 2013. Discusses access control using containers, support of multiple point of presence (MPOP) using aggregation, and general programming patterns for presence publication and subscription.

  - [Lync-specific features of Enhanced Presence](lync-specific-features-of-enhanced-presence.md)  
    Describes how Lync 2013 publishes and uses enhanced presence information.

  - [Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)  
    Describes how a third-party application can support presence privacy and interoperability with Lync.

  - [Extension and customization of a category schema](extension-and-customization-of-a-category-schema.md)  
    Discusses how publication grammars are used to support presence privacy and interoperability, especially the interoperability with Lync 2013.

  - [Serialization of Enhanced Presence category instances](serialization-of-enhanced-presence-category-instances.md)  
    Explains how to the category schema files and the XmlSerialization namespace to create and parse enhanced presence category instances.

## See also

#### Reference

[Lync-defined Enhanced Presence category instance elements](lync-defined-enhanced-presence-category-instance-elements.md)

#### Concepts

[Unified Communications Enhanced Presence Schemas for Lync Server 2013 general reference](unified-communications-enhanced-presence-schemas-for-lync-server-2013-general-reference.md)

#### Other resources

[Lync Videos on Channel9](http://channel9.msdn.com/tags/lync)

[\[MS-PRES\]: Presence Protocol Specification](http://go.microsoft.com/fwlink/?linkid=195873)

[Video: Introduction to the Enhanced Presence Schemas](http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.html?cid=ldc%26from=mscomldc%26videoid=bda5af63-bcf5-4fa7-8d68-fa936da0c2c9)

