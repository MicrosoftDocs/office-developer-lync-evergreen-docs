---
title: Bye element (MessageType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Bye element
ms:assetid: a29011b3-2b28-e663-5137-13d6307d312f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912683(v=office.15)
ms:contentKeyID: 64126852
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Bye element 

(MessageType complexType) (Lync SDN Interface 2.1.1)

Event that a Sip call has ended and all media stream terminated.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="byetype-complextype-lync-sdn-interface-2-1-1.md">ByeType</a></p></td>
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

    <xs:element name="Bye"  type="ByeType">
    
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
<td><p><a href="endpoint-element-byetype-complextype-lync-sdn-interface-2-1-1.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

