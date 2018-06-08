---
title: URI element (EndPointType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: URI element (EndPointType complexType)
ms:assetid: 4c8a826e-d4ba-aa13-3da4-f03d43d096df
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912828(v=office.15)
ms:contentKeyID: 64126996
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# URI element (EndPointType complexType) 

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
<td><p><a href="callee-element-invitetype-complextype-lync-sdn-interface-2-1-1.md">Callee</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Properties of the callee.</p></td>
</tr>
<tr class="even">
<td><p><a href="caller-element-invitetype-complextype-lync-sdn-interface-2-1-1.md">Caller</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Properties of the caller.</p></td>
</tr>
<tr class="odd">
<td><p><a href="endpoint-element-errortype-complextype-lync-sdn-interface-2-1-1.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="even">
<td><p><a href="endpoint-element-endedtype-complextype-lync-sdn-interface-2-1-1.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="endpoint-element-byetype-complextype-lync-sdn-interface-2-1-1.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="even">
<td><p><a href="from-element-startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">From</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Source of the media stream.</p></td>
</tr>
<tr class="odd">
<td><p><a href="from-element-endedtype-complextype-lync-sdn-interface-2-1-1.md">From</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="even">
<td><p><a href="from-element-errortype-complextype-lync-sdn-interface-2-1-1.md">From</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="to-element-startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">To</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-errortype-complextype-lync-sdn-interface-2-1-1.md">To</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="to-element-endedtype-complextype-lync-sdn-interface-2-1-1.md">To</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

