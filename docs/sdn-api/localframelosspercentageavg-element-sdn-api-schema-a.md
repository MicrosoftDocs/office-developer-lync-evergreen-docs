﻿---
title: LocalFrameLossPercentageAvg element  (Lync SDN API Schema A)
TOCTitle: LocalFrameLossPercentageAvg element
ms:assetid: 1737ba2c-0766-f080-87ff-66b0eec9f559
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439215(v=office.15)
ms:contentKeyID: 57260952
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# LocalFrameLossPercentageAvg element 

(Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Average percentage of video frames lost as they are displayed to the user, including frames recovered from network losses. This metric is reported for video streams when available. (percent)


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
<td><p>xs:string</p></td>
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
<xs:element name="LocalFrameLossPercentageAvg" type="xs:string"></xs:element>
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

