---
title: categoryData element
TOCTitle: categoryData element
ms:assetid: 2e11a89d-a5ab-4d21-b584-636e214031db
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439010(v=office.15)
ms:contentKeyID: 57094053
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# categoryData element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the category data to be published. This can be a category instance XML string or an XSLT routine that generates a category instance XML string from a given input.

```xml
<categoryData>
</categoryData>
```

xs:string

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
<td><p><a href="publicationrule-element.md">publicationRule element</a></p></td>
<td><p>The publication rule to be applied to the specified category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

The element value can be a category instance XML string or an XSLT that produces a category instance XML string.

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

In this example, the category data is a hard-coded XML string of an [state\[@type='aggregateState'\] element](state-element_4.md) category instance.

The following example shows a publication rule for publishing a [note category instance value element](note-category-instance-value-element.md) category instance to the Public container.

```xml
    <publicationRule ruleType="transformation" categoryName="note" containerId="100">
      <categoryData>
        <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
             version="1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
             xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" 
             xmlns:tns="http://schemas.microsoft.com/2006/09/sip/note" 
             exclude-result-prefixes="tns ct"> 
          <xsl:output method="xml" encoding="utf-8" indent="yes"/> 
          <xsl:strip-space elements="*"/> 
          <xsl:template match="node()"> 
            <xsl:apply-templates select="//tns:note"/> 
          </xsl:template> 
          <xsl:template match="tns:note"> 
            <xsl:copy /> 
          </xsl:template> 
        </xsl:stylesheet>
      </categoryData> 
    </publicationRule>
```

In this example, the category data is an XSLT-generated XML string of the [note category instance value element](note-category-instance-value-element.md) category instance.

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

