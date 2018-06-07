---
title: Properties element (StartOrUpdateType complexType) (Lync SDN API Schema A)
TOCTitle: Properties element (StartOrUpdateType complexType)
ms:assetid: 3af6ff24-a392-d9f1-fcd1-86923438009e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775134(v=office.15)
ms:contentKeyID: 62626108
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (StartOrUpdateType complexType) (Lync SDN API Schema A)

Properties of the started or updated media stream.


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
<td><p>Not defined</p></td>
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
<xs:element name="Properties" minOccurs="0">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="Protocol" type="xs:string"></xs:element>
            <xs:element name="Codec" type="CodecType" maxOccurs="unbounded"></xs:element>
        </xs:sequence>
    </xs:complexType>
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
<td><p><a href="start-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Start</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-api-schema-a.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream is started. Every Start element contains a report about a particular media stream. This event is raised when the call is established, i.e., when the call is picked up and the SIP INVITE is answered with a 200 OK response. The LyncDiagnostics element will not contain any event elements (e.g., Invite, LRSInvite, Start, Update, etc.), when all media streams are inactive (usually when the call is on-hold).</p></td>
</tr>
<tr class="even">
<td><p><a href="update-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Update</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-api-schema-a.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream is started. Every Start element contains a report about a particular media stream. This event is raised when the call is established, i.e., when the call is picked up and the SIP INVITE is answered with a 200 OK response. The LyncDiagnostics element will not contain any event elements (e.g., Invite, LRSInvite, Start, Update, etc.), when all media streams are inactive (usually when the call is on-hold).</p></td>
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
<td><p><a href="codec-element-properties-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-api-schema-a.md">CodecType</a></p></td>
<td><p>Codec and estimates for the bandwidth that the codecs will use. This list contains all codecs that are agreed upon by the two endpoints. Both end-points may decide to switch amoung these codecs at any time (without additional signalling).</p></td>
</tr>
<tr class="even">
<td><p><a href="protocol-element-properties-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">Protocol</a></p></td>
<td><p>xs:string</p></td>
<td><p>Transmission protocol of the media stream such as TCP or UDP.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

