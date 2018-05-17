---
title: sourceNetworks element
TOCTitle: sourceNetworks element
ms:assetid: 4b677c32-a8e3-4e16-869b-c98851c0b546
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438992(v=office.15)
ms:contentKeyID: 57094043
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# sourceNetworks element


_**Applies to:** Lync Server 2013_

Specifies the networks to which a particular member belongs.

``` xml
<sourceNetworks>
   < sourceNetwork>...</ sourceNetwork>
</ sourceNetworks >
```

sourceNetworksType

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
<td><p><a href="sourcenetwork-element.md">sourceNetwork element</a></p></td>
<td><p>1 or more</p></td>
<td><p>A particular source network.</p></td>
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
<td><p><a href="member-element.md">member element</a></p></td>
<td><p>The member belonging to the specified networks.</p></td>
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

