---
title: MediationServerLegPosition element (ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: MediationServerLegPosition element
ms:assetid: 8f2c8877-1931-9c48-56ce-32cb0294f795
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912761(v=office.15)
ms:contentKeyID: 64126931
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# MediationServerLegPosition element 

(ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)

Indicates whether the call was incoming to a mediation server or outgoing from the medation server. It is provided only in QualityUpdate events.

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
<td><p>LyncSDNInterface.Schema.C.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

```xml

    <xs:element name="MediationServerLegPosition"  type="xs:string" minOccurs="0">
    
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
<td><p><a href="connectioninfo-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">ConnectionInfo</a></p></td>
<td><p><a href="connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">ConnectionInfoType</a></p></td>
<td><p>Connection-related properties regardless of the media stream and end points.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

