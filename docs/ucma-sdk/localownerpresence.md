﻿---
title: LocalOwnerPresence
TOCTitle: LocalOwnerPresence
ms:assetid: d30af895-3675-4c7c-b3d5-136ff621683a
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466019(v=office.15)
ms:contentKeyID: 57103006
ms.date: 07/25/2014
mtps_version: v=office.15
---

# LocalOwnerPresence


**Applies to:** Lync 2013 | Lync Server 2013


 

The [LocalOwnerPresence](https://msdn.microsoft.com/library/hh382370\(v=office.15\)) class has members that a presentity can use to publish its presence information to Microsoft Lync Server 2013.

## Presence publication

The [LocalOwnerPresence](https://msdn.microsoft.com/library/hh348476\(v=office.15\)) property on the endpoint can be used to manage the presence information of the endpoint owner (also known as the local presentity). Presence information consists of units of presence information called categories that can be assigned to various Access Control Lists (ACLs) that are referred to as containers. These containers provide a way for the local presentity to control access to the presentity’s presence information. For more information, see "Relationship level management" later in this topic.

Categories, identified by type, represent objects that can be published or deleted. The well-known categories that are recognized by Lync Server 2013, have schematic representations. If an application is intended to use a customized category, the category name must be configured at the server's end. Otherwise publication of such a category will be rejected by the server.

Microsoft Unified Communications Managed API 4.0 provides strongly typed definitions for some commonly used presence categories, such as [ContactCard](https://msdn.microsoft.com/library/hh382040\(v=office.15\)), [PresenceState](https://msdn.microsoft.com/library/hh350296\(v=office.15\)), [Services](https://msdn.microsoft.com/library/hh385140\(v=office.15\)), and [Note](https://msdn.microsoft.com/library/hh382265\(v=office.15\)). These classes have a common base class, the [PresenceCategory](https://msdn.microsoft.com/library/hh349560\(v=office.15\)) class. Applications can extend this base class to define custom categories and publish them using the UCMA 4.0 described here. If a developer wishes to use a simplified model to publish a category that is represented by a name and a string representation of the content XML, the [CustomPresenceCategory](https://msdn.microsoft.com/library/hh348294\(v=office.15\)) class is a simpler alternative.

Category publication involves providing the category data together with the container and instances IDs that identify where the category data are to be published. Applications that use user endpoints are strongly encouraged to take advantage of the Manifest-based publication model. Application endpoints represent an advanced publication scenario and are required to provide these details.

Category publication also involves version management, which is internally managed by UCMA 4.0.

### Manifest-based publication for UserEndpoint

It is recommended that the following simplified asynchronous methods be used for user endpoints so that a consistent behavior is achieved when interoperating with Lync so that they can remain agnostic to container ID and instance ID details.

  - [BeginPublishPresence(ICollection\<PresenceCategory\>, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh384771\(v=office.15\))

  - [EndPublishPresence(IAsyncResult)](https://msdn.microsoft.com/library/hh349982\(v=office.15\))

The application can publish a collection of presence categories as a batch process using the aforementioned methods. UCMA 4.0 ensures that the presence categories will be published to the proper containers, providing instance IDs where relevant. It is to be noted that the categories must be subscribed to LocalOwnerPresence in order to use these methods. Any exception during the publication of an individual category in the list will result in the failure of the entire batch.

Applications must provide the instance IDs for custom categories and the **ContactCard** category. For others, UCMA 4.0 automatically supplies them.

UCMA 4.0 and Lync endpoints drive their publication behavior based on a common non-configurable manifest that is defined by the administrator in the enterprise. This manifest specifies publication rules for well-known categories recognized by Lync Server 2013. If an application attempts to publish an unrecognized category using the **BeginPublishPresence** method, an **InvalidOperationException** is thrown. All publications using this method are queued and completed in a serial fashion.

The corresponding methods to delete the published categories are the [BeginDeletePresence(ICollection\<PresenceCategory\>, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh384090\(v=office.15\)) and [EndDeletePresence(IAsyncResult)](https://msdn.microsoft.com/library/hh381394\(v=office.15\)) methods.

### Presence publication for ApplicationEndpoint and advanced publication scenarios for UserEndpoint

For advanced usage scenarios, use the [BeginPublishPresence(ICollection\<PresenceCategoryWithMetaData\>, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh349916\(v=office.15\)) and [EndPublishPresence(IAsyncResult)](https://msdn.microsoft.com/library/hh349982\(v=office.15\)) methods.

The [PresenceCategoryWithMetaData](https://msdn.microsoft.com/library/hh381915\(v=office.15\)) class encapsulates the **PresenceCategory** being published, together with other publishing details such as container ID, instance ID, version, and expiry type. It is expected that an advanced user will understand the impact of his publication and can manage relationship levels (watcher list).

For application endpoints that are intended to persist their presence information; that is, that rarely change their presence information, developers can take advantage of the simplified presence publication mechanism that UCMA 4.0 offers.

To delete the published categories, use the [BeginDeletePresence(ICollection\<PresenceCategoryWithMetaData\>, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh381122\(v=office.15\)) and [EndDeletePresence(IAsyncResult)](https://msdn.microsoft.com/library/hh381394\(v=office.15\)) methods.

## Presence categories provided by UCMA 4.0

  - **ContactCard**
    
    The [ContactCard](https://msdn.microsoft.com/library/hh382040\(v=office.15\)) class represents the "contactCard" category. This category represents a variety of contact information about the user represented by the endpoint.

  - **PresenceState**
    
    The [PresenceState](https://msdn.microsoft.com/library/hh350296\(v=office.15\)) class represents the "state" category. This category represents the availability of the endpoint owner and how "reachable" they are for communications. The different types of the state category represented by [PresenceStateType](https://msdn.microsoft.com/library/hh382179\(v=office.15\)) are shown in the following table.
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>State category type</p></th>
    <th><p>Description</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>AggregateState</strong></p></td>
    <td><p>The overall availability of the endpoint owner.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>EndpointState</strong></p></td>
    <td><p>The availability of the endpoint owner from this particular endpoint.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>UserState</strong></p></td>
    <td><p>The availability preference of the endpoint owner.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>PhoneState</strong></p></td>
    <td><p>Whether and how the endpoint owner is using a phone.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>CalendarState</strong></p></td>
    <td><p>The availability of the endpoint owner based on their calendar data.</p></td>
    </tr>
    </tbody>
    </table>
    
    The availability value of a presentity is represented by a long integer, in which smaller values indicate higher availability. There are many static helper methods on the **PresenceState** class that can be used to publish well-known availability values.
    
    Typically, only endpoint, user, phone, and calendar states are published by enterprise endpoints, thereby allowing the server to combine them using certain rules into one final aggregated value.
    
    UCMA 4.0 does not allow instantiating and publishing a **CalendarState** category.

  - **Note**
    
    The [Note](https://msdn.microsoft.com/library/hh382265\(v=office.15\)) class represents the "note" category. A note category contains a message that watchers can view. There are two types of note: personal and out-of-office. UCMA 4.0 provides methods to configure and publish both types of notes.

  - **Services**
    
    The [Services](https://msdn.microsoft.com/library/hh385140\(v=office.15\)) class represents the "services" category, which represents the cumulative service capabilities of a presentity. When endpoints publish a "device" category that represents the capabilities of the device (such as support for audio, video, and text), the server aggregates these capabilities into a single services category that can be consumed by watchers as well as the endpoint owner.
    
    UCMA 4.0 does not recommend direct publication of the services category for user endpoints. Application endpoints can publish the services category directly, given that there is usually only a single instance of the application endpoint contact object.

  - **CustomPresenceCategory**
    
    If a UCMA 4.0 application is intended to publish a custom category or a well-known category for which the API does not have a strongly-typed implementation, the application can do so by instantiating a [CustomPresenceCategory](https://msdn.microsoft.com/library/hh348294\(v=office.15\)) with the name and a string representing the XML content. Optionally, an instance ID can be supplied. Otherwise, the value is automatically determined, provided that it is a well-known category in the Lync Server 2013 subsystem (defined in the server manifest).

## Presence subscription and notification handling

A local presentity who wishes to know its current presence data and be informed of any changes to this data can do so by subscribing to its own presence information. This can be done by calling the [BeginSubscribe(AsyncCallback, Object)](https://msdn.microsoft.com/library/hh383375\(v=office.15\)) and [EndSubscribe(IAsyncResult)](https://msdn.microsoft.com/library/hh348322\(v=office.15\)) methods.

The following table shows the events on the **LocalOwnerPresence** class and the name of the presence data obtained from them.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Event</p></th>
<th><p>Presence data obtained from event</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh349160(v=office.15)">ContainerNotificationReceived</a></p></td>
<td><p>Access control lists that list member URIs and domains.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh161755(v=office.15)">DelegateNotificationReceived</a></p></td>
<td><p>List of delegates of the endpoint owner.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh382793(v=office.15)">PresenceNotificationReceived</a></p></td>
<td><p>Details on presence categories and the containers to which they are published.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh348482(v=office.15)">SubscriberNotificationReceived</a></p></td>
<td><p>List of watchers (subscribers).</p></td>
</tr>
</tbody>
</table>


### Category notification parsing

For [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)) instances, key publishing APIs cannot be used unless the object referred to by the [LocalOwnerPresence](https://msdn.microsoft.com/library/hh348476\(v=office.15\)) property is in the **Subscribed** state. For [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)) instances, it is recommended, but not required, that **LocalOwnerPresence** be in the **Subscribed** state.

The list of presence categories returned by the [AllCategories](https://msdn.microsoft.com/library/hh384873\(v=office.15\)) property on the [LocalPresentityNotificationEventArgs](https://msdn.microsoft.com/library/hh350176\(v=office.15\)) object can be extensive. For this reason, Lync Server 2013 filters this list to a smaller representative list that highlights categories published to the local owner’s self container. For user objects this is a different container for different categories representing the container that is most representative of that category. For contact objects, the list includes all categories in the container 0.

Lync Server 2013 further pre-parses this information and populates the common categories on the **LocalPresentityNotificationEventArgs** object, including those in the following list:

  - [ContactCard](https://msdn.microsoft.com/library/hh349921\(v=office.15\))
    
    Separate **ContactCard** instances are aggregated to produce a single instance for easy consumption.

  - [AggregatedPresenceState](https://msdn.microsoft.com/library/hh383578\(v=office.15\))

  - [EndpointPresenceState](https://msdn.microsoft.com/library/hh349175\(v=office.15\))

  - [UserPresenceState](https://msdn.microsoft.com/library/hh383830\(v=office.15\))

  - [ServiceCapabilities](https://msdn.microsoft.com/library/hh384733\(v=office.15\))

  - [OutOfOfficeNote](https://msdn.microsoft.com/library/hh365713\(v=office.15\))

  - [PersonalNote](https://msdn.microsoft.com/library/hh349124\(v=office.15\))

### Container notification parsing

Container notifications represent the Access Control Lists of the endpoint owner and are indexed by the container ID. These ACLs represent individual member URIs, specific domain URIs and broad domain URIs such as watchers in the enterprise, public cloud. or federated. This data can be used to control which presence data of the endpoint owner watchers are allowed to see. For more information, see "Relationship level management", later in this topic.

### Subscriber notification parsing

Subscribers represent details of the watchers subscribed to the endpoint owner's data.

### Delegates notification parsing

This notification gives information of the delegates of the endpoint owner (the delegator) and also whether they can publish or assign other delegatees on their behalf.

## Relationship level management

Presentities in a Lync subsystem can control access to their presence data by doing relationship management. This involves assigning subscribers or watchers to various ACLs or containers limiting their viewership to the presence data in those containers.

Entries in an ACL can be:

  - Specific URIs of watchers.

  - Specific domains names, such as contoso.com or hotmail.com.

  - SourceNetwork flags indicating broad domains such as users in the same enterprise, users on servers that are federated with this enterprise, users in the public cloud, or everyone.

The [BeginUpdateContainerMembership(ICollection\<ContainerUpdateOperation\>, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh365994\(v=office.15\)) and [EndUpdateContainerMembership(IAsyncResult)](https://msdn.microsoft.com/library/hh384067\(v=office.15\)) methods on a **LocalOwnerPresence** object can be used to assign watchers to the various containers.

Applications can register to receive container notifications when the [ContainerNotificationReceived](https://msdn.microsoft.com/library/hh349160\(v=office.15\)) event is raised.

### Relationship level

A relationship level between a presentity and a watcher is defined as the highest container that the presentity has assigned the watcher to. Lync assigns a specific relationship name to certain well-defined containers. UCMA 4.0 defines the relationship levels in the [PresenceRelationshipLevel](https://msdn.microsoft.com/library/hh161865\(v=office.15\)) enumeration.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Relationship level</p></th>
<th><p>Container ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Unknown</p></td>
<td><p>-1</p></td>
<td><p>Relationship level cannot be determined or found a container ID that does not match the known relationship containers.</p></td>
</tr>
<tr class="even">
<td><p>Everyone</p></td>
<td><p>0</p></td>
<td><p>No specific relationship level was found for the contact. This is the default relationship level</p></td>
</tr>
<tr class="odd">
<td><p>External</p></td>
<td><p>100</p></td>
<td><p>Contact is external.</p></td>
</tr>
<tr class="even">
<td><p>Colleagues</p></td>
<td><p>200</p></td>
<td><p>Contact belongs to the same company.</p></td>
</tr>
<tr class="odd">
<td><p>Workgroup</p></td>
<td><p>300</p></td>
<td><p>Contact belongs to the same workgroup or team.</p></td>
</tr>
<tr class="even">
<td><p>Personal</p></td>
<td><p>400</p></td>
<td><p>Contact is personal (friends and family).</p></td>
</tr>
<tr class="odd">
<td><p>Blocked</p></td>
<td><p>32000</p></td>
<td><p>Contact is blocked.</p></td>
</tr>
</tbody>
</table>


To determine the relationship of the watcher to the local owner (or endpoint owner), call the [GetPresenceRelationshipLevel(RealTimeAddress, SourceNetwork)](https://msdn.microsoft.com/library/hh365958\(v=office.15\)) method. This method can be accessed through the [PresenceServices](https://msdn.microsoft.com/library/hh349242\(v=office.15\)) property on a **UserEndpoint** instance.

### Relationship level determination

Because a subscriber can be present in multiple containers owned by a publisher, the following steps can be used to determine the relationship level (container). Lync Server 2013 determines a subscriber’s container for a particular category request using a similar algorithm.

1.  Find the container with the highest container ID in which the subscriber’s URI is explicitly listed. If one such container is found, end the search.

2.  Find the container with the highest container ID in which the subscriber’s domain is listed in any of its domain membership lists. If one such container is found, end the search.

3.  If the subscriber is in the same enterprise as the publisher, choose the container with the highest container ID that has the same-enterprise bit set. If one such container is found, end the search.

4.  If the subscriber is a federated user, select the container with the highest container ID that has its federated-user flag set. If one such container is found, end the search.

5.  If the subscriber is a public-cloud user, select the container with the highest container ID that has its public-cloud-user flag set. If one such container is found, end the search.

6.  If the default container contains the category, select that container.

### Bootstrapping

When a user is provisioned on Lync Server 2013, there are no ACLs in any of the containers except container 0, the container that allows access by every presentity ([SourceNetwork](https://msdn.microsoft.com/library/hh385294\(v=office.15\)).**Everyone**). Users who take advantage of presence services in UCMA 4.0 or those logged in to Microsoft Lync 2013 are "bootstrapped," which means that some containers are automatically assigned certain memberships as dictated by the server manifest. For example, in Lync Server 2013, users not operating in Private mode have members of their enterprise automatically assigned to the Colleagues (200) container, and members of federated networks are assigned to their Public (100) container.

Lync Server 2013 relationship management APIs are designed under the assumption that relationship management is primarily of importance to **UserEndpoint** objects. Bootstrapping is not done for **ApplicationEndpoint** instances, as this endpoint type is usually intended to have its presence information available to all. It is for this reason that application endpoints publish data directly into container 0.

## Managing watchers

A watcher (also known as a subscriber) is an entity that receives presence information published by another presentity. When one user subscribes to another user's presence by assigning a non-null value to the [SubscriptionContext](https://msdn.microsoft.com/library/hh384093\(v=office.15\)) property on the [RemotePresentitySubscriptionTarget](https://msdn.microsoft.com/library/hh349759\(v=office.15\)) object with the intention of building a contact relationship with the publishing user, the server notifies the publishing user of the subscription request.

After the publishing user is notified with the subscription request, the publisher is expected to acknowledge the request to the server so that the server can remove the entry that caused the notification to occur. This is an opportunity for the publishing user to find out who is subscribing to the information being published, and to place the subscribing user into the appropriate ACL using the update operations in the [ContainerUpdateOperation](https://msdn.microsoft.com/library/hh365925\(v=office.15\)) class, if necessary.

The notified user acknowledges the request by calling the [BeginAcknowledgeSubscriber(String, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh384870\(v=office.15\)) method.

An endpoint can register for watcher notifications by registering a handler for the [SubscriberNotificationReceived](https://msdn.microsoft.com/library/hh348482\(v=office.15\)) event on a **LocalOwnerPresence** instance. The [SubscriberNotificationEventArgs](https://msdn.microsoft.com/library/hh383812\(v=office.15\)) class, which is associated with this event, has a [WatcherList](https://msdn.microsoft.com/library/hh349512\(v=office.15\)) property that lists all watchers who have subscribed to the application’s presence information.

Watcher notifications and acknowledgement is not a gatekeeping mechanism, in that the watcher who requests information does not require permissions before doing so. However, a user can assign memberships to the watcher, thereby controlling the amount of data being shared.

## LocalOwnerPresence state transitions

The **LocalOwnerPresence** state transitions are shown in the following illustration. The state values are the members of the [CollaborationSubscriptionState](https://msdn.microsoft.com/library/hh380964\(v=office.15\)) enumerated type.

![ContactGroupServices state transitions](images/Dn466019.StateMach_LocalOwnerPresence(Office.15).jpg "ContactGroupServices state transitions")

1.  The transition from **Idle** to **Subscribing** occurs when the application calls [BeginSubscribe(AsyncCallback, Object)](https://msdn.microsoft.com/library/hh383375\(v=office.15\)).

2.  The transition from **Subscribing** to **Subscribed** occurs when the subscription succeeds.

3.  The transition from **Subscribing** to **Terminating** occurs when the subscription fails. This error occurs when the server is busy. The application can try to subscribe again later.

4.  The transition from **Subscribing** to **WaitingForRetry** occurs when the subscription cannot be successfully created, because the server is busy or the UserServices pool is offline. UCMA 4.0 automatically refreshes the subscription when the UserServices pool is online again.

5.  The transition from **WaitingForRetry** to **Subscribing** occurs when another subscription to the local presentity is attempted for the reason given in step 4.

6.  The transition from **WaitingForRetry** to **Terminating** occurs when the application calls [BeginUnsubscribe(AsyncCallback, Object)](https://msdn.microsoft.com/library/hh161891\(v=office.15\)) and this session is in the **WaitingForRetry** state.

7.  The transition from **Subscribed** to **WaitingForRetry** occurs for connectivity failures and reasons such as the following.
    
      - The server requests UCMA 4.0 to close this subscription and to create a new subscription by sending a NOTIFY request with an Expires:0 parameter. The server can make this request at any time.
    
      - Route-set recovery begins.
    
      - The server sends a "481 Call leg unavailable" response.
    
      - The endpoint owner’s home server’s UserServices pool is offline and cannot respond to service requests. UCMA 4.0 automatically recovers when the UserServices pool is online again.

8.  The transition from **Subscribed** to **Terminating** occurs when [BeginUnsubscribe(AsyncCallback, Object)](https://msdn.microsoft.com/library/hh161891\(v=office.15\)) is called.

9.  The transition from **Terminating** to **Idle** occurs when the call to **BeginUnsubscribe** ends successfully. The subscription can be reused; that is, an application can call **BeginSubscribe** when the state is **Idle**.

