---
title: calendarData category instance value element
TOCTitle: calendarData category instance value element
ms:assetid: 972e3637-d1fe-4c92-b34c-5c6063f9c35b
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454705(v=office.15)
ms:contentKeyID: 57093392
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData category instance value element


**Applies to:** Lync 2013 | Lync Server 2013

Holds calendar data obtained from an integrated Exchange Server computer.

```xml
<calendarData xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData"
    mailboxID="xs:anyURI"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt"
    anyAttr="anyattr">
    <WorkingHours xmlns="http://schemas.microsoft.com/exchange/services/2006/types">......</WorkingHours>
    <freeBusy xmlns="http://schemas.microsoft.com/exchange/services/2006/types"
        startTime="0001-01-01T00:00:00" granularity="granularity" encodingVersion="0" anyAttr="anyattr">......</freeBusy>
    <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any] >Any element</[any]>
    <ct:end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <ct:extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any] >any element in any namespace</[any]>
    </ct:extension>
</calendarData>
```

calendarType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Attribute</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>mailBoxID</p></td>
<td><p>Required attribute to hold the SMTP address of the user whose calendar data is contained in this element. For example, &quot;mary@contoso.com&quot;</p></td>
</tr>
<tr class="even">
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent major version information.</p></td>
</tr>
<tr class="odd">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent minor version information.</p></td>
</tr>
<tr class="even">
<td><p>anyAttr</p></td>
<td><p>Optional custom attribute of any name and namespace</p></td>
</tr>
</tbody>
</table>


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
<td><p><a href="calendardata-workinghours-element.md">calendarData/WorkingHours element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A user’s working-hours information as specified in the underlying Exchange Server computer. Each calendarData instance can have either a WorkingHours or freeBusy child element, but not both.</p></td>
</tr>
<tr class="even">
<td><p><a href="calendardata-freebusy-element.md">calendarData/freeBusy element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A user’s free-busy time slots as specified in the underlying Exchange Server computer. Each calendarData instance can have either a WorkingHours or freeBusy child element, but not both.</p></td>
</tr>
<tr class="odd">
<td><p>ct:delimiter</p></td>
<td><p>0 or more</p></td>
<td><p>An empty element, of the CommonTypes (ct) namespace, to mark the start of a schema extension to its parent element. Elements describing the extension are enclosed between a ct:delimiter and ct:end elements or between two ct:delimiter elements.</p></td>
</tr>
<tr class="even">
<td><p>ct:end</p></td>
<td><p>0 or 1</p></td>
<td><p>An empty element, of the CommonTypes (ct) namespace, to mark the end of all the schema extensions to its parent element.</p></td>
</tr>
<tr class="odd">
<td><p>ct:extension</p></td>
<td><p>0 or more</p></td>
<td><p>An element, of the CommonTypes (ct) namespace, to hold any elements of any namespace as an application-defined custom extension to the parent element.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>A custom element describing an extension to its parent element. When enclosed between a ct:delimiter element and a ct:end element or between two ct:delimiter elements, this element serves to describe a schema extension and can have any name in the namespace of its parent element. When contained in an ct:extension element, this element describes the application-defined custom extension and can have any name in any namespace.</p></td>
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
<td><p>None</p></td>
<td><p>This is a top-level element that contains the value of a calendarData enhanced presence category instance</p></td>
</tr>
</tbody>
</table>


## Text value

This element has no text value.

## Remarks

A calendarData category instance element can contain either a **WorkingHours** child element or a **freeBusy** child element or both. Microsoft Lync 2013 uses separate calendarData elements for WorkingHours and freeBusy. It can be an empty element, especially when it's used to block remote users from accessing the local user’s calendar data.

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

Lync 2013 uses a separate calendarData element for WorkingHours and freeBusyData.

The following XML snippet of a calendarData category instance contains a **freeBusy** data.

    <calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData" mailboxID="bob@contoso.com">
       <freeBusy startTime="2009-10-27T07:00:00Z" 
         granularity="PT15M" 
         encodingVersion="1" >AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABVAABVAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAqgAAAAAAVQAA</freeBusy> 
    </calendarData>

The base64 encoded string value corresponds to a contiguous timeslots having the unit length of 15 minutes and the total length of 96 hours. The starting time corresponds to the midnight Pacific Daylight Time, October 27th, 2009.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/calendarData</p></td>
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

[Category instance elements for presence](category-instance-elements-for-presence.md)

