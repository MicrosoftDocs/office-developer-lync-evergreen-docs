---
title: Properties element (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: Properties element (QualityUpdate element) (LyncDiagnostics element)
ms:assetid: 175f3116-f334-fb01-1260-9e866e73c873
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439244(v=office.15)
ms:contentKeyID: 57260981
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (QualityUpdate element) (LyncDiagnostics element) (Lync SDN API Schema A)

Properties of the media stream, including a selected set of quality metrics reported and thresholds that are used to determinine a bad call.


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
<td><p><a href="qualityupdate-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">QualityUpdate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Specifies the event that a SIP call has ended and contains an updated report of the quality metrics of individual media streams. These quality metrics for a stream may include updates provided by other endpoints during the call. By default, LDL raises this event (and thus reports the quality updates) only if the call quality is under the quality thresholds defined in the QoE database or in the LDL configuration file. Alterantively, you can configure Lync Dialog Listener (LDL) to send all quality updates. Quality updates are based on individual streams instead of the call.</p></td>
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
<td><p><a href="appliedbandwidthlimit-element-sdn-api-schema-a.md">AppliedBandwidthLimit</a></p></td>
<td><p>xs:unsignedInt</p></td>
<td><p>Displays the limits applied. It is provided only in QualityUpdate events when Call Admission Control is used.</p></td>
</tr>
<tr class="even">
<td><p><a href="bitrateavg-element-sdn-api-schema-a.md">BitRateAvg</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average bit rate, in bits per second, sent or received for a video stream and computed over the duration of the session. This includes raw video and transport bits. This metric is reported for video streams when available. (bits/s)</p></td>
</tr>
<tr class="odd">
<td><p><a href="bitratemax-element-sdn-api-schema-a.md">BitRateMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum bit rate, in bits per second, sent or received for a video stream and computed over the duration of the session. This metric is reported for video streams when available. (bits/s)</p></td>
</tr>
<tr class="even">
<td><p><a href="burstdensity-element-sdn-api-schema-a.md">BurstDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average burst density, as specified in [RFC3611] section 4.7.2, is computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available. The fraction of RTP data packets within burst periods since the beginning of reception that were either lost or discarded. This value is expressed as a fixed point number with the binary point at the left edge of the field. It is calculated by dividing the total number of packets lost or discarded (excluding duplicate packet discards) within burst periods by the total number of packets expected within the burst periods, multiplying the result of the division by 256, limiting the maximum value to 255 (to avoid overflow), and taking the integer part. This field MUST be populated and MUST be set to zero if no packets have been received.</p></td>
</tr>
<tr class="odd">
<td><p><a href="burstduration-element-sdn-api-schema-a.md">BurstDuration</a></p></td>
<td><p>Not defined</p></td>
<td><p>The average burst duration, as specified in [RFC3611] section 4.7.2, is computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="burstgapdensity-element-sdn-api-schema-a.md">BurstGapDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average burst gap density, as specified in [RFC3611] section 4.7.2, computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="burstgapduration-element-sdn-api-schema-a.md">BurstGapDuration</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average burst gap duration, as specified in [RFC3611] section 4.7.2, computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="codec-element-qualityupdate-element-sdn-api-schema-a.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-api-schema-a.md">CodecType</a></p></td>
<td><p>Describes the last codec used for the media.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversationalmos-element-sdn-api-schema-a.md">ConversationalMOS</a></p></td>
<td><p>xs:string</p></td>
<td><p>Conversational clarity index for remote party, as described in [ITUP.562] section 6.3. This metric is reported for all available modalities and media types.</p></td>
</tr>
<tr class="even">
<td><p><a href="degradationavg-element-sdn-api-schema-a.md">DegradationAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Difference between the OverallAvg value and the maximum possible MOS-LQO for the audio codec used in the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="degradationjitteravg-element-sdn-api-schema-a.md">DegradationJitterAvg</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average fraction of the degradation jitter average applies to inter-arrival packet jitter. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="degradationmax-element-sdn-api-schema-a.md">DegradationMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum degradation as the difference between the OverallMin and the maximum possible MOS-LQO for the audio codec used in the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="degradationpacketlossavg-element-sdn-api-schema-a.md">DegradationPacketLossAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction of the DegradationAvg that was caused by packet loss. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="dynamiccapabilitypercent-element-sdn-api-schema-a.md">DynamicCapabilityPercent</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of time that the client is running under capability of less than 70% of expected capability for this type of CPU. Inbound and Outbound are identical because it measures the capability of the client instead of the channel. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="echoeventcauses-element-sdn-api-schema-a.md">EchoEventCauses</a></p></td>
<td><p>Not defined</p></td>
<td><p>Reasons of device echo detection and reported for audio streams when available. The causes are coded by the following bit flags: &quot;0x01&quot; - Sample timestamps from capture or render device were poor quality. &quot;0x04&quot; - High level of echo remained after echo cancellation. &quot;0x10&quot; - Signal from capture device had significant instances of maximum signal level.</p></td>
</tr>
<tr class="even">
<td><p><a href="echopercentmicin-element-sdn-api-schema-a.md">EchoPercentMicIn</a></p></td>
<td><p>xs:string</p></td>
<td><p>Percentage of time when echo is detected in the audio from the capture or microphone device prior to echo cancellation. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="echopercentsend-element-sdn-api-schema-a.md">EchoPercentSend</a></p></td>
<td><p>xs:string</p></td>
<td><p>Percentage of time when echo is detected in the audio from the capture or microphone device after echo cancellation. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="echoreturn-element-properties-element-sdn-api-schema-a.md">EchoReturn</a></p></td>
<td><p>Not defined</p></td>
<td><p>Echo returns reported for audio streams, when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="framerate-element-sdn-api-schema-a.md">FrameRate</a></p></td>
<td><p>xs:decimal</p></td>
<td><p>Average frame rate (in frames per second). When available, this metric is only reported for application sharing streams and only for Lync 2013. (frames/s)</p></td>
</tr>
<tr class="even">
<td><p><a href="hdqualityratio-element-sdn-api-schema-a.md">HDQualityRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of the duration of a call that is using the HD720 resolution. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="healerpacketdropratio-element-sdn-api-schema-a.md">HealerPacketDropRatio</a></p></td>
<td><p>xs:string</p></td>
<td><p>Ratio of audio packets dropped by a healer over total number of audio packets received by the healer. This metric is reported for all modalities/media types when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="jitterinterarrival-element-sdn-api-schema-a.md">JitterInterArrival</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average inter-arrival jitter, as specified in [RFC3550] section 6.4.1. This metric is reported for all available modalities/media types. (ms)</p></td>
</tr>
<tr class="odd">
<td><p><a href="jitterinterarrivalmax-element-sdn-api-schema-a.md">JitterInterArrivalMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum inter-arrival jitter, as specified in [RFC3550] section 6.4.1. This metric is reported for all modalities/media types when available. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="localframelosspercentageavg-element-sdn-api-schema-a.md">LocalFrameLossPercentageAvg</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average percentage of video frames lost as they are displayed to the user, including frames recovered from network losses. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="lowframeratecallpercent-element-sdn-api-schema-a.md">LowFrameRateCallPercent</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of time of the call where frame rate is less than 7.5 frames per second. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="lowresolutioncallpercent-element-sdn-api-schema-a.md">LowResolutionCallPercent</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of time of the call where resolution is low. Threshold is 120 pixels for smaller dimension. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="overallavgnetworkmos-element-sdn-api-schema-a.md">OverallAvgNetworkMOS</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average of MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, based on the audio codec used, the observed packet loss and inter-arrival packet jitter. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="overallminnetworkmos-element-sdn-api-schema-a.md">OverallMinNetworkMOS</a></p></td>
<td><p>xs:string</p></td>
<td><p>Minimum of MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, based on the audio codec used, the observed packet loss and inter-arrival packet jitter. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="packetlossrate-element-sdn-api-schema-a.md">PacketLossRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction lost computed over the duration of the session, as specified in [RFC3550] section 6.4.1. This metric is reported for all available modalities and media types. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="packetlossratemax-element-sdn-api-schema-a.md">PacketLossRateMax</a></p></td>
<td><p>Not defined</p></td>
<td><p>Maximum fraction lost, as specified in [RFC3550] section 6.4.1, computed over the duration of the session. This metric is reported for all available modalities/media types. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="packetutilization-element-sdn-api-schema-a.md">PacketUtilization</a></p></td>
<td><p>xs:string</p></td>
<td><p>Number of Real-time Transport Protocol (RTP) packets received in the session. This metric is reported for all available modalities and media types.</p></td>
</tr>
<tr class="even">
<td><p><a href="protocol-element-qualityupdate-element-sdn-api-schema-a.md">Protocol</a></p></td>
<td><p>xs:string</p></td>
<td><p>Transmission protocol of the call such as TCP or UDP.</p></td>
</tr>
<tr class="odd">
<td><p><a href="ratioconcealedsamplesavg-element-sdn-api-schema-a.md">RatioConcealedSamplesAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Ratio of the number of audio frames with samples generated by packet loss concealment to the total number of audio frames. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="rdptileprocessinglatencyaverage-element-sdn-api-schema-a.md">RDPTileProcessingLatencyAverage</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average processing time for remote desktop protocol (RDP) tiles. A higher total value implies a longer delay in the viewing experience. When available, this metric is only reported for application sharing streams using Lync 2013. (ms)</p></td>
</tr>
<tr class="odd">
<td><p><a href="rdptileprocessinglatencyburstdensity-element-sdn-api-schema-a.md">RDPTileProcessingLatencyBurstDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Burst density in the processing time for remote desktop protocol (RDP) tiles. A &quot;bursty&quot; transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric is only reported for application sharing streams using Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="recvframerateaverage-element-sdn-api-schema-a.md">RecvFrameRateAverage</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average frames per second received for all video streams and computed over the duration of the session. This metric is reported for video streams when available. (frames/s)</p></td>
</tr>
<tr class="odd">
<td><p><a href="recvlistenmos-element-sdn-api-schema-a.md">RecvListenMOS</a></p></td>
<td><p>Not defined</p></td>
<td><p>MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, for decoded audio received by the reporting entity during the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="recvlistenmosmin-element-sdn-api-schema-a.md">RecvListenMOSMin</a></p></td>
<td><p>Not defined</p></td>
<td><p>Minimum of the RecvListenMOS for the stream during the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="recvnoiselevel-element-sdn-api-schema-a.md">RecvNoiseLevel</a></p></td>
<td><p>xs:string</p></td>
<td><p>Received noise level in units of dB that is reported for audio streams when available. Average energy level of received audio is classified as noise, mono signal or the left channel of stereo signal. (dB)</p></td>
</tr>
<tr class="even">
<td><p><a href="recvsignallevel-element-sdn-api-schema-a.md">RecvSignalLevel</a></p></td>
<td><p>xs:string</p></td>
<td><p>Received signal level in units of dB. This metric is reported for audio streams when available. Average energy level of received audio is classified as mono speech, or left channel of stereo speech. (dB)</p></td>
</tr>
<tr class="odd">
<td><p><a href="relativeonewayaverage-element-sdn-api-schema-a.md">RelativeOneWayAverage</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average amount of one-way latency. Relative one-way latency measures the delay between the client and the server. This metric is only reported for application sharing streams using Lync 2013. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="relativeonewayburstdensity-element-sdn-api-schema-a.md">RelativeOneWayBurstDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Total one-way burst density involving unsteady transmission. An unsteady transmission is one where data flows in random bursts as opposed to a steady stream. This metric measures data flow between the client and the server and is only reported for application sharing streams using Lync 2013.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roundtrip-element-sdn-api-schema-a.md">RoundTrip</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average network propagation round-trip time as specified in [RFC3550] section 6.4.1. This metric is reported for all modalities/media types when available. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="roundtripmax-element-sdn-api-schema-a.md">RoundTripMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum network propagation round-trip time as specified in [RFC3550] section 6.4.1. This metric is reported for all modalities/media types when available. (ms)</p></td>
</tr>
<tr class="odd">
<td><p><a href="sendlistenmos-element-sdn-api-schema-a.md">SendListenMOS</a></p></td>
<td><p>Not defined</p></td>
<td><p>MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, for pre-encoded audio sent by the reporting entity during the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="sendlistenmosmin-element-sdn-api-schema-a.md">SendListenMOSMin</a></p></td>
<td><p>Not defined</p></td>
<td><p>Minimum of the SendListenMOS for the stream over the duration of the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="spoiledtilepercentaverage-element-sdn-api-schema-a
">SpoiledTilePercentAverage</a></p></td>
<td><p>xs:decimal</p></td>
<td><p>Average percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content. When available, this metric is only reported for application sharing streams and only for Lync 2013. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="spoiledtilepercenttotal-element-sdn-api-schema-a.md">SpoiledTilePercentTotal</a></p></td>
<td><p>Not defined</p></td>
<td><p>Total percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content. When available, this metric is only reported for application sharing streams and only for Lync 2013. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="vgaqualityratio-element-sdn-api-schema-a.md">VGAQualityRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of the duration of a call that is using the VGA resolution. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="videoframelossrate-element-sdn-api-schema-a.md">VideoFrameLossRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction of frames lost on the video receiver side as computed over the duration of the session. This metric is reported for video streams when available. (frames/s)</p></td>
</tr>
<tr class="odd">
<td><p><a href="videolocalframelosspercentageavg-element-sdn-api-schema-a.md">VideoLocalFrameLossPercentageAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average percentage of video frames lost as they are displayed to the user. This includes frames recovered from network losses. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="videopacketlossrate-element-sdn-api-schema-a.md">VideoPacketLossRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction lost, as specified in [RFC3550] section 6.4.1, computed over the duration of the session. This metric is reported for video streams when available. (packets/s)</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

