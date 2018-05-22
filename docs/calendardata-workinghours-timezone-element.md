---
title: calendarData/WorkingHours/TimeZone element
TOCTitle: calendarData/WorkingHours/TimeZone element
ms:assetid: e4aea7d8-3e3d-440d-aa1c-f11de968feea
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454700(v=office.15)
ms:contentKeyID: 57093383
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours/TimeZone element


_**Applies to:** Lync 2013 | Lync Server 2013_

Holds the user’s local time zone information.

``` xml
    <TimeZone>
      <Bias>480</Bias>
      <DaylightTime>...</DaylightTime>
      <StandardTime>...</StandardTime>
    </TimeZone>
```

SerializableTimeZone

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
<td><p>Offset in minutes between the local time zone and Coordinated Universal Time (UTC).</p></td>
</tr>
<tr class="even">
<td><p>DayLightTime</p></td>
<td><p>1</p></td>
<td><p>The daylight time of a given time zone.</p></td>
</tr>
<tr class="odd">
<td><p>StandardTime</p></td>
<td><p>1</p></td>
<td><p>The standard time of a given time zone.</p></td>
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

## Example

The following XML code snippet shows the US Pacific time zone information in a working-hours specification:

``` xml
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

The US Pacific time zone is 8 hour behind UTC (Bias of 480) containing the standard and daylight times. The standard time is in the same time zone of the user’s local time zone (with zero Bias) and begins at 2 AM on the first Sunday of November. The daylight time is in the time zone one hour the local time zone (with Bias of 60) and begins at 2AM on the second Sunday of March.

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

[Category instance elements for presence](category-instance-elements-for-presence.md)

