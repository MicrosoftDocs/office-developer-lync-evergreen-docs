---
title: ConnectionInfo element (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: ConnectionInfo element
ms:assetid: d60bd27c-678f-e500-7259-fee25b2d3118
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454994(v=office.15)
ms:contentKeyID: 57260872
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# ConnectionInfo element (LyncDiagnostics element) (Lync SDN API Schema A)

Connection-related properties regardless of the media stream and end points.


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
<xs:element name="ConnectionInfo">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="CallId" type="xs:string"></xs:element>
            <xs:element name="StartTime" type="xs:dateTime" minOccurs="0"></xs:element>
            <xs:element name="ConversationId" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="MediationServerLegPosition" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="CSEQ" type="xs:unsignedInt" minOccurs="0"></xs:element>
            <xs:element name="Connectivity" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="MediaBypass" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="TimeStamp" type="xs:dateTime" minOccurs="0"></xs:element>
            <xs:element name="EndTime" type="xs:dateTime" minOccurs="0"></xs:element>
            <xs:element name="CorrelationId" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="ConferenceId" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="ConferenceURI" type="xs:anyURI" minOccurs="0"></xs:element>
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
<td><p><a href="callid-element-sdn-api-schema-a.md">CallId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Unique identifier for the SIP call. This field should be used to correlate messages referring to the same call.</p></td>
</tr>
<tr class="even">
<td><p><a href="conferenceid-element-sdn-api-schema-a.md">ConferenceId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier to correlate call legs that belong to the same conference.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conferenceuri-element-sdn-api-schema-a.md">ConferenceURI</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>Sip URI used for the conference. This field is obfuscated unless hidepii is set to false in configuration.</p></td>
</tr>
<tr class="even">
<td><p><a href="connectivity-element-sdn-api-schema-a.md">Connectivity</a></p></td>
<td><p>xs:string</p></td>
<td><p>Denotes whether the call is internal or external through the edge server. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversationid-element-sdn-api-schema-a.md">ConversationId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier to correlate different SIP calls involved in the same conversation. In some cases Lync uses different SIP calls for different modalities. This identifier permits correlating these SIP calls in the same conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="correlationid-element-sdn-api-schema-a.md">CorrelationId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier to correlate two SIP calls where mediation server is involved. Both SIP calls belong to the same conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="cseq-element-sdn-api-schema-a.md">CSEQ</a></p></td>
<td><p>xs:unsignedInt</p></td>
<td><p>Call sequence number as part of SIP standard that needs to be used to filter for unrelated error messages. This field is not provided for QualityUpdates.</p></td>
</tr>
<tr class="even">
<td><p><a href="endtime-element-sdn-api-schema-a.md">EndTime</a></p></td>
<td><p>xs:dateTime</p></td>
<td><p>Denotes then time when the conversation ended. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="odd">
<td><p><a href="mediabypass-element-sdn-api-schema-a.md">MediaBypass</a></p></td>
<td><p>xs:string</p></td>
<td><p>Denotes media bypass. It is provided only in QualityUpdate message when mediabypass was part of the call.</p></td>
</tr>
<tr class="even">
<td><p><a href="mediationserverlegposition-element-sdn-api-schema-a.md">MediationServerLegPosition</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates whether the call was incoming to a mediation server or outgoing from the medation server. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="odd">
<td><p><a href="starttime-element-sdn-api-schema-a.md">StartTime</a></p></td>
<td><p>xs:dateTime</p></td>
<td><p>Denotes the time when the conversation started. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="even">
<td><p><a href="timestamp-element-sdn-api-schema-a.md">TimeStamp</a></p></td>
<td><p>xs:dateTime</p></td>
<td><p>UTC time when the report is processed.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

