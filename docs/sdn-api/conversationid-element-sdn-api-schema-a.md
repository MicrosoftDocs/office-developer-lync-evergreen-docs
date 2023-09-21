﻿---
title: ConversationId element  (Lync SDN API Schema A)
TOCTitle: ConversationId element
ms:assetid: d6affa3d-1983-880a-8fdf-f310b7026d3f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn455007(v=office.15)
ms:contentKeyID: 57260883
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# ConversationId element 

(ConnectionInfo element) (LyncDiagnostics element) (Lync SDN API Schema A)

Identifier to correlate different SIP calls involved in the same conversation. In some cases Lync uses different SIP calls for different modalities. This identifier permits correlating these SIP calls in the same conversation.


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
<xs:element name="ConversationId" type="xs:string" minOccurs="0"></xs:element>
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

