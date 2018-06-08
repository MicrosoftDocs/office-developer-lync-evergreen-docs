---
title: QualityEndPointType complexType (Lync SDN Interface 2.1.1)
TOCTitle: QualityEndPointType complexType
ms:assetid: 4f8917cd-a2d4-ccf6-ea0e-1806a21f20b2
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912857(v=office.15)
ms:contentKeyID: 64127026
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# QualityEndPointType complexType (Lync SDN Interface 2.1.1)

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
<td><p>LyncSDNInterface.Schema.C.xsd</p></td>
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
<td><p><a href="bssid-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">BSSID</a></p></td>
<td><p>Not defined</p></td>
<td><p>Id of an access point for a WiFi/wireless connection.</p></td>
</tr>
<tr class="even">
<td><p><a href="connection-element-sdn-interface-2-1-1.md">Connection</a></p></td>
<td><p>xs:string</p></td>
<td><p>Connection type such as &quot;wired&quot; or &quot;wireless&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contact-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">Contact</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user as extracted from the Contact header of the underlying SIP message. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
<tr class="even">
<td><p><a href="cpuname-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">CPUName</a></p></td>
<td><p>Not defined</p></td>
<td><p>Name of the CPU.</p></td>
</tr>
<tr class="odd">
<td><p><a href="cpunumberofcores-element-sdn-interface-2-1-1.md">CPUNumberOfCores</a></p></td>
<td><p>Not defined</p></td>
<td><p>Number of CPU cores in the endpoint device.</p></td>
</tr>
<tr class="even">
<td><p><a href="cpuprocessorspeed-element-sdn-interface-2-1-1.md">CPUProcessorSpeed</a></p></td>
<td><p>Not defined</p></td>
<td><p>Processor speed rating.</p></td>
</tr>
<tr class="odd">
<td><p><a href="dscpinbound-element-sdn-interface-2-1-1.md">DSCPInbound</a></p></td>
<td><p>Not defined</p></td>
<td><p>QoS category marking when the stream is received on this endpoint. This field is populated only from Lync clients newer than Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="dscpoutbound-element-sdn-interface-2-1-1.md">DSCPOutbound</a></p></td>
<td><p>Not defined</p></td>
<td><p>QoS category marking used on send the stream from this endpoint. This field is populated only from Lync clients newer than Lync 2013.</p></td>
</tr>
<tr class="odd">
<td><p><a href="epid-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">EPId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Endpoint Id of the endpoint.</p></td>
</tr>
<tr class="even">
<td><p><a href="eptype-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">EPType</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates that this endpoint is of the Lync Room System type or not.</p></td>
</tr>
<tr class="odd">
<td><p><a href="id-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">Id</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier of the endpoint.</p></td>
</tr>
<tr class="even">
<td><p><a href="inside-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">Inside</a></p></td>
<td><p>xs:boolean</p></td>
<td><p>(Deprecated - since Lync 2013, this field is not reliable anymore.) Indicates if the source is registered within the enterprise (True) or not (False).</p></td>
</tr>
<tr class="odd">
<td><p><a href="ip-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">IP</a></p></td>
<td><p>xs:string</p></td>
<td><p>IP address of the the media stream source or destination.</p></td>
</tr>
<tr class="even">
<td><p><a href="linkspeed-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">LinkSpeed</a></p></td>
<td><p>Not defined</p></td>
<td><p>Basic bandwidth of the connection.</p></td>
</tr>
<tr class="odd">
<td><p><a href="macaddr-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">MACAddr</a></p></td>
<td><p>Not defined</p></td>
<td><p>MAC address of the endpoint.</p></td>
</tr>
<tr class="even">
<td><p><a href="os-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">OS</a></p></td>
<td><p>Not defined</p></td>
<td><p>Operating System used on the endpoint device.</p></td>
</tr>
<tr class="odd">
<td><p><a href="port-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">Port</a></p></td>
<td><p>xs:unsignedInt</p></td>
<td><p>Port number of the destination or source of the media stream used by this endpoint.</p></td>
</tr>
<tr class="even">
<td><p><a href="reflexiveip-element-qualityendpointtype-sdn-interface-2-1-1.md">ReflexiveIP</a></p></td>
<td><p>Not defined</p></td>
<td><p>IP used outside of the NAT.</p></td>
</tr>
<tr class="odd">
<td><p><a href="reflexiveport-element-qualityendpointtype-sdn-interface-2-1-1.md">ReflexivePort</a></p></td>
<td><p>Not defined</p></td>
<td><p>Port used on the NAT.</p></td>
</tr>
<tr class="even">
<td><p><a href="relay-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">Relay</a></p></td>
<td><p>Not defined</p></td>
<td><p>IP Address of the first relay used in the media traffic.</p></td>
</tr>
<tr class="odd">
<td><p><a href="relayport-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">RelayPort</a></p></td>
<td><p>Not defined</p></td>
<td><p>Port number of the relay.</p></td>
</tr>
<tr class="even">
<td><p><a href="uri-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">URI</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>SIP URI of the user signed in via the endpoint as extracted from the SIP header.. This field is obfuscated unless hidepii is set to false in the LDL configuration file.</p></td>
</tr>
<tr class="odd">
<td><p><a href="useragent-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">UserAgent</a></p></td>
<td><p>Not defined</p></td>
<td><p>Lync client and version.</p></td>
</tr>
<tr class="even">
<td><p><a href="virtualization-element-sdn-interface-2-1-1.md">Virtualization</a></p></td>
<td><p>Not defined</p></td>
<td><p>Type of virtualization used.</p></td>
</tr>
<tr class="odd">
<td><p><a href="vpn-element-qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">VPN</a></p></td>
<td><p>xs:boolean</p></td>
<td><p>Indicates if the user is on VPN (True) or not (False).</p></td>
</tr>
<tr class="even">
<td><p><a href="wifidriverdevicedesc-element-sdn-interface-2-1-1.md">WifiDriverDeviceDesc</a></p></td>
<td><p>Not defined</p></td>
<td><p>Wifi Driver Device description.</p></td>
</tr>
<tr class="odd">
<td><p><a href="wifidriverversion-element-sdn-interface-2-1-1.md">WifiDriverVersion</a></p></td>
<td><p>Not defined</p></td>
<td><p>Wifi Driver Version.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

