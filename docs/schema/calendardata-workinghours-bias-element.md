---
title: calendarData/WorkingHours/Bias element
TOCTitle: calendarData/WorkingHours/Bias element
ms:assetid: 9b2c6b52-140f-4c3e-85bc-c33a3a9d6cf4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454699(v=office.15)
ms:contentKeyID: 57093386
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- vb
---

# calendarData/WorkingHours/Bias element


_**Applies to:** Lync 2013 | Lync Server 2013_

Holds the offset from the Coordinated Universal Time (UTC) of the user’s local time zone and the applicable standard time and daylight savings time in that time zone times.

``` vb
<Bias xmlns="http://schemas.microsoft.com/exchange/services/2006/types">
   Offset from the Coorindated Universal Time (UTC)
</Bias>
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
<td><p><a href="calendardata-workinghours-daylighttime-element.md">calendarData/WorkingHours/DaylightTime element</a></p></td>
<td><p>Dayligh Savings Time.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-workinghoursstandardtime-element.md">calendarData/WorkingHoursStandardTime element</a></p></td>
<td><p>Standard Time.</p></td>
</tr>
<tr class="odd">
<td><p><a href="calendardata-workinghours-timezone-element.md">calendarData/WorkingHours/TimeZone element</a></p></td>
<td><p>User’s local time zone.</p></td>
</tr>
</tbody>
</table>


## Text value

A signed number in minutes

## Remarks

The value of this element has the following meaning depending on the parent element:

  - DaylightTime  
    As part of the Daylight Savings Time specification, the Bias element contains the signed number in minute between the daylight savings time and the local time zone.

  - StandardTime  
    As part of the Standard Time specification, the Bias element contains the signed number in minute between the standard time and the local time zone.

  - TimeZone  
    As part of the time zone specification, the Bias element contains the signed number in minute between the local time zone and Coordinate Universal Time (UTC).

## Example

The following XML code snippet indicates the US Pacific time zone.

``` 
    <TimeZone>
      <Bias>480</Bias>
      <StandardTime>
        <Bias>0</Bias>
        <Time>02:00:00</Time>
        <DayOrder>1</DayOrder>
        <Month>11</Month>
        <DayOfWeek>Sunday</DayOfWeek>
      </StandardTime>
      <DaylightTime>
        <Bias>60</Bias>
        <Time>02:00:00</Time>
        <DayOrder>2</DayOrder>
        <Month>3</Month>
        <DayOfWeek>Sunday</DayOfWeek>
      </DaylightTime>
    </TimeZone>
```

The US Pacific time zone is eight hours (480 minutes) behind the UTC. Its standard time coincides with that of the local time zone (with zero bias) and its daylight savings time is another hour (60 minutes) behind the standard time.

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

[calendarData category instance value element](calendardata-category-instance-value-element.md)

[calendarData/WorkingHours element](calendardata-workinghours-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

