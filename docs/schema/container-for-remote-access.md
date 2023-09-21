---
title: Container for remote access
TOCTitle: Container for remote access
ms:assetid: 4e633c8e-033c-4156-8151-da6b24d5289f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454664(v=office.15)
ms:contentKeyID: 57093111
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Container for remote access


**Applies to:** Lync 2013 | Lync Server 2013

Microsoft Lync 2013 uses the following containers to publish category instances for other (remote) users or entities to receive the presence data. Microsoft Lync Server 2013 can also publish presence data to these containers on behalf of the local user. The remote users or entities allowed to receive the published presence data are specified as members of the containers. The membership is specified by a list of SIP URIs for individual users or domains. The membership can also be specified by a membership type. Supported membership types include everyone, sameEnterprise, or publicCloud. They are defined in the ContainerManifest.XSD schema file.

## Remote access containers

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Container Id</p></th>
<th><p>Friendly name</p></th>
<th><p>Default ACEs</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Default</p></td>
<td><p>Unspecified</p></td>
<td><p>This is the default container to control access to the local user’s non-private presence publication by remote users who are not a member of any other containers. The only non-private presence information published to this container is the identity of the local user. It is represented by a <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a> category instance that contains only the identity information that is comprised of the user’s display name and his or her email address. The server publishes the display name and email address on behalf of the local user regardless of whether the user is signed in or not. The publication of this information ensures that the local user can be discovered by any other user or entity even when the local user is not signed in. This container also contains private <a href="routing-category-instance-value-element.md">routing category instance value element</a> and <a href="dndstate-category-instance-value-element.md">dndState category instance value element</a> category instances that are used, respectively, to determine how to forward incoming calls made by anyone not assigned to any of the other containers and how to block the incoming calls when the local user is in the Do Not Disturb state.</p></td>
</tr>
<tr class="even">
<td><p>100</p></td>
<td><p>External Contacts</p></td>
<td><p>Federated</p></td>
<td><p>Non-private category instances placed in this container are visible to federated users. Non-private category instances include the <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a>, <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a>, <a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a>, <a href="note-category-instance-value-element.md">note category instance value element</a>, <a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a>, <a href="services-category-instance-value-element.md">services category instance value element</a>, and <a href="state-category-instance-value-elements.md">state category instance value elements</a> instance. This container also contains private <a href="routing-category-instance-value-element.md">routing category instance value element</a> and <a href="dndstate-category-instance-value-element.md">dndState category instance value element</a> category instances that are used, respectively, to determine how to forward incoming calls made by anyone within the membership scope of this container and how to block the incoming calls when the local user is in the Do Not Disturb state.</p></td>
</tr>
<tr class="odd">
<td><p>200</p></td>
<td><p>Colleagues</p></td>
<td><p>sameEnterprise</p></td>
<td><p>Non-private category instances placed in this container are visible to the users within the same enterprise network of the container owner. Non-private category instances include the <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a>, <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a>, <a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a>, <a href="note-category-instance-value-element.md">note category instance value element</a>, <a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a>, <a href="services-category-instance-value-element.md">services category instance value element</a>, and <a href="state-category-instance-value-elements.md">state category instance value elements</a> instance. This container also contains private <a href="routing-category-instance-value-element.md">routing category instance value element</a> and <a href="dndstate-category-instance-value-element.md">dndState category instance value element</a> category instances that are used, respectively, to determine how to forward incoming calls made by anyone within the membership scope of this container and how to block the incoming calls when the local user is in the Do Not Disturb state.</p></td>
</tr>
<tr class="even">
<td><p>300</p></td>
<td><p>Workgroup</p></td>
<td><p>Unspecified</p></td>
<td><p>The local user must designate specific users or domains as members of this container. Non-private category instances include the <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a>, <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a>, <a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a>, <a href="note-category-instance-value-element.md">note category instance value element</a>, <a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a>, <a href="services-category-instance-value-element.md">services category instance value element</a>, and <a href="state-category-instance-value-elements.md">state category instance value elements</a> instance. This container also contains <a href="routing-category-instance-value-element.md">routing category instance value element</a> and <a href="dndstate-category-instance-value-element.md">dndState category instance value element</a> category instances that are used, respectively, to determine how to forward incoming calls made by anyone within the membership scope of this container and how to block the incoming calls when the local user is in the Do Not Disturb state.</p></td>
</tr>
<tr class="odd">
<td><p>400</p></td>
<td><p>Friends and Family</p></td>
<td><p>Unspecified</p></td>
<td><p>The local user must designate specific users or domains as members of this container. Non-private category instances include the <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a>, <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a>, <a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a>, <a href="note-category-instance-value-element.md">note category instance value element</a>, <a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a>, <a href="services-category-instance-value-element.md">services category instance value element</a>, and <a href="state-category-instance-value-elements.md">state category instance value elements</a> instance. This container also contains <a href="routing-category-instance-value-element.md">routing category instance value element</a> and <a href="dndstate-category-instance-value-element.md">dndState category instance value element</a> category instances that are used, respectively, to determine how to forward incoming calls made by anyone within the membership scope of this container and how to block the incoming calls when the local user is in the Do Not Disturb state.</p></td>
</tr>
<tr class="even">
<td><p>32000</p></td>
<td><p>Blocked Contacts</p></td>
<td><p>Unspecified</p></td>
<td><p>By default, empty category instances of <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a>, <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a>, <a href="note-category-instance-value-element.md">note category instance value element</a>, <a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a>, and <a href="services-category-instance-value-element.md">services category instance value element</a> are published to this container. In addition, a <a href="routing-category-instance-value-element.md">routing category instance value element</a> category instance with a <strong>block</strong> rule, a <a href="state-category-instance-value-elements.md">state category instance value elements</a> category instance of the aggregateState type and a <a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a> category instance, both containing an availability number of 18500 to indicate the Offline status, and an identity-specific <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a> category instance provisioned from Active Directory by Microsoft Lync Server 2013 are also published to this container.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Containers and categories used by Lync](containers-and-categories-used-by-lync.md)

