---
title: Introducing Enhanced Presence
TOCTitle: Introducing Enhanced Presence
ms:assetid: 625a191d-12f0-4af7-bf9d-6d33710e919c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454618(v=office.15)
ms:contentKeyID: 57092867
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Introducing Enhanced Presence


_**Applies to:** Lync 2013 | Lync Server 2013_

In real-time communications, presence refers to information used to describe a user's availability status. For example, Microsoft Lync 2013 displays a list of your contacts together with their status indicating if they are available, busy, inactive, away, or offline.

When a contact's status shows available, you know that the contact is likely to answer your instant message or voice call. A busy or inactive contact, however, is less likely to respond to your invitation. An away or offline status suggests that perhaps you should send the contact an email message instead of text messages.

In addition to the availability status, the presence can also include other information to indicate a person’s ability and willingness to communicate with others. For example, you may leave a personal note to inform others of your current traveling itinerary and to provide them with a list of alternative communications means to reach you in case of emergency.

## Simple presence model

In the simplest form, the availability status is often used to describe the presence of a user or another entity. The presence availability status may be represented simply by a number or a bit flag. In Lync 2013, the following integers are used to indicate the degrees of availability.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Availability number</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>3500</p></td>
<td><p>Available</p></td>
</tr>
<tr class="even">
<td><p>6500</p></td>
<td><p>Busy</p></td>
</tr>
<tr class="odd">
<td><p>9500</p></td>
<td><p>Do not disturb</p></td>
</tr>
<tr class="even">
<td><p>12500</p></td>
<td><p>Be right back</p></td>
</tr>
<tr class="odd">
<td><p>15500</p></td>
<td><p>Away</p></td>
</tr>
<tr class="even">
<td><p>18500</p></td>
<td><p>Offline</p></td>
</tr>
</tbody>
</table>


For many applications, such a simple representation of the availability is an insufficient presence indicator. When a contact is busy, you may want to know if the individual is busy on the phone, in a meeting, catching up with the latest emails or working on another task. The additional information can help you decide the best way to reach the contact. Similarly, when you are away from the desk, you may want to let others know if you are on a lunch break, out of office, or in a meeting.

## Enhanced Presence

When publishing presence information to share with other users, a presence publisher typically wants to control who can access the presence data, what kinds of presence information various users may view, and for how long the publication of a particular piece of data lasts. With enhanced presence, the following application scenarios are readily supported:

  - A user may want to distribute the work phone number to everyone, while allowing only a small group with access to a mobile phone number.

  - While working on an important project, the user may want to permit urgent interruptions by the members of her team, but not anyone else.

  - While traveling, the user may want to inform some people of the detailed itinerary and to tell others that his agenda involves interstate travel.

Microsoft Lync Server 2013 uses the concept of containers as the mechanism to control access to published presence data.

Enhanced presence data is described by enhanced presence category instances that are characterized by the following general features:

  - Enhanced presence category instances are of XML data types and can be used to describe any type of data.

  - Enhanced presence category instances can be extended to support custom presence features.

  - Access to enhanced presence category instances can be controlled with great flexibility.

  - Enhanced presence category instances can be easily managed with the built-in support of version tracking, life-time management, and unique data identification schemes.

As an example, let us compare the simple presence state with the enhanced presence state used by Lync 2013. In addition to the availability, the enhanced presence state contains other state information including the activity description, the endpoint location, and state types.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>State Property</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Availability</p></td>
<td><p>Indicates if the presentity is free and available, idle, away, or offline.</p></td>
</tr>
<tr class="even">
<td><p>Activity</p></td>
<td><p>Describes the current activity the presentity is engaged in. Examples include &quot;Out of office&quot;, &quot;In a meeting&quot;, or &quot;On the phone&quot;.</p></td>
</tr>
<tr class="odd">
<td><p>Endpoint Location</p></td>
<td><p>Shows the location from which the presentity is logged on and to which the presentity's state applies.</p></td>
</tr>
<tr class="even">
<td><p>Type</p></td>
<td><p>Specifies whether a presence state is a user state, machine state, calendar state, or aggregated state.</p></td>
</tr>
</tbody>
</table>


An application can extend this enhanced presence state type to include custom data.

## See also

#### Reference

[state category instance value elements](state-category-instance-value-elements.md)

#### Concepts

[Enhanced Presence data](enhanced-presence-data.md)

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

[General features of Enhanced Presence](general-features-of-enhanced-presence.md)

