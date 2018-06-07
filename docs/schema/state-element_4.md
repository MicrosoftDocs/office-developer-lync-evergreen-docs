---
title: state[@type='aggregateState'] element
TOCTitle: state[@type='aggregateState'] element
ms:assetid: 5068097e-f2e0-4d96-82b5-b4747f4e71a6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438960(v=office.15)
ms:contentKeyID: 57093996
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state\[\@type='aggregateState'\] element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies an aggregated presence state category instance.

``` xml
<st:state xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" 
          xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:type="aggregateState"
       manual="xs:boolean" 
       startTime="xs:dateTime" 
       majorVersion="xs:unsignedInt" 
       minorVersion="xs:unsignedInt"
       [anyAttri]="anyAttribute">
       lastActive="xs:dateTime"
   <st:availability>xs:unsignedInt</st:availability>
   <st:activity>st:activityType</st:activity>
   <st:endpointLocation>st:endpointLocationEnumEx</st:endpointLocation>
   <st:extension>st:extensionType</st:extension>
   <st:meetingSubject>st:LCIDType</st:meetingSubject>
   <st:meetingLocation>st:LCIDType</st:meetingLocation>
   <st:timeZoneBias>xs:long</st:timeZoneBias>
   <st:timeZoneName>xs:string</st:timeZoneName>
   <st:timeZoneAbbreviation>xs:string</st:timeZoneAbbreviation>
   <st:device>st:deviceTypeEnumEx</st:device>
   <ct:delimiter/>
   <st:[any]>any element</st:[any]>
   <ct:end/>
   <ct:extension>
     <[any] xmlns="any.namespace">...</[any]>
   </ct:extension>
</st:state>
```

aggregateState : stateType

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
<td><p>xsi:type</p></td>
<td><p>Required attribute with the fixed value of &quot;aggregateMachineState&quot;. This attribute is not explicitly defined, but permitted as one of any custom attributes (@[anyAttr]) described below.</p></td>
</tr>
<tr class="even">
<td><p>manual</p></td>
<td><p>Optional attribute to specify if the publication of this state is manual (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="odd">
<td><p>startTime</p></td>
<td><p>Optional attribute to specify the starting time of this state publication. The default value is unspecified.</p></td>
</tr>
<tr class="even">
<td><p>lastActive</p></td>
<td><p>Optional attribute describing the date and time when the presence state was last active. This attribute is specific to the presence state category instance of the aggregateState type.</p></td>
</tr>
<tr class="odd">
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent major version information. The default value is unspecified.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent minor version information. The default value is unspecified.</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace.</p></td>
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
<td><p><a href="state-availability-element.md">state/availability element</a></p></td>
<td><p>0 ore 1</p></td>
<td><p>Availability number indicating the presence status.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-activity-element.md">state/activity element</a></p></td>
<td><p>0 or more</p></td>
<td><p>An activity string and/or token describing the presence status.</p></td>
</tr>
<tr class="odd">
<td><p><a href="state-endpointlocation-element.md">state/endpointLocation element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Location of the endpoint associated with this presence state</p></td>
</tr>
<tr class="even">
<td><p><a href="state-endpointlocation-element.md">state/endpointLocation element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Custom extension to the presence state</p></td>
</tr>
<tr class="odd">
<td><p><a href="state-meetingsubject-element.md">state/meetingSubject element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Contains the meeting subject as specified in a calendar state category instance derived from the calendar data of the presentity.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-meetinglocation-element.md">state/meetingLocation element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Contains the meeting location as specified in a calendar state category instance derived from the calendar data of the presentity.</p></td>
</tr>
<tr class="odd">
<td><p><a href="state-timezonebias-element.md">state/timeZoneBias element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Contains the time zone bias from UTC in minutes of the local time zone where this publication is made.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-timezonename-element.md">state/timeZoneName element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Contains the name of the local time zone where this publication is made.</p></td>
</tr>
<tr class="odd">
<td><p><a href="state-timezoneabbreviation-element.md">state/timeZoneAbbreviation element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Contains the abbreviation of the local time zone where this publication is made.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-device-element.md">state/device element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Contains the type of the device where this publication is made. Valid values are of the st:deviceTypeEnumEx tokens.</p>
<p>Microsoft Lync 2013 recognizes the following device type tokens:</p>
<dl>
<dt>computer</dt>
<dd><p>The device is a computer on which Lync 2013 is running.</p>
</dd>
<dt>deskphone</dt>
<dd><p>The device is a desk phone on which Lync Phone Edition is running.</p>
</dd>
<dt>mobile</dt>
<dd><p>The device is a mobile phone on which Microsoft Lync 2010 for Android, iPad, iPhone, Nokia, or Windows Phone is running.</p>
</dd>
<dt>web</dt>
<dd><p>This is a computer on which Microsoft Lync Web App is running.</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker of a schema extension to this element.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Schema extension</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The ending marker of all the schema extensions to this element.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-specific custom extension.</p></td>
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
<td><p>This is a top-level element as an aggregated state category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

stateType is the base type of the aggregateState. Use stateType as the serialization type to serialize or de-serialize an aggregateState category instance.

Lync 2013 allows remote subscribers to receive this type of state category instances only.

## Example

The following XML snippet shows an aggregated state category instance value.

    <state xsi:type="aggregateState" 
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           xmlns="http://schemas.microsoft.com/2006/09/sip/state">
       <availability>3500</availability>
       <endpointLocation>Building 10, Room 101, West Campus</endpointLocation>
       <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
       <timeZoneBias>480</timeZoneBias>
       <timeZoneName>Pacific Standard Time</timeZoneName>
       <timeZoneAbbreviation>Pacific Standard Time</timeZoneAbbreviation>
       <device>computer</device>
       <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    </state>

The above presence state category instance value describes that the overall presence state is available (availability=3500) of a presentity located in Room 101 of Building 10 on West Campus situated in the US Pacific Standard Time zone.

Notice that a schema extension to this element is enclosed between the ct:delimiter and ct:end elements.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/state</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>state</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>state.xsd, statetypes.xsd</p></td>
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

[state category instance value elements](state-category-instance-value-elements.md)

#### Other resources

Presence State and state Category Instances

