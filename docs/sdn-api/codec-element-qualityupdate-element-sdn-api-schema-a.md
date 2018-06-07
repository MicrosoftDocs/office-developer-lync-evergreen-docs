---
title: Codec element (Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: Codec element (Properties element) (QualityUpdate element) (LyncDiagnostics element)
ms:assetid: 2eea8bee-366c-cbf6-ae25-da326948002b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775109(v=office.15)
ms:contentKeyID: 62626088
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Codec element (Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Describes the last codec used for the media.


**Applies to**: Lync 2013

**In this article**  
Element information  
Definition  
Elements and attributes  

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="codectype-complextype-lync-sdn-api-schema-a.md">CodecType</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Namespace</strong></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Schema file</strong></p></td>
<td><p>LyncSdnApi.Schema.A.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml
<xs:element name="Codec" type="CodecType"></xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as sequence, minOccurs, maxOccurs, and choice, see the definition section.

### Parent elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="properties-element-qualityupdate-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Properties</a></p></td>
<td><p>Not defined</p></td>
<td><p>Properties of the media stream, including a selected set of quality metrics reported and thresholds that are used to determinine a bad call.</p></td>
</tr>
</tbody>
</table>


### Child elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="bandwidth-element-codectype-complextype-lync-sdn-api-schema-a.md">Bandwidth</a></p></td>
<td><p>xs:string</p></td>
<td><p>Lower limit of the estimated bandwidth.</p></td>
</tr>
<tr class="even">
<td><p><a href="maxbandwidth-element-codectype-complextype-lync-sdn-api-schema-a.md">MaxBandwidth</a></p></td>
<td><p>xs:string</p></td>
<td><p>Upper limit of the estimated bandwidth.</p></td>
</tr>
</tbody>
</table>


### Attributes

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Attribute</p></th>
<th><p>Type</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
<th><p>Possible values</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>xs:string</p></td>
<td><p>required</p></td>
<td><p>Name of the standard SIP codec used for the media stream.</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

