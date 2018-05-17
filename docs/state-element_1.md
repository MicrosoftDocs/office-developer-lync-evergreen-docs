---
title: state element
TOCTitle: state element
ms:assetid: 6d396c50-6ae4-4bc2-bdd4-7a162255a15b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454802(v=office.15)
ms:contentKeyID: 57093884
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies an enhanced presence phone state category instance value.

``` xml
<st:state xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" 
          xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:type="phoneState"
       manual="xs:boolean" 
       startTime="xs:dateTime" 
       majorVersion="xs:unsignedInt" 
       minorVersion="xs:unsignedInt"
       [anyAttri]="anyAttribute"
       uri="anyURI">
   <st:availability>xs:unsignedInt</st:availability>
   <st:activity>st:activityType</st:activity>
   <st:endpointLocation>st:endpointLocationEnumEx</st:endpointLocation>
   <st:extension>st:extensionType</st:extension>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <st:[any]>any element in the state namespace</st:[any]>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >
      <[any] xmlns="any.namespace">...</[any>
   </ct:extension>
</st:state>
```

phoneState : stateType

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
<td><p>Required attribute with the fixed value of phoneState. This attribute is not explicitly defined, but permitted as one of any custom attributes (@[anyAttr]) described below.</p></td>
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
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent major version information. The default value is unspecified.</p></td>
</tr>
<tr class="odd">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent minor version information. The default value is unspecified.</p></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace.</p></td>
</tr>
<tr class="odd">
<td><p>uri</p></td>
<td><p>Optional attribute to specify the TEL URI of the phone.</p></td>
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
<td><p>This is a top-level element as a phone state category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

stateType is the base type of the phoneState. Use stateType as the serialization type to serialize or de-serialize a phoneState category instance.

Microsoft Lync 2013 publishes a phone state when an audio or video call is established.

## Example

The following XML snippet shows a phone state category instance value describing a conference call is under way.

    <state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           manual="false" 
           xsi:type="phoneState">
        <availability>7000</availability>
        <activity token="in-a-conference" minAvailability="7000" maxAvailability="8999" />
    </state>

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

