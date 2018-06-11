---
title: RawSDP element (MessageType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: RawSDP element
ms:assetid: 336f8dc9-377f-f12d-1084-ce4fa4e7f527
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912789(v=office.15)
ms:contentKeyID: 64126958
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# RawSDP element 

(MessageType complexType) (Lync SDN Interface 2.1.1)

Raw Session Description Protocol (SDP) data that is included as the payload of the underlying SIP messages of the Invite, LRSInvite and StartOrUpdate type, if the sendrawsdp entry is set to True in the LDL configuration file.

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

    <xs:element name="RawSDP"  type="xs:string" minOccurs="0">
    
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
<td><p><a href="lyncdiagnostics-element-lync-sdn-interface-2-1-1.md">LyncDiagnostics</a></p></td>
<td><p><a href="messagetype-complextype-lync-sdn-interface-2-1-1.md">MessageType</a></p></td>
<td><p>The root element for output from the Lync SDN Manager.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

