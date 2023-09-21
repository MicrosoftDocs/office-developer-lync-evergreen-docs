﻿---
title: Properties element (QualityType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Properties element (QualityType complexType)
ms:assetid: 6a2c0cfa-9d0f-0a8c-69eb-d5ab1dcbd268
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912786(v=office.15)
ms:contentKeyID: 64126955
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (QualityType complexType) 

(Lync SDN Interface 2.1.1)

Properties of the media stream, including a selected set of quality metrics reported and thresholds that are used to determine a bad call.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="qualitypropertiestype-complextype-lync-sdn-interface-2-1-1.md">QualityPropertiesType</a></p></td>
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

    <xs:element name="Properties"  type="QualityPropertiesType">
    
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
<td><p><a href="incallquality-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">InCallQuality</a></p></td>
<td><p><a href="qualitytype-complextype-lync-sdn-interface-2-1-1.md">QualityType</a></p></td>
<td><p>Indicates that a significant quality related event occured in the client. Either the quality dropped into another level or improved. There are 3 levels: Good, Poor, Bad. The media stack determines the quality level. Furthermore, this event is also sent when a video stream is deescalated. Even in an issue free network at least one IncallQuality message is sent.</p></td>
</tr>
<tr class="even">
<td><p><a href="qualityupdate-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">QualityUpdate</a></p></td>
<td><p><a href="qualitytype-complextype-lync-sdn-interface-2-1-1.md">QualityType</a></p></td>
<td><p>Specifies the event that a call has ended and contains a report of the quality metrics of individual media streams. These quality metrics for a stream may include updates provided by both endpoints which are merged.</p></td>
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
<td><p><a href="appliedbandwidthlimit-element-sdn-interface-2-1-1.md">AppliedBandwidthLimit</a></p></td>
<td><p>xs:unsignedInt</p></td>
<td><p>This is the actual bandwidth applied to the given send side stream given various policy settings (TURN, API, SDP, Policy Server, and so on). This is not to be confused with the effective bandwidth because there can be a lower effective bandwidth based on the bandwidth estimate. This is basically the maximum bandwidth the send stream can take barring limits imposed by the bandwidth estimate.</p></td>
</tr>
<tr class="even">
<td><p><a href="audiotimestamperrormicms-element-sdn-interface-2-1-1.md">AudioTimestampErrorMicMs</a></p></td>
<td><p>Not defined</p></td>
<td><p>Speaking device clock drift rate, relative to CPU clock. Average error of microphone-captured-stream time stamp, in milliseconds, for the last 20 seconds of a call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="audiotimestamperrorspkms-element-sdn-interface-2-1-1.md">AudioTimestampErrorSpkMs</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average error of speech render stream time stamp, in milliseconds, or the last 20 seconds of the call.</p></td>
</tr>
<tr class="even">
<td><p><a href="bitrateavg-element-sdn-interface-2-1-1.md">BitRateAvg</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average bit rate, in bits per second, sent or received for a video stream and computed over the duration of the session. This includes raw video and transport bits. This metric is reported for video streams when available. (bits/s)</p></td>
</tr>
<tr class="odd">
<td><p><a href="bitratemax-element-sdn-interface-2-1-1.md">BitRateMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum bit rate, in bits per second, sent or received for a video stream and computed over the duration of the session. This metric is reported for video streams when available. (bits/s)</p></td>
</tr>
<tr class="even">
<td><p><a href="burstdensity-element-sdn-interface-2-1-1.md">BurstDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average burst density, as specified in [RFC3611] section 4.7.2, is computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available and measures the average density of packet Loss during bursts of losses during the call. This field MUST be populated and MUST be set to zero if no packets have been received.</p></td>
</tr>
<tr class="odd">
<td><p><a href="burstduration-element-sdn-interface-2-1-1.md">BurstDuration</a></p></td>
<td><p>Not defined</p></td>
<td><p>The average burst duration, as specified in [RFC3611] section 4.7.2, is computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="burstgapdensity-element-sdn-interface-2-1-1.md">BurstGapDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average burst gap density, as specified in [RFC3611] section 4.7.2, computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="burstgapduration-element-sdn-interface-2-1-1.md">BurstGapDuration</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average burst gap duration (in microsecond, ms), as specified in [RFC3611] section 4.7.2, computed with a Gmin=16 for the received RTP packets. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="capturedevice-element-sdn-interface-2-1-1.md">CaptureDevice</a></p></td>
<td><p>Not defined</p></td>
<td><p>The name of a capture device used to produce the media of this stream. This device is in the FROM endpoint and usually represents a microphone.</p></td>
</tr>
<tr class="odd">
<td><p><a href="capturedevicedriver-element-sdn-interface-2-1-1.md">CaptureDeviceDriver</a></p></td>
<td><p>Not defined</p></td>
<td><p>Device driver name and version of the capture device used to produce the media of this stream</p></td>
</tr>
<tr class="even">
<td><p><a href="codec-element-qualitypropertiestype-complextype-lync-sdn-interface-2-1-1.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-interface-2-1-1.md">CodecType</a></p></td>
<td><p>Describes the last codec used for the media.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversationalmos-element-sdn-interface-2-1-1.md">ConversationalMOS</a></p></td>
<td><p>xs:string</p></td>
<td><p>Conversational clarity index for remote party, as described in [ITUP.562] section 6.3. This metric is reported for all available modalities and media types. This field is unused and deprecated for Lync clients 2013 and beyond.</p></td>
</tr>
<tr class="even">
<td><p><a href="cpuinsufficienteventratio-element-sdn-interface-2-1-1.md">CPUInsufficientEventRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of sessions where the insufficient CPU event was fired when CPU cycles are insufficient for processing with the current modalities and applications, establish causeing distortions in the audio channel.</p></td>
</tr>
<tr class="odd">
<td><p><a href="degradationavg-element-sdn-interface-2-1-1.md">DegradationAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Difference between the OverallAvg value and the maximum possible MOS-LQO for the audio codec used in the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="degradationjitteravg-element-sdn-interface-2-1-1.md">DegradationJitterAvg</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average fraction of the degradation jitter average applies to inter-arrival packet jitter. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="degradationmax-element-sdn-interface-2-1-1.md">DegradationMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum degradation as the difference between the OverallMin and the maximum possible MOS-LQO for the audio codec used in the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="degradationpacketlossavg-element-sdn-interface-2-1-1.md">DegradationPacketLossAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction of the DegradationAvg that was caused by packet loss. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="devicecapturenotfunctioningeventratio-element-sdn-interface-2-1-1.md">DeviceCaptureNotFunctioningEventRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of sessions the DeviceCaptureNotFunctioning event was fired when the capture device currently being used for the session is not functioning correctly and, possibly, preventing one-way audio from working correctly.</p></td>
</tr>
<tr class="even">
<td><p><a href="deviceclippingeventratio-element-sdn-interface-2-1-1.md">DeviceClippingEventRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of sessions the DeviceClipping event was fired when a speaker clips the microphone, causing the remote listener receives clipping-induced distortions. It is important to avoid the microphone clipping.</p></td>
</tr>
<tr class="odd">
<td><p><a href="deviceechoeventratio-element-sdn-interface-2-1-1.md">DeviceEchoEventRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of sessions the DeviceEchoEvent event was fired when a device or setup is causing echo beyond the compensatory ability of the system.</p></td>
</tr>
<tr class="even">
<td><p><a href="devicehowlingeventcount-element-sdn-interface-2-1-1.md">DeviceHowlingEventCount</a></p></td>
<td><p>Not defined</p></td>
<td><p>Number of times during a session the DeviceHowlingEvent event was fired when audio feedback loop, caused by multiple endpoints sharing the audio path, is detected.</p></td>
</tr>
<tr class="odd">
<td><p><a href="devicenearendtoechoratioeventratio-element-sdn-interface-2-1-1.md">DeviceNearEndToEchoRatioEventRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of sessions the DeviceNearEndToEcho event was fired when the user speech is too low compared to the echo being captured which impacts the users experience because it limits how easy it is to interrupt a user. The situation can be improved by reducing speaker volume or moving the microphone closer to the speaker.</p></td>
</tr>
<tr class="even">
<td><p><a href="devicerendernotfunctioningeventratio-element-sdn-interface-2-1-1.md">DeviceRenderNotFunctioningEventRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of sessions the DeviceRenderNotFunctioning event was fired when the render device currently being used for the session is not functioning correctly and, possibly, causing one-way audio issues.</p></td>
</tr>
<tr class="odd">
<td><p><a href="dynamiccapabilitypercent-element-sdn-interface-2-1-1.md">DynamicCapabilityPercent</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of time that the client is running under capability of less than 70% of expected capability for this type of CPU. Inbound and Outbound are identical because it measures the capability of the client instead of the channel. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="echoeventcauses-element-sdn-interface-2-1-1.md">EchoEventCauses</a></p></td>
<td><p>Not defined</p></td>
<td><p>Reasons of device echo detection and reported for audio streams when available. The causes are coded with the following bit flags: &quot;0x01&quot; - Sample timestamps from capture or render device were poor quality. &quot;0x04&quot; - High level of echo remained after echo cancellation. &quot;0x10&quot; - Signal from capture device had significant instances of maximum signal level.</p></td>
</tr>
<tr class="odd">
<td><p><a href="echopercentmicin-element-sdn-interface-2-1-1.md">EchoPercentMicIn</a></p></td>
<td><p>xs:string</p></td>
<td><p>Percentage of time when echo is detected in the audio from the capture or microphone device prior to echo cancellation. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="echopercentsend-element-sdn-interface-2-1-1.md">EchoPercentSend</a></p></td>
<td><p>xs:string</p></td>
<td><p>Percentage of time when echo is detected in the audio from the capture or microphone device after echo cancellation. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="echoreturn-element-sdn-interface-2-1-1.md">EchoReturn</a></p></td>
<td><p>Not defined</p></td>
<td><p>Echo returns reported for audio streams, when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="framerate-element-sdn-interface-2-1-1.md">FrameRate</a></p></td>
<td><p>xs:decimal</p></td>
<td><p>Average frame rate (in frames per second). When available, this metric is only reported for application sharing streams and only for Lync 2013. (frames/s)</p></td>
</tr>
<tr class="odd">
<td><p><a href="hdqualityratio-element-sdn-interface-2-1-1.md">HDQualityRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of the duration of a call that is using the HD720 resolution. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="healerpacketdropratio-element-sdn-interface-2-1-1.md">HealerPacketDropRatio</a></p></td>
<td><p>xs:string</p></td>
<td><p>Ratio of audio packets dropped by a healer over total number of audio packets received by the healer. This metric is reported for all modalities/media types when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="jitterinterarrival-element-sdn-interface-2-1-1.md">JitterInterArrival</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average inter-arrival jitter, as specified in [RFC3550] section 6.4.1. This metric is reported for all available modalities/media types. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="jitterinterarrivalmax-element-sdn-interface-2-1-1.md">JitterInterArrivalMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum inter-arrival jitter, as specified in [RFC3550] section 6.4.1. This metric is reported for all modalities/media types when available. (ms)</p></td>
</tr>
<tr class="odd">
<td><p><a href="localframelosspercentageavg-element-sdn-interface-2-1-1.md">LocalFrameLossPercentageAvg</a></p></td>
<td><p>xs:string</p></td>
<td><p>(Deprecated, use VideoLocalFrameLossPercentageAvg instead) Average percentage of video frames lost as they are displayed to the user, including frames recovered from network losses. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="lowframeratecallpercent-element-sdn-interface-2-1-1.md">LowFrameRateCallPercent</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of time of the call where frame rate is less than 7.5 frames per second. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="lowresolutioncallpercent-element-sdn-interface-2-1-1.md">LowResolutionCallPercent</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of time of the call where resolution is low. Threshold is 120 pixels for smaller dimension. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="micglitchrate-element-sdn-interface-2-1-1.md">MicGlitchRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average glitches per five minutes for the microphone capture. For good quality this should be less than one per five minutes. This will not be reported by audio/video conferencing servers, mediation servers, or IP phones.</p></td>
</tr>
<tr class="odd">
<td><p><a href="networkdelayeventratio-element-sdn-interface-2-1-1.md">NetworkDelayEventRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of sessions the the NetworkDelayEvent event was fired when network latency is severe and impacting the experience by preventing interactive communication</p></td>
</tr>
<tr class="even">
<td><p><a href="overallavgnetworkmos-element-sdn-interface-2-1-1.md">OverallAvgNetworkMOS</a></p></td>
<td><p>xs:string</p></td>
<td><p>Average of MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, based on the audio codec used, the observed packet loss and inter-arrival packet jitter. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="overallminnetworkmos-element-sdn-interface-2-1-1.md">OverallMinNetworkMOS</a></p></td>
<td><p>xs:string</p></td>
<td><p>Minimum of MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, based on the audio codec used, the observed packet loss and inter-arrival packet jitter. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="packetlossrate-element-sdn-interface-2-1-1.md">PacketLossRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction lost computed over the duration of the session, as specified in [RFC3550] section 6.4.1. This metric is reported for all available modalities and media types. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="packetlossratemax-element-sdn-interface-2-1-1.md">PacketLossRateMax</a></p></td>
<td><p>Not defined</p></td>
<td><p>Maximum fraction lost, as specified in [RFC3550] section 6.4.1, computed over the duration of the session. This metric is reported for all available modalities/media types. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="packetutilization-element-sdn-interface-2-1-1.md">PacketUtilization</a></p></td>
<td><p>xs:string</p></td>
<td><p>Number of Real-time Transport Protocol (RTP) packets received in the session. This metric is reported for all available modalities and media types.</p></td>
</tr>
<tr class="odd">
<td><p><a href="protocol-element-qualitypropertiestype-sdn-interface-2-1-1.md">Protocol</a></p></td>
<td><p>xs:string</p></td>
<td><p>Transmission protocol of the call such as TCP or UDP.</p></td>
</tr>
<tr class="even">
<td><p><a href="ratioconcealedsamplesavg-element-sdn-interface-2-1-1.md">RatioConcealedSamplesAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Ratio of the number of audio frames with samples generated by packet loss concealment to the total number of audio frames. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="rdptileprocessinglatencyaverage-element-sdn-interface-2-1-1.md">RDPTileProcessingLatencyAverage</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average processing time for remote desktop protocol (RDP) tiles. A higher total value implies a longer delay in the viewing experience. When available, this metric is only reported for application sharing streams using Lync 2013. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="rdptileprocessinglatencyburstdensity-element-sdn-interface-2-1-1.md">RDPTileProcessingLatencyBurstDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Burst density in the processing time for remote desktop protocol (RDP) tiles. A &quot;bursty&quot; transmission is a transmission where data flows in unpredictable bursts as opposed to a steady stream. This metric is only reported for application sharing streams using Lync 2013.</p></td>
</tr>
<tr class="odd">
<td><p><a href="recvframerateaverage-element-sdn-interface-2-1-1.md">RecvFrameRateAverage</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average frames per second received for all video streams and computed over the duration of the session. This metric is reported for video streams when available. (frames/s)</p></td>
</tr>
<tr class="even">
<td><p><a href="recvlistenmos-element-sdn-interface-2-1-1.md">RecvListenMOS</a></p></td>
<td><p>Not defined</p></td>
<td><p>MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, for decoded audio received by the reporting entity during the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="recvlistenmosmin-element-sdn-interface-2-1-1.md">RecvListenMOSMin</a></p></td>
<td><p>Not defined</p></td>
<td><p>Minimum of the RecvListenMOS for the stream during the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="recvnoiselevel-element-sdn-interface-2-1-1.md">RecvNoiseLevel</a></p></td>
<td><p>xs:string</p></td>
<td><p>Received noise level in units of dB that is reported for audio streams when available. Average energy level of received audio is classified as noise, mono signal or the left channel of stereo signal. (dB)</p></td>
</tr>
<tr class="odd">
<td><p><a href="recvsignallevel-element-sdn-interface-2-1-1.md">RecvSignalLevel</a></p></td>
<td><p>xs:string</p></td>
<td><p>Received signal level in units of dB. This metric is reported for audio streams when available. Average energy level of received audio is classified as mono speech, or left channel of stereo speech. (dB)</p></td>
</tr>
<tr class="even">
<td><p><a href="relativeonewayaverage-element-sdn-interface-2-1-1.md">RelativeOneWayAverage</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average amount of one-way latency. Relative one-way latency measures the delay between the client and the server. This metric is only reported for application sharing streams using Lync 2013. (ms)</p></td>
</tr>
<tr class="odd">
<td><p><a href="relativeonewayburstdensity-element-sdn-interface-2-1-1.md">RelativeOneWayBurstDensity</a></p></td>
<td><p>Not defined</p></td>
<td><p>Total one-way burst density involving unsteady transmission. An unsteady transmission is one where data flows in random bursts as opposed to a steady stream. This metric measures data flow between the client and the server and is only reported for application sharing streams using Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="renderdevice-element-sdn-interface-2-1-1.md">RenderDevice</a></p></td>
<td><p>Not defined</p></td>
<td><p>The name of a render device used to provide the media to for this stream. This device is in the TO endpoint and usually represents a speaker.</p></td>
</tr>
<tr class="odd">
<td><p><a href="renderdevicedriver-element-sdn-interface-2-1-1.md">RenderDeviceDriver</a></p></td>
<td><p>Not defined</p></td>
<td><p>Device driver name and version of the render device used to consume the media of this call</p></td>
</tr>
<tr class="even">
<td><p><a href="roundtrip-element-sdn-interface-2-1-1.md">RoundTrip</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average network propagation round-trip time as specified in [RFC3550] section 6.4.1. This metric is reported for all modalities/media types when available. (ms)</p></td>
</tr>
<tr class="odd">
<td><p><a href="roundtripmax-element-sdn-interface-2-1-1.md">RoundTripMax</a></p></td>
<td><p>xs:string</p></td>
<td><p>Maximum network propagation round-trip time as specified in [RFC3550] section 6.4.1. This metric is reported for all modalities/media types when available. (ms)</p></td>
</tr>
<tr class="even">
<td><p><a href="sendlistenmos-element-sdn-interface-2-1-1.md">SendListenMOS</a></p></td>
<td><p>Not defined</p></td>
<td><p>MOS-LQO wideband, as specified by [ITUP.800.1] section 2.1.2, for pre-encoded audio sent by the reporting entity during the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sendlistenmosmin-element-sdn-interface-2-1-1.md">SendListenMOSMin</a></p></td>
<td><p>Not defined</p></td>
<td><p>Minimum of the SendListenMOS for the stream over the duration of the session. This metric is reported for audio streams when available.</p></td>
</tr>
<tr class="even">
<td><p><a href="speakerglitchrate-element-sdn-interface-2-1-1.md">SpeakerGlitchRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average glitches per five minutes for the loudspeaker rendering. For good quality, this should be less than one per five minutes. This will not be reported by audio/video conferencing servers, mediation servers, or IP phones.</p></td>
</tr>
<tr class="odd">
<td><p><a href="spoiledtilepercentaverage-element-sdn-interface-2-1-1.md">SpoiledTilePercentAverage</a></p></td>
<td><p>xs:decimal</p></td>
<td><p>Average percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content. When available, this metric is only reported for application sharing streams and only for Lync 2013. (percent)</p></td>
</tr>
<tr class="even">
<td><p><a href="spoiledtilepercenttotal-element-sdn-interface-2-1-1.md">SpoiledTilePercentTotal</a></p></td>
<td><p>Not defined</p></td>
<td><p>Total percentage of the content that did not reach the viewer but was instead discarded and overwritten by fresh content. When available, this metric is only reported for application sharing streams and only for Lync 2013. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="streamquality-element-sdn-interface-2-1-1.md">StreamQuality</a></p></td>
<td><p>xs:string</p></td>
<td><p>Estimated quality of the stream: Good, Poor, Bad</p></td>
</tr>
<tr class="even">
<td><p><a href="vgaqualityratio-element-sdn-interface-2-1-1.md">VGAQualityRatio</a></p></td>
<td><p>Not defined</p></td>
<td><p>Percentage of the duration of a call that is using the VGA resolution. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="videoframelossrate-element-sdn-interface-2-1-1.md">VideoFrameLossRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction of frames lost on the video receiver side as computed over the duration of the session. This metric is reported for video streams when available. (frames/s)</p></td>
</tr>
<tr class="even">
<td><p><a href="videolocalframelosspercentageavg-element-sdn-interface-2-1-1.md">VideoLocalFrameLossPercentageAvg</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average percentage of video frames lost as they are displayed to the user, including frames recovered from network losses. This metric is reported for video streams when available. (percent)</p></td>
</tr>
<tr class="odd">
<td><p><a href="videopacketlossrate-element-sdn-interface-2-1-1.md">VideoPacketLossRate</a></p></td>
<td><p>Not defined</p></td>
<td><p>Average fraction lost, as specified in [RFC3550] section 6.4.1, computed over the duration of the session. This metric is reported for video streams when available. (packets/s)</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

