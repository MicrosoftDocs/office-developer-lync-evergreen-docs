---
title: EndPointType complexType (Lync SDN API Schema A)
TOCTitle: EndPointType complexType
ms:assetid: 6ad6a1d4-eac3-bb04-d71c-aa2ed76fa3ca
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775147(v=office.15)
ms:contentKeyID: 62626121
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# EndPointType complexType (Lync SDN API Schema A)

**Applies to**: Lync 2013

## Type information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Namespace</strong></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Schema file</strong></p></td>
<td><p>LyncSdnApi.Schema.A.xsd</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension base</strong></p></td>
<td><p>None</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml
<xs:complexType name="EndPointType">
    <xs:sequence>
        <xs:element name="Port" type="xs:unsignedInt" minOccurs="0"></xs:element>
        <xs:element name="Contact" type="xs:anyURI" minOccurs="0"></xs:element>
        <xs:element name="EPId" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="EPType" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="IP" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="URI" type="xs:anyURI"></xs:element>
        <xs:element name="Id" type="xs:string" minOccurs="0"></xs:element>
    </xs:sequence>
</xs:complexType>
```

## Elements and attributes

If the schema defines specific requirements, such as sequence, minOccurs, maxOccurs, and choice, see the definition section.

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

