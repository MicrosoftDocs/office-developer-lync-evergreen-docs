﻿---
title: Subscribing to presence
TOCTitle: Subscribing to presence
ms:assetid: 1ce5c2e2-d15c-46b7-8a21-c425223e8aef
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465955(v=office.15)
ms:contentKeyID: 57102446
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Subscribing to presence


**Applies to:** Lync 2013 | Lync Server 2013

A communication application often must watch the presence of other users to make smart decisions when routing a call. Here are few examples:

  - A watcher application in a Contact Center watches for the presence of agents so that a new customer call can be routed successfully to an available agent as soon as possible. To increase customer satisfaction, Contact Centers have an incentive to resolve customers’ calls in the first call to an agent.

  - A Microsoft Unified Communications Managed API 4.0-based web reach application might enable its users to persistently subscribe to its contacts’ presence so that the user may use the presence information before starting a conversation. An example of how this can be useful is a user not even trying to start a phone call when the remote user is offline and instead using email.

  - A UCMA 4.0-based notification application might use a remote user’s presence to decide how to route a notification in an appropriate modality. For example, the notification application can decide to send an instant message when the remote user is online, and send an e-mail when the remote user is offline.

## Problems in subscribing to remote presentities

When an application accesses the presence data for a remote presentity, it must often overcome the following common problems.

### Subscribing to a remote presentity in multiple contexts

For collaboration applications, a common requirement is to be able to monitor and display the presence for a given set of presentities in different contexts, such as the following:

  - Showing the presence of contacts in a contact list.

  - Showing the presence of participants in a conversation window.

  - Showing the presence of others in web applications such as Outlook Web Access.

All of these scenarios require an endpoint to dynamically subscribe to, unsubscribe from, or query for the presence of a different set of presentities. A Microsoft Lync Server 2013 protocol constraint—Lync Server 2013 allows only one subscription dialog per endpoint per server—makes it difficult for applications to build such contextual presence monitoring from a single endpoint. In addition, subscribing to the same user from an endpoint in different contexts causes an error condition. Applications must deal with this situation either by creating their own complex reference counting mechanism (keeping track of who is and who is not already subscribed to), or by falling back to suboptimal ways of obtaining presence information, such as polling for presence at some regular interval, or by performing one-time presence queries.

### Deciding between persistent subscriptions, polling, or one-time queries

Different applications have different needs with regard to how up-to-date presence data must be. Some applications that manage contact lists for users might require persistent subscriptions to receive the most current presence state of their contacts. Applications that show presence in conversation windows, and that do not require the most current presence information, can perform a one-time presence query. For still other applications, polling for presence at regular intervals might be all that is needed. Application developers must weigh the costs and benefits of each technique—persistent subscriptions, polling, one-time queries—of receiving presence information.

### Working with server constraints

Due to server resource constraints, Lync Server 2013 has a limit on the number of subscribers who can subscribe to a given presentity. All persistent subscriptions are submitted to the server and not directly to the individual publishers being subscribed to. The maximum number of subscribers who can subscribe to a given presentity is specified in the Presence Policy Settings that can be configured by a Lync Server 2013 administrator. For more information about the details of the presence policy, see "Receiving Presence Category Instances" in Unified Communications Enhanced Presence Schema Reference (2013 Release).

Lync Server 2013 also places a limit on the subscription response body length, so an application that subscribes to a large number of users (typically more than 1000 users) might receive an error response from Lync Server 2013.

## UCMA solution for subscribing to remote presentities

Most of the problems described above are addressed by the [RemotePresenceView](https://msdn.microsoft.com/library/hh381152\(v=office.15\)) class.

  - Applications can use a consistent programming model in subscribing to presence, choosing among a pull model with a refresh interval (polling Lync Server 2013), a push model (persistent subscription to Lync Server 2013), or an autopilot model (the default).
    
    If an application uses the default model, UCMA 4.0 optimizes subscriptions to switch to polling for presentities whose subscription limits are reached (such as bots). Other presentities that are subscribed to in the remote presence view remain unaffected by the downgrade from persistent subscription to polling.

  - Applications can create multiple views in different contexts without being concerned about the underlying protocol details or server limitations.

  - By default, the **contactCard**, **calendarData**, **state**, **services**, and **note** presence categories are subscribed to. The default categories can be easily modified to include non-default categories such as **noteHistory**.

  - There are several ways to deal with the problem of a large number of persistent subscriptions, resulting in an error response from Lync Server 2013.
    
      - Because the limit is for each endpoint, the application can create multiple watcher endpoints to distribute the load.
    
      - Because the limit is for each Lync Server 2013 pool, the administrator can distribute users across multiple pools to distribute the load.
    
      - As a best practice for dealing with a large number of subscriptions, it is recommended that a UCMA 4.0 application limit the number of categories it subscribes to. This can be accomplished by supplying a filter when the endpoint is created. By limiting the number of categories, more subscriptions are allowed.

  - If users in the public cloud (such as Windows Live Messenger or Yahoo™) are subscribed to, the default subscription mode in **RemotePresenceView** should be used. The polling mode is not inherently supported from a protocol perspective.

UCMA 4.0 also supports a one-time presence query of a remote presentity, as using the **RemotePresenceView** class may not be an optimal solution in that situation.

UCMA 4.0 also enables applications to raise a notification on the remote-user side when a user subscribes to the remote-user for the first time. This notification enables the remote-user to assign an appropriate relationship level.

For more information, see [RemotePresenceView](remotepresenceview.md).

