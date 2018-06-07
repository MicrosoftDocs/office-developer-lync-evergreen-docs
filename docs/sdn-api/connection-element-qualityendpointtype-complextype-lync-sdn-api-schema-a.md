---
title: Connection element (QualityEndPointType complexType) (Lync SDN API Schema A)
TOCTitle: Connection element
ms:assetid: e6b8e6a2-4346-48d4-c9c8-ffb11425de69
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775112(v=office.15)
ms:contentKeyID: 62626083
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Connection element (QualityEndPointType complexType) (Lync SDN API Schema A)

Connection type such as "wired" or "wireless".


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
<xs:element name="Connection" type="xs:string" minOccurs="0"></xs:element>
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
<td><p><a href="from-element-qualityupdate-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">From</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>The source of the reported media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-qualityupdate-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">To</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

