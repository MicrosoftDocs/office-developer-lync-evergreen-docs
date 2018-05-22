---
title: categoryPublicationManifest element
TOCTitle: categoryPublicationManifest element
ms:assetid: c70a8103-64af-4e93-a2bd-f650657646e9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438993(v=office.15)
ms:contentKeyID: 57094045
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# categoryPublicationManifest element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the list of publication of enhanced presence category instances following the publication grammar prescribed by Microsoft Lync Server 2013 and Microsoft Lync 2013.

``` xml
<categoryPublicationManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
     xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
     minSupportedClientVersion="2.0.0.0" 
     xmlns="http://schemas.microsoft.com/2008/09/sip/categoryPublicationManifest">
   <publicationList>...</publicationList>
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...</ct:extension>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
   <[any>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</categoryPublicationManifes>
```

categoryPublicationManifestType

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
<td><p>minSupportedClientVersion</p></td>
<td><p>A token of the xs:token type specifying the earliest version of Lync 2013 that supports this feature.</p></td>
</tr>
<tr class="even">
<td><p>majorVersion</p></td>
<td><p>An unsigned integer of the (xs:unsignedInt) type to specify the major version of the schema defining this element.</p></td>
</tr>
<tr class="odd">
<td><p>minorVersion</p></td>
<td><p>An unsigned integer of the (xs:unsignedInt) type to specify the minor version of the schema defining this element.</p></td>
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
<td><p><a href="publicationlist-element.md">publicationList element</a></p></td>
<td><p>1</p></td>
<td><p>A list of publication rules prescribing how enhanced presence category instances are published.</p></td>
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
<td><p>None</p></td>
<td><p>This is the top-level element of the category instance value containing the publication grammar.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

The publication grammar defines the predefined rules used by Lync 2013 and Lync Server 2013 to publish enhanced presence category data. For more information about publication grammar, see the [Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md) topic.

Understanding of the publication grammar is important to ensure a smooth interoperation of your application with Lync 2013 and Lync Server 2013.

## Example

The following shows an excerpt of the publication grammar that stipulates how [state category instance value elements](state-category-instance-value-elements.md) category instances are published.

``` xml
<categoryPublicationManifest 
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
     xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
     minSupportedClientVersion="2.0.0.0" 
     xmlns="http://schemas.microsoft.com/2008/09/sip/categoryPublicationManifest">
  <publicationList>
    <publicationRule ruleType="transformation" categoryName="state" containerId="2" preferredSelfConsumption="true" /> 
    <publicationRule ruleType="transformation" categoryName="state" containerId="3">
      <categoryData>
        <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" 
             xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
             xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" 
             xmlns:tns="http://schemas.microsoft.com/2006/09/sip/state" 
             exclude-result-prefixes="tns ct"> 
           <xsl:output method="xml" encoding="utf-8" indent="yes"/> 
           <xsl:strip-space elements="*"/> 
           <xsl:template match="node()"> 
             <xsl:apply-templates select="//tns:state"/> 
           </xsl:template> 
           <xsl:template match="tns:state"> 
             <xsl:copy> 
               <xsl:copy-of select="@*" /> 
               <xsl:choose> 
                 <xsl:when test="@xsi:type='userState' and 
                                 tns:availability &ge; 9000 and 
                                 11999 &ge; tns:availability and 
                                 @manual='true'"> 
                   <xsl:element name="availability" xmlns="http://schemas.microsoft.com/2006/09/sip/state">6900</xsl:element> 
                   <xsl:element name="activity" xmlns="http://schemas.microsoft.com/2006/09/sip/state"> 
                     <xsl:attribute name="token">urgent-interruptions-only</xsl:attribute> 
                     <xsl:attribute name="minAvailability">6900</xsl:attribute> 
                     <xsl:attribute name="maxAvailability">8999</xsl:attribute> 
                   </xsl:element> 
               </xsl:when> 
               <xsl:otherwise> 
                 <xsl:copy-of select="tns:availability" /> 
                 <xsl:copy-of select="tns:activity" /> 
               </xsl:otherwise> 
             </xsl:choose> 
             <xsl:copy-of select="tns:endpointLocation" /> 
             <xsl:copy-of select="tns:meetingSubject" /> 
             <xsl:copy-of select="tns:meetingLocation" /> 
             <xsl:choose> 
               <xsl:when test="count(ct:delimiter) &gt; 0"> 
                 <xsl:copy-of select="ct:delimiter[1]" /> 
                 <xsl:copy-of select="tns:timeZoneBias" /> 
                 <xsl:copy-of select="tns:timeZoneName" /> 
                 <xsl:copy-of select="tns:timeZoneAbbreviation" /> 
                 <xsl:copy-of select="tns:device" /> 
               </xsl:when> 
             </xsl:choose> 
             <xsl:choose> 
               <xsl:when test="count(ct:delimiter) &gt; 1"> 
                 <xsl:copy-of select="ct:delimiter[2]" /> 
                 <xsl:copy-of select="ct:delimiter[2]/following-sibling::*" /> 
               </xsl:when> 
               <xsl:otherwise> 
                 <xsl:copy-of select="ct:end" />
                 <xsl:copy-of select="ct:extension" /> 
               </xsl:otherwise> 
             </xsl:choose> 
           </xsl:copy> 
         </xsl:template> 
       </xsl:stylesheet>
      </categoryData> 
    </publicationRule>
    ......
  </publicationList>
</categoryPublicationManifest>
```

The example above stipulates that all the [state category instance value elements](state-category-instance-value-elements.md) category instances are to be published to the two aggregation container, namely, Container 2 and 3. The state category instances are published without modification to Container 2 that is also designated as the preferred container for self-consumption. For the state category instances placed in Container 3, if a manually-set [state\[@type='userState'\] element](state-element.md) availability number falls between 9000 and 11999 (i.e., the do-not-disturb mode), availability number of this [state\[@type='userState'\] element](state-element.md) is converted to 6900 and the corresponding activity token is reset to "urgent-interruptions-only". The transformation is specified in an XSLT routine.

The following shows an excerpt of the publication grammar that stipulates a [state\[@type='aggregateState'\] element](state-element_4.md) category instance with the Offline availability mode (18500) be published to the Block container when a client launches the first time.

``` xml
<categoryPublicationManifest 
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
     xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
     minSupportedClientVersion="2.0.0.0" 
     xmlns="http://schemas.microsoft.com/2008/09/sip/categoryPublicationManifest">
  <publicationList>
    <!-- rules for the first-time publication -->
    <publicationRule ruleType="bootstrap" categoryName="state" containerId="32000">
      <instanceId type="constant" value="0" /> 
      <expireType type="static" /> 
      <categoryData>
        <state xmlns="http://schemas.microsoft.com/2006/09/sip/state" 
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
               manual="false" 
               xsi:type="aggregateState"> 
          <availability>18500</availability>
        </state>
      </categoryData> 
    </publicationRule>
   ......
  </publicationList>
</categoryPublicationManifest>
```

In this initial publication an [state\[@type='aggregateState'\] element](state-element_4.md) category instance with an availability number of 18500 (Offline) is published persistently (expireType="static") to the Block container (32000). This type of publications is of the "bootstrap" type (type="bootstrap") and it does not use any XLST transformation.

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
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for publication grammar](category-instance-elements-for-publication-grammar.md)

#### Concepts

[Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)

