﻿---
title: containerManifest element
TOCTitle: containerManifest element
ms:assetid: 33d72ea1-647e-4977-b762-48faa51fe784
ms:mtpsurl: https://msdn.microsoft.com/library/Dn438979(v=office.15)
ms:contentKeyID: 57094023
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# containerManifest element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a container manifest specifying prescribed container semantics for enhanced presence category publications

```xml
<containerManifest [anyAttribute]="anyValue">
   <containers>...</containers>
   <members>...</members>
   <blockRules>...</blockRules>
   <rolePrecedence>...</rolePrecedence>
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...</ct:extension>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
   <[any>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</containerManifest>
```

containerManifestType

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
<td><p>[anyAttribute]</p></td>
<td><p>Any attribute</p></td>
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
<td><p><a href="containers-element.md">containers element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Containers used in grammar-based publication.</p></td>
</tr>
<tr class="even">
<td><p><a href="members-element.md">members element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Membership scopes that can be assigned to the containers.</p></td>
</tr>
<tr class="odd">
<td><p><a href="blockrules-element.md">blockRules element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Rules to block specified members from being notified of events of the specified types.</p></td>
</tr>
<tr class="even">
<td><p><a href="roleprecedence-element.md">rolePrecedence element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Role-based precedence to be notified of and receive new or updated publications in multiple containers. role.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A marker to begin a version-dependent schema extension.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Any element in the namespace of the parent element, specifying the extension to the parent element introduced in a particular version of the schema.</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The marker to end all the schema extensions.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-specified extension to the parent element.</p></td>
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
<td><p><a href="containermanifestlist-element.md">containerManifestList element</a></p></td>
<td><p>This is the top-level element holding the container manifest.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

A container manifest is comprised of four parts: containers, members, block rules and role precedence. An example of container manifest is listed in the [containerManifestList element](containermanifestlist-element.md) topic. For more information about publication grammar, see the [Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md) topic.

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

