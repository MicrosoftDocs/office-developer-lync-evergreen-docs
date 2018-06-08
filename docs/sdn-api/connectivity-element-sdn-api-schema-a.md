---
title: Connectivity element  (Lync SDN API Schema A)
TOCTitle: Connectivity element
ms:assetid: cebebb42-22b2-4fa6-7807-75097dfaae9c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454995(v=office.15)
ms:contentKeyID: 57260875
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Connectivity element 

(ConnectionInfo element) (LyncDiagnostics element) (Lync SDN API Schema A)

Denotes whether the call is internal or external through the edge server. It is provided only in QualityUpdate events.


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
<xs:element name="Connectivity" type="xs:string" minOccurs="0"></xs:element>
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
<td><p><a href="connectioninfo-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">ConnectionInfo</a></p></td>
<td><p>Not defined</p></td>
<td><p>Connection-related properties regardless of the media stream and end points.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

