---
title: expireType element
TOCTitle: expireType element
ms:assetid: 18ed48c1-2b77-49cd-a1bc-41fab94e9220
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439007(v=office.15)
ms:contentKeyID: 57094051
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# expireType element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the expiry policy of the category publication.

```xml
<expireType type="expireTypeValuesEnumEx" expireTime="xs:integer"  [anyAttribute]="anyType" />
```

expireTypeType

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
<td><p>A required string value to specify the expiry policy. Microsoft Lync Server 2013 supports the following predefined values:</p>
<dl>
<dt>endpoint</dt>
<dd><p>Expires when the endpoint logs off.</p>
</dd>
<dt>static</dt>
<dd><p>The publication does not expire.</p>
</dd>
<dt>user</dt>
<dd><p>The publication expires when the user signs out of Lync Server 2013.</p>
</dd>
<dt>time</dt>
<dd><p>The publication expires at the end of a time period specified by the expireTime attribute.</p>
</dd>
<dt>custom</dt>
<dd><p>The publication has a custom expiry policy.</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p>expireTime</p></td>
<td><p>An optional integer value specifying the time duration at the end of which the publication expires. This attribute can be specified only when the type attribute has a value of &quot;time&quot;.</p></td>
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

This element is optional. If it's unspecified, the publication is endpoint-bound.

## Example

The following example shows a publication rule for publishing an [state\[@type='aggregateState'\] element](state-element_4.md) category instance to the Block container.

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

