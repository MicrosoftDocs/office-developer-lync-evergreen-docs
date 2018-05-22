---
title: UCMA 4.0 building blocks
TOCTitle: UCMA 4.0 building blocks
ms:assetid: 8ca81f41-3f8c-427c-a9a4-18d16672a725
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465945(v=office.15)
ms:contentKeyID: 57102661
ms.date: 07/25/2014
mtps_version: v=office.15
---

# UCMA 4.0 building blocks


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Architecture  
Key features and UCMA classes  
In this section  

To understand the Microsoft Unified Communications Managed API 4.0 architecture, it is helpful to understand the classes that represent the key features of the architecture as described in [Key features of UCMA 4.0](key-features-of-ucma-4-0.md). It is also helpful to recognize that the architecture has been designed to enable these features.

## Architecture

UCMA 4.0 is divided into layers, as shown in the following illustration. At the top level are the classes that enable communication and collaboration. The next level below that provides classes that represent the collaboration platform, the foundation of UCMA 4.0 applications, and endpoints, which represent users or applications that can impersonate users. The lowest level exposed by UCMA is the signaling layer, which provides classes that encapsulate low-level Session Initiation Protocol (SIP) functionalities.

Each of the layers shown in the illustration is described in [UCMA 4.0 details](ucma-4-0-details.md).

![Major components of UCMA 4.0](images/Dn465945.UCMA-Blocks(Office.15).jpg "Major components of UCMA 4.0")

In UCMA 4.0, the entry point class is [CollaborationPlatform](https://msdn.microsoft.com/en-us/library/hh385176\(v=office.15\)). An application can create multiple CollaborationPlatform instances, and each platform instance can host multiple endpoints.

An endpoint (represented as a [UserEndpoint](https://msdn.microsoft.com/en-us/library/hh348819\(v=office.15\)) or [ApplicationEndpoint](https://msdn.microsoft.com/en-us/library/hh384825\(v=office.15\)) instance) acts as a gateway to communication and collaboration functionality in UCMA, providing access through its methods and properties to the classes that implement these functionalities.

An endpoint can use this functionality to:

  - Initiate and manage a conversation (the [GetConversations()](https://msdn.microsoft.com/en-us/library/hh349978\(v=office.15\)) method).

  - Schedule and manage conferences offline (the [ConferenceServices](https://msdn.microsoft.com/en-us/library/hh161814\(v=office.15\)) property).

  - Subscribe to the presence of remote presentities (the [PresenceServices](https://msdn.microsoft.com/en-us/library/hh384331\(v=office.15\)) property.

  - Publish presence for the endpoint owner (the [PresenceServices](https://msdn.microsoft.com/en-us/library/hh384331\(v=office.15\)) and [LocalOwnerPresence](https://msdn.microsoft.com/en-us/library/hh348476\(v=office.15\)) properties).

  - Manage contacts and groups (the [ContactGroupServices](https://msdn.microsoft.com/en-us/library/hh383122\(v=office.15\)) property).
    

    > [!IMPORTANT]
    > <P>The <STRONG>ContactGroupServices</STRONG> property is present only on a <STRONG>UserEndpoint</STRONG> object. For more information, see <A href="endpoint-services.md">Endpoint services</A>.</P>



The following illustration shows the relationships among the principal objects of the architecture as well as the personas (see [Personas](personas.md)) involved in each type of object. The numbers shown between two objects indicate the kind of pairing between the two objects that can occur. For example, one local endpoint can be associated with zero or more **Conversation** objects, but can be associated with only one Presence Subscription object.

Contacts and Groups are present only on [UserEndpoint](https://msdn.microsoft.com/en-us/library/hh348819\(v=office.15\)) instances.

![Principal objects of the UCMA architecture](images/Dn465945.UcmaArch01(Office.15).jpg "Principal objects of the UCMA architecture")

## Key features and UCMA classes

Each of the top-level feature areas described in [Key features of UCMA 4.0](key-features-of-ucma-4-0.md) is implemented in a UCMA 4.0 class. The following table lists the top-level feature areas and the class that implements the area.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Feature</p></th>
<th><p>Area</p></th>
<th><p>Main Class Name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Conversation</p></td>
<td><p>Communication</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh349224(v=office.15)">Conversation</a></p></td>
</tr>
<tr class="even">
<td><p>Conference scheduling and management</p></td>
<td><p>Communication</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh348907(v=office.15)">ConferenceServices</a></p></td>
</tr>
<tr class="odd">
<td><p>Presence publishing</p></td>
<td><p>Collaboration</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh350157(v=office.15)">LocalEndpointPresenceServices</a> and <a href="https://msdn.microsoft.com/en-us/library/hh382370(v=office.15)">LocalOwnerPresence</a></p></td>
</tr>
<tr class="even">
<td><p>Presence subscription</p></td>
<td><p>Collaboration</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh381152(v=office.15)">RemotePresenceView</a></p></td>
</tr>
<tr class="odd">
<td><p>Contacts and groups</p></td>
<td><p>Collaboration</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh381099(v=office.15)">ContactGroupServices</a></p></td>
</tr>
</tbody>
</table>


## In this section

  - [Personas](personas.md)

  - [Collaboration platform](collaboration-platform.md)

  - [Endpoint services](endpoint-services.md)

  - [Calls, flows, conversations, and MCU sessions](calls-flows-conversations-and-mcu-sessions.md)

  - [Conference scheduling and management](conference-scheduling-and-management.md)

  - [Presence - self and remote](presence-self-and-remote.md)

  - [Contacts and groups](contacts-and-groups.md)

