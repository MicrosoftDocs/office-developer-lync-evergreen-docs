---
title: calendarData/WorkingHours//WorkingPeriod element
TOCTitle: calendarData/WorkingHours//WorkingPeriod element
ms:assetid: 90e5b226-9b0a-4352-95aa-4151c3e4e8db
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454731(v=office.15)
ms:contentKeyID: 57093445
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours//WorkingPeriod element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies a work period of a given contact.

``` xml
<WorkingPeriod>
    <StartTimeInMinutes>Start time of this working period</StartTimeInMinutes>
    <EndTimeInMinutes>End time of this working period</EndTimeInMinutes>
    <DayOfWeek>Week day or days </DayOfWeek>
</WorkingPeriod>
```

WorkingPeriod

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
<td><p>DayOfWeek</p></td>
<td><p>1</p></td>
<td><p>Week day or days when the user works</p></td>
</tr>
<tr class="even">
<td><p>StartTimeInMinutes</p></td>
<td><p>1</p></td>
<td><p>Starting time of this working period.</p></td>
</tr>
<tr class="odd">
<td><p>EndTimeInMinutes</p></td>
<td><p>1</p></td>
<td><p>Ending time of this working period.</p></td>
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
<td><p>WorkingPeriodArray</p></td>
<td><p>The user’s working periods.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Example

The following XML code snippet shows a working period:

``` xml
      <WorkingPeriod>
        <DayOfWeek>Monday Tuesday Wednesday Thursday Friday</DayOfWeek>
        <StartTimeInMinutes>480</StartTimeInMinutes>
        <EndTimeInMinutes>1020</EndTimeInMinutes>
      </WorkingPeriod>
```

The specified working period is 08:00-17:00 Monday through Friday.

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
<td><p>False</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

calendarData

WorkingHours

[Category instance elements for presence](category-instance-elements-for-presence.md)

