---
title: instanceId element
TOCTitle: instanceId element
ms:assetid: 11df8750-f3f0-4319-a7d4-c106415197b6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439016(v=office.15)
ms:contentKeyID: 57094059
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# instanceId element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a particular category instance to which the publication rule is applied.

```xml
<instanceId type="instanceIdValuesEnumEx" value="xs:integer" [anyAttribute]="anyType" />
```

instanceIdType

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
<tr class="even">
<td><p>type</p></td>
<td><p>A required string value to specify the type of instance Id. Microsoft Lync Server 2013 supports the following predefined values:</p>
<dl>
<dt>constant</dt>
<dd><p>The instance Id will not change.</p>
</dd>
<dt>custom</dt>
<dd><p>The instanced Id can be custom-defined.</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p>value</p></td>
<td><p>A required integer value specifying the Id of a category instance to be published according to the given publication rule.</p></td>
</tr>
</tbody>
</table>


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
<td><p><a href="publicationrule-element.md">publicationRule element</a></p></td>
<td><p>The publication rule to be applied to the specified category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

This element is optional. If an instance Id is specified, the publication rule applies to the specified instance of a given category. Otherwise, the publication rule applies to all the instances of a given category.

## Example

The following example shows the publication rules for publishing note category instances used by Microsoft Lync 2013.

```xml
<publicationRule ruleType="bootstrap" categoryName="state" containerId="32000"> 
   <instanceId type="constant" value="0" /> 
   <expireType type="static" /> 
   <categoryData> 
     <state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
            manual="false" xsi:type="aggregateState"> 
        <availability>18500</availability> 
     </state> 
   </categoryData> 
</publicationRule> 
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

