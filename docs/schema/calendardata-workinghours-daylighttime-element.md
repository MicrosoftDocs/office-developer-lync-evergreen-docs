---
title: calendarData/WorkingHours/DaylightTime element
TOCTitle: calendarData/WorkingHours/DaylightTime element
ms:assetid: de33b6e5-c1b8-4c13-a52f-409099786887
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454701(v=office.15)
ms:contentKeyID: 57093387
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours/DaylightTime element


**Applies to:** Lync 2013 | Lync Server 2013

Holds the daylight savings time of the user’s local time zone.

```xml
<DaylightTime>
    <Bias>Timezone offset in minutes from the local time zone </Bias>
    <Time>Starting time (hh:mm:ss) of the daylight time</Time>
    <DayOrder>integer:[1, 4|5]</DayOrder>
    <Month>integer:[1, 12]</Month>    <DayOfWeek>Sunday|Monday|Tuesday|Wednseday|Thursday|Friday|Saturday </DayOfWeek>
</DaylightTime>
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
<td><p>Offset in minutes between the daylight savings time and the local time zone.</p></td>
</tr>
<tr class="even">
<td><p>DayOfWeek</p></td>
<td><p>1</p></td>
<td><p>The week day (Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, or Sunday) when the daylight savings time begins.</p></td>
</tr>
<tr class="odd">
<td><p>DayOrder</p></td>
<td><p>1</p></td>
<td><p>The order in a month of the week day (DayOfWeek) when the daylight time begins. This is an unsigned number between 1 and 4 or 5, depending on the month chosen.</p></td>
</tr>
<tr class="even">
<td><p>Month</p></td>
<td><p>1</p></td>
<td><p>The number of month (between 1 and 12, inclusively) when the daylight time begins.</p></td>
</tr>
<tr class="odd">
<td><p>Time</p></td>
<td><p>1</p></td>
<td><p>The time of the HH:MM:SS format when the daylight time begins, where HH stands for two digits in hours, MM for two digits in minutes and SS for two digits in seconds.</p></td>
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

The following XML code snippet shows the daylight time in a given time zone:

``` 
      <DaylightTime>
        <Bias>60</Bias>
        <Time>02:00:00</Time>
        <DayOrder>2</DayOrder>
        <Month>3</Month>
        <DayOfWeek>Sunday</DayOfWeek>
      </DaylightTime>
```

The specified Daylight time is an hour behind the local time zone and begins at 2 AM on the second Sunday of March.

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

