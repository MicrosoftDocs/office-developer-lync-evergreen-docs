---
title: Invite element (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: Invite element
ms:assetid: 6e20c53d-cda5-a8f3-aba3-419ee8110529
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn455060(v=office.15)
ms:contentKeyID: 57260939
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Invite element (LyncDiagnostics element) (Lync SDN API Schema A)

Event that an endpoint attempts to esablish a call. LDL will include this element in its output if the sendcallinvites entry is set to True (activated) in the LDL configuration file. In addition, LDL will also notifies any SIP Invite messages (re-invites), not just the first one. Following this message Earlymedia may be flowing but this element is not intended to report on early media streams.


_**Applies to:** Lync 2013_

**In this article**  
Element information  
Definition  
Elements and attributes  

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="invitetype-complextype-lync-sdn-api-schema-a.md">InviteType</a></p></td>
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

``` xml
<xs:element name="Invite" type="InviteType" minOccurs="0"></xs:element>
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
<td><p><a href="lyncdiagnostics-element-lync-sdn-api-schema-a.md">LyncDiagnostics</a></p></td>
<td><p>Not defined</p></td>
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
<td><p><a href="callee-element-invitetype-complextype-lync-sdn-api-schema-a.md">Callee</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Properties of the callee.</p></td>
</tr>
<tr class="even">
<td><p><a href="caller-element-invitetype-complextype-lync-sdn-api-schema-a.md">Caller</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Properties of the caller.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

