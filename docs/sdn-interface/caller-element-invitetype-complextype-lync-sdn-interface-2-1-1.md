﻿---
title: Caller element (InviteType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Caller element
ms:assetid: 2e4e2c9f-f1bd-ece9-0288-835d0ad85863
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912685(v=office.15)
ms:contentKeyID: 64126855
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Caller element 

(InviteType complexType) (Lync SDN Interface 2.1.1)

Properties of the caller.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
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

    <xs:element name="Caller"  type="EndPointType">
    
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
<td><p><a href="invite-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Invite</a></p></td>
<td><p><a href="invitetype-complextype-lync-sdn-interface-2-1-1.md">InviteType</a></p></td>
<td><p>Event that an endpoint attempts to establish a call. LDL will include this element in its output if the sendcallinvites entry is set to True (activated) in the LDL configuration file. In addition, LDL will also notifies any SIP Invite messages (re-invites), not just the first one. Following this message Earlymedia may be flowing but this element is not intended to report on early media streams.</p></td>
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
<td><p><a href="contact-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">Contact</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user as extracted from the Contact header of the underlying SIP message. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
<tr class="even">
<td><p><a href="epid-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">EPId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Endpoint Id of the endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><a href="eptype-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">EPType</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates that this endpoint is of the Lync Room System type or not.</p></td>
</tr>
<tr class="even">
<td><p><a href="id-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">Id</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier of the endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><a href="incallenabled-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">IncallEnabled</a></p></td>
<td><p>xs:boolean</p></td>
<td><p>Whether the endpoint (Lync client) is capable to send incall quality update messages. This flag does not indicate whether the client is configured to send incall QoE reports.</p></td>
</tr>
<tr class="even">
<td><p><a href="ip-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">IP</a></p></td>
<td><p>xs:string</p></td>
<td><p>IP address of the the media stream source or destination.</p></td>
</tr>
<tr class="odd">
<td><p><a href="port-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">Port</a></p></td>
<td><p>xs:unsignedInt</p></td>
<td><p>Port number of the destination or source of the media stream used by this endpoint.</p></td>
</tr>
<tr class="even">
<td><p><a href="reflexiveip-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">ReflexiveIP</a></p></td>
<td><p>Not defined</p></td>
<td><p>IP used outside of the NAT.</p></td>
</tr>
<tr class="odd">
<td><p><a href="reflexiveport-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">ReflexivePort</a></p></td>
<td><p>Not defined</p></td>
<td><p>Port used on the NAT.</p></td>
</tr>
<tr class="even">
<td><p><a href="relay-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">Relay</a></p></td>
<td><p>Not defined</p></td>
<td><p>IP Address of the first relay used in the media traffic.</p></td>
</tr>
<tr class="odd">
<td><p><a href="relayport-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">RelayPort</a></p></td>
<td><p>Not defined</p></td>
<td><p>Port number of the relay.</p></td>
</tr>
<tr class="even">
<td><p><a href="uri-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">URI</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user signed in via the endpoint as extracted from the SIP header.. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
<tr class="odd">
<td><p><a href="useragent-element-endpointtype-complextype-lync-sdn-interface-2-1-1.md">UserAgent</a></p></td>
<td><p>xs:string</p></td>
<td><p>Lync client name and version.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

