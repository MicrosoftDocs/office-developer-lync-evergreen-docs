---
title: LSM command-line executable input and output example
TOCTitle: LSM command-line executable input and output example
ms:assetid: 7a7c63ad-4f64-46a1-9e2c-2dd51f261aeb
ms:mtpsurl: https://msdn.microsoft.com/library/Dn802610(v=office.15)
ms:contentKeyID: 62952710
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# LSM command-line executable input and output example

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

The following code sample shows the input and output resulting from running the LSM console application.

## Sample of input and output of the LSM console application

```xml
C:\Program Files\Microsoft Lync Server\Microsoft Lync SDN Manager>SDNManager.exe /d
Response code: SUCCESS Detail: Logical Version 0
<Configuration Version="1.0" culture="en-US">
  <parameter key="alternativeuri"></parameter>
  <parameter key="applicationsharing-AppliedBandwidthLimitAcceptable">500000</parameter>
  <parameter key="applicationsharing-AppliedBandwidthLimitOptimal">1000000</parameter>
  <parameter key="applicationsharing-JitterInterArrivalAcceptable">100</parameter>
  <parameter key="applicationsharing-JitterInterArrivalOptimal">50</parameter>
  <parameter key="applicationsharing-RDPTileProcessingLatencyAverageAcceptable">400</parameter>
  <parameter key="applicationsharing-RDPTileProcessingLatencyAverageOptimal">200</parameter>
  <parameter key="applicationsharing-RDPTileProcessingLatencyBurstDensityAcceptable">200</parameter>
  <parameter key="applicationsharing-RDPTileProcessingLatencyBurstDensityOptimal">100</parameter>
  <parameter key="applicationsharing-RelativeOneWayAverageAcceptable">1.75</parameter>
  <parameter key="applicationsharing-RelativeOneWayAverageOptimal">1</parameter>
  <parameter key="applicationsharing-RelativeOneWayBurstDensityAcceptable">2000</parameter>
  <parameter key="applicationsharing-RelativeOneWayBurstDensityOptimal">1000</parameter>
  <parameter key="applicationsharing-SpoiledTilePercentTotalAcceptable">36</parameter>
  <parameter key="applicationsharing-SpoiledTilePercentTotalOptimal">11</parameter>
  <parameter key="audio-DegradationAvgAcceptable">1</parameter>
  <parameter key="audio-DegradationAvgOptimal">0.6</parameter>
  <parameter key="audio-DeviceCaptureNotFunctioningEventRatioAcceptable">0.3</parameter>
  <parameter key="audio-DeviceCaptureNotFunctioningEventRatioOptimal">0.1</parameter>
  <parameter key="audio-DeviceHalfDuplexAECEventRatioAcceptable">0.3</parameter>
  <parameter key="audio-DeviceHalfDuplexAECEventRatioOptimal">0.1</parameter>
  <parameter key="audio-DeviceRenderNotFunctioningEventRatioAcceptable">0.3</parameter>
  <parameter key="audio-DeviceRenderNotFunctioningEventRatioOptimal">0.1</parameter>
  <parameter key="audio-JitterInterArrivalAcceptable">25</parameter>
  <parameter key="audio-JitterInterArrivalOptimal">15</parameter>
  <parameter key="audio-PacketLossRateAcceptable">0.05</parameter>
  <parameter key="audio-PacketLossRateOptimal">0.02</parameter>
  <parameter key="audio-RatioCompressedSamplesAvgAcceptable">1</parameter>
  <parameter key="audio-RatioCompressedSamplesAvgOptimal">1</parameter>
  <parameter key="audio-RatioConcealedSamplesAvgAcceptable">0.07</parameter>
  <parameter key="audio-RatioConcealedSamplesAvgOptimal">0.03</parameter>
  <parameter key="audio-RatioStretchedSamplesAvgAcceptable">1</parameter>
  <parameter key="audio-RatioStretchedSamplesAvgOptimal">1</parameter>
  <parameter key="audio-RoundTripAcceptable">500</parameter>
  <parameter key="audio-RoundTripOptimal">200</parameter>
  <parameter key="calltimeout">1.00:00:00</parameter>
  <parameter key="checkdns">False</parameter>
  <parameter key="clientcertificateid"></parameter>
  <parameter key="configurationrefresh">00:00:50</parameter>
  <parameter key="endedtimeout">00:00:15</parameter>
  <parameter key="hidepii">True</parameter>
  <parameter key="invitetimeout">00:03:00</parameter>
  <parameter key="maxbackoff">30</parameter>
  <parameter key="maxcachesize">1000</parameter>
  <parameter key="maxdelaylimit">25</parameter>
  <parameter key="maxopen">100</parameter>
  <parameter key="maxretry">100</parameter>
  <parameter key="maxretrybeforefailover">20</parameter>
  <parameter key="mode">Cache</parameter>
  <parameter key="qoetimeout">00:00:05</parameter>
  <parameter key="quality">True</parameter>
  <parameter key="sendrawsdp">False</parameter>
  <parameter key="settingsrefresh">00:01:00</parameter>
  <parameter key="signaling">False</parameter>
  <parameter key="submitqueuelen">100</parameter>
  <parameter key="submituri">10.12.12.0/24,10.12.13.0/24=http://networkcontroller1.contoso.com/;10.12.14.0/24,southbranc
h.contoso.com=[C54CF0D5AC4ED742E3B6B96C76774EC6F863F4D5]https://networkcontroller2.contoso.com/</parameter>
  <parameter key="timeouthandlerperiod">00:00:01</parameter>
  <parameter key="video-DynamicCapabilityPercentAcceptable">10</parameter>
  <parameter key="video-DynamicCapabilityPercentOptimal">5</parameter>
  <parameter key="video-LowFrameRateCallPercentAcceptable">10</parameter>
  <parameter key="video-LowFrameRateCallPercentOptimal">5</parameter>
  <parameter key="video-LowResolutionCallPercentAcceptable">10</parameter>
  <parameter key="video-LowResolutionCallPercentOptimal">5</parameter>
  <parameter key="video-RecvFrameRateAverageAcceptable">7</parameter>
  <parameter key="video-RecvFrameRateAverageOptimal">12</parameter>
  <parameter key="video-VideoFrameRateAvgAcceptable">7</parameter>
  <parameter key="video-VideoFrameRateAvgOptimal">12</parameter>
  <parameter key="video-VideoLocalFrameLossPercentageAvgAcceptable">10</parameter>
  <parameter key="video-VideoLocalFrameLossPercentageAvgOptimal">5</parameter>
  <parameter key="video-VideoPacketLossRateAcceptable">0.1</parameter>
  <parameter key="video-VideoPacketLossRateOptimal">0.05</parameter>
  <parameter key="video-VideoPostFECPLRAcceptable">0.1</parameter>
  <parameter key="video-VideoPostFECPLROptimal">0.05</parameter>
</Configuration>
```

