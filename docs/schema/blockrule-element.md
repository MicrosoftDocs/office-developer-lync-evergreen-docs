---
title: blockRule element
TOCTitle: blockRule element
ms:assetid: 27e8d71b-0aec-4ddb-a810-74b8a5c4a121
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438986(v=office.15)
ms:contentKeyID: 57094030
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# blockRule element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a rule defining the blocking actions that clients are expected to perform.

``` xml
<blockRule type="blockTypeEnumEx" [anyAttribute]="anyValue">
   <containers>...</containers>
   <sourceNetworks>...</sourceNetworks>
   <maxAvailability>...</maxAvailability>
   <minAvailability>...</minAvailability>
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...</ct:extension>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
   <[any>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</blockRule>
```

blockRuleType

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
<td><p>A token specifying a type of this blocking rule. Supported tokens are invites for blocking in-bound calls and subscriberPrompt for disabling subscriber prompts.</p></td>
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
<td><p><a href="blockrule-containers-element.md">blockRule/containers element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Containers to which this blocking rule applies.</p></td>
</tr>
<tr class="even">
<td><p><a href="sourcenetworks-element.md">sourceNetworks element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Networks from which the to-be-blocked events originate.</p></td>
</tr>
<tr class="odd">
<td><p>maxAvailability</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element whose value specifies the upper bound of an availability number range to which this blocking rule applies.</p></td>
</tr>
<tr class="even">
<td><p>minAvailability</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple XML element whose value specifies the lower bound of an availability number range to which this blocking rule applies.</p></td>
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
<td><p><a href="blockrules-element.md">blockRules element</a></p></td>
<td><p>The list of blocking rules of which this blockRule is a member.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

This element is introduced in the Microsoft Lync Server 2010 release.

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

