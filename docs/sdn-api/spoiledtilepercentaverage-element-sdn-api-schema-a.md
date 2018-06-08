---
title: SpoiledTilePercentAverage element  (Lync SDN API Schema A)
TOCTitle: SpoiledTilePercentAverage element
ms:assetid: 58640be4-d970-1ee9-d540-78d28aabff9c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439267(v=office.15)
ms:contentKeyID: 57261003
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# SpoiledTilePercentAverage element 

(Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Average percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content. When available, this metric is only reported for application sharing streams and only for Lync 2013. (percent)


**Applies to**: Lync 2013

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p>xs:decimal</p></td>
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

```xml
<xs:element name="SpoiledTilePercentAverage" type="xs:decimal"></xs:element>
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
<td><p><a href="properties-element-qualityupdate-element-sdn-api-schema-a.md">Properties</a></p></td>
<td><p>Not defined</p></td>
<td><p>Properties of the media stream, including a selected set of quality metrics reported and thresholds that are used to determinine a bad call.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

