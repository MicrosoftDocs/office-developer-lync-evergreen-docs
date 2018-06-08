---
title: rccOptions category instance value element
TOCTitle: rccOptions category instance value element
ms:assetid: d76e8ffc-4829-4d79-8640-477d3febb6a5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454783(v=office.15)
ms:contentKeyID: 57093668
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# rccOptions category instance value element


**Applies to:** Lync 2013 | Lync Server 2013

Holds the roaming options for remote call control (of PBX phones).

```xml
<rccOptions xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns="http://schemas.microsoft.com/2006/09/sip/options/rccOptions"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt"
    [anyAttr]="any_attribute" >
    <forwarding>
       <mode>...</mode>
       <toPhoneType>...</toPhoneType>
    </forwarding>
    <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any]>Custom extension of any name in any namespace</any>
    </extension>
    <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any] xmlns="http://schemas.microsoft.com/2006/09/sip/options/rccOptions">A schema extension to the parent element</any>
    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</rccOptions>
```

rccOptionsType

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
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify the major version information of this element.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify the minor version information of this element.</p></td>
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
<td><p>forwarding</p></td>
<td><p>1</p></td>
<td><p>Contains a specification on where and how to forward a call from a PBX phone.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-dependent custom extension to this element.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A marker to begin a version-dependent schema extension.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Custom element of any name in the same namespace describing a schema extension to this element. This element must be enclosed between a delimiter element and an end element or between a two delimiter elements.</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The marker to end all the schema extensions.</p></td>
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
<td><p>This is a top-level element as an enhanced presence category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Example

The following XML code snippet specifies that a call from a PBX phone is always forwarded to the user’s mobile phone.

    <ro:rccOptions xmlns="http://schemas.microsoft.com/2006/09/sip/options/rccOptions">
      <ro:forwarding>
        <ro:mode>static</ro:mode>
        <ro:toPhoneType>mobile</ro:toPhoneType>
      </ro:forwarding>
      <ct:extension>false</ct:extension>
    </ro:rccOptions>

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/options/rccOptions</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>options-rccOptions</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>options-rccOptions.xsd</p></td>
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

