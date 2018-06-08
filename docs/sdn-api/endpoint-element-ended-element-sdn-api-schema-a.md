---
title: EndPoint element (Ended element) (Lync SDN API Schema A)
TOCTitle: EndPoint element (Ended element) (LyncDiagnostics element)
ms:assetid: e63f3c63-61a4-d8e4-173a-8dd5ec28cf59
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn455035(v=office.15)
ms:contentKeyID: 57260912
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# EndPoint element (Ended element) 

(LyncDiagnostics element) (Lync SDN API Schema A)

Endpoint involved in the ended SIP call.


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

``` xml
<xs:element name="EndPoint" type="EndPointType" maxOccurs="unbounded"></xs:element>
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
<td><p><a href="ended-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Ended</a></p></td>
<td><p>Not defined</p></td>
<td><p>Event that a Sip call has ended and all media stream terminated.</p></td>
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

