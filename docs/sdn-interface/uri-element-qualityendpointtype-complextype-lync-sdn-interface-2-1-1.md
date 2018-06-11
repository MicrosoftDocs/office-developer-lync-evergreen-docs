---
title: URI element (QualityEndPointType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: URI element (QualityEndPointType complexType)
ms:assetid: 8d675777-1770-d8f1-9888-5dad34f91e61
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912830(v=office.15)
ms:contentKeyID: 64126998
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# URI element (QualityEndPointType complexType) 

(Lync SDN Interface 2.1.1)

SIP URI of the user signed in via the endpoint as extracted from the SIP header.. This field is obfuscated unless hidepii is set to false in the LDL configuration file.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p>xs:anyURI</p></td>
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

    <xs:element name="URI"  type="xs:anyURI">
    
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

