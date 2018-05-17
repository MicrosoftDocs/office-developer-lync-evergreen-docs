---
title: calendarData/WorkingHoursStandardTime element
TOCTitle: calendarData/WorkingHoursStandardTime element
ms:assetid: b36836d1-e42c-400e-ab14-d8d7b0653b27
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454696(v=office.15)
ms:contentKeyID: 57093366
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHoursStandardTime element


_**Applies to:** Lync Server 2013_

Holds the standard time of the user’s local time zone.

``` xml
<StandardTime>
    <Bias>Timezone offset in minutes from the local time zone </Bias>
    <Time>Starting time (hh:mm:ss) of the standard time</Time>
    <DayOrder>integer:[1, 4|5]</DayOrder>
    <Month>integer:[1,12]</Month>    <DayOfWeek>Sunday|Monday|Tuesday|Wednseday|Thursday|Friday|Saturday </DayOfWeek>
</ StandardTime >
```

SerializableTimeZoneTime

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
<td><p>Bias</p></td>
<td><p>1</p></td>
<td><p>Offset in minutes between the standard time and the local time zone.</p></td>
</tr>
<tr class="even">
<td><p>DayOfWeek</p></td>
<td><p>1</p></td>
<td><p>The week day (Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, or Sunday) when the standard time begins.</p></td>
</tr>
<tr class="odd">
<td><p>DayOrder</p></td>
<td><p>1</p></td>
<td><p>The order in a month of the week day (DayOfWeek) when the daylight time begins. This is an unsigned number between 1 and 4 or 5, depending on the month chosen.</p></td>
</tr>
<tr class="even">
<td><p>Month</p></td>
<td><p>1</p></td>
<td><p>The number of month (between 1 and 12, inclusively) when the standard time begins.</p></td>
</tr>
<tr class="odd">
<td><p>Time</p></td>
<td><p>1</p></td>
<td><p>The time of the HH:MM:SS format when the standard time begins, where HH stands for two digits in hours, MM for two digits in minutes and SS for two digits in seconds.</p></td>
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
<td><p>TimeZone</p></td>
<td><p>The user’s local time zone.</p></td>
</tr>
</tbody>
</table>


## Text value

None

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
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

calendarData

WorkingHours

[Category instance elements for presence](category-instance-elements-for-presence.md)

