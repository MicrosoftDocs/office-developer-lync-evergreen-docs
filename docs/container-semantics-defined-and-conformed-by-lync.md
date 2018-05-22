---
title: Container semantics defined and conformed by Lync
TOCTitle: Container semantics defined and conformed by Lync
ms:assetid: cc304c9b-6808-493a-80de-c5d0b812e05a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454663(v=office.15)
ms:contentKeyID: 57093186
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Container semantics defined and conformed by Lync


_**Applies to:** Lync 2013 | Lync Server 2013_

This section describes the containers that Microsoft Lync 2013 uses to control user access to published presence data.

## In this section

  - [Default container](default-container.md)  
    Used to allow access to the contained non-private category instances by users or entities that are not members of any other containers and to apply specified routing rules to forward or block calls from such remote users.

  - [Self container](self-container.md)  
    Used as a local cache of category instances that are accessible to the local user only.

  - [Aggregation containers](aggregation-containers.md)  
    Used to contain presence data that are subject to aggregation by the server-hosted aggregation script. The contained data is visible to the local user only.

  - [External Contacts container](external-contacts-container.md)  
    By default, this is used to allow federated network users to access the contained non-private presence data and to apply specified routing rules to forward or block calls from such remote users.

  - [Colleagues container](colleagues-container.md)  
    Used to allow users of the same enterprise network to access the contained non-private presence data and to route or block calls from such remote users.

  - [Workgroup container](workgroup-container.md)  
    Used to allow the specified users, who are considered as belonging to the local user’s work groups, to access the contained non-private presence data and to apply the specified routing rules to forward or block calls from such remote users.

  - [Friends and Family container](friends-and-family-container.md)  
    Used to allow the specified users, who are considered as the local user’s friends and family members, to access the contained non-private presence data and to apply specified routing rules to forward or block calls from such remote users.

  - [Blocked Contacts container](blocked-contacts-container.md)  
    Used to prevent the specified users from accessing the specified category data and to apply specified routing rules to block calls from such remote users.

## See also

#### Concepts

[Lync-specific features of Enhanced Presence](lync-specific-features-of-enhanced-presence.md)

