---
title: Publishing presence category instances
TOCTitle: Publishing presence category instances
ms:assetid: 182b7fe0-2f86-4427-822a-09382956228a
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454632(v=office.15)
ms:contentKeyID: 57093176
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Publishing presence category instances


**Applies to:** Lync 2013 | Lync Server 2013

In a Microsoft Lync Server 2013 deployment, a presence publisher makes his or her presence available to other users by publishing the presence category instances. The publication amounts to specifying one or more containers, adding desired container members, and placing the presence data, as represented by category instances, through a SIP request.

Presence publication does not involve the direct exchange between the presence publisher and the presence subscriber. Instead, the server mediates the exchange between the two by simply delivering presence category instances published to a container to the registered subscribers matching the membership scope of the same container.

Lync Server 2013 supports two ways to publish presence. In one way, the presence is published according to a registered publication grammar. A publication grammar prescribes a set of publication rules and dictates the container semantics and how a particular type of presence data is published to certain containers. This is called grammar-based publication. In the other way, no publication grammar is used. This is known as grammar-free publication.

For grammar-based publications, the publishing client must follow the publication rules specified in the registered publication grammar. In Microsoft Unified Communications Managed API 4.0, the rules are enforced by the API and the publishing application needs to specify only the category names and data value and the data will go to the grammar-stipulated containers.

For grammar-free publications, the publishing client using UCMA must also specify the Container ID as well as other attributes of a category instance.

Microsoft Lync 2013 defines two publication grammars to publish presence to the predefined containers. One set of publication grammars is used in the privacy mode and the other is used in the non-privacy mode, also known as the open mode. In the privacy mode, the grammar specifies the container semantics only and the user must explicitly specify what presence data should be published. By default, no presence data should be made available in the privacy mode. In the open mode, however, a set of default category instances are published without any user intervention.

In a Microsoft Lync Server 2013 deployment, a grammar-based publication implies using a publication grammar defined by Lync 2013. With this grammar, for example, when the user sets a personal note message using Lync 2013, a [note category instance value element](note-category-instance-value-element.md) presence category instance containing the user-supplied message text is placed to Container 200, 300 and 400. An empty [note category instance value element](note-category-instance-value-element.md) category instance is also placed to Containers 100 and 3200 at the same time. The same behavior is followed by all the grammar-based publications of other category instances. Thus, the grammar-based publication ensures that other unified communications clients follow the same publication logic implemented by Lync 2013 and that they interoperate with each other seamlessly. In grammar-free publications, an application and Lync 2013 can publish the same category data in different containers or may publish different data in the same container, causing other clients to interfere with Lync or to behave unexpectedly.

## Programming flows of presence publication

A publication involves the following three types of programming tasks:

  - To publish new presence data, add category instances containing specified category names, presence data values, instance IDs, expiration types and applicable expiration times, publication times, and version numbers to the specific containers.

  - To delete existing presence data, remove the category instances of specified category names, instance IDs, publication times, and version numbers from the specific containers. In Lync Server 2013, deleting a publication of a category instance involves publishing the category instance with the expiration type set to user and the expiration time set to zero (0). A unified communications API may expose this operation as a dedicated method. For example, UCMA exposes the **LocalOwnerPresence.BeginDeletePresence** and **LocalOwner.EndDeletePresence** method.

  - To modify existing presence data, replace the values on the category instances of specified category names, instance IDs, expiration types and applicable expiration times, publication times, and version numbers in the specific containers. Replacing a category instance amounts to republishing the category instance.

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

[Programming with Enhanced Presence](programming-with-enhanced-presence.md)

