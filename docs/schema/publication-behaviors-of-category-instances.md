---
title: Publication behaviors of category instances
TOCTitle: Publication behaviors of category instances
ms:assetid: aff7a03c-a95f-463b-b93f-11b679f5c9d6
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454673(v=office.15)
ms:contentKeyID: 57093147
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Publication behaviors of category instances


**Applies to:** Lync 2013 | Lync Server 2013

The following table summarizes the default publication behaviors of category instances that are used in Microsoft Lync 2013. For more information, including the aggregation logic, see [\[MS-PRES\]: Presence Protocol Specification](http://go.microsoft.com/fwlink/?linkid=195873).

Category instances published or used by Lync 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category</p></th>
<th><p>Instance ID</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="alerts-category-instance-value-element.md">alerts category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Published to Container 1 as static instance when one or more <strong>Alerts</strong> options are updated.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>0</p></td>
<td><ul>
<li><p>Published to Containers 1, 200, 300, or 400 as a static instance that contains the user’s working-hours information when the information is updated in Microsoft Exchange.</p></li>
<li><p>Published to Container 100 or 32000 as a static instance that contains an empty value when the workingHours information is updated in Microsoft Exchange.</p></li>
</ul>
<div class="alert">

> [!NOTE]
> <P>The workingHours information is used by the aggregation script.</P>


</div></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>A hash dependent on the user’s SMTP address.</p></td>
<td><ul>
<li><p>Published to Containers 200, 300, or 400 as a time-bounded instance that contains the local user’s freeBusy information when the information is updated in Microsoft Exchange.</p></li>
<li><p>Published to Container 1, 100, or 32000 as a time-bounded instance containing an empty value when the user signs in or when the user’s freeBusy information is updated in Microsoft Exchange.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>0</p></td>
<td><ul>
<li><p>Published to Container 0, 100, 200, 300, and 400 as static instances containing the user’s identity information consisting of the display name and email address.</p></li>
<li><p>Published to Container 32000 as a static instance containing an empty value.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>1</p></td>
<td><ul>
<li><p>Published to Container 400 as a static instance containing the user’s home, cell, and other phone numbers if any is specified.</p></li>
<li><p>Published to Container 300 as a static instance containing the user’s cell phone number if it is specified.</p></li>
<li><p>Published to Container 100, 200, and 32000 as static instances, each containing an empty value.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>3</p></td>
<td><ul>
<li><p>Published to Container 100 as a static instance containing the user’s job title and company name.</p></li>
<li><p>Published to Container 200, 300, and 400 as a static instance containing the user’s job title, company name, office location, and work phone number.</p></li>
<li><p>Published to Container 32000 as a static instance containing an empty value.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>4</p></td>
<td><ul>
<li><p>Published to Container 100, 200, 300, and 400 as a static instance containing the user’s voice mail URL.</p></li>
<li><p>Published to Container 32000 as a static instance containing an empty value.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>6</p></td>
<td><ul>
<li><p>Published to Container 100 as a static instance containing the user’s job title and photo display information.</p></li>
<li><p>Published to Container 200, 300, and 400 as a static instance containing the user’s job title, office location, and photo display information.</p></li>
<li><p>Published to Container 32000 as a static instance containing an empty value.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="device-category-instance-value-element.md">device category instance value element</a></p></td>
<td><p>A hash dependent on the device GRUU.</p></td>
<td><p>Published to Container 2 as an endpoint-bounded instance when the user signs in to Microsoft Lync Server 2013 or when the device changes its state from active to idle or from idle to active. These include user sign-in or sign-out, screen lock, or unlock.</p></td>
</tr>
<tr class="even">
<td><p><a href="dndstate-category-instance-value-element.md">dndState category instance value element</a></p></td>
<td><p>0</p></td>
<td><ul>
<li><p>Published to Containers 0, 2, 100, 200, and 400 as static instance containing the availability number of 9500 to enable blocking in-bound calls when the user’s availability mode is Do Not Disturb.</p></li>
<li><p>Published to Containers 3 and 300 as static instance containing an empty value to disable blocking in-bound calls when the user’s availability mode is Do Not Disturb.</p></li>
<li><p>Published to Containers 0, 2, 3, 100, 200, 300, and 400 as static instance containing an empty value to disable blocking in-bound calls when the user’s availability mode is not Do Not Disturb.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="legacyinterop-category-instance-value-element.md">legacyInterop category instance value element</a></p></td>
<td><p>1</p></td>
<td><p>Published to container 100, 200, 300, and 400 as a user-bounded instance containing the availability numbers of the corresponding <a href="state-element_4.md">state[@type='aggregateState'] element</a> instances in their respective containers.</p></td>
</tr>
<tr class="even">
<td><p><a href="note-category-instance-value-element.md">note category instance value element</a></p></td>
<td><p>0</p></td>
<td><ul>
<li><p>Published to Container 100 and 32000 as a static instance containing an empty value when the user sets a personal note by using Lync 2013.</p></li>
<li><p>Published to Container 200, 300, and 400 as a static instance containing a user-specified text message when the user sets a personal note by using Lync 2013.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>A hash dependent on the user’s SMTP address.</p></td>
<td><ul>
<li><p>Published to Container 100 and 32000 as a time-bounded instance containing an empty value for the OOF message when Automatic Replies is turned on in Microsoft Exchange.</p></li>
<li><p>Published to Container 200, 300, and 400 as a time-bounded instance containing the specified OOF message when Automatic Replies is turned on in Microsoft Exchange.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="notehistory-category-instance-value-element.md">noteHistory category instance value element</a></p></td>
<td><p></p></td>
<td><p>Published to Container 200, 300, and 400 as a static instance representing a previously published personal note when a new personal <a href="note-category-instance-value-element.md">note category instance value element</a> instance is published. By default, no more than three publications of noteHistory instances are kept in each container. When two note instances are published less than 30 seconds apart, the latest publication of the noteHistory replaces the most recently prior publication of the noteHistory instance.</p></td>
</tr>
<tr class="odd">
<td><p><a href="otheroptions-category-instance-value-element.md">otherOptions category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Published to Container 1 as a static instance containing the permissions to use the personal information manager when this kind of information is changed.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>1</p></td>
<td><p>Published to Container 1 as a static instance containing the last access timestamp for voice mail or missed conversations when the timestamp is changed.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>2</p></td>
<td><p>Published to Container 1 as a static instance containing the privacy mode-related options when this kind of option is changed.</p></td>
</tr>
<tr class="even">
<td><p><a href="routing-category-instance-value-element.md">routing category instance value element</a></p></td>
<td><p></p></td>
<td><p>Published to Container 0, 100, 200, 300, and 400 as a static instance containing various in-bound call routing rules when such rules were specified.</p></td>
</tr>
<tr class="odd">
<td><p><a href="services-category-instance-value-element.md">services category instance value element</a></p></td>
<td><p>0</p></td>
<td><ul>
<li><p>Published, by aggregation script, to Container 2 as a user-bounded instance containing presence service and calendar service capabilities of the local user.</p></li>
<li><p>Published, by aggregation script, to Containers 100, 200, 300, and 400 as a user-bounded instance containing presence service capability of the local user.</p></li>
<li><p>Published, by aggregation script, to Container 32000 as a user-bounded instance containing an empty value.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>0</p></td>
<td><p>Published to Container 32000 as a static instance containing an availability number of 18500 indicating the Offline presence status.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>1</p></td>
<td><p></p>
<ul>
<li><p>Published to Container 100 as a user-bounded instance containing an aggregated availability number.</p></li>
<li><p>Published to Container 2, 200, and 400 as a user-bounded instance containing an aggregated availability number of 9500 as well as aggregated location, time zone and device type when the user sets the availability to Do Not Disturb.</p></li>
<li><p>Published to Container 3 and 300 as a user-bounded instance containing an availability number of 6900 and an activity token of &quot;urgent-interruptions-only&quot; as well as aggregated location, time zone, and device type when the user sets the availability to Do Not Disturb.</p></li>
<li><p>Published to Container 2, 3, 200, 300, and 400 as a user-bounded instance containing the aggregated availability number, location, time zone and device type when the user sets the availability to any mode other than Do Not Disturb.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="state-element_5.md">state[@type='aggregateMachineState'] element</a></p></td>
<td><p>0x10000000</p></td>
<td><p>Published to Container 2 as a user-bounded instance containing the current aggregated machine availability status that is determined by the most active device that has the lowest availability number.</p></td>
</tr>
<tr class="odd">
<td><p><a href="state-element.md">state[@type='userState'] element</a></p></td>
<td><p>0x20000000</p></td>
<td><p>Published to Container 2 and 3 as a static instance when the local user sets an availability mode that is not Busy or Do Not Disturb.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>0x24000000</p></td>
<td><ul>
<li><p>Published to Container 2 and 3 as a time-bounded instance containing the availability number of 6500 when the user sets the availability mode to <strong>Busy</strong>. By default, this publication expires in 24 hours if it is left unchanged.</p></li>
<li><p>Published to Container 2 as a time-bounded instance containing the availability number of 9500 when the user sets the availability mode to <strong>Do Not Disturb</strong>. By default, this publication expires in 24 hours if it is left unchanged.</p></li>
<li><p>Published to Container 3 as a time-bounded instance containing the availability number of 6900 (Busy with Urgent interruptions only) when the user sets the availability mode to <strong>Do Not Disturb</strong>. By default, this publication expires in 24 hours if it is left unchanged.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="state-element_2.md">state[@type='machineState'] element</a></p></td>
<td><p>A hash dependent on the device GRUU and of the 0x3YYYYYYY format.</p></td>
<td><p>Published to Container 2 and 3 as an endpoint-bounded instance when the local user signs in, when the device times out because it becomes idle or away, when the device is disconnected or reconnected, or when the device detects a mouse or keyboard activity. However, when a not-the-most active device has an active machine state published three times in three minutes, further detections of user input on this device will not cause any new publication of an active machine state until the device becomes idle or until three minutes has elapsed.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-element_3.md">state[@type='calendarState'] element</a></p></td>
<td><p>A hash dependent on the SMTP address and of the 0x4YYYYYYY format.</p></td>
<td><p>Published to Container 2 and 3 as an endpoint-bounded instance containing an availability number of 6500 (Busy) and an &quot;in-a-meeting&quot; activity token, plus any specified meeting subject or location about an ongoing meeting scheduled in the Microsoft Exchange calendar store.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>A hash dependent on the SMTP address and uses the 0x6YYYYYYY format.</p></td>
<td><p>Published to Container 2 and 3 as a static instance containing the &quot;out-of-office&quot; activity token when Automatic Replies is turned on in Microsoft Exchange.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-element_1.md">state[@type='phoneState'] element</a></p></td>
<td><p>A hash dependent on the local user’s SIP URI plus the phone device GRUU and uses the 0x8YYYYYYY format.</p></td>
<td><p>Published to Container 2 and 3 as an endpoint-bounded instance containing an availability number of 6500 (Busy) and the &quot;on-the-phone&quot; activity token when the user has established a VoIP call.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>A hash dependent on the local user’s SIP URI plus the phone device GRUU and uses the 0x7YYYYYYY format.</p></td>
<td><p>Published to Container 2 and 3 as an endpoint-bounded instance containing an availability number of 6500 (Busy) and the &quot;on-the-phone&quot; activity token when the user has established a RCC phone call.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>A hash dependent on the local user’s SIP URI plus the phone device GRUU and uses the 0x9YYYYYYY format.</p></td>
<td><p>Published to Container 2 and 3 as an endpoint-bounded instance containing an availability number of 6500 (Busy) and the &quot;on-the-phone&quot; activity token when the user has established a UC-enabled PSTN phone call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Published to Container 1 as a static instance containing the use-specified <strong>Phone</strong> options. The information is used to construct <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a> of Instance ID 1.</p></td>
</tr>
<tr class="even">
<td><p><a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Published to Container 1 as a static instance containing the server-provisioned user identity information. The information is used to construct <a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a> of Instance ID 0.</p></td>
</tr>
<tr class="odd">
<td><p><a href="workinghours-category-instance-value-element.md">workingHours category instance value element</a></p></td>
<td><p>0</p></td>
<td><p>Published to Container 1 as a static instance containing the Microsoft Exchange-provisioned workingHours information. This is used by the call routing script to block in-bound calls outside of the user’s working-hours period.</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[\[MS-PRES\]: Presence Protocol Specification](http://go.microsoft.com/fwlink/?linkid=195873)

#### Concepts

[Presence data source and category instance ID](presence-data-source-and-category-instance-id.md)

[Presence category instances published or used by Lync](presence-category-instances-published-or-used-by-lync.md)

