---
title: state/meetingLocation element
TOCTitle: state/meetingLocation element
ms:assetid: 0a8abf70-90e4-46a7-a879-6e606606190e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438968(v=office.15)
ms:contentKeyID: 57094013
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# state/meetingLocation element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the location of a meeting according to a presence state of the user’s calendar.

``` xml
<st:meetingLocation xmlns:st="http://schemas.microsoft.com/2006/09/sip/state"     LCID="xs:unsignedInt"
    updated="xs:dateTime"
    [anyAttribute]="any_attribute">xs:string<st:meetingLocation>
```

st:LCIDType

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
<td><p>LCID</p></td>
<td><p>Locale ID of the meeting location string</p></td>
</tr>
<tr class="even">
<td><p>updated</p></td>
<td><p>The date and time when the publication of this element was last updated.</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttribute</p></td>
<td><p>Any attribute of any namespace.</p></td>
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
<td><p><a href="state-category-instance-value-elements.md">state category instance value elements</a></p></td>
<td><p>An enhanced presence state category instance value with the specification of a meeting location.</p></td>
</tr>
</tbody>
</table>


## Text value

None

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

