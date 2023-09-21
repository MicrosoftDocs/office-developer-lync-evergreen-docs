﻿---
title: High availability and failover in UCMA 4.0
TOCTitle: High availability and failover in UCMA 4.0
ms:assetid: c8224e1f-0295-424e-9d93-d04f291816c3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466068(v=office.15)
ms:contentKeyID: 57103060
ms.date: 07/25/2014
mtps_version: v=office.15
---

# High availability and failover in UCMA 4.0


**Applies to:** Lync 2013 | Lync Server 2013



This topic discusses the APIs in Microsoft Unified Communications Managed API 4.0 that are associated with High Availability and Failover.

## SipEndpoint class

The following are members of the [SipEndpoint](https://msdn.microsoft.com/library/hh348350\(v=office.15\)) class. When a SIP NOTIFY message is received with USC unavailable, the [RegistrationStateChanged](https://msdn.microsoft.com/library/hh383178\(v=office.15\)) event is raised. In the associated [RegistrationStateChangedEventArgs](https://msdn.microsoft.com/library/hh349790\(v=office.15\)) object, the [Reason](https://msdn.microsoft.com/library/hh383265\(v=office.15\)) property is set to **None** (a value of the [RegistrationTransitionReason](https://msdn.microsoft.com/library/hh382280\(v=office.15\)) enumeration) and the [UserServicesState](https://msdn.microsoft.com/library/hh381689\(v=office.15\)) property is set to **Unavailable** (a value of the [ServiceState](https://msdn.microsoft.com/library/hh350118\(v=office.15\)) enumeration).

When the registration is subsequently healed by means of a registration refresh, the **RegistrationStateChanged** event is raised, and the **Reason** property is set to **Refreshed**, and **UserServicesState** property is set to **Available**. The **SipEndpoint** class does not expose **UserServicesState** as a property.

### ServiceState enumeration

The values of the [ServiceState](https://msdn.microsoft.com/library/hh350118\(v=office.15\)) enumeration represent the state of a service. The enumeration values and their descriptions are shown in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Unknown</strong></p></td>
<td><p>The state of the service is unknown.</p></td>
</tr>
<tr class="even">
<td><p><strong>Available</strong></p></td>
<td><p>The service is available.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Unavailable</strong></p></td>
<td><p>The service is unavailable.</p></td>
</tr>
</tbody>
</table>


### RegistrationStateChangedEventArgs class

Three properties of the [RegistrationStateChangedEventArgs](https://msdn.microsoft.com/library/hh349790\(v=office.15\)) class are related to high availability and failover. These properties and their descriptions are shown in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh383265(v=office.15)">Reason</a></p></td>
<td><p>Gets the reason, if known, for the state transition.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh348693(v=office.15)">MessageData</a></p></td>
<td><p>Gets the message data containing the message received when a state transition occurs. The value of this property is null when the state transition contains no message data.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh381689(v=office.15)">UserServicesState</a></p></td>
<td><p>Gets the availability state of the User Services pool.</p></td>
</tr>
</tbody>
</table>


## LocalEndpointStateChangedEventArgs class

Two properties on the [LocalEndpointStateChangedEventArgs](https://msdn.microsoft.com/library/hh348674\(v=office.15\)) class are shown in the following table. Most of the **Reason** values are self-explanatory, but when a SIP NOTIFY message is received, the **Reason** value is **RegistrarNotificationReceived** and the **Notification** value indicates the type of notification.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh381953(v=office.15)">MessageData</a></p></td>
<td><p>Gets the message received when a state transition occurs.</p>
<p>Can be null if the state transition does not contain any message data.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh382088(v=office.15)">Reason</a></p></td>
<td><p>Gets the reason for the state change, a value in the <a href="https://msdn.microsoft.com/library/hh349697(v=office.15)">LocalEndpointStateTransitionReason</a> enumeration.</p></td>
</tr>
</tbody>
</table>


### MessageData property

The **MessageData** property on the **LocalEndpointStateChangedEventArgs** class is of type [SipMessageData](https://msdn.microsoft.com/library/hh383952\(v=office.15\)).

### Reason property

The **Reason** property on the **LocalEndpointStateChangedEventArgs** class can be set to a value in the [LocalEndpointStateTransitionReason](https://msdn.microsoft.com/library/hh349697\(v=office.15\)) enumeration. These values are shown in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>None</strong></p></td>
<td><p>No SIP NOTIFY message or a SIP NOTIFY message of unknown type.</p></td>
</tr>
<tr class="even">
<td><p><strong>OwnerDisabledOrRemoved</strong></p></td>
<td><p>The user or application endpoint owner has been disabled or removed.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RegistrationRefreshFailed</strong></p></td>
<td><p>Registration refresh attempt failed.</p></td>
</tr>
<tr class="even">
<td><p><strong>RegistrationRefreshSucceeded</strong></p></td>
<td><p>Registration was refreshed successfully.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TooManyActiveEndpoints</strong></p></td>
<td><p>The number of active endpoints exceeds the limit.</p></td>
</tr>
</tbody>
</table>


## SipSubscription class

There are no public API changes in the [SipSubscription](https://msdn.microsoft.com/library/hh383437\(v=office.15\)) class, but there are behavior changes that are triggered only from the UCMA platform. When used as part of the UCMA platform, the retry behavior of **SipSubscription** objects is optimized to eliminate unnecessary attempts to recover when the User Services pool is unresponsive. When the User Services pool does not respond, a failure to refresh a subscription does not cause a **SipSubscription** instance to terminate. The UCMA platform triggers this behavior only for subscriptions tied to the User Services pool that the owner is homed on.

## LocalOwnerPresence and ContactGroupServices classes

When the User Services pool is offline, [LocalOwnerPresence](https://msdn.microsoft.com/library/hh382370\(v=office.15\)) and [ContactGroupServices](https://msdn.microsoft.com/library/hh381099\(v=office.15\)) objects change state to **WaitingForRetry** (see [SubscriptionSignalingState](https://msdn.microsoft.com/library/hh382512\(v=office.15\))) with a [TransitionReason](https://msdn.microsoft.com/library/hh349213\(v=office.15\)) value of **ServerEvent**. In this state, publish operations fail with **InvalidOperationException** being thrown. Also, if the [CurrentState](https://msdn.microsoft.com/library/hh366187\(v=office.15\)) property of the underlying **SipSubscription** instance changes to **Terminated**, the **CurrentState()** property on the **LocalOwnerPresence** instance changes to **WaitingForRetry** instead of **Idle**. When the User Services pool finally recovers, the subscription will be re-established.

## RemotePresence class

The home pool subscription of **RemotePresence** objects is the same as that of **LocalOwnerPresence** objects.

