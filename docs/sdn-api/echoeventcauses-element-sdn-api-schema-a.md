---
title: EchoEventCauses element (Lync SDN API Schema A)
TOCTitle: EchoEventCauses element
ms:assetid: 64d4599d-e895-c7a3-ca8c-245ca28fff05
ms:mtpsurl: https://msdn.microsoft.com/library/Dn455029(v=office.15)
ms:contentKeyID: 57260904
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# EchoEventCauses element 

(Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Reasons of device echo detection and reported for audio streams when available. The causes are coded by the following bit flags: "0x01" - Sample timestamps from capture or render device were poor quality. "0x04" - High level of echo remained after echo cancellation. "0x10" - Signal from capture device had significant instances of maximum signal level.


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
<xs:element name="EchoEventCauses"></xs:element>
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

