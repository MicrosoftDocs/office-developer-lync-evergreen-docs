---
title: Callee element  (Lync SDN API Schema A)
TOCTitle: Callee element
ms:assetid: 4bd40c88-e1c6-f859-8234-6143508d50aa
ms:mtpsurl: https://msdn.microsoft.com/library/Dn775107(v=office.15)
ms:contentKeyID: 62626086
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Callee element 

(InviteType complexType) (Lync SDN API Schema A)

Properties of the callee.

**Applies to**: Lync 2013

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
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

```xml
<xs:element name="Callee" type="EndPointType"></xs:element>
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
<td><p><a href="invite-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Invite</a></p></td>
<td><p><a href="invitetype-complextype-lync-sdn-api-schema-a.md">InviteType</a></p></td>
<td><p>Event that an endpoint attempts to esablish a call. LDL will include this element in its output if the sendcallinvites entry is set to True (activated) in the LDL configuration file. In addition, LDL will also notifies any SIP Invite messages (re-invites), not just the first one. Following this message Earlymedia may be flowing but this element is not intended to report on early media streams.</p></td>
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
<td><p><a href="contact-element-endpointtype-complextype-lync-sdn-api-schema-a.md">Contact</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user as extracted from the Contact header of the underlying SIP message. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
<tr class="even">
<td><p><a href="epid-element-endpointtype-complextype-lync-sdn-api-schema-a.md">EPId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Endpoint Id of the endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><a href="eptype-element-endpointtype-complextype-lync-sdn-api-schema-a.md">EPType</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates that this endpoint is of the Lync Room System type or not, when the sendmeetingroominfo option is set to True in the LDL configeration.</p></td>
</tr>
<tr class="even">
<td><p><a href="id-element-endpointtype-complextype-lync-sdn-api-schema-a.md">Id</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier of the endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><a href="ip-element-endpointtype-complextype-lync-sdn-api-schema-a.md">IP</a></p></td>
<td><p>xs:string</p></td>
<td><p>IP address of the the media stream source or destination.</p></td>
</tr>
<tr class="even">
<td><p><a href="port-element-endpointtype-complextype-lync-sdn-api-schema-a.md">Port</a></p></td>
<td><p>xs:unsignedInt</p></td>
<td><p>Port number of the destination or source of the media stream used by this endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uri-element-endpointtype-complextype-lync-sdn-api-schema-a.md">URI</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user signed in via the endpoint as extracted from the SIP header.. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

