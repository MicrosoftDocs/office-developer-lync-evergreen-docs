---
title: Remotely accessible category instances
TOCTitle: Remotely accessible category instances
ms:assetid: d62d52cd-77bc-4f3d-b608-1297d4fe0380
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454662(v=office.15)
ms:contentKeyID: 57092993
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Remotely accessible category instances


**Applies to:** Lync 2013 | Lync Server 2013

The following category instances are published for remote users to subscribe to.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category name</p></th>
<th><p>Container Id</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>100, 200, 300, 400, 32000</p></td>
<td><p>The calendarData category instances in Container 100, 200, 300, and 400 contain the local user’s working hours and/or free-busy information that is intended to be shared with the specified container members through remote subscriptions. Those in Container 32000 are used to block the specified container members from accessing the local user’s calendar data.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>0, 100, 200, 300, 400, 32000</p></td>
<td><p>The contactCard category instances contain various contact information about the local user. They are intended for share with members of the hosting containers other than the Blocked container. The contactCard category instances placed in Container 32000 (Blocked container) are used to block any members of that container from accessing the local user’s contact information.</p></td>
</tr>
<tr class="odd">
<td><p><a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a></p></td>
<td><p>100, 200, 300, 400, 32000</p></td>
<td><p>The legacyInterop category instances are created and published by Microsoft Lync Server 2013 to provide some backward compatibility for clients that do not support the enhanced presence data model. A legacyInterop category instance contains an availability number, the value of which corresponds to the availability number of the <a href="state-element_4.md">state[@type='aggregateState'] element</a> category instance in the same container.</p></td>
</tr>
<tr class="even">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>100, 200, 300, 400, 32000</p></td>
<td><p>The note category instance in each container prescribes the presence note to be shared with or blocked to the members of the hosting container.</p></td>
</tr>
<tr class="odd">
<td><p><a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a></p></td>
<td><p>100, 200, 300, 400, 32000</p></td>
<td><p>A noteHistory category instance is just a <a href="note-category-instance-value-element.md">note category instance value element</a> category instance with a registered category name of noteHistory. Such category instances are used to enumerate the most recently published note category instances and will appear in the presence feed of the container members who have subscribed to the <a href="note-category-instance-value-element.md">note category instance value element</a> category instances of the local user. By default the last three note category instances are published to Container 200, 300, and 400 and no such category instances are published to Container 100 and 3200.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>100, 200, 300, 400, 32000</p></td>
<td><p>The state category instances in these containers are of the aggregateState type. They are produced by the aggregation script.</p></td>
</tr>
<tr class="odd">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>100, 200, 300, 400, 32000</p></td>
<td><p>The services category instances are produced by the aggregation script and represent the device-independent user-bound presence capabilities of the local user.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Containers and categories used by Lync](containers-and-categories-used-by-lync.md)

