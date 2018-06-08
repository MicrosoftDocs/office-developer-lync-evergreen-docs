---
title: ConnectionInfo element (MessageType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: ConnectionInfo element
ms:assetid: 9ffce14c-1c15-3b7f-0edb-f8e32c01f058
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912693(v=office.15)
ms:contentKeyID: 64126863
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# ConnectionInfo element (MessageType complexType) (Lync SDN Interface 2.1.1)

Connection-related properties regardless of the media stream and end points.


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
<td><p><a href="connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">ConnectionInfoType</a></p></td>
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

    <xs:element name="ConnectionInfo"  type="ConnectionInfoType">
    
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
<td><p><a href="lyncdiagnostics-element-lync-sdn-interface-2-1-1.md">LyncDiagnostics</a></p></td>
<td><p><a href="messagetype-complextype-lync-sdn-interface-2-1-1.md">MessageType</a></p></td>
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
<td><p><a href="callid-element-connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">CallId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Unique identifier for the SIP call. This field should be used to correlate messages referring to the same call.</p></td>
</tr>
<tr class="even">
<td><p><a href="conferenceid-element-sdn-interface-2-1-1.md">ConferenceId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier to correlate call legs that belong to the same conference.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conferenceuri-element-sdn-interface-2-1-1.md">ConferenceURI</a></p></td>
<td><p>xs:anyURI</p></td>
<td><p>(Deprecated - use ConferenceId instead) Sip URI used for the conference. This field is obfuscated unless hidepii is set to false in configuration.</p></td>
</tr>
<tr class="even">
<td><p><a href="connectivity-element-sdn-interface-2-1-1.md">Connectivity</a></p></td>
<td><p>xs:string</p></td>
<td><p>(Obsolete) The inclusion of Relay Ip/port indicates that a particular endpoint uses a media relay (edge server) and if not access the remote address directly. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversationid-element-sdn-interface-2-1-1.md">ConversationId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier to correlate different SIP calls involved in the same conversation. In some cases Lync uses different SIP calls for different modalities. This identifier permits correlating these SIP calls in the same conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="correlationid-element-sdn-interface-2-1-1.md">CorrelationId</a></p></td>
<td><p>xs:string</p></td>
<td><p>Identifier to correlate two SIP calls where mediation server is involved. Both SIP calls belong to the same conversation.</p></td>
</tr>
<tr class="odd">
<td><p><a href="cseq-element-connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">CSEQ</a></p></td>
<td><p>xs:string</p></td>
<td><p>Call sequence number as part of SIP standard that needs to be used to filter for unrelated error messages. This field is not provided for QualityUpdates.</p></td>
</tr>
<tr class="even">
<td><p><a href="endtime-element-connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">EndTime</a></p></td>
<td><p>xs:dateTime</p></td>
<td><p>Denotes then time when the conversation ended. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="odd">
<td><p><a href="mediabypass-element-sdn-interface-2-1-1.md">MediaBypass</a></p></td>
<td><p>xs:boolean</p></td>
<td><p>Denotes media bypass. It is provided only in QualityUpdate message when mediabypass was part of the call.</p></td>
</tr>
<tr class="even">
<td><p><a href="mediationserverlegposition-element-sdn-interface-2-1-1.md">MediationServerLegPosition</a></p></td>
<td><p>xs:string</p></td>
<td><p>Indicates whether the call was incoming to a mediation server or outgoing from the medation server. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sourcepool-element-connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">SourcePool</a></p></td>
<td><p>xs:string</p></td>
<td><p>Name of the Lync/Skype pool this message originated. If a QualityUpdate message is merged and originated from two pools only one is included here. Currently, the FQDN of one sourcepool is provided, expect a comma delimited list in future releases.</p></td>
</tr>
<tr class="even">
<td><p><a href="starttime-element-connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">StartTime</a></p></td>
<td><p>xs:dateTime</p></td>
<td><p>Denotes the time when the conversation started. It is provided only in QualityUpdate events.</p></td>
</tr>
<tr class="odd">
<td><p><a href="timestamp-element-connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">TimeStamp</a></p></td>
<td><p>xs:dateTime</p></td>
<td><p>UTC time when the report is processed.</p></td>
</tr>
</tbody>
</table>


### Attributes

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Attribute</p></th>
<th><p>Type</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
<th><p>Possible values</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Originator</p></td>
<td><p>xs:string</p></td>
<td><p>optional</p></td>
<td><p>Indicates source endpoint (Endpoint Id) that provided the quality metrics used for this report. It is provided only in QualityUpdate events.</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

