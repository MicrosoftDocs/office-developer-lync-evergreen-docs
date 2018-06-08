---
title: Using the Lync SDN API 2.0
TOCTitle: Using the Lync SDN API 2.0
ms:assetid: 21e92d14-f20d-4bdb-9f2b-a01169abb401
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439294(v=office.15)
ms:contentKeyID: 57261030
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Using the Lync SDN API 2.0

**Applies to:** Lync 2013 | Lync Server 2013

When a Lync user calls another Lync user, a SIP dialog is established. SIP messages are exchanged between the client and Lync Server. Specific SIP messages contain data reflecting media-related information relevant for Lync SDN API 2.0 and are forwarded to the Lync SDN Manager (LSM). The LSM is then responsible for packaging the diagnostic data in XML and posting them to the preconfigured web service of one or more network management systems. The following figure presents a graphical depiction of this process.

**Simple Lync call handled by the Lync SDN API**

![Simple Lync call handled by Lync SDN API](images/Dn439294.simple_lync_sdn_call(Office.15).jpg "Simple Lync call handled by Lync SDN API")

## Using the Lync SDN API

The XML output from LSM consists of a collection of the \<LyncDiagnostics\> elements. Each element corresponds to a snapshot of a diagnostic state in a call. A \<LyncDiagnostics\> element contains one \<ConnectionInfo\> child element and zero or more of the \<Ended\>, \<Error\>, \<Invite\>, \<LRSInvite\>, \<QualityUpdate\>, \<RawSdp\>, \<RawRoot\>, \<Start\>, and \<Update\> elements. 

These child elements fall into two groups:

- The first one includes \<Ended\>, \<Error\>, \<Invite\>, \<LRSInvite\>, \<Start\>, \<Update\> and \<QualityUpdate\>. They contain data pertaining to the named message types. The first four elements of this group describe real-time data of a call and the last element describes the quality data of the call.

- The second group includes \<ConnectionInfo\>, \<RawSDP\> and they represent different parts of a message.

The \<ConnectionInfo\> element contains information pertaining to the connection between the endpoints involved in media streaming. The information can include a dialog Id (\<CallId\>) and conversation Id (\<ConversationId\>) among others. An example of the connection information is shown as follows:

```xml 
<LyncDiagnostics Version="A">
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
            <Codec Name="X-MSRTA/16000">
                <Low>62000</Low>
                <High>91000</High>
            </Codec>    
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


<QualityUpdate Type="audio">
    <From>……</From>
    <To>……</To>
    <Properties>
    …
    <PacketUtilization>1461</PacketUtilization>
    <JitterInterArrival Limit="25">11</JitterInterArrival>
    <JitterInterArrivalMax>15</JitterInterArrivalMax>
    <DegradationAvg Limit="1">0.06</DegradationAvg>
    <RatioConcealedSamplesAvg Limit="0.07">0.000999001</RatioConcealedSamplesAvg>
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

The diagnostics data is described by the properties of a \<QualityUpdate\> or \<Error\> child of \<LyncDiagnostics\>. The \<QualityUpdate\> properties are a direct reflection of the quality of experience metrics. The \<Error\> properties contain data extracted from the diagnostics headers of the SIP messages. 

An example output of \<QualityUpdate\> element is shown as follows:

```xml
<QualityUpdate Type="audio">
    <From>……</From>
    <To>……</To>
    <Properties>
    …
    <PacketUtilization>1461</PacketUtilization>
    <JitterInterArrival Limit="25">11</JitterInterArrival>
    <JitterInterArrivalMax>15</JitterInterArrivalMax>
    <DegradationAvg Limit="1">0.06</DegradationAvg>
    <RatioConcealedSamplesAvg Limit="0.07">0.000999001</RatioConcealedSamplesAvg>
    <RecvNoiseLevel>-51</RecvNoiseLevel>
    <RecvSignalLevel>-15</RecvSignalLevel>
    <SampleRate>16000</SampleRate>
    <BurstGapDuration>27720</BurstGapDuration>
    <DegradationMax>0.09</DegradationMax>
    <OverallMinNetworkMOS>4.15</OverallMinNetworkMOS>
    <OverallAvgNetworkMOS>4.19</OverallAvgNetworkMOS>
    …
    </Properties>
</QualityUpdate>
```

For more information about LSM-generated Lync SDN API 2.0 data, see [Lync SDN API 2.0 reference](lync-sdn-api-2-0-reference.md).

