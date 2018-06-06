---
title: publicationList element
TOCTitle: publicationList element
ms:assetid: 3f3606c6-dd73-4f76-b1fc-1c4bd173046f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438995(v=office.15)
ms:contentKeyID: 57094036
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# publicationList element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies a list of publication rules comprising a publication grammar for enhanced presence category instances.

``` xml
  <publicationList [anyAttribute]="anyType">
     <publicationRule 
          rulType="ruleTypeEnumEx" 
          categoryName="xs:string"
          containerId="xs:integer"
          preferredSelfConsumption="xs:boolean"
          [anyAttribute]="anyType">[0..*]
     ......
     </publicationRule>
     <ct:delimiter/>[0..*]
     <[any]>anyType</[any]>[0..*]
     <ct:end/>[0..1]
     <ct:extension>[any]</ct:extension>[0..1]
  </publicationList>
```

publicationListType

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
<td><p><a href="publicationlist-element.md">publicationList element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A publication rules prescribing how enhanced presence category instances are published.</p></td>
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
<td><p><a href="categorypublicationmanifest-element.md">categoryPublicationManifest element</a></p></td>
<td><p>A category publication manifest specifying a publication grammar.</p></td>
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
<td><p>http://schemas.microsoft.com/2008/09/sip/categoryPublicationManifest</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>categoryPublicationManifest</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>PublicationGrammarSchemaForNewPublicationManifest.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>False</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for publication grammar](category-instance-elements-for-publication-grammar.md)

#### Concepts

[Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)

