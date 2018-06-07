---
title: publicationRule element
TOCTitle: publicationRule element
ms:assetid: 72ef64da-cd23-4170-8e38-5649c37ebf76
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438994(v=office.15)
ms:contentKeyID: 57094041
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# publicationRule element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a list of publication rules comprising a publication grammar for enhanced presence category instances.

``` xml
     <publicationRule 
          rulType="ruleTypeEnumEx" 
          categoryName="xs:string"
          containerId="xs:integer"
          preferredSelfConsumption="xs:boolean"
          [anyAttribute]="anyType">[0..*]
        <instanceId 
             type="instanceIdValuesEnumEx" 
             value="xs:integer" 
             [anyAttribute]="anyType">[0..1]
        </instanceId>
        <expireType 
             type="expireTypeValuesEnumEx"  
             expireTime="xs:integer"  --> required only @type="time"
             [anyAttribute]="anyType">[0..1]
        </expireType>
        <categoryData>xs:string</categoryData>[0..1]
        <ct:delimiter/>[0..*]
        <[any]>anyType</[any]>[0..*]
        <ct:end/>[0..1]
        <ct:extension>[any]</ct:extension>[0..1]
     </publicationRule>
```

publicationRuleType

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
<td><p>ruleType</p></td>
<td><p>A required string value to specify type of this publication rule. Microsoft Lync Server 2013 supports the following predefined values:</p>
<dl>
<dt>transformation</dt>
<dd><p>The rule is for normal publication in which XLST transformation can be used to determine the final published data</p>
</dd>
<dt>bootstrap</dt>
<dd><p>The rule is for the initial publication performed by Microsoft Lync 2013 or another client when it starts the first time.</p>
</dd>
<dt>cleanup</dt>
<dd><p>The publication rule is used to clean up a publication.</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p>categoryName</p></td>
<td><p>A required string value specifying the name of a category whose instances are published according to this publication rule.</p></td>
</tr>
<tr class="even">
<td><p>containerId</p></td>
<td><p>A required integer value specifying the Id of a container where the specified category data is published.</p></td>
</tr>
<tr class="odd">
<td><p>preferredSelfConsumption</p></td>
<td><p>An optional Boolean value to indicate if the specified publication is preferred for self-consumption. The default value is false.</p></td>
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
<td><p><a href="instanceid-element.md">instanceId element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the Id of the category instance published according to this publication rule.</p></td>
</tr>
<tr class="even">
<td><p><a href="expiretype-element.md">expireType element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the expiry policy of this publication.</p></td>
</tr>
<tr class="odd">
<td><p><a href="categorydata-element.md">categoryData element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies an XSLT transform to compute the category data to be published.</p></td>
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
<td><p><a href="publicationlist-element.md">publicationList element</a></p></td>
<td><p>The list of publication rules that includes this one.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Example

The following example shows the publication rules for publishing note category instances used by Lync 2013.

``` xml
<categoryPublicationManifest 
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
     xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
     minSupportedClientVersion="2.0.0.0" 
     xmlns="http://schemas.microsoft.com/2008/09/sip/categoryPublicationManifest">
  <publicationList>

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
    <publicationRule ruleType="transformation" categoryName="note" containerId="200" /> 
    <publicationRule ruleType="transformation" categoryName="note" containerId="300" /> 
    <publicationRule ruleType="transformation" categoryName="note" containerId="400" preferredSelfConsumption="true" /> 
    <publicationRule ruleType="transformation" categoryName="note" containerId="32000">
      <categoryData>
        <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" 
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
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

  </publicationList>
</categoryPublicationManifest>
```

The publication rule in the above example specifies that the [note category instance value element](note-category-instance-value-element.md) category instances are published as follows when a publication request is made.

  - Publish [note category instance value element](note-category-instance-value-element.md) category instances, without modification, to Containers 200, 300, and 400.

  - Remove the data value of the [note category instance value element](note-category-instance-value-element.md) category instance using the supplied XSLT transform and publishes the empty note category instance to Containers 100 and 32000.

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

