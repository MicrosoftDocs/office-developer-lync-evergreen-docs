---
title: Using the Lync SDN Interface 2.1
TOCTitle: Using the Lync SDN Interface 2.1
ms:assetid: 542be3ea-3144-4e21-b320-c479cb0397bd
ms:mtpsurl: https://msdn.microsoft.com/library/Dn785190(v=office.15)
ms:contentKeyID: 62952674
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Using the Lync SDN Interface 2.1

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

Lync service providers and customers can use the Lync SDN Interface to obtain call and quality data about the states of audio and video streams across the Lync network. The Lync SDN Interface relies on the Lync Dialog Listener component (LDL) to capture call and quality data and then dispatches the captured data to Lync SDN Manager (LSM) to process the raw data. The processed and aggregated data is then sent to network controllers, which can in turn correlate the data with their own observations from the network, readjust policies, or reallocate network resources to improve the service quality.

For example, a Lync service provider or customer finds that conference calls initiated during a certain timeframe in a given geographical region experience more frequent dropped calls. To find out what happens, they can install and configure the Lync SDN Interface in their Lync topology and connect it with a Lync SDN-aware network controller. The combined information from Lync clients and the network manager will enable the service provider or customer to resolve issues within the Lync deployment by, for example, identifying a bottleneck in a segment of their network during specific Lync-related load patterns. As a result, they can adjust the network resources accordingly. In other cases, the analysis might result in a need to add more server resources or allocate additional PSTN ports/sessions to reduce the incidence of dropped calls.

## Parse the Lync call and quality data

The XML output from LSM consists of a set of messages that have \<LyncDiagnostics\> elements. Each message corresponds to a snapshot of the data stream in a call. A \<LyncDiagnostics\> element contains one \<ConnectionInfo\> child element and one or more of the \<Invite\>, \<Start\>, \<Error\>, \<InCallQuality\>, \<Ended\>, \<Bye\> and \<QualityUpdate\> elements. Optionally, a \<RawSDP\> element might be present to contain the SDP content of the SIP message that triggered this SDN message. These child elements fall into the following groups:

1.  The first group, including \<ConnectionInfo\>, \<RawSDP\>, describe attributes of the overall state of the call and connection between the endpoints involving the media streams. The group can include a dialog Id (\<CallId\>) and conversation Id (\<ConversationId\>) among others, which can be used to correlate this call with other calls.

2.  The second group includes \<Invite\>, \<Error\>, and \<Bye\>, which are used to forward signaling events about the overall call. These elements are optional.

3.  The third group includes \<Start\>, \<Update\>, and \<Ended\>. They describe the individual states of the call streams in real time.

4.  The last group, including \<InCallQuality\> and \<QualityUpdate\>, provides insight into the quality of individual streams of the call. These elements are optional.

The following is an example of a Lync SDN Interface message.

```xml
    <LyncDiagnostics Version="C">
        <ConnectionInfo>
              …
        </ConnectionInfo>
        <Start Type="audio">
            <From>
              …
            </From>
            <To>
              …
            </To>
            <Properties>
                <Protocol>UDP</Protocol>
                … 
            </Properties>
        </Start>
        <Start Type="audio">
           …
        </Start>
        <Start Type="video">
           …
        </Start>
        …
    </LyncDiagnostics>
```

<br/>

The **From** and **To** sections contain information related to the endpoints with the IP and Ports being most relevant for identifying the data streams (RTP). The RTCP streams use the same IP and the next port number (+1). A quality update section provides numerous properties related to the end points and streams, as shown in the following code example.

```xml
<QualityUpdate Type="audio">
    <From>……</From>
    <To>……</To>
    <Properties>
    …
    <PacketUtilization>1461</PacketUtilization>
    <JitterInterArrival>11</JitterInterArrival>
    <JitterInterArrivalMax>15</JitterInterArrivalMax>
    <DegradationAvg>0.06</DegradationAvg>
    <RatioConcealedSamplesAvg>0.000999001</RatioConcealedSamplesAvg>
    <RecvNoiseLevel>-51</RecvNoiseLevel>
    <RecvSignalLevel>-15</RecvSignalLevel>
    <BurstGapDuration>27720</BurstGapDuration>
    <DegradationMax>0.09</DegradationMax>
    <OverallMinNetworkMOS>4.15</OverallMinNetworkMOS>
    <OverallAvgNetworkMOS>4.19</OverallAvgNetworkMOS>
    …
    </Properties>
</QualityUpdate>
```

For more information about LSM-generated Lync SDN Interface 2.1.1 data, see [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md).

## See also

- [Understanding Lync SDN Interface 2.1.1](understanding-lync-sdn-interface-2-1-1.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

