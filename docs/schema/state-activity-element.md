---
title: state/activity element
TOCTitle: state/activity element
ms:assetid: 04baa316-bc4a-4405-96ff-b8ed572cf8ff
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454801(v=office.15)
ms:contentKeyID: 57093879
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state/activity element


**Applies to:** Lync 2013 | Lync Server 2013

Describes an activity associated with the accompanying availability mode.

```xml
<st:activity xmlns:st="http://schemas.microsoft.com/2006/09/sip/state" 
       toekn="st:activityTokenEnumEx"
       maxAvailability="st:unsignedInt" 
       minAvailability="st:unsignedInt" 
       [anyAttri]="anyAttribute">
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <[any]>any element</[any]>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...<ct:extension>
</st:state>
```

activityType

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
<td><p>token</p></td>
<td><p>Optional attribute to specify an activity token of the activityTokenEnumEx type as a supplemental description of the given availability mode. Microsoft Lync 2013 recognizes the following tokens:</p>
<dl>
<dt>on-the-phone</dt>
<dd><p>The presentity is on the phone. When no valid custom activity string is supplied, Lync 2013 displays the standard activity string of &quot;On the phone&quot;.</p>
</dd>
<dt>in-a-conference</dt>
<dd><p>The presentity is in a conference. When no valid custom activity string is supplied, Lync 2013 displays the standard activity string of &quot;In a conference&quot;.</p>
</dd>
<dt>in-a-meeting</dt>
<dd><p>The presentity is in a meeting. When no valid custom activity string is supplied, Lync 2013 displays the standard activity string of &quot;In a meeting&quot;.</p>
</dd>
<dt>out-of-office</dt>
<dd><p>The presentity is out of office. When no valid custom activity string is supplied, Lync 2013 displays the standard activity string of &quot;Out of office&quot;.</p>
</dd>
<dt>urgent-interruptions-only</dt>
<dd><p>The presentity wishes not to be disturbed except for urgent interruptions. When no valid custom activity string is supplied, Lync 2013 displays the standard activity string of &quot;Urgent interruptions only.</p>
</dd>
<dt>off-work</dt>
<dd><p>The presentity is off work. Lync 2013 supplies a corresponding custom activity string of &quot;Off work&quot;. Here, being off work is just another form of being away..</p>
</dd>
<dt>in-presentation</dt>
<dd><p>The presentity is in the PRESENT mode of sharing using Microsoft Lync 2013. Lync 2013 supplies a corresponding custom activity string of &quot;Presenting&quot;. A presenting state is another Do Not Disturb state.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>maxAvailability</p></td>
<td><p>Optional attribute to specify the maximal availability mode associated with this activity description. The default value is unbounded.</p></td>
</tr>
<tr class="odd">
<td><p>minAvailability</p></td>
<td><p>Optional attribute to specify the minimal availability mode associated with this activity description. The default value is 0.</p></td>
</tr>
<tr class="even">
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
<td><p>custom</p></td>
<td><p>0 or more</p></td>
<td><p>Specifies application-provided locale-specific activity string. This element is of the LCIDType defined in the same namespace.</p></td>
</tr>
<tr class="even">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker of a schema extension to this element.</p></td>
</tr>
<tr class="odd">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Schema extension</p></td>
</tr>
<tr class="even">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The ending marker of all the schema extensions to this element.</p></td>
</tr>
<tr class="odd">
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
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>A presence state category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

Multiple occurrences of the custom element can be specified to support multiple locale-specific versions of the same custom activity string.

## Example

The following XML example shows a userState category instance value containing an availability number of 15500 to indicate the Out of Office status and a custom activity string of "Away at an off-site".

    <state xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xsi:type="userState" 
           xmlns="http://schemas.microsoft.com/2006/09/sip/state">
       <availability>15500</availability>
       <activity>
          <custom LCID="1033">Away at an off-site</custom>
       </activity>
    </state>

This user state category instance shows that the user’s presence status is available (3500).

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

