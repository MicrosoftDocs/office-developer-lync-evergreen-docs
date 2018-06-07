---
title: Schema map (LyncSDNApiData)
TOCTitle: Schema map (LyncSDNApiData)
ms:assetid: 005e6b2a-dd90-a403-7b4b-8c90b78bbf72
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn455005(v=office.15)
ms:contentKeyID: 57260887
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Schema map (LyncSDNApiData)

This topic shows the schema definition for LyncSdnApi.Schema.A.xsd.


**Applies to:** Lync 2013 | Lync Server 2013

``` xml
<xs:schema elementFormDefault="qualified" attributeFormDefault="unqualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:complexType name="CodecType">
        <xs:sequence>
            <xs:element name="Bandwidth" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="MaxBandwidth" type="xs:string" minOccurs="0"></xs:element>
        </xs:sequence>
        <xs:attribute name="Name" type="xs:string" use="required" />
    </xs:complexType>
    <xs:complexType name="EndPointType">
        <xs:sequence>
            <xs:element name="Port" type="xs:unsignedInt" minOccurs="0"></xs:element>
            <xs:element name="Contact" type="xs:anyURI" minOccurs="0"></xs:element>
            <xs:element name="EPId" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="EPType" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="IP" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="URI" type="xs:anyURI"></xs:element>
            <xs:element name="Id" type="xs:string" minOccurs="0"></xs:element>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="InviteType">
        <xs:sequence>
            <xs:element name="Caller" type="EndPointType"></xs:element>
            <xs:element name="Callee" type="EndPointType"></xs:element>
        </xs:sequence>
    </xs:complexType>
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
    <xs:complexType name="QualityEndPointType">
        <xs:sequence>
            <xs:element name="URI" type="xs:anyURI"></xs:element>
            <xs:element name="Relay" minOccurs="0"></xs:element>
            <xs:element name="IP" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="Contact" type="xs:anyURI" minOccurs="0"></xs:element>
            <xs:element name="EPId" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="BSSID" minOccurs="0"></xs:element>
            <xs:element name="VPN" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="Inside" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="Id" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="EPType" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="RelayPort" minOccurs="0"></xs:element>
            <xs:element name="Port" type="xs:unsignedInt" minOccurs="0"></xs:element>
            <xs:element name="Connection" type="xs:string" minOccurs="0"></xs:element>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="StartOrUpdateType">
        <xs:sequence>
            <xs:element name="EndPoint" type="EndPointType" minOccurs="0" maxOccurs="2"></xs:element>
            <xs:element name="From" type="EndPointType" minOccurs="0"></xs:element>
            <xs:element name="To" type="EndPointType" minOccurs="0"></xs:element>
            <xs:element name="Properties" minOccurs="0">
                <xs:complexType>
                    <xs:sequence>
                        <xs:element name="Protocol" type="xs:string"></xs:element>
                        <xs:element name="Codec" type="CodecType" maxOccurs="unbounded"></xs:element>
                    </xs:sequence>
                </xs:complexType>
            </xs:element>
        </xs:sequence>
        <xs:attribute name="Type" type="xs:string" use="required" />
    </xs:complexType>
</xs:schema>
```

