---
title: Endpoint services
TOCTitle: Endpoint services
ms:assetid: ede76548-3ff1-4c12-a4ca-08f62399be7c
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465953(v=office.15)
ms:contentKeyID: 57102444
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Endpoint services


**Applies to:** Lync 2013 | Lync Server 2013

The endpoint (an [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) or [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)) instance) plays a central role in Microsoft Unified Communications Managed API 4.0 because of the access it provides to the communication and collaboration infrastructure.

After a [CollaborationPlatform](https://msdn.microsoft.com/library/hh385176\(v=office.15\)) instance is created, it can be used to create one or more endpoints. An endpoint can then be used to create a conversation, schedule an upcoming conference, publish presence information to others, subscribe to the presence of other parties, manage your contacts, or collect related contacts into groups.

## Communication framework

The communication framework can be used to create conversations or to schedule and manage an upcoming conference.

### Conversations

An endpoint owner (the endpoint’s local owner) can use it to create multiple conversations ([Conversation](https://msdn.microsoft.com/library/hh349224\(v=office.15\)) instances), where each conversation can have one or more remote participants, and can use a single media mode (such as instant message) or use multiple media modes (such as instant message and audio). For more information, see Conversation.

### Conference management

An endpoint’s access to a [ConferenceServices](https://msdn.microsoft.com/library/hh348907\(v=office.15\)) instance makes it possible for the organizer of a conference to schedule, update, or cancel a conference, and carry out other operations in advance of a conference. For more information, see [Conference scheduling and management](conference-scheduling-and-management.md) and [ConferenceServices](https://msdn.microsoft.com/library/dd279792\(v=office.15\)).

## Collaboration framework

The collaboration framework represents the functionality that can be used to convey the presence information of a presentity to others, get the presence information of remote participants, manage contacts, and organize contacts into meaningful groups.

### Presence publishing

An endpoint provides access to a [LocalEndpointPresenceServices](https://msdn.microsoft.com/library/hh350157\(v=office.15\)) instance and a [LocalOwnerPresence](https://msdn.microsoft.com/library/hh382370\(v=office.15\)) instance, which enable an endpoint’s local owner to publish presence information, acknowledge subscriptions requests from remote participants, and carry out related operation. For more information, see [Presence - self and remote](presence-self-and-remote.md), Publishing Presence, and [LocalOwnerPresence](https://msdn.microsoft.com/library/dd279776\(v=office.15\)).

### Presence subscription

An endpoint also provides access to a [RemotePresence](https://msdn.microsoft.com/library/hh349758\(v=office.15\)) instance. The local owner of the endpoint can use this object to subscribe to the presence information of remote presentities. For more information, see [Presence - self and remote](presence-self-and-remote.md), [Subscribing to Presence](https://msdn.microsoft.com/library/dd280151\(v=office.15\)), and [RemotePresence](https://msdn.microsoft.com/library/dd280143\(v=office.15\)).

### Contacts and groups

**UserEndpoint** instances (but not **ApplicationEndpoint** instances) have access to a [ContactGroupServices](https://msdn.microsoft.com/library/hh381099\(v=office.15\)) instance. This access makes it possible to add, update, or delete a contact, add, update, or delete a group, and carry out other operations on contacts or groups. For more information, see [Contacts and groups](contacts-and-groups.md) and [ContactGroupServices](contactgroupservices.md).

