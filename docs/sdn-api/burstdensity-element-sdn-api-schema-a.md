---
title: BurstDensity element (Lync SDN API Schema A)
TOCTitle: BurstDensity element
ms:assetid: 5c2a0920-27aa-71fc-28cb-7c0cda95a4a8
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454988(v=office.15)
ms:contentKeyID: 57260867
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# BurstDensity element 

(Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Average burst density, as specified in \[RFC3611\] section 4.7.2, is computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available. The fraction of RTP data packets within burst periods since the beginning of reception that were either lost or discarded. This value is expressed as a fixed point number with the binary point at the left edge of the field. It is calculated by dividing the total number of packets lost or discarded (excluding duplicate packet discards) within burst periods by the total number of packets expected within the burst periods, multiplying the result of the division by 256, limiting the maximum value to 255 (to avoid overflow), and taking the integer part. This field MUST be populated and MUST be set to zero if no packets have been received.

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
<xs:element name="BurstDensity"></xs:element>
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

