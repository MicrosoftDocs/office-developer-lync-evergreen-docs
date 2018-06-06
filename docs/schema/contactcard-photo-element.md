---
title: contactCard/photo element
TOCTitle: contactCard/photo element
ms:assetid: 9b61765d-7e0f-49f1-83ed-e5bfaec1867a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454714(v=office.15)
ms:contentKeyID: 57093401
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/photo element


_**Applies to:** Lync 2013 | Lync Server 2013_

Information about the contact’s phone, including the display name and email address.

``` xml
<photo xmlns="http://schemas.microsoft.com/2006/09/sip/contactCard"
    updated="DateTime" [anyAttr]="String" type="token">
    <uri updated="DateTime" [anyAttr]="String">URI to the photo</uri>
    <hash>hash value</hash>
    <[any] >custom element</[any]>
    <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any] >[any]</[any]>
    </extension>
    <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
       <[any] xmlns="http://schemas.microsoft.com/2006/09/sip/contactCard" />
    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</photo>
```

photoType

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
<td><p>type</p></td>
<td><p>The photo type of a photoTypeEnumEx value. Microsoft Lync 2013 recognizes the following photo type tokens for this attribute:</p>
<dl>
<dt><em>default</em></dt>
<dd><p>Default photo.</p>
</dd>
<dt><em>enterprise</em></dt>
<dd><p>Workplace photo.</p>
</dd>
<dt><em>other</em></dt>
<dd><p>This is some other photo.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Custom attribute of any name in any namespace</p></td>
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
<td><p>uri</p></td>
<td><p>0 or 1</p></td>
<td><p>The URI of the photo</p></td>
</tr>
<tr class="even">
<td><p>hash</p></td>
<td><p>1</p></td>
<td><p>The hash of the photo</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker to start a version-specific schema extension.</p></td>
</tr>
<tr class="even">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The ending marker to end all the schema extensions.</p></td>
</tr>
<tr class="odd">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-specific custom extension to this element.</p></td>
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
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>A contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

There can be at most one sequence of version-dependent schema extensions that are enclosed between one or more delimiter elements and an end element. Each delimiter element can be followed by zero or more of any elements in the same namespace of this element.

## Example

The following XML code snippet shows a contactCard category instance containing a contact’s work phone information, in addition to the company name, professional title and office location.

``` xml
```

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/contactcard</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>contactCard</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>contactCard.xsd, contactCardTypes.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>False</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[contactCard category instance value element](contactcard-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

