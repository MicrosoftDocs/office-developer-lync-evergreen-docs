---
title: Parsing Lync-published category instances
TOCTitle: Parsing Lync-published category instances
ms:assetid: 356fb386-d8a7-478c-afb2-d151bdfa7c12
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454671(v=office.15)
ms:contentKeyID: 57093145
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Parsing Lync-published category instances

_**Applies to:** Lync 2013 | Lync Server 2013_

The following table shows how to parse some of the presence category instances that are published by Microsoft Lync 2013.

<br/>

<table>
<colgroup>
<col style="width: 40%" />
<col style="width: 10%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category name</p></th>
<th><p>Presence data</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>freeBusy information</p></td>
<td><p>Lync 2013 describes the contiguous block of free and busy time slots according to the user’s calendar.<br/><br/>This block of free-busy time slots is described by a Base64 encoded string of a stream of binary bits.<br/><br/>Every 2 bits represent the smallest unit of time (or the smallest time slot).<br/><br/>Four types of distinct time slots are used. Each represents a time when the user is free, tentative busy, busy, or out of office (OOF).<br/><br/>The corresponding binary bits are 00, 01, 10, and 11, respectively.<br/><br/>Thus, if the time slot is 15 minutes, a contiguous one-hour block of 30 minutes free and 30 minutes busy is described by a stream of binary bits of 00001010.<br/><br/>The corresponding Base64 encoded string value is &quot;Cg==&quot;.</p>
<p>The following is an example of a calendar data containing a freeBusy block.</p>

```XML
<calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData"
              mailboxID="johnD@exchange.contoso.com">
   <freeBusy startTime="2009-11-18T08:00:00Z" 
             granularity="PT15M" encodingVersion="1">AAAAAAAAAAAAAAAAAAAAVQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAVQoAqqoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
   </freeBusy>
</calendarData>
```
<p>In this example, the length of the smallest time slot is 15 minutes that is specified by the granularity attribute PT15M value, where PT stands for Pacific Time.<br/><br/>The user is identified by the mailboxID attribute johnD@exchange.contoso.com value.<br/><br/>The free-busy block starts at midnight of the US Pacific time on November 18, 2009, which is specified by the startTime attribute.<br/><br/>Once properly decoded, the length of the entire free-busy block is 96 hours, which can be determined by counting the number of bytes in the Base64 encoded string.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>Availability</p></td>
<td><p>Lync 2013 interprets the received availability number as follows.</p>
<div class="caption">
</div>
<div class="tableSection">
<table>
<colgroup>
<col style="width: 10%" />
<col style="width: 10%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Availability number range</p></th>
<th><p>Availability mode</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0-2999</p></td>
<td><p>Undefined</p></td>
<td><p>The contact is not found in the network.</p></td>
</tr>
<tr class="even">
<td><p>3000-4499</p></td>
<td><p><strong>Available</strong></p></td>
<td><p>The contact is willing and able to communicate.</p></td>
</tr>
<tr class="odd">
<td><p>4500-5999</p></td>
<td><p><strong>Available - Idle</strong></p></td>
<td><p>The contact is willing but may be unable to communicate.</p></td>
</tr>
<tr class="even">
<td><p>6000-7499</p></td>
<td><p><strong>Busy</strong></p></td>
<td><p>The contact is able but may be unwilling to communicate.</p></td>
</tr>
<tr class="odd">
<td><p>7500-8999</p></td>
<td><p><strong>Busy - Idle</strong></p></td>
<td><p>The contact is able but may be unwilling to communicate.</p></td>
</tr>
<tr class="even">
<td><p>9000-11999</p></td>
<td><p><strong>Do Not Disturb</strong></p></td>
<td><p>The contact is able but unwilling to communicate.</p></td>
</tr>
<tr class="odd">
<td><p>12000-14999</p></td>
<td><p><strong>Be Right Back</strong></p></td>
<td><p>The contact is willing but unable to communicate.</p></td>
</tr>
<tr class="even">
<td><p>15000-17999</p></td>
<td><p><strong>Away</strong></p></td>
<td><p>The contact is unable to communicate.</p></td>
</tr>
<tr class="odd">
<td><p>18000 and higher</p></td>
<td><p><strong>Offline</strong></p></td>
<td><p>The contact is not connected to the network.</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Standard Activities</p></td>
<td><p>Lync 2013 interprets the received activity tokens as the following standard activity strings, if the activity element is not specified in a received aggregateState instance.</p>
<p></p>
<div class="caption">

