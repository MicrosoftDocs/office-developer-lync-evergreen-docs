---
title: calendarData/WorkingHours/Time element
TOCTitle: calendarData/WorkingHours/Time element
ms:assetid: 280ab004-5cfb-44c3-8382-36568e48f08a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454698(v=office.15)
ms:contentKeyID: 57093385
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours/Time element


**Applies to:** Lync 2013 | Lync Server 2013

Holds the time when the standard or daylight time zone begins

```xml
<Time>string</Time>
```

string

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

A string value of the time in the format of HH:MM:SS.

## Remarks

The time string value is of the HH:MM:SS format, where HH stands for two digits in hours, MM for two digits in minutes and SS for two digits in seconds.

## Example

The following XML code snippet shows the standard time in a given time zone:

```xml
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

