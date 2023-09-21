---
title: Configuring LSM execution options
TOCTitle: Configuring LSM execution options
ms:assetid: 93e0281f-b44f-4772-a4e1-174aad80e92b
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785212(v=office.15)
ms:contentKeyID: 62952696
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Configuring LSM execution options

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

You can change some parameters by editing the SDNManager.exe.config file or by using the SDNManager.exe command line tool, depending on whether LSM is deployed as a singleton or settings are maintained in a database. The parameters listed below affect how LSM runs.

## Configuration settings affecting LSM execution

The following configuration settings are also known as the LSM execution options.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Name</strong></p></td>
<td><p><strong>Description</strong></p></td>
</tr>
<tr class="even">
<td><p>submituri</p></td>
<td><p>Specifies the list of URIs, filters and client certificates for network controllers to receive call and quality data.</p></td>
</tr>
<tr class="odd">
<td><p>submitqueuelen</p></td>
<td><p>Sets value to the maximum unanswered and waiting messages to send to each recipient. Change this value only if network conditions require a longer queue length caused by fluctuating delays in messages delivered to the network management systems.</p></td>
</tr>
<tr class="even">
<td><p>calltimeout</p></td>
<td><p>Maximum time expected for a call, after the call is assumed to be terminated and cleaned up.</p></td>
</tr>
<tr class="odd">
<td><p>invitetimeout</p></td>
<td><p>Maximum time expected for ringing, before either an error is sent or the user picked up the call.</p></td>
</tr>
<tr class="even">
<td><p>qoetimeout</p></td>
<td><p>Time to wait for the second raw QoE report before forwarding a merged report to the network controller(s)</p></td>
</tr>
<tr class="odd">
<td><p>endedtimeout</p></td>
<td><p>Time to wait after the Ended message before cleaning up the call if no raw QoE report is received.</p></td>
</tr>
<tr class="even">
<td><p>hidepii</p></td>
<td><p>Set the value attribute to true (the default value) to obfuscate or hide personal identifiable information (PII) in the messages. Set value to false to see PII, in particular a full SIP UI that includes the account name and telephone numbers.</p></td>
</tr>
<tr class="odd">
<td><p>sendrawsdp</p></td>
<td><p>Set value to true to forward any SDP info (using the &quot;RawSDP&quot; tag). Set value to false to prevent sending raw SDP content.</p></td>
</tr>
<tr class="even">
<td><p>timeouthandlerperiod</p></td>
<td><p>Applied to LSM, it is the time period to check for call timeouts in the database.</p></td>
</tr>
<tr class="odd">
<td><p>settingsrefresh</p></td>
<td><p>Applied to LSM, it is the time period for refreshing the settings from the database (if a database is used to share settings.</p></td>
</tr>
<tr class="even">
<td><p>maxcachesize</p></td>
<td><p>Applied to LSM, it is the maximum number of call states cached (in cache mode)</p></td>
</tr>
<tr class="odd">
<td><p>quality</p></td>
<td><p>It specifies whether to process QualityUpdate and InCallQuality messages (True) or not (False).</p></td>
</tr>
<tr class="even">
<td><p>signaling</p></td>
<td><p>It specifies whether to process &lt;Invite&gt;, &lt;Error&gt; and &lt;Bye&gt; messages.</p></td>
</tr>
<tr class="odd">
<td><p>configurationrefresh</p></td>
<td><p>Applied to LDL, it specifies the polling period for LDL to get updated configuration settings from LSM.</p></td>
</tr>
<tr class="even">
<td><p>maxretry</p></td>
<td><p>Applied to LSM and LDL, it specifies the maximum number of retransmission attempts before a message is dropped.</p></td>
</tr>
<tr class="odd">
<td><p>maxdelaylimit</p></td>
<td><p>Applied to LSM and LDL, it specifies the number of transmission failures before slowing down the transmission of call and quality messages.</p></td>
</tr>
<tr class="even">
<td><p>maxbackoff</p></td>
<td><p>Applied to LSM and LDL, it specifies the maximum number of seconds to delay message delivery upon transmission errors. The delay starts with 1 sec and increments with every failed delivery up to the maxbackoff number of seconds.</p></td>
</tr>
<tr class="odd">
<td><p>maxopen</p></td>
<td><p>Applied to LSM and LDL, it specifies the maximum number of messages sent concurrently.</p></td>
</tr>
<tr class="even">
<td><p>maxretrybeforefailover</p></td>
<td><p>Applied to LDL, it specifies the maximum number of message transmission failures before attempting to fail over to the secondary LSM in the Active/Standby configuration.</p></td>
</tr>
</tbody>
</table>


In addition to the configuration settings in the previous table, the configuration file also contains a list of threshold values used by LSM to determine the stream quality. These thresholds are used as default from the Lync Server QoEMetrics database to determine the call quality.

There are two threshold values for each metrics: Optimal and Acceptable. They define the three quality bands for each modality. For a call stream to have the Good quality, all the quality metrics must be below (i.e., better than) the Optimal level. A call is of poor quality when all the metrics are below the Acceptable threshold level and one or more of them are above the Optimal threshold. A call is bad when one or more of the metrics are above/worse than the Acceptable threshold.

You can modify these thresholds using the SDNManager.exe /p command or using the SDNManager.exe /q command. The /p command updates the value individually and the /q command downloads all of the thresholds from the Lync Server QoEMetrics database and have the values updated.

## Example

The following example shows some stream quality thresholds as configured in the SDNManager.exe.config.file:

```xml
    <add key="audio-DegradationAvgOptimal" value="0.6"/>
    <add key="audio-DegradationAvgAcceptable" value="1"/>
    <add key="audio-RoundTripOptimal" value="200"/>
    <add key="audio-RoundTripAcceptable" value="500"/>
    <add key="audio-PacketLossRateOptimal" value="0.02"/>
    <add key="audio-PacketLossRateAcceptable" value="0.05"/>
    <add key="audio-JitterInterArrivalOptimal" value="15"/>
    <add key="audio-JitterInterArrivalAcceptable" value="25"/>
    <add key="audio-RatioConcealedSamplesAvgOptimal" value="0.03"/>
    <add key="audio-RatioConcealedSamplesAvgAcceptable" value="0.07"/>
    <add key="audio-RatioStretchedSamplesAvgOptimal" value="1"/>
    <add key="audio-RatioStretchedSamplesAvgAcceptable" value="1"/>
    <add key="audio-RatioCompressedSamplesAvgOptimal" value="1"/>
    <add key="audio-RatioCompressedSamplesAvgAcceptable" value="1"/>
    <add key="audio-DeviceHalfDuplexAECEventRatioOptimal" value="0.1"/>
    <add key="audio-DeviceHalfDuplexAECEventRatioAcceptable" value="0.3"/>
    <add key="audio-DeviceRenderNotFunctioningEventRatioOptimal" value="0.1"/>
    <add key="audio-DeviceRenderNotFunctioningEventRatioAcceptable" value="0.3"/>
    <add key="audio-DeviceCaptureNotFunctioningEventRatioOptimal" value="0.1"/>
    <add key="audio-DeviceCaptureNotFunctioningEventRatioAcceptable" value="0.3"/>
    <add key="video-VideoPostFECPLROptimal" value="0.05"/>
    <add key="video-VideoPostFECPLRAcceptable" value="0.1"/>
    <add key="video-VideoLocalFrameLossPercentageAvgOptimal" value="5"/>
    <add key="video-VideoLocalFrameLossPercentageAvgAcceptable" value="10"/>
    <add key="video-RecvFrameRateAverageOptimal" value="12"/>
    <add key="video-RecvFrameRateAverageAcceptable" value="7"/>
    <add key="video-LowFrameRateCallPercentOptimal" value="5"/>
    <add key="video-LowFrameRateCallPercentAcceptable" value="10"/>
    <add key="video-LowResolutionCallPercentOptimal" value="5"/>
    <add key="video-LowResolutionCallPercentAcceptable" value="10"/>
    <add key="video-VideoPacketLossRateOptimal" value="0.05"/>
    <add key="video-VideoPacketLossRateAcceptable" value="0.1"/>
    <add key="video-VideoFrameRateAvgOptimal" value="12"/>
    <add key="video-VideoFrameRateAvgAcceptable" value="7"/>
    <add key="video-DynamicCapabilityPercentOptimal" value="5"/>
    <add key="video-DynamicCapabilityPercentAcceptable" value="10"/>
    <add key="applicationsharing-AppliedBandwidthLimitOptimal" value="1000000"/>
    <add key="applicationsharing-AppliedBandwidthLimitAcceptable" value="500000"/>
    <add key="applicationsharing-SpoiledTilePercentTotalOptimal" value="11"/>
    <add key="applicationsharing-SpoiledTilePercentTotalAcceptable" value="36"/>
    <add key="applicationsharing-JitterInterArrivalOptimal" value="50"/>
    <add key="applicationsharing-JitterInterArrivalAcceptable" value="100"/>
    <add key="applicationsharing-RelativeOneWayBurstDensityOptimal" value="1000"/>
    <add key="applicationsharing-RelativeOneWayBurstDensityAcceptable" value="2000"/>
    <add key="applicationsharing-RDPTileProcessingLatencyBurstDensityOptimal" value="100"/>
    <add key="applicationsharing-RDPTileProcessingLatencyBurstDensityAcceptable" value="200"/>
    <add key="applicationsharing-RelativeOneWayAverageOptimal" value="1"/>
    <add key="applicationsharing-RelativeOneWayAverageAcceptable" value="1.75"/>
    <add key="applicationsharing-RDPTileProcessingLatencyAverageOptimal" value="200"/>
    <add key="applicationsharing-RDPTileProcessingLatencyAverageAcceptable" value="400"/>
```

