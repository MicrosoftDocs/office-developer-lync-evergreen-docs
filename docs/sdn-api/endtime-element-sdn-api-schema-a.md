---
title: EndTime element  (Lync SDN API Schema A)
TOCTitle: EndTime element
ms:assetid: f59c6b9c-9b2f-de3e-87d1-bc13c0b742b9
ms:mtpsurl: https://msdn.microsoft.com/library/Dn455038(v=office.15)
ms:contentKeyID: 57260915
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
description: Learn about the EndTime element in Lync 2013's SDN API Schema A. Understand its role in QualityUpdate events and connection-related properties.
---

# EndTime element 

(ConnectionInfo element) (LyncDiagnostics element) (Lync SDN API Schema A)

Denotes then time when the conversation ended. It's provided only in QualityUpdate events.


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
<td><p>xs:dateTime</p></td>
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
<xs:element name="EndTime" type="xs:dateTime" minOccurs="0"></xs:element>
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

