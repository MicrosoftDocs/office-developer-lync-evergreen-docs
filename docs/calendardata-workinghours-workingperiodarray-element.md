---
title: calendarData/WorkingHours/WorkingPeriodArray element
TOCTitle: calendarData/WorkingHours/WorkingPeriodArray element
ms:assetid: f113e849-9f89-48ff-b802-fd28924404f2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454718(v=office.15)
ms:contentKeyID: 57093405
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours/WorkingPeriodArray element


_**Applies to:** Lync 2013 | Lync Server 2013_

Holds an array of working-hours periods of a user.

``` xml
    <WorkingPeriodArray>
      <WorkingPeriod>         <DayOfWeek>string</DayOfWeek>
         <StartTimeInMinutes>int</StartTimeInMinutes >
         <EndTimeInMinutes>int</EndTimeInMinutes >
      </WorkingPeriod>
      <WorkingPeriod>
         ......
      </WorkingPeriod>
    </ WorkingPeriodArray >
```

ArrayOfWorkingPeriod

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

#### Child elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Occurrence</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>WorkingPeriod</p></td>
<td><p>0 or more</p></td>
<td><p>A working period.</p></td>
</tr>
</tbody>
</table>


#### Parent elements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>WorkingHours</p></td>
<td><p>The working-hours specification obtained from the underlying Exchange Server.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

A working period array can have zero or more working periods. For

## Example

The following XML code snippet shows an array of two working periods:

``` xml
    <WorkingPeriodArray>
      <WorkingPeriod>
        <DayOfWeek>Monday Wednesday Friday</DayOfWeek>
        <StartTimeInMinutes>480</StartTimeInMinutes>
        <EndTimeInMinutes>1020</EndTimeInMinutes>
      </WorkingPeriod>
      <WorkingPeriod>
        <DayOfWeek>Tuesday Thursday</DayOfWeek>
        <StartTimeInMinutes>600</StartTimeInMinutes>
        <EndTimeInMinutes>1140</EndTimeInMinutes>
      </WorkingPeriod>
    </WorkingPeriodArray>
```

The above working hour period array specification indicates that the specified contact works 08:00-17:00 on Mondays, Wednesdays and Fridays and on Tuesdays and Thursdays, the user also works 10:00-19:00.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/exchange/services/2006/types</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>calendarData</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>calendarData.xsd, calendardatatypes.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

calendarData

[Category instance elements for presence](category-instance-elements-for-presence.md)

