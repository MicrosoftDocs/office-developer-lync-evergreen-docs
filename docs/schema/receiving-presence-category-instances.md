---
title: Receiving presence category instances
TOCTitle: Receiving presence category instances
ms:assetid: 071c0511-743b-4665-920e-6d8371aa2097
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454640(v=office.15)
ms:contentKeyID: 57093181
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Receiving presence category instances


**Applies to:** Lync 2013 | Lync Server 2013

 

By using the Microsoft Lync Server 2013, a user can access and monitor the presence published by his or her contacts or other unified communications-enabled clients through subscription or query, provided that the subscriber is granted permission by the publishers to access the presence information. For information about access controls, see [Controlling access to presence publications](controlling-access-to-presence-publications.md).

Both subscription and query involves the following steps:

  - A client submits SUBSCRIBE requests containing the specified category names and publisher’s SIP URI.

  - The server dispenses permissible publications to the requesting clients through event notifications.

The difference is that the subscription is tied to a period of time whereas the query is one-time only.

Subscription can be further classified as persistent subscription and polling subscription. In a persistent subscription, the client submits a single SUBSCRIBE request and the server continues to dispatch the event notifications, until the subscription period ends, whenever a publication is created or modified. The client must be registered with the server as a presence watcher. In a polling subscription, the client continues to submit SUBSCRIBE requests periodically, each at a fixed time interval, and the server issues notifications in response to each request. The client is not registered as a watcher with the server.

## Persistent subscription

Persistent subscription enables the subscriber to receive new or modified publications in real time over a period of time, also referred to as a subscription session. The period starts when the subscriber submits a SUBSCRIBE request to the server successfully. It ends when the subscriber terminates the subscription or when the subscribing endpoint logs off. Throughout a subscription period, the subscriber is automatically updated with the latest presence data.

All the subscription requests are submitted to the server, not directly to the individual publishers. For persistent subscription, the server maintains a list of presence subscribers for each presence publisher. Due to the resource constraints on the server, this number is limited. The maximum number is specified as the presence policy settings that can be configured by a Lync Server 2013 administrator.

A presence policy is set using the following two properties:

  - CategorySubscriptions  
    This is the maximum number of categories that can be subscribed to on a presence publisher. The value of this property ranges between 0 and 3000, inclusively. When this is set to zero, no one can persistently subscribe to any presence of a presentity. If it is greater than zero, the maximum number of persistent subscribers permitted on a presentity is determined by the CategorySubscriptions value divided by the number of subscribed categories. If CategorySubscriptions is set to 3000 and a client chooses to subscribe to a single category, for example, the state category, the maximum number of persistent subscribers will be 3000. If a client subscribes to two categories, for example, the state and note categories, the maximum number of persistent subscribers will be 1500.

  - PromptedSubscribers  
    This is the maximum number of queued presence subscription alerts. It determines the maximum number of prompts that user can get when someone else subscribes to his or her presence. The value ranges between 0 and 500. The zero value means that the user is not notified when he or she is added to a persistent subscription by someone else. When the number of persistent subscriptions in the queue reaches the limit set by this property, the user will not be notified of any additional subscription attempts.

By default, Lync Server 2013 is configured with the following two presence policies:

  - Default policy  
    This is the default presence policy for typical users in which the CategorySubscriptions property is set to 1000 and the PromptedSubscribers property is set to 200.

  - Service: medium  
    This is the presence policy for applications or services in which a large number of users must subscribe to the presence published by the applications or services. The CategorySubscriptions property is set to 3000 and the PromptedSubscribers property is set to 0.

Setting too high a value on the CategorySubscriptions property can have a significant adverse impact on the server performance when the average user has a large number of persistent presence watchers. Setting a value too low on this property may prevent some contacts from receiving the presentity’s presence at all. For a popular contact whose presence is subscribed to by many other users, it is possible that the contact’s presence may appear unknown to some subscribers.

For information about how to configure the presence policy, see [Managing Presence Policies](http://go.microsoft.com/fwlink/?linkid=188704).

When the required number of persistent subscriptions reaches beyond the maximum limit or when the maximum value is too high to ensure reliable performance, a presence application can resort to polling subscriptions in which the policies do not apply.

## Polling subscription

Polling subscription lets the subscriber receive presence publications at fixed time intervals over a period of time. At the prescribed time intervals, the subscribing client submits SUBSCRIBE requests and the server delivers the requested information to the watcher as event notifications. As with the persistent subscription, the process is asynchronous. However, unlike in a persistent subscription, it does not require the presence watcher be registered with the server. To obtain another view of the presence of the same publishers at a later time, the presence watcher must resubmit another polling SUBSCRIBE request.

For polling subscriptions, the presence policy setting of the **CategorySubscriptions** property does not apply and there is no limit on how many presence watchers the server can handle.

## Querying presence

A query allows the requesting client to receive published presence information at a single point of time. It involves a single SUBSCRIBE request to the server. As with subscription, the server delivers the requested publication to the requesting client through event notifications. As with polling subscriptions, presence queries are not subject to the limit set by the presence policy of the **CategorySubscriptions** property. A polling subscription can be thought of as a series of queries periodically executed at fixed time intervals.

## Local and remote presence

The Lync Server 2013-supported presence publication and subscription can be thought of as a general-purpose mechanism for data provisioning. As long as it can be modeled as category instances, the data can be about presence or some other information related to a user. The publication lets a user organize and store data on the server and lets the user control how the data may be accessed by the other users. The subscription, persistent or polling, allows the other users to receive or retrieve the accessible information from the server.

A user can use the publication and subscription infrastructure to publish data for others to consume. This user can also use it to store data for self-consumption. An example of the latter case is the roaming data of the user. In Lync Server 2013, the data used by others is sometimes referred to as remote presence and the data used for self-consumption is known as self presence. To receive both the remote and self presence, separate subscription sessions are needed.

In self-subscription, you get more detailed information whereas in remote subscription you get only a limited amount of information due to the restrictions imposed by the other publishers. For example, in self-subscription you can confirm not only what presence category you have published, but also which containers they were published to. However, in remote subscription, you do not get any information about the containers from which the received presence data came from. This also means that for certain presence data, such as the presence state, published from multiple endpoints, you will receive individual endpoint-specific presence states in a self-subscription.

However, in remote subscription you will only receive a single user-specific presence state that is aggregated over all the endpoint-specific presence states, as shown in the following presence state received in a remote subscription session.

    <state xsi:type="aggregateState" 
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           xmlns="http://schemas.microsoft.com/2006/09/sip/state">
        <availability>3500</availability>
        <device>computer</device>
    </state>

In Microsoft Unified Communications Managed API (UCMA) 4.0, the self-subscription is encapsulated by the **LocalOwnerPresence** class and a remote subscription is managed by using a **RemotePresenceView** object. Query is handled by using the LocalEndpointPresenceServices object. Both the **LocalOwnerPresence**, **LocalEndpointPresenceServices** and **RemotePresenceView** objects are obtained from a local **LocalEndpoint** instance. **LocalOwnerPresence** encapsulates the features of presence publication as well.

## See also

#### Concepts

[Receiving Enhanced Presence](receiving-enhanced-presence.md)

[Programming with Enhanced Presence](programming-with-enhanced-presence.md)

