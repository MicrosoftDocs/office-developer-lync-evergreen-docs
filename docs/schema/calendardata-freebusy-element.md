---
title: calendarData/freeBusy element
TOCTitle: calendarData/freeBusy element
ms:assetid: dbd4803a-c1d0-44a6-85cc-72780b5af2a0
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454707(v=office.15)
ms:contentKeyID: 57093394
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# calendarData/freeBusy element


**Applies to**: Lync Server 2013

Contains a contiguous calendar block, showing free-busy intervals of a specified duration from a specified starting time.

[calendarData category instance value element](calendardata-category-instance-value-element.md)  
  freeBusy Element  

```xml
<freeBusy xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData"
    startTime="dateTime" granularity="duration" encodingVersion="decimal"> 
   A Base64 encode string of a binary stream
</freeBusy>
```

base64Binary

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
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name in any namespace</p></td>
</tr>
<tr class="even">
<td><p>encodingVersion</p></td>
<td><p>Required attribute of the xs:duration type specifying the encoding version of the element value.</p></td>
</tr>
<tr class="odd">
<td><p>granularity</p></td>
<td><p>Required attribute of the xs:duration type specifying the smallest timeslot period as the unit of a contiguous block of time known as the freeBusy block.</p></td>
</tr>
<tr class="even">
<td><p>startTime</p></td>
<td><p>Required attribute of the xs:dateTime type specifying the beginning point of time when the freeBusy block starts.</p></td>
</tr>
</tbody>
</table>


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
<td><p><a href="calendardata-category-instance-value-element.md">calendarData category instance value element</a></p></td>
<td><p>The calendarData category instance containing this freeBusy data.</p></td>
</tr>
</tbody>
</table>


## Text value

Base64 encoded value of the binary stream.

## Remarks

This element contains a user’s free-busy timeslots specified in the underlying Exchange Server. The value of this element represents a contiguous timeslots with the unit length specified by the granularity attribute and the starting time by the startTime attribute. Each timeslot is represented by 2 bits. There are four types of timeslots:

  - Free timeslot  
    The binary value of a Free timeslot is 00.

  - Tentative timeslot  
    The binary value of a Tentative timeslot is 01.

  - Busy timeslot  
    The binary value of a Busy timeslot is 10.

  - Out of Office timeslot  
    The binary value of an Out of Office timeslot is 11.

For example, given a granularity value of "PT15M", each timeslot spans 15 minutes and a contiguous block consisting of

1.  a busy period of 60 minutes, 10101010

2.  a free period of 75 minutes, 0000000000

3.  a tentative period of 60 minutes, 01010101

4.  an Out of Office period of 60 minutes, 11111111, and

5.  another free period of 30 minutes, 0000

is thus represented by a bit stream of 10101010000000000001010101111111110000. Converting this bit stream to a Base64 encoded string yields the value of the freeBusy element.

## Example

This is the description for a Code Example.

    <calendarData xmlns="http://schemas.microsoft.com/2006/09/sip/calendarData" mailboxID="bob@contoso.com">
       <freeBusy xmlns="http://schemas.microsoft.com/exchange/services/2006/types"
           startTime="0001-01-01T00:00:00" 
           granularity="granularity" 
           encodingVersion="1" 
           anyAttr="anyattr">AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABVAABVAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAqgAAAAAAVQAA</freeBusy>
    </calendarData>

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

[calendarData category instance value element](calendardata-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

