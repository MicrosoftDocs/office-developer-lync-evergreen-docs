---
title: calendarData/WorkingHours element
TOCTitle: calendarData/WorkingHours element
ms:assetid: 9e4d9ee0-e82b-4e38-b32a-3399c29df0cb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454695(v=office.15)
ms:contentKeyID: 57093363
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/WorkingHours element


_**Applies to:** Lync 2013 | Lync Server 2013_

A user’s working-hours information as specified in the underlying Exchange Server computer.

[calendarData category instance value element](calendardata-category-instance-value-element.md)  
  WorkingHours Element  

``` xml
< WorkingHours xmlns="http://schemas.microsoft.com/exchange/services/2006/types">
    <TimeZone>
        <Bias>Timezone offset from GMT in minutes</Bias>
        <StandardTime>
            <Bias>Timezone offset from GMT in minutes </Bias>
            <Time>Starting time (hh:mm:ss)</Time>
            <DayOrder>integer:[1,4|5]</DayOrder>
            <Month>integer:[1,12]</Month>
            <DayOfWeek>Sunday|Monday|Tuesday|Wednseday|Thursday|Friday|Saturday</DayOfWeek>
        </StandardTime>
        <DaylightTime>
            <Bias>Timezone offset from GMT in minutes</Bias>
            <Time>Starting time (hh:mm:ss)</Time>
            <DayOrder>integer:[1, 4|5]</DayOrder>
            <Month>integer:[1,12]</Month>
            <DayOfWeek>Sunday|Monday|Tuesday|Wednseday|Thursday|Friday|Saturday </DayOfWeek>
        </DaylightTime>
    </TimeZone>
    <WorkingPeriodArray>
        <WorkingPeriod>
            <DayOfWeek>[Sunday[ Monday[ Tuesday[ Wednseday[ Thursday[ Friday [Saturday]]]]]]]</DayOfWeek>
            <StartTimeInMinutes>Minutes starting from the midnight</StartTimeInMinutes>
            <EndTimeInMinutes>Minutes starting from the midnight</EndTimeInMinutes>
        </WorkingPeriod>
    </WorkingPeriodArray>
</WorkingHours>
```

WorkingHours

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
<td><p><a href="calendardata-workinghours-timezone-element.md">calendarData/WorkingHours/TimeZone element</a></p></td>
<td><p>1</p></td>
<td><p>Current time zone of the user’s working hours.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-workinghours-workingperiodarray-element.md">calendarData/WorkingHours/WorkingPeriodArray element</a></p></td>
<td><p>1</p></td>
<td><p>An array of working periods forming the user’s working hours.</p></td>
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
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>calendarData category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

This element is defined in the Microsoft Exchange Service namespace, the name of which is "http://schemas.microsoft.com/exchange/services/2006/types".

## Example

The following XML code example of a **calendarData** category instance shows the working hours of a contact (bob@contoso.com) consist of Monday through Friday between 8:00 and 17:00 in the US Pacific Time Zone.

    <?xml version="1.0" encoding="utf-8" ?>
    <calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData" mailboxID="bob@contoso.com">
      <WorkingHours xmlns="http://schemas.microsoft.com/exchange/services/2006/types">
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
        <WorkingPeriodArray>
          <WorkingPeriod>
            <DayOfWeek>Monday Tuesday Wednesday Thursday Friday</DayOfWeek>
            <StartTimeInMinutes>480</StartTimeInMinutes>
            <EndTimeInMinutes>1020</EndTimeInMinutes>
          </WorkingPeriod>
        </WorkingPeriodArray>
      </WorkingHours> 
    </calendarData>

Microsoft Lync 2013 uses separate calendarData elemenst to specify WorkingHours and freeBusyData, respectively.

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

[Category instance elements for presence](category-instance-elements-for-presence.md)

