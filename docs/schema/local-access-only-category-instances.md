---
title: Local-access only category instances
TOCTitle: Local-access only category instances
ms:assetid: 3600e1ac-9471-4642-8509-e742355837ea
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454661(v=office.15)
ms:contentKeyID: 57092976
ms.date: 07/24/2014
mtps_version: v=office.15
description: Explore Microsoft Lync 2013's local access only category instances. Learn about alerts, calendar data, device info, DND state, and more for enhanced presence services.
---

# Local-access only category instances


**Applies to:** Lync 2013 | Lync Server 2013

The following category instances are published or used by Microsoft Lync 2013 for local access only or self-consumption.

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
<td><p><a href="alerts-category-instance-value-element.md">alerts category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Present in the Self container, this category instance specifies how the user is notified of the events when the user is added to someone’s contact list or when the user is in a Do Not Disturb (DND) state. These options can be set through the Alerts option panel on Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Present in the Self container, this type of category instances contains the user’s working-hours specification or a contiguous block of free-busy time intervals. This kind of calendar data is provisioned from the Microsoft Exchange calendar store.</p></td>
</tr>
<tr class="odd">
<td><p><a href="device-category-instance-value-element.md">device category instance value element</a></p></td>
<td><p>2</p></td>
<td><p>Present the first aggregation container, this kind of category instances contains the information about signed-in devices. The device information includes the device capabilities that are used as the input to the aggregation script to produce aggregated capabilities attributed to a device-independent user-bound enhanced presence services category instance.</p></td>
</tr>
<tr class="even">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0, 2, 3, 100, 200, 300, and 400</p></td>
<td><p>This type of category instance is used to determine whether to block routing inbound calls from any container members (specified) or not (unspecified) when the local user is in a Do Not Disturb state. A dndState category instance is just an empty <a href="state-category-instance-value-elements.md">state category instance value elements</a> category instance of the userState type, but has a registered category name of dndState.</p></td>
</tr>
<tr class="odd">
<td><p><a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>The otherOptions category instances include the privacy mode settings, timestamps of the last access to the user’s voice mail, permissions for handling personal information. Multiple instances are used to describe different parts of such data.</p></td>
</tr>
<tr class="even">
<td><p><a href="rccoptions-category-instance-value-element.md">rccOptions category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>The rccOptions category instances contain roaming options for remote call control when PSTN/PBX phones are supported by Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p>0, 100, 200, 300, 400, and 32000</p></td>
<td><p>The routing category instances contain routing rules to forward inbound calls made by any members of a hosting container. They are private category instances and are not visible to the remote users who are members of the hosting containers.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>2, 3</p></td>
<td><p>Non-aggregated state category instances are used as input to the aggregation script that, in turn, produces aggregated state category instance as the output. Non-aggregated state category instances in the first aggregation container (2) are used to produce the aggregated state for publication in Container 100, 200, and 400. Those in the second aggregation container (3) are used to produce the aggregated state for publication in Container 300.</p></td>
</tr>
<tr class="odd">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>2</p></td>
<td><p>The services category instance is produced by the aggregation script and represents the device-independent user-bound presence capabilities of the user.</p></td>
</tr>
<tr class="even">
<td><p><a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Present in the Self container only, this type of category instances contains phone numbers that can be set by the local user or provisioned by the server. Server-provisioned phone numbers are read-only. User-configurable phone numbers can be set through the <strong>Lync Options</strong> dialog box.</p></td>
</tr>
<tr class="odd">
<td><p><a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>This type of category instances contains server-provisioned user data that includes phone lines assigned to the user and the voice mail URL if the user has unified messaging enabled.</p></td>
</tr>
<tr class="even">
<td><p><a href="workinghours-category-instance-value-element.md">workingHours category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>This type of category instances contains the user’s working-hours specification. A workingHours category instance is just a <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a> category instance containing working-hours information, where the category name of workingHours is registered. A workingHours category instance is used to determine the user’s working hour period when incoming calls should be routed.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Containers and categories used by Lync](containers-and-categories-used-by-lync.md)

