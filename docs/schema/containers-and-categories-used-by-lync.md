---
title: Containers and categories used by Lync
TOCTitle: Containers and categories used by Lync
ms:assetid: daa69a3b-25d6-4a5a-9398-95373ef24d15
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454630(v=office.15)
ms:contentKeyID: 57093185
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Containers and categories used by Lync


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Lync 2013 makes a distinction between the data that can be accessed only by the local user and the data that can be accessed by other users. It does so by designating one set of containers for local user access and another set of containers for remote user access.

  - The local-access only containers are used to contain the user’s presence information, server configuration, user settings, including contact lists, and other application data. The Ids of these containers are 1, 2, and 3. They are also known as Self Container, Aggregation Container 1, and Aggregation Container 2, respectively. The data is visible only to the local user through self-subscription. Lync 2013 uses these containers to roam the user settings, including the contact list, and to initiate presence aggregation across multiple endpoints, to determine the server configuration, or to facilitate scheduling and establishing conference calls. For more information about these containers, see [Containers for local access](containers-for-local-access.md). For information about what data is published to the locally accessible containers, see [Local-access only category instances](local-access-only-category-instances.md).

  - The remotely accessible containers are used to contain the user’s sharable presence information and rules to route incoming calls. The Ids of these containers are 0, 100, 200, 300, 400, and 32000. They are also referred to, respectively, as Default Container, External Contacts Container, Colleagues Container, Workgroup Container, Friends and Family Container, and Blocked Contacts Container. Remote users receive the data by subscribing to specified categories published by the local user, provided that the remote users are members of one or more of these containers, except for the Blocked Contacts Container. Remote users do not specify containers when submitting a subscription. Lync 2013 uses these containers to control who can view what data. For more information, see [Container for remote access](container-for-remote-access.md). For information about what data is published to the remotely accessible containers, see [Remotely accessible category instances](remotely-accessible-category-instances.md).

In addition to Lync 2013, Microsoft Lync Server 2013 components (including the User Replicator and Aggregation Script) also publish certain information on behalf of the local user. Examples of such information include user properties as provisioned from the underlying Active Directory and aggregated presence information performed by the Aggregation Script.

## In this section

  - [Containers for local access](containers-for-local-access.md)  
    Describes the local-access containers used by Lync 2013.

  - [Container for remote access](container-for-remote-access.md)  
    Describes the remote-access containers defined by Lync 2013.

  - [Local-access only category instances](local-access-only-category-instances.md)  
    Describes local-access category instances published by Lync 2013 and Lync Server 2013.

  - [Remotely accessible category instances](remotely-accessible-category-instances.md)  
    Describes remote-access category instances published by Lync 2013.

## See also

#### Concepts

[Lync-specific features of Enhanced Presence](lync-specific-features-of-enhanced-presence.md)

