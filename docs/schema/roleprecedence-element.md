﻿---
title: rolePrecedence element
TOCTitle: rolePrecedence element
ms:assetid: 056c6e6c-f626-49c1-b448-c96057b6802a
ms:mtpsurl: https://msdn.microsoft.com/library/Dn438989(v=office.15)
ms:contentKeyID: 57094033
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# rolePrecedence element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the precedence hierarchy of roles when a member is assigned multiple roles.

```xml
<rolePrecedence >
   < rolePrecedenceEntry >...</ rolePrecedenceEntry >
</ rolePrecedence >
```

rolePrecedenceType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

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
<td><p><a href="roleprecedenceentry-element.md">rolePrecedenceEntry element</a></p></td>
<td><p>1 or more</p></td>
<td><p>An entry in an ordered list showing the role-based precedence hierarchy.</p></td>
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
<td><p><a href="containermanifest-element.md">containerManifest element</a></p></td>
<td><p>The container manifest used in grammar-based publication.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

This feature is introduced in the Microsoft Lync Server 2010 release.

An example of container manifest is listed in the [containerManifestList element](containermanifestlist-element.md) topic. For more information about publication grammar, see the [Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md) topic.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2008/09/sip/ContainerManifest</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>ContainerManifest</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>ContainerManifestSchema.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for publication grammar](category-instance-elements-for-publication-grammar.md)

#### Concepts

[Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)

