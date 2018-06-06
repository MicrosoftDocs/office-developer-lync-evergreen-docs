---
title: LyncDiagnostics element (Lync SDN API Schema A)
TOCTitle: LyncDiagnostics element
ms:assetid: bfcbac5f-7519-21c9-3ec7-20e2bbd34c53
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439218(v=office.15)
ms:contentKeyID: 57260955
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# LyncDiagnostics element (Lync SDN API Schema A)

The root element for output from the Lync SDN Manager.


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
<xs:element name="LyncDiagnostics">
    <xs:complexType>
        <xs:sequence>
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
            <xs:element name="Ended" maxOccurs="unbounded" minOccurs="0">
                <xs:complexType>
                    <xs:sequence>
                        <xs:element name="EndPoint" type="EndPointType" maxOccurs="unbounded"></xs:element>
                    </xs:sequence>
                    <xs:attribute name="Type" type="xs:string" use="required" />
                </xs:complexType>
            </xs:element>
            <xs:element name="RawSDP" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="Update" type="StartOrUpdateType" minOccurs="0" maxOccurs="unbounded"></xs:element>
            <xs:element name="Properties" minOccurs="0">
                <xs:complexType>
                    <xs:sequence>
                        <xs:element name="MSDiagnosticsPublic" minOccurs="0"></xs:element>
                        <xs:element name="MSDiagnosticsClient" minOccurs="0"></xs:element>
                        <xs:element name="MSDiagnostics" type="xs:string" minOccurs="0"></xs:element>
                        <xs:element name="ResponseCode">
                            <xs:attribute name="Code" type="xs:unsignedShort" use="required" />
                        </xs:element>
                    </xs:sequence>
                </xs:complexType>
            </xs:element>
            <xs:element name="Start" type="StartOrUpdateType" maxOccurs="unbounded" minOccurs="0"></xs:element>
            <xs:element name="Invite" type="InviteType" minOccurs="0"></xs:element>
            <xs:element name="QualityUpdate" minOccurs="0" maxOccurs="unbounded">
                <xs:complexType>
                    <xs:sequence>
                        <xs:element name="From" type="QualityEndPointType"></xs:element>
                        <xs:element name="To" type="QualityEndPointType"></xs:element>
                        <xs:element name="Properties">
                            <xs:complexType>
                                <xs:sequence maxOccurs="unbounded">
                                    <xs:element name="RelativeOneWayAverage">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="VideoFrameLossRate"></xs:element>
                                    <xs:element name="VideoPacketLossRate">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="BurstGapDensity"></xs:element>
                                    <xs:element name="SpoiledTilePercentTotal">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="PacketLossRateMax"></xs:element>
                                    <xs:element name="JitterInterArrival">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="Codec" type="CodecType"></xs:element>
                                    <xs:element name="BurstGapDuration" type="xs:string"></xs:element>
                                    <xs:element name="RecvSignalLevel" type="xs:string"></xs:element>
                                    <xs:element name="SendListenMOS"></xs:element>
                                    <xs:element name="RelativeOneWayBurstDensity">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="DegradationAvg">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="VGAQualityRatio"></xs:element>
                                    <xs:element name="HealerPacketDropRatio" type="xs:string"></xs:element>
                                    <xs:element name="EchoPercentSend" type="xs:string"></xs:element>
                                    <xs:element name="SpoiledTilePercentAverage" type="xs:decimal"></xs:element>
                                    <xs:element name="RecvListenMOSMin"></xs:element>
                                    <xs:element name="RoundTrip">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="RecvListenMOS"></xs:element>
                                    <xs:element name="PacketLossRate">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="RDPTileProcessingLatencyAverage">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="ConversationalMOS" type="xs:string"></xs:element>
                                    <xs:element name="SendListenMOSMin"></xs:element>
                                    <xs:element name="EchoReturn"></xs:element>
                                    <xs:element name="LowResolutionCallPercent">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="VideoLocalFrameLossPercentageAvg">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="DegradationPacketLossAvg"></xs:element>
                                    <xs:element name="BurstDuration"></xs:element>
                                    <xs:element name="OverallAvgNetworkMOS" type="xs:string"></xs:element>
                                    <xs:element name="JitterInterArrivalMax" type="xs:string"></xs:element>
                                    <xs:element name="HDQualityRatio"></xs:element>
                                    <xs:element name="LowFrameRateCallPercent">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="Protocol" type="xs:string"></xs:element>
                                    <xs:element name="EchoEventCauses"></xs:element>
                                    <xs:element name="DegradationMax" type="xs:string"></xs:element>
                                    <xs:element name="RecvFrameRateAverage">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="OverallMinNetworkMOS" type="xs:string"></xs:element>
                                    <xs:element name="AppliedBandwidthLimit" type="xs:unsignedInt" minOccurs="0"></xs:element>
                                    <xs:element name="PacketUtilization" type="xs:string"></xs:element>
                                    <xs:element name="BurstDensity"></xs:element>
                                    <xs:element name="RDPTileProcessingLatencyBurstDensity">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="RatioConcealedSamplesAvg">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                    <xs:element name="RecvNoiseLevel" type="xs:string"></xs:element>
                                    <xs:element name="FrameRate" type="xs:decimal"></xs:element>
                                    <xs:element name="BitRateMax" type="xs:string"></xs:element>
                                    <xs:element name="LocalFrameLossPercentageAvg" type="xs:string"></xs:element>
                                    <xs:element name="DegradationJitterAvg" type="xs:string"></xs:element>
                                    <xs:element name="BitRateAvg" type="xs:string"></xs:element>
                                    <xs:element name="EchoPercentMicIn" type="xs:string"></xs:element>
                                    <xs:element name="RoundTripMax" type="xs:string"></xs:element>
                                    <xs:element name="DynamicCapabilityPercent">
                                        <xs:attribute name="Limit" type="xs:decimal" use="optional" />
                                    </xs:element>
                                </xs:sequence>
                            </xs:complexType>
                        </xs:element>
                    </xs:sequence>
                    <xs:attribute name="Type" type="xs:string" use="required" />
                </xs:complexType>
            </xs:element>
            <xs:element name="LRSInvite"></xs:element>
            <xs:element name="Route" minOccurs="0">
                <xs:complexType>
                    <xs:sequence>
                        <xs:element name="Hop" type="xs:string" maxOccurs="unbounded"></xs:element>
                    </xs:sequence>
                </xs:complexType>
            </xs:element>
            <xs:element name="Error" minOccurs="0" maxOccurs="unbounded">
                <xs:complexType>
                    <xs:sequence>
                        <xs:element name="EndPoint" type="EndPointType" maxOccurs="unbounded"></xs:element>
                    </xs:sequence>
                    <xs:attribute name="Type" type="xs:string" use="required" />
                </xs:complexType>
            </xs:element>
        </xs:sequence>
        <xs:attribute name="Version" />
    </xs:complexType>
</xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as sequence, minOccurs, maxOccurs, and choice, see the definition section.

### Parent elements

None.

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
<td><p><a href="connectioninfo-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">ConnectionInfo</a></p></td>
<td><p>Not defined</p></td>
<td><p>Connection-related properties regardless of the media stream and end points.</p></td>
</tr>
<tr class="even">
<td><p><a href="ended-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Ended</a></p></td>
<td><p>Not defined</p></td>
<td><p>Event that a Sip call has ended and all media stream terminated.</p></td>
</tr>
<tr class="odd">
<td><p><a href="error-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Error</a></p></td>
<td><p>Not defined</p></td>
<td><p>Error event that a SIP call has failed and all active media streams for the corresponding CallId (and Cseq) are terminated. Error events are also sent for SIP calls that are terminated even before a media stream is started or for failed to be updated.</p></td>
</tr>
<tr class="even">
<td><p><a href="invite-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Invite</a></p></td>
<td><p><a href="invitetype-complextype-lync-sdn-api-schema-a.md">InviteType</a></p></td>
<td><p>Event that an endpoint attempts to esablish a call. LDL will include this element in its output if the sendcallinvites entry is set to True (activated) in the LDL configuration file. In addition, LDL will also notifies any SIP Invite messages (re-invites), not just the first one. Following this message Earlymedia may be flowing but this element is not intended to report on early media streams.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lrsinvite-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">LRSInvite</a></p></td>
<td><p>Not defined</p></td>
<td><p>Event that a Lync Room System (LRS) endpoint (i.e., a Lync meeting room) attempts to establish a call. LDL sends LRSInvite messages depending on how the LDL configuration is set. If the sendmeetingroominfo entry is set to True (activated) and the sendcallinvites entry is set to false (deactivated), LDL send LRSInvite when the call is made from a Lync meeting room. If the sendcallinvites and sendmeetingroominfo entries are both activated, LDL will not send LRSInvite because the Inivte element will already contain the necessary information about which endpoints are of meeting rooms.</p></td>
</tr>
<tr class="even">
<td><p><a href="properties-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Properties</a></p></td>
<td><p>Not defined</p></td>
<td><p>Details of the Error.</p></td>
</tr>
<tr class="odd">
<td><p><a href="qualityupdate-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">QualityUpdate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Specifies the event that a SIP call has ended and contains an updated report of the quality metrics of individual media streams. These quality metrics for a stream may include updates provided by other endpoints during the call. By default, LDL raises this event (and thus reports the quality updates) only if the call quality is under the quality thresholds defined in the QoE database or in the LDL configuration file. Alterantively, you can configure Lync Dialog Listener (LDL) to send all quality updates. Quality updates are based on individual streams instead of the call.</p></td>
</tr>
<tr class="even">
<td><p><a href="rawsdp-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">RawSDP</a></p></td>
<td><p>xs:string</p></td>
<td><p>Raw Session Description Protocol (SDP) data that is included as the payload of the underlying SIP messages of the Invite, LRSInvite and StartOrUpdate type, if the sendrawsdp entry is set to True in the LDL configuration file.</p></td>
</tr>
<tr class="odd">
<td><p><a href="route-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Route</a></p></td>
<td><p>Not defined</p></td>
<td><p>Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.</p></td>
</tr>
<tr class="even">
<td><p><a href="start-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Start</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-api-schema-a.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream is started. Every Start element contains a report about a particular media stream. This event is raised when the call is established, i.e., when the call is picked up and the SIP INVITE is answered with a 200 OK response. The LyncDiagnostics element will not contain any event elements (e.g., Invite, LRSInvite, Start, Update, etc.), when all media streams are inactive (usually when the call is on-hold).</p></td>
</tr>
<tr class="odd">
<td><p><a href="update-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Update</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-api-schema-a.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream is started. Every Start element contains a report about a particular media stream. This event is raised when the call is established, i.e., when the call is picked up and the SIP INVITE is answered with a 200 OK response. The LyncDiagnostics element will not contain any event elements (e.g., Invite, LRSInvite, Start, Update, etc.), when all media streams are inactive (usually when the call is on-hold).</p></td>
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
<td><p></p></td>
<td><p>optional</p></td>
<td><p>Version number of this data structure. It provides a simple distinction between LyncDiagnostics messages formats. LyncDiagnostics message matching to this xsd use Version A.</p></td>
<td><p>Values of the type.</p></td>
</tr>
</tbody>
</table>

