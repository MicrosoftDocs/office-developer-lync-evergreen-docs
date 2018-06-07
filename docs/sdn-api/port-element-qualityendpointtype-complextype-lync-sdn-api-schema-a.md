---
title: Port element (QualityEndPointType complexType) (Lync SDN API Schema A)
TOCTitle: Port element (QualityEndPointType complexType)
ms:assetid: aa227436-dd26-dfa9-1b2c-7536d19551ba
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775131(v=office.15)
ms:contentKeyID: 62626106
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Port element (QualityEndPointType complexType) (Lync SDN API Schema A)

Port number of the destination or source of the media stream used by this endpoint.


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
<td><p>xs:unsignedInt</p></td>
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
<xs:element name="Port" type="xs:unsignedInt" minOccurs="0"></xs:element>
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
<td><p><a href="from-element-qualityupdate-element-sdn-api-schema-a.md">From</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>The source of the reported media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-qualityupdate-element-sdn-api-schema-a.md">To</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

