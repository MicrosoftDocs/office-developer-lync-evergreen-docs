---
title: members element
TOCTitle: members element
ms:assetid: f397a110-3a16-4370-bd57-ee9b557e977a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438990(v=office.15)
ms:contentKeyID: 57094034
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# members element


_**Applies to:** Lync 2013 | Lync Server 2013_

Holds a list of membership scopes that can be assigned to the containers used in grammar-based enhanced presence publication.

``` xml
<members>
   <member>...</member>
</members>
```

membersType

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
<td><p><a href="container-element.md">container element</a></p></td>
<td><p>1 or more</p></td>
<td><p>A particular membership scope that can be assigned to the containers used in grammar-based publication.</p></td>
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