</div>
<div class="tableSection">
<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Standard activity token</p></th>
<th><p>Standard activity string</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>in-a-meeting</p></td>
<td><p>In a meeting</p></td>
</tr>
<tr class="even">
<td><p>In-a-conference</p></td>
<td><p>In a conference</p></td>
</tr>
<tr class="odd">
<td><p>on-the-phone</p></td>
<td><p>In a call</p></td>
</tr>
<tr class="even">
<td><p>out-of-office</p></td>
<td><p>Out of office</p></td>
</tr>
<tr class="odd">
<td><p>Urgent-interruptions-only</p></td>
<td><p>Urgent interruptions only</p></td>
</tr>
</tbody>
</table>
</div>
<p></p>
<p><b>NOTE</b>: Activity tokens are case-sensitive.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Default Activity Strings</p></td>
<td><p>Lync 2013 maps the availability modes to the following default activity strings, if no activity is specified in the received aggregateState instance.</p>
<div class="caption">

</div>
<div class="tableSection">
<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Availability number</p></th>
<th><p>Default activity string</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0-2999</p></td>
<td><p>Presence unknown</p></td>
</tr>
<tr class="even">
<td><p>3000-4499</p></td>
<td><p>Available</p></td>
</tr>
<tr class="odd">
<td><p>4500-5999</p></td>
<td><p>Inactive</p></td>
</tr>
<tr class="even">
<td><p>6000-7499</p></td>
<td><p>Busy</p></td>
</tr>
<tr class="odd">
<td><p>7500-8999</p></td>
<td><p>Busy</p></td>
</tr>
<tr class="even">
<td><p>9000-11999</p></td>
<td><p>Do not disturb</p></td>
</tr>
<tr class="odd">
<td><p>12000-14999</p></td>
<td><p>Be right back</p></td>
</tr>
<tr class="even">
<td><p>15000-17999</p></td>
<td><p>Away</p></td>
</tr>
<tr class="odd">
<td><p>18000 or higher</p></td>
<td><p>Offline</p></td>
</tr>
<tr class="even">
<td><p>Unspecified</p></td>
<td><p>Offline</p></td>
</tr>
</tbody>
</table>

</div>
<p></p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>Activity string display</p></td>
<td><p>Lync 2013 uses the following logic to display a contact’s activity string:</p>
<ul>
<li><p>For a blocked contact, the activity string of &quot;Blocked&quot; is displayed.</p></li>
<li><p>If a standard activity token is specified, the corresponding standard activity string is displayed.</p></li>
<li><p>If a standard activity token is not specified but an activity string is specified, the specified activity string is displayed.</p></li>
<li><p>If a standard activity token is not specified and no activity strings are specified, the default activity string corresponding to the specified availability number is displayed.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Capabilities Summary String</p></td>
<td><p>Lync 2013 displays the following capabilities summary string to supplement an activity string.</p>
<div class="caption">
</div>
<div class="tableSection">
<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Capabilities summary string</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>No IM</p></td>
<td><p>This is displayed when the availability of the most active device supporting an instant messaging capability is Offline and the aggregated availability is not Offline.</p></td>
</tr>
<tr class="even">
<td><p>Voice Only</p></td>
<td><p>This is displayed when the availability of the most active device supporting an instant messaging capability is Offline and the aggregated availability is no less active than Inactive.</p></td>
</tr>
<tr class="odd">
<td><p>Mobile</p></td>
<td><p>This is displayed if the only active endpoint is a mobile device.</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p>lastActive attribute</p></td>
<td><p>For an inactive mode of Available – Idle, Busy – Idle, Be Right Back, Away, or Offline, Lync 2013 displays the time period in which an aggregated state has remained inactive since the last active mode of Available, Busy, or Do Not Disturb. This inactive time period is appended to an inactive state as &quot;<em>Inactive for 5 mins</em>&quot;, &quot;<em>Away for 5 hours</em>&quot; or &quot;<em>Offline for 20 mins</em>&quot;. The following example shows how this scenario is computed. lastActiveTime has the value of the lastActive attribute of an appropriate aggregated state.</p>
<p> `inactiveTimePeriod = currentTime - lastActiveTime` </p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p>Location</p></td>
<td><p>The subscriber receives a computed location that is determined in the following manner:</p>
<p>When the aggregated availability number is less than 12000 and the most active computer (with the lowest availability number) has its location specified (in the <a href="state-endpointlocation-element.md">state/endpointLocation element</a> element), this location information will be included in the <a href="state-element_4.md">state[@type='aggregateState'] element</a> instance.</p>

<p><b>NOTE</b>: The received location information indicates a place either set by the publisher or provided by the Microsoft Lync Server 2013 Location Information Service. The location information that the publisher wants the remote watchers to see is present. It is not necessarily the location where the user is actually located.</p>
</td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## See also

- [Presence category instances published or used by Lync](presence-category-instances-published-or-used-by-lync.md)

