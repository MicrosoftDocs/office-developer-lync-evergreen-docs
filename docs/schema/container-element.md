---
title: container element
TOCTitle: container element
ms:assetid: 6b959ee9-8950-4e71-99ad-08ba35fe8ffe
ms:mtpsurl: https://msdn.microsoft.com/library/Dn438988(v=office.15)
ms:contentKeyID: 57094032
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# container element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a container used in grammar-based publication.

```xml
<container id="xs:unsignedInt" [anyAttribute]="anyValue">
   <visible>xs:boolean</visible>
   <avoidRedundantMembers>xs:boolean</avoidRedundantMembers>
   <blocked>xs:boolean</blocked>
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...</ct:extension>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
   <[any>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</ container >
```

containerType

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
<td><p>id</p></td>
<td><p>An integer specifying the Id of a container.</p></td>
</tr>
<tr class="even">
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
<td><p>avoidRedundantMembers</p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag to indicate this container should avoid redundant members (true) or not (false).</p></td>
</tr>
<tr class="even">
<td><p>blocked</p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag to indicate this container is blocked (true) or not (false).</p>
<p>This feature is deprecated in the Microsoft Lync Server 2010 release.</p></td>
</tr>
<tr class="odd">
<td><p>Visible</p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag to indicate this container is visible to remote presentities (true) or not (false).</p></td>
</tr>
<tr class="even">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A marker to begin a version-dependent schema extension.</p></td>
</tr>
<tr class="odd">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Any element in the namespace of the parent element, specifying the extension to the parent element introduced in a particular version of the schema.</p></td>
</tr>
<tr class="even">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The marker to end all the schema extensions.</p></td>
</tr>
<tr class="odd">
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
<td><p><a href="containers-element.md">containers element</a></p></td>
<td><p>Containers holder containing this particular container.</p></td>
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

