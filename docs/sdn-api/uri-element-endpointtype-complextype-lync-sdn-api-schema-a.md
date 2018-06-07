---
title: URI element (EndPointType complexType) (Lync SDN API Schema A)
TOCTitle: URI element (EndPointType complexType)
ms:assetid: acf5d4dd-9b2f-25b0-ea47-75afd6f21fe7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775141(v=office.15)
ms:contentKeyID: 62626116
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# URI element (EndPointType complexType) (Lync SDN API Schema A)

SIP URI of the user signed in via the endpoint as extracted from the SIP header.. This field is obfuscated unless hidepii is set to false in the LDL configuration file.


**Applies to**: Lync 2013

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
<td><p>xs:anyURI</p></td>
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
<xs:element name="URI" type="xs:anyURI"></xs:element>
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
<td><p><a href="callee-element-invitetype-complextype-lync-sdn-api-schema-a.md">Callee</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Properties of the callee.</p></td>
</tr>
<tr class="even">
<td><p><a href="caller-element-invitetype-complextype-lync-sdn-api-schema-a.md">Caller</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Properties of the caller.</p></td>
</tr>
<tr class="odd">
<td><p><a href="endpoint-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Endpoint while the call is on-hold.</p></td>
</tr>
<tr class="even">
<td><p><a href="endpoint-element-error-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the error event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="endpoint-element-ended-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="even">
<td><p><a href="from-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">From</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Source of the media stream.</p></td>
</tr>
<tr class="odd">
<td><p><a href="to-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">To</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

