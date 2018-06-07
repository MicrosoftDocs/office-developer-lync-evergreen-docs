---
title: QualityUpdate element (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: QualityUpdate element
ms:assetid: 4948a34e-0ffe-2282-2e77-010f3db136db
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439275(v=office.15)
ms:contentKeyID: 57261011
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# QualityUpdate element (LyncDiagnostics element) (Lync SDN API Schema A)

Specifies the event that a SIP call has ended and contains an updated report of the quality metrics of individual media streams. These quality metrics for a stream may include updates provided by other endpoints during the call. By default, LDL raises this event (and thus reports the quality updates) only if the call quality is under the quality thresholds defined in the QoE database or in the LDL configuration file. Alterantively, you can configure Lync Dialog Listener (LDL) to send all quality updates. Quality updates are based on individual streams instead of the call.


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
<td><p><a href="from-element-qualityupdate-element-sdn-api-schema-a.md">From</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>The source of the reported media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="properties-element-qualityupdate-element-sdn-api-schema-a.md">Properties</a></p></td>
<td><p>Not defined</p></td>
<td><p>Properties of the media stream, including a selected set of quality metrics reported and thresholds that are used to determinine a bad call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="to-element-qualityupdate-element-sdn-api-schema-a.md">To</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
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
<td><p>Type</p></td>
<td><p>xs:string</p></td>
<td><p>required</p></td>
<td><p>Modelity or media type for which the quality metrics are reported. The supported options are audio, video and applicationsharing.</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

