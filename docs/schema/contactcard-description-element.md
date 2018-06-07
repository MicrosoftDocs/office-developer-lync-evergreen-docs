---
title: contactCard/description element
TOCTitle: contactCard/description element
ms:assetid: b7171a08-0c72-4899-b8ed-523340640614
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454713(v=office.15)
ms:contentKeyID: 57093400
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/description element


**Applies to:** Lync 2013 | Lync Server 2013

The description about the contact.

``` xml
<description>a string less than 1024 characters long</description>
```

presentityDescriptionType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

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
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>A contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

A string less than 1024 characters long.

## Remarks

This element is introduced in the Office Communications Server 2007 release.

## Example

The following XML code snippet shows a contactCard category instance for a person entity.

    <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" isUCEnabled="true">
       <description>some description about the contact</description>
    </contactCard>

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
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[contactCard category instance value element](contactcard-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

