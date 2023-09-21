---
title: QualityEndPointType complexType (Lync SDN API Schema A)
TOCTitle: QualityEndPointType complexType
ms:assetid: 1e3d62a9-13cc-657b-3b11-f94e97b1809f
ms:mtpsurl: https://msdn.microsoft.com/library/Dn775149(v=office.15)
ms:contentKeyID: 62626123
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# QualityEndPointType complexType 

(Lync SDN API Schema A)


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

```xml
<xs:complexType name="QualityEndPointType">
    <xs:sequence>
        <xs:element name="URI" type="xs:anyURI"></xs:element>
        <xs:element name="Relay" minOccurs="0"></xs:element>
        <xs:element name="IP" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="Contact" type="xs:anyURI" minOccurs="0"></xs:element>
        <xs:element name="EPId" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="BSSID" minOccurs="0"></xs:element>
        <xs:element name="VPN" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="Inside" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="Id" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="EPType" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="RelayPort" minOccurs="0"></xs:element>
        <xs:element name="Port" type="xs:unsignedInt" minOccurs="0"></xs:element>
        <xs:element name="Connection" type="xs:string" minOccurs="0"></xs:element>
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
<td><p><a href="bssid-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">BSSID</a></p></td>
<td><p>Not defined</p></td>
<td><p>Id of an access point for a WiFi/wireless connection.</p></td>
</tr>
<tr class="even">
<td><p><a href="connection-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">Connection</a></p></td>
<td><p>xs:string</p></td>
<td><p>Connection type such as &quot;wired&quot; or &quot;wireless&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contact-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">Contact</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user as extracted from the Contact header of the underlying SIP message. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
<tr class="even">
<td><p><a href="epid-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">EPId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Endpoint Id of the endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><a href="eptype-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">EPType</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates that this endpoint is of the Lync Room System type or not, when the sendmeetingroominfo option is set to True in the LDL configeration.</p></td>
</tr>
<tr class="even">
<td><p><a href="id-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">Id</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier of the endpoint.</p></td>
</tr>
<tr class="odd">
<td><p><a href="inside-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">Inside</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates if the source is registered within the enterprise (True) or not (False).</p></td>
</tr>
<tr class="even">
<td><p><a href="ip-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">IP</a></p></td>
<td><p>xs:string</p></td>
<td><p>IP address of the the media stream source or destination.</p></td>
</tr>
<tr class="odd">
<td><p><a href="port-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">Port</a></p></td>
<td><p>xs:unsignedInt</p></td>
<td><p>Port number of the destination or source of the media stream used by this endpoint.</p></td>
</tr>
<tr class="even">
<td><p><a href="relay-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">Relay</a></p></td>
<td><p>Not defined</p></td>
<td><p>IP Address of the first relay used in the media traffic.</p></td>
</tr>
<tr class="odd">
<td><p><a href="relayport-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">RelayPort</a></p></td>
<td><p>Not defined</p></td>
<td><p>Port number of the relay.</p></td>
</tr>
<tr class="even">
<td><p><a href="uri-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">URI</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user signed in via the endpoint as extracted from the SIP header.. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
<tr class="odd">
<td><p><a href="vpn-element-qualityendpointtype-complextype-lync-sdn-api-schema-a.md">VPN</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates if the user is on VPN (True) or not (False).</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

