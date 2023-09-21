---
title: CallId element (ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: CallId element
ms:assetid: 07ab43a7-10f7-a03a-8617-549361e06960
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912686(v=office.15)
ms:contentKeyID: 64126856
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# CallId element 

(ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)

Unique identifier for the SIP call. This field should be used to correlate messages referring to the same call.

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

    <xs:element name="CallId"  type="xs:string">
    
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

