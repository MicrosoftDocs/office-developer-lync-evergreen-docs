---
title: Containers for local access
TOCTitle: Containers for local access
ms:assetid: c03e53b0-73b6-4ef3-ac5a-1a8d2ab79e7c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454658(v=office.15)
ms:contentKeyID: 57092920
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Containers for local access


_**Applies to:** Lync 2013 | Lync Server 2013_

Microsoft Lync 2013 uses the following containers to store category instances for local use. The category instances represent local presence information, roaming user data, server configurations, and other application data. Both Lync 2013 and the Microsoft Lync Server 2013 components, such as the aggregation script, publish data to these locally-accessible containers or use the data in them.

## Local access containers

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
<td><p>1</p></td>
<td><p>Self</p></td>
<td><p>Unspecified</p></td>
<td><p>Lync 2013 uses this container to cache data about the local user or data used by the local client. The cached data includes the user information (<a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a> and <a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a>), his or her working hours (<a href="workinghours-category-instance-value-element.md">workingHours category instance value element</a> or <a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a>), contact list, and any user-configured options (<a href="alerts-category-instance-value-element.md">alerts category instance value element</a> and <a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a>) that dictate Lync 2013 how to display alerts, to operate in privacy modes, and to forward calls.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Aggregation 1</p></td>
<td><p>Unspecified</p></td>
<td><p>Lync 2013 publishes the endpoint-specific presence state and device information that must be aggregated to produce endpoint-independent aggregated presence state, capabilities of the user, and the most current active location. The aggregation script takes the data in this container as the input and outputs the aggregated results to the Container 100, 200, and 400.</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Aggregation 2</p></td>
<td><p>Unspecified</p></td>
<td><p>As with the first aggregation container, the aggregation script takes the endpoint-dependent presence state data in this aggregation container as the input to produce endpoint-independent aggregated presence states. The aggregation logic is slightly different from that applied to the input in the first aggregation container: when the local user is in the Do Not Disturb (DND) state, the aggregated state is set to busy with Urgent Interruptions Only. The aggregated results are output only to Container 300.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[Containers and categories used by Lync](containers-and-categories-used-by-lync.md)

