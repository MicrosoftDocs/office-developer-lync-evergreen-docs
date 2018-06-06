---
title: calendarData/WorkingHours/DayOrder element
TOCTitle: calendarData/WorkingHours/DayOrder element
ms:assetid: 0d756fe0-6ec1-4b55-b31b-4e2afdc37c17
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454703(v=office.15)
ms:contentKeyID: 57093390
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours/DayOrder element


_**Applies to:** Lync 2013 | Lync Server 2013_

Holds the order of a week day (specified in a DayOfWeek element) in a month when the standard or daylight time zone begins.

Root Element  
  Next Element  

``` xml
<DayOrder>Positional number of a given week day in a month</DayOrder>
```

short

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
<td><p>DaylightTime</p></td>
<td><p>The daylight time of a given time zone.</p></td>
</tr>
<tr class="even">
<td><p>StandardTime</p></td>
<td><p>The standard time of a given time zone.</p></td>
</tr>
</tbody>
</table>


## Text value

An integer value between 1 and 4 or 5.

## Example

The following XML code snippet shows the standard time in a given time zone:

``` xml
<StandardTime>
    <Bias>0</Bias>
    <Time>02:00:00</Time>
    <DayOrder>1</DayOrder>
    <Month>11</Month>
    <DayOfWeek>Sunday</DayOfWeek>
</StandardTime>
```

The specified standard time is in the same time zone of the user’s local time zone (with zero Bias) and begins at 2 AM on the first Sunday of November.

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

