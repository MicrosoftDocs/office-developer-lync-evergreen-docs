---
title: LowResolutionCallPercent element  (Lync SDN API Schema A)
TOCTitle: LowResolutionCallPercent element
ms:assetid: 7539e8be-ea1a-7076-56a1-4972f9f77e08
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439216(v=office.15)
ms:contentKeyID: 57260954
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# LowResolutionCallPercent element 

(Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Percentage of time of the call where resolution is low. Threshold is 120 pixels for smaller dimension. This metric is reported for video streams when available. (percent)


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
<td><p>Not defined</p></td>
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
<xs:element name="LowResolutionCallPercent">
    <xs:attribute name="Limit" type="xs:decimal" use="optional" />
</xs:element>
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
<td><p>Limit</p></td>
<td><p>xs:decimal</p></td>
<td><p>optional</p></td>
<td><p>Limit as defined in the QoE database or in the LDL configuration file.</p></td>
<td><p>Values of the xs:decimal type.</p></td>
</tr>
</tbody>
</table>

