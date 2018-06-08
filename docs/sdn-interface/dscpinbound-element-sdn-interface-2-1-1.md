---
title: DSCPInbound element (QualityEndPointType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: DSCPInbound element
ms:assetid: 517a39d8-3a76-25d7-09f6-dd7108770148
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912717(v=office.15)
ms:contentKeyID: 64126887
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# DSCPInbound element 

(QualityEndPointType complexType) (Lync SDN Interface 2.1.1)

QoS category marking when the stream is received on this endpoint. This field is populated only from Lync clients newer than Lync 2013.

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
<td><p>LyncSDNInterface.Schema.C.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

```xml

    <xs:element name="DSCPInbound"  minOccurs="0">
    
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
<td><p><a href="from-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">From</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">QualityEndPointType</a></p></td>
<td><p>The source of the reported media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">To</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">QualityEndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

