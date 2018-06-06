---
title: calendarData/WorkingHoursStartTimeInMinutes element
TOCTitle: calendarData/WorkingHoursStartTimeInMinutes element
ms:assetid: c56f5283-ba0f-4260-a5b8-5c8fc5e67aa6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454697(v=office.15)
ms:contentKeyID: 57093388
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHoursStartTimeInMinutes element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the starting time of a work period.

``` xml
    <StartTimeInMinutes>Start time of this working period</StartTimeInMinutes>
```

int

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

#### Child elements

None

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
<td><p>WorkingPeriod</p></td>
<td><p>A working period.</p></td>
</tr>
</tbody>
</table>


## Text value

An integer

## Remarks

The element value is a number in minutes starting from 00:00 (midnight) of the local time.

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

