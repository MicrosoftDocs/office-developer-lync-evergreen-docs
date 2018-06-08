---
title: calendarData/WorkingHours/DayOfWeek element
TOCTitle: calendarData/WorkingHours/DayOfWeek element
ms:assetid: 2e29261a-8cdf-4581-b74c-cffcce697bb1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454702(v=office.15)
ms:contentKeyID: 57093384
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours/DayOfWeek element


**Applies to:** Lync 2013 | Lync Server 2013

Holds the day of a week when the standard or daylight time zone begins or the days of a week designated as the working days of the user.

```xml
<DayOfWeek>The week day or days.</DayOfWeek>
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
<tr class="odd">
<td><p>WorkingPeriod</p></td>
<td><p>A period of days as working days.</p></td>
</tr>
</tbody>
</table>


## Text value

A string

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

