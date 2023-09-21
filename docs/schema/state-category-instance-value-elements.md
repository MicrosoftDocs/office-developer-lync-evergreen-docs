---
title: state category instance value elements
TOCTitle: state category instance value elements
ms:assetid: 641377fc-596f-4d07-a5be-b90808e82a7e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454811(v=office.15)
ms:contentKeyID: 57093958
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state category instance value elements


**Applies to**: Lync Server 2013

Specifies the abstract base type of any presence state category instance value.

```xml
<st:state xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" 
       manual="xs:boolean" 
       startTime="xs:dateTime" 
       majorVersion="xs:unsignedInt" 
       minorVersion="xs:unsignedInt"
       [anyAttri]="anyAttribute">
   <st:availability>xs:unsignedInt</st:availability>
   <st:activity>st:activityType</st:activity>
   <st:endpointLocation>st:endpointLocationEnumEx</st:endpointLocation>
   <st:extension>st:extensionType</st:extension>
</st:state>
```

stateType

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
<td><p>manual</p></td>
<td><p>Optional attribute to specify if the publication of this state is manual (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="even">
<td><p>startTime</p></td>
<td><p>Optional attribute to specify the starting time of this state publication. The default value is unspecified.</p></td>
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
<td><p><a href="state-extension-element.md">state/extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Custom extension to the presence state</p></td>
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
<td><p>This is a top-level element as a presence state category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

stateType is an abstract XML type and services as the base type of all of the following concrete presence state types: aggregateMachineState, aggregateState, calendarState, machineState, phoneState, userState

All the concrete presence state category instance values has an xsi:type attribute declared. The value of this attribute is the name of concrete presence state derived from stateType. For example, the userState category instance value is expressed as \<state type="userState"\> ...\</state\>

While the attributes and elements tables above list all the common features of the enhanced presence state category instance can have, the features specific to the individual concrete state types are documented in the XML elements of the following XSD types:

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concrete Presence State</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="state-element_5.md">state[@type='aggregateMachineState'] element</a></p></td>
<td><p>Aggregated presence state over all the signed-in devices.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-element_4.md">state[@type='aggregateState'] element</a></p></td>
<td><p>Aggregated presence state over all the presence states data of a presentity.</p></td>
</tr>
<tr class="odd">
<td><p><a href="state-element_3.md">state[@type='calendarState'] element</a></p></td>
<td><p>Presence state according the user’s calendar data.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-element_2.md">state[@type='machineState'] element</a></p></td>
<td><p>Presence state of individual signed-in devices.</p></td>
</tr>
<tr class="odd">
<td><p><a href="state-element_1.md">state[@type='phoneState'] element</a></p></td>
<td><p>Presence state of a voice/video call.</p></td>
</tr>
<tr class="even">
<td><p><a href="state-element.md">state[@type='userState'] element</a></p></td>
<td><p>User-specific presence state.</p></td>
</tr>
</tbody>
</table>



> [!TIP]
> <P>Programming with the enhanced presence state involves creating XML elements of the concrete presence state types in publication and parsing them in subscription or query. These programming tasks can be facilitated by using the .NET Framework’s System.Xml.Serialization namespace. However, to serialize or de-serialize the XML elements of the concrete presence state types, you must specify their base type, stateType, as the serialization type. For more information, see <A href="serialization-of-enhanced-presence-category-instances.md">Serialization of Enhanced Presence category instances</A>s.</P>



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

#### Other resources

Presence State and state Category Instances

