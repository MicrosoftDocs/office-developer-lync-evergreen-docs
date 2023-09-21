---
title: contactCard/displayADPhoto element
TOCTitle: contactCard/displayADPhoto element
ms:assetid: 518521c2-7cd0-47fa-9a65-24ac7573ae4b
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454730(v=office.15)
ms:contentKeyID: 57093439
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/displayADPhoto element


**Applies to:** Lync 2013 | Lync Server 2013

A Boolean flag to indicate whether to display contact photo stored in Active Directory (True) or from a custom photo store (False).

```xml
<displayADPhoto>Boolean</displayADPhoto>
```

xs:boolean

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

True or False

## Remarks

This element is introduced in the Microsoft Lync Server 2010 release.

## Example

The following XML code snippet shows a contactCard category instance with a display of the photo stored in Active Directory.

    <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" isUCEnabled="true">
       <displayADPhoto>true</displayADPhoto>
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

