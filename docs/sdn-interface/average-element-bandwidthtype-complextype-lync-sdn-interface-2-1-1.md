---
title: Average element (Lync SDN Interface 2.1.1)
TOCTitle: Average element
ms:assetid: 6a5fe4d2-427d-376b-a899-189ed844e6f1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912677(v=office.15)
ms:contentKeyID: 64126846
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Average element 

(BandwidthType complexType) (Lync SDN Interface 2.1.1)

Estimated average amount of the bandwidth.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p>xs:long</p></td>
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

    <xs:element name="Average"  type="xs:long" minOccurs="0">
    
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
<td><p><a href="bandwidth-element-startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">Bandwidth</a></p></td>
<td><p><a href="bandwidthtype-complextype-lync-sdn-interface-2-1-1.md">BandwidthType</a></p></td>
<td><p>Describes the maximum and average amount of bandwidth needed by this stream. It takes the possible codecs and stream multiplexing into account.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

