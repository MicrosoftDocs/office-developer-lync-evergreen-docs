---
title: RecvSignalLevel element (Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: RecvSignalLevel element
ms:assetid: 38b86ea5-c1ae-2557-90e6-ac090d4b6fe8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439255(v=office.15)
ms:contentKeyID: 57260991
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# RecvSignalLevel element (Properties element) (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Received signal level in units of dB. This metric is reported for audio streams when available. Average energy level of received audio is classified as mono speech, or left channel of stereo speech. (dB)


_**Applies to:** Lync 2013_

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

``` xml
<xs:element name="RecvSignalLevel" type="xs:string"></xs:element>
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

None.

### Attributes

None.

