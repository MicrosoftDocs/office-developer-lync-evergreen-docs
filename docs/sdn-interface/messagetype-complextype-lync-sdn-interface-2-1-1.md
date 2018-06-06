---
title: MessageType complexType (Lync SDN Interface 2.1.1)
TOCTitle: MessageType complexType
ms:assetid: de3feda7-42bc-8f23-3ade-2aee10d1058a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912855(v=office.15)
ms:contentKeyID: 64127024
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# MessageType complexType (Lync SDN Interface 2.1.1)


**In this article**  
Type information  
Definition  
Elements and attributes  

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

``` xml
      <xs:complexType name="MessageType">
    <xs:attribute name="Version" type="xs:string" use="optional"/>
  
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
<td><p><a href="bye-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Bye</a></p></td>
<td><p><a href="byetype-complextype-lync-sdn-interface-2-1-1.md">ByeType</a></p></td>
<td><p>Event that a Sip call has ended and all media stream terminated.</p></td>
</tr>
<tr class="even">
<td><p><a href="connectioninfo-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">ConnectionInfo</a></p></td>
<td><p><a href="connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">ConnectionInfoType</a></p></td>
<td><p>Connection-related properties regardless of the media stream and end points.</p></td>
</tr>
<tr class="odd">
<td><p><a href="ended-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Ended</a></p></td>
<td><p><a href="endedtype-complextype-lync-sdn-interface-2-1-1.md">EndedType</a></p></td>
<td><p>Event that a Sip call has ended and all media stream terminated.</p></td>
</tr>
<tr class="even">
<td><p><a href="error-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Error</a></p></td>
<td><p><a href="errortype-complextype-lync-sdn-interface-2-1-1.md">ErrorType</a></p></td>
<td><p>This event is optional. Error event that a SIP dialog has failed. Error events are also sent for SIP calls that are terminated even before a media stream is started or for failed to be updated.</p></td>
</tr>
<tr class="odd">
<td><p><a href="incallquality-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">InCallQuality</a></p></td>
<td><p><a href="qualitytype-complextype-lync-sdn-interface-2-1-1.md">QualityType</a></p></td>
<td><p>Indicates that a significant quality related event occured in the client. Either the quality dropped into another level or improved. There are 3 levels: Good, Poor, Bad. The media stack determines the quality level. Furthermore, this event is also sent when a video stream is deescalated. Even in an issue free network at least one IncallQuality message is sent.</p></td>
</tr>
<tr class="even">
<td><p><a href="invite-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Invite</a></p></td>
<td><p><a href="invitetype-complextype-lync-sdn-interface-2-1-1.md">InviteType</a></p></td>
<td><p>Event that an endpoint attempts to establish a call. LDL will include this element in its output if the sendcallinvites entry is set to True (activated) in the LDL configuration file. In addition, LDL will also notifies any SIP Invite messages (re-invites), not just the first one. Following this message Earlymedia may be flowing but this element is not intended to report on early media streams.</p></td>
</tr>
<tr class="odd">
<td><p><a href="properties-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Properties</a></p></td>
<td><p><a href="messageproperties-complextype-lync-sdn-interface-2-1-1.md">MessageProperties</a></p></td>
<td><p>Details of the Error or reason for ending the streams.</p></td>
</tr>
<tr class="even">
<td><p><a href="qualityupdate-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">QualityUpdate</a></p></td>
<td><p><a href="qualitytype-complextype-lync-sdn-interface-2-1-1.md">QualityType</a></p></td>
<td><p>Specifies the event that a call has ended and contains a report of the quality metrics of individual media streams. These quality metrics for a stream may include updates provided by both endpoints which are merged.</p></td>
</tr>
<tr class="odd">
<td><p><a href="rawsdp-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">RawSDP</a></p></td>
<td><p>xs:string</p></td>
<td><p>Raw Session Description Protocol (SDP) data that is included as the payload of the underlying SIP messages of the Invite, LRSInvite and StartOrUpdate type, if the sendrawsdp entry is set to True in the LDL configuration file.</p></td>
</tr>
<tr class="even">
<td><p><a href="route-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Route</a></p></td>
<td><p><a href="routetype-complextype-lync-sdn-interface-2-1-1.md">RouteType</a></p></td>
<td><p>Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.</p></td>
</tr>
<tr class="odd">
<td><p><a href="start-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Start</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream is started. Every Start element contains a report about a particular media stream. This event is raised when the call is established, i.e., when the call is picked up and the SIP INVITE is answered with a 200 OK response.</p></td>
</tr>
<tr class="even">
<td><p><a href="update-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Update</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream previously started has been updated. This event is raised when an update to core parameters of call have changed and the change is established, i.e., when the request is answered with a 200 OK response.</p></td>
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
<td><p>Version</p></td>
<td><p>xs:string</p></td>
<td><p>optional</p></td>
<td><p>Version number of this data structure. It provides a simple distinction between LyncDiagnostics messages formats. LyncDiagnostics message matching to this xsd use Version C.</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

