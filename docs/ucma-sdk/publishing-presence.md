---
title: Publishing presence
TOCTitle: Publishing presence
ms:assetid: 49504cd7-0dc0-4bee-9a28-1a81e33c69a2
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465950(v=office.15)
ms:contentKeyID: 57102442
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Publishing presence


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Unified Communications Managed API 4.0 permits automatic presence publications for UCMA 4.0 endpoints during endpoint establishment. This applies to the [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) and [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)) types.

## Automatic presence publication

Automata and automated service applications that persist their presence information (such as by publishing "always online") can use new and simplified APIs to publish this information one time during endpoint startup. Similarly, user endpoints can have their presence information enabled at startup and can use the simplified APIs to maintain their presence information for the life of the endpoint. This functionality can be achieved by setting a single property.

Using UCMA 4.0, it is also easy to modify or delete an existing presence publication. UCMA 4.0 can be used to delete or modify all publications that are made to different relationship levels to address different types of watchers.

For more information, see [Presence, contacts, and groups](presence-contacts-and-groups.md).

## Simplified category publication

For applications whose publishing needs are more complex, UCMA 4.0 provides new classes for common presence categories, including the [ContactCard](https://msdn.microsoft.com/library/hh382040\(v=office.15\)), [PresenceState](https://msdn.microsoft.com/library/hh350296\(v=office.15\)), [Note](https://msdn.microsoft.com/library/hh382265\(v=office.15\)), and [Services](https://msdn.microsoft.com/library/hh385140\(v=office.15\)) classes. The developer is not expected to know the XML schema for the common presence categories. However, XML can be used in advanced scenarios that involve publishing advanced categories (such as the routing category, which is used to specify routing rules for forwarding incoming calls), or publishing a custom category. For more information about registering a custom category name with Microsoft Lync Server 2013, see [Registering Custom Category Names](http://msdn.microsoft.com/library/hh380075\(v=office.15\)) in Unified Communications Enhanced Presence Schemas for Lync Server 2013 Documentation.

