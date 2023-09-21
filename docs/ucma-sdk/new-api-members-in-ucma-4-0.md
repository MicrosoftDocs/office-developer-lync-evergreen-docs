---
title: New API members in UCMA 4.0
TOCTitle: New API members in UCMA 4.0
ms:assetid: dd83d64d-21b2-4ddf-a9a7-1ee4df15dcb0
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465977(v=office.15)
ms:contentKeyID: 57102751
ms.date: 07/25/2014
mtps_version: v=office.15
---

# New API members in UCMA 4.0


**Applies to**: Lync 2013

 

The following tables list the API additions between Microsoft Unified Communications Managed API (UCMA) 3.0 and UCMA 4.0. The changes are grouped by namespace.

## Microsoft.Rtc.Collaboration namespace

The following members of the [Microsoft.Rtc.Collaboration](https://msdn.microsoft.com/library/hh384297\(v=office.15\)) namespace are new in UCMA 4.0.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Member name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ApplicationEndpoint class</p></td>
<td><p>SetProxyInformation(ConnectionContext) method</p></td>
</tr>
<tr class="even">
<td><p>ApplicationEndpointSettings class</p></td>
<td><p>ApplicationEndpointSettings(String, ConnectionContext) constructor</p></td>
</tr>
<tr class="odd">
<td><p>Call</p></td>
<td><p>UpdatePerformanceCountersOnStateChange(CallState, CallState, CallStateTransitionReason) method</p></td>
</tr>
<tr class="even">
<td><p>ClientPlatformSettings class</p></td>
<td><p>IpV6SupportDisabled property</p></td>
</tr>
<tr class="odd">
<td><p>ClientPlatformSettings class</p></td>
<td><p>OutboundConnectionConfiguration property</p></td>
</tr>
<tr class="even">
<td><p>CollaborationPlatform class</p></td>
<td><p>OutboundConnectionDefaultAddressFamilyHint property</p></td>
</tr>
<tr class="odd">
<td><p>ConferenceJoinOptions class</p></td>
<td><p>AdHocConferenceAutomaticLeaderAssignment property</p></td>
</tr>
<tr class="even">
<td><p>ConferenceJoinOptions class</p></td>
<td><p>AdHocConferenceAccessLevel property</p></td>
</tr>
<tr class="odd">
<td><p>ConferenceSession class</p></td>
<td><p>BeginJoin(MeetNowOptions, AsyncCallback, Object) method</p></td>
</tr>
<tr class="even">
<td><p>ConferencingCapabilities class</p></td>
<td><p>IsRecordingAllowedForExternalUsers property</p></td>
</tr>
<tr class="odd">
<td><p>ConferencingCapabilities class</p></td>
<td><p>IsRecordingAllowedForInternalUsers property</p></td>
</tr>
<tr class="even">
<td><p>Conversation class</p></td>
<td><p>GetRemoteParticipantsCount() method</p></td>
</tr>
<tr class="odd">
<td><p>ConversationParticipantProperties class</p></td>
<td><p>DisplayName property</p></td>
</tr>
<tr class="even">
<td><p>ConversationParticipantProperties class</p></td>
<td><p>OtherPhoneUri property</p></td>
</tr>
<tr class="odd">
<td><p>ConversationParticipantProperties class</p></td>
<td><p>PhoneUri property</p></td>
</tr>
<tr class="even">
<td><p>ConversationParticipantProperties class</p></td>
<td><p>DisplayNamePropertyName field</p></td>
</tr>
<tr class="odd">
<td><p>ConversationParticipantProperties class</p></td>
<td><p>OtherPhoneUriPropertyName field</p></td>
</tr>
<tr class="even">
<td><p>ConversationParticipantProperties class</p></td>
<td><p>PhoneUriPropertyName field</p></td>
</tr>
<tr class="odd">
<td><p>InstantMessagingCall class</p></td>
<td><p>UpdatePerformanceCountersOnStateChange(CallState, CallState, CallStateTransitionReason) method</p></td>
</tr>
<tr class="even">
<td><p>LocalEndpoint class</p></td>
<td><p>OutboundConnectionDefaultAddressFamilyHint property</p></td>
</tr>
<tr class="odd">
<td><p>LocalEndpointSettings class</p></td>
<td><p>LocalEndpointSettings(String, ConnectionContext) constructor</p></td>
</tr>
<tr class="even">
<td><p>LocalEndpointSettings class</p></td>
<td><p>AdditionalHeaders property</p></td>
</tr>
<tr class="odd">
<td><p>LocalEndpointSettings class</p></td>
<td><p>OutboundConnectionConfiguration property</p></td>
</tr>
<tr class="even">
<td><p>McuMediaChannel class</p></td>
<td><p>MediaSourceId property</p></td>
</tr>
<tr class="odd">
<td><p>MediaChannelEstablishmentData class</p></td>
<td><p>GetMediaEdgeResourceAllocationDiagnosticsReason() method</p></td>
</tr>
<tr class="even">
<td><p>MediaEdgeResourceAllocationDiagnosticsReason enumeration</p></td>
<td><p>New enumeration type</p></td>
</tr>
<tr class="odd">
<td><p>MediaType class</p></td>
<td><p>PanoramicVideo field</p></td>
</tr>
<tr class="even">
<td><p>MeetNowOptions class</p></td>
<td><p>New class</p></td>
</tr>
<tr class="odd">
<td><p>ParticipantAttendanceChangedEventArgs class</p></td>
<td><p>ParticipantCount property</p></td>
</tr>
<tr class="even">
<td><p>ProvisionedApplicationPlatformSettings class</p></td>
<td><p>CmsLoadBalancingDisabled property</p></td>
</tr>
<tr class="odd">
<td><p>ProvisionedApplicationPlatformSettings class</p></td>
<td><p>SecondaryListeningIPAddress property</p></td>
</tr>
<tr class="even">
<td><p>ServerPlatformSettings class</p></td>
<td><p>IpV6StackSupportDisabled property</p></td>
</tr>
<tr class="odd">
<td><p>ServerPlatformSettings class</p></td>
<td><p>SecondaryListeningIPAddress property</p></td>
</tr>
<tr class="even">
<td><p>ServerPlatformSettings class</p></td>
<td><p>OutboundConnectionConfiguration property</p></td>
</tr>
<tr class="odd">
<td><p>UserEndpoint class</p></td>
<td><p>AcpInformation property</p></td>
</tr>
<tr class="even">
<td><p>UserEndpointSettings class</p></td>
<td><p>UserEndpointSettings(String, ConnectionContext) constructor</p></td>
</tr>
<tr class="odd">
<td><p>UserEndpointSettings class</p></td>
<td><p>IsFederatedUser property</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.AudioVideo namespace

The following members of the [Microsoft.Rtc.Collaboration.AudioVideo](https://msdn.microsoft.com/library/hh365775\(v=office.15\)) namespace are new in UCMA 4.0.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Member name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AudioVideoMcuDialInOptions class</p></td>
<td><p>IsAudioMuted property</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuDialInOptions class</p></td>
<td><p>IsVideoMuted property</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuParticipantEndpointProperties class</p></td>
<td><p>IsAudioMuted property</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuParticipantEndpointProperties class</p></td>
<td><p>IsVideoMuted property</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>IsMultiViewVideoSupported property</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>AudioMuteAllMode property</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>AudioSelfUnmuteAssignment property</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>VideoSource property</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuSessionProperties class</p></td>
<td><p>SupportsMultiViewVideo property</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuSessionProperties class</p></td>
<td><p>AudioMuteAllMode property</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuSessionProperties class</p></td>
<td><p>AudioSelfUnmuteAssignment property</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuSessionProperties class</p></td>
<td><p>VideoSource property</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMediaType enumeration</p></td>
<td><p>New enumeration</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoSettings class</p></td>
<td><p>FipsCompliantMediaEncryptionRequired property</p></td>
</tr>
<tr class="odd">
<td><p>EnableMuteAllModeOptions class</p></td>
<td><p>MuteAllModeAssignment property</p></td>
</tr>
<tr class="even">
<td><p>MuteAllMode enumeration</p></td>
<td><p>EnabledForAttendees member added</p></td>
</tr>
<tr class="odd">
<td><p>MuteAllModeAssignment enumeration</p></td>
<td><p>New enumeration</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728862(v=office.15)">MuteAllModeAssignment</a>.</p></td>
</tr>
<tr class="even">
<td><p>MuteOptions class</p></td>
<td><p>MediaType property</p></td>
</tr>
<tr class="odd">
<td><p>UnmuteOptions class</p></td>
<td><p>MediaType property</p></td>
</tr>
<tr class="even">
<td><p>VideoSource class</p></td>
<td><p>New class</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728877(v=office.15)">VideoSource</a>.</p></td>
</tr>
<tr class="odd">
<td><p>VideoSourceMode enumeration</p></td>
<td><p>New enumeration</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728962(v=office.15)">VideoSourceMode</a>.</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.ComponentModel namespace

The following members of the [Microsoft.Rtc.Collaboration.ComponentModel](https://msdn.microsoft.com/library/hh384699\(v=office.15\)) namespace are new in UCMA 4.0.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Member name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>MediaProvider class</p></td>
<td><p>FipsCompliantMediaEncryptionRequired property</p></td>
</tr>
<tr class="even">
<td><p>NetworkStackHint enumeration</p></td>
<td><p>New enumeration</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728941(v=office.15)">NetworkStackHint</a>.</p></td>
</tr>
<tr class="odd">
<td><p>OfferAnswerContext class</p></td>
<td><p>OfferAnswerContext(CallDialogContext, MediaRelayToken, SdpOfferAnswerReason, NetworkStackHint) constructor</p></td>
</tr>
<tr class="even">
<td><p>OfferAnswerContext class</p></td>
<td><p>StackHint property</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.Presence namespace

The following members of the [Microsoft.Rtc.Collaboration.Presence](https://msdn.microsoft.com/library/hh350235\(v=office.15\)) namespace are new in UCMA 4.0.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Member name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ContactCard class</p></td>
<td><p>ContactCard(ContactCard) constructor</p></td>
</tr>
<tr class="even">
<td><p>LocationPolicyConfiguration class</p></td>
<td><p>EmergencyDialMask property</p></td>
</tr>
<tr class="odd">
<td><p>LocationPolicyConfiguration class</p></td>
<td><p>EmergencyDialString property</p></td>
</tr>
<tr class="even">
<td><p>LocationPolicyConfiguration class</p></td>
<td><p>Properties property</p></td>
</tr>
<tr class="odd">
<td><p>NormalizationRule class</p></td>
<td><p>ApplyIfInternalNumber property</p></td>
</tr>
<tr class="even">
<td><p>Note class</p></td>
<td><p>PublishTime property</p></td>
</tr>
<tr class="odd">
<td><p>PersistentChatConfiguration class</p></td>
<td><p>New class</p>
<p>See <strong>PersistentChatConfiguration</strong>.</p></td>
</tr>
<tr class="even">
<td><p>ProvisioningData class</p></td>
<td><p>PersistentChatConfiguration property</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Signaling namespace

The following members of the [Microsoft.Rtc.Signaling](https://msdn.microsoft.com/library/hh365949\(v=office.15\)) namespace are new in UCMA 4.0.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Member name</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AddressFamilyHint enumeration</p></td>
<td><p>New enumeration</p>
<p>Members: All, IpV4Only, IpV6Only</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728964(v=office.15)">AddressFamilyHint</a>.</p></td>
</tr>
<tr class="even">
<td><p>ConnectionContext class</p></td>
<td><p>AddressFamilyHint property</p></td>
</tr>
<tr class="odd">
<td><p>ConnectionContext class</p></td>
<td><p>Equals(ConnectionContext) method</p></td>
</tr>
<tr class="even">
<td><p>ConnectionContext class</p></td>
<td><p>Equals(Object obj) override method</p></td>
</tr>
<tr class="odd">
<td><p>ConnectionContext class</p></td>
<td><p>GetHashCode() override method</p></td>
</tr>
<tr class="even">
<td><p>ConnectionContext class</p></td>
<td><p>operator==(ConnectionContext, Object) method</p></td>
</tr>
<tr class="odd">
<td><p>ConnectionContext class</p></td>
<td><p>operator!=(ConnectionContext, Object ) method</p></td>
</tr>
<tr class="even">
<td><p>OutboundConnectionConfiguration class</p></td>
<td><p>New class</p>
<p>Member: DefaultAddressFamilyHint</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeConnectionManager class</p></td>
<td><p>OutboundConnectionDefaultAddressFamilyHint property</p></td>
</tr>
<tr class="even">
<td><p>RealTimeConnectionManager class</p></td>
<td><p>DisableIpV6Support() method</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeConnectionManager class</p></td>
<td><p>GetDestinationTuple(SipTransportType, String, Int32, AddressFamilyHint, String) method</p></td>
</tr>
<tr class="even">
<td><p>RealTimeConnectionManager class</p></td>
<td><p>DisableCrlChecks() method</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeConnectionManager class</p></td>
<td><p>GetLocalMachineFqdn() method</p></td>
</tr>
<tr class="even">
<td><p>RealTimeEndpoint class</p></td>
<td><p>OutboundConnectionDefaultAddressFamilyHint property</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeEndpoint class</p></td>
<td><p>EndTerminate(IAsyncResult )</p>
<p>No longer virtual.</p></td>
</tr>
<tr class="even">
<td><p>RealTimeEndpointSettings class</p></td>
<td><p>New class</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728811(v=office.15)">RealTimeEndpointSettings</a>.</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeServerConnectionManager class</p></td>
<td><p>BeginStartListening(Int32, AsyncCallback, Object) method</p></td>
</tr>
<tr class="even">
<td><p>RealTimeServerConnectionManager class</p></td>
<td><p>BeginStartListening(Int32, IEnumerable&lt;IPAddress&gt;, StartListeningOptions, AsyncCallback, Object) method</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeServerConnectionManager class</p></td>
<td><p>BeginStopListening(AsyncCallback, Object) method</p></td>
</tr>
<tr class="even">
<td><p>RealTimeServerConnectionManager class</p></td>
<td><p>DisableIpV6Support() method</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeServerConnectionManager class</p></td>
<td><p>EndStartListening(IAsyncResult) method</p></td>
</tr>
<tr class="even">
<td><p>RealTimeServerConnectionManager class</p></td>
<td><p>EndStopListening(IAsyncResult) method</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeServerTlsConnectionManager class</p></td>
<td><p>GetDestinationTuple(SipTransportType, String, Int32, AddressFamilyHint, String) method</p></td>
</tr>
<tr class="even">
<td><p>SdpGlobalDescription class</p></td>
<td><p>Bandwidths property</p></td>
</tr>
<tr class="odd">
<td><p>SdpMediaDescription class</p></td>
<td><p>Bandwidths property</p></td>
</tr>
<tr class="even">
<td><p>SipEndpoint class</p></td>
<td><p>SipEndpoint(String, RealTimeConnectionManager, SipEndpointSettings) constructor</p></td>
</tr>
<tr class="odd">
<td><p>SipEndpoint class</p></td>
<td><p>SipEndpoint(String, SipAuthenticationProtocols, SipTransportType, String) constructor</p>
<p>Parameter name change</p></td>
</tr>
<tr class="even">
<td><p>SipEndpoint class</p></td>
<td><p>SipEndpoint(String, SipAuthenticationProtocols, SipTransportType, String, Int32, Boolean, RealTimeConnectionManager, String) constructor</p>
<p>Parameter name change</p></td>
</tr>
<tr class="odd">
<td><p>SipEndpoint class</p></td>
<td><p>SipEndpoint(String, SipAuthenticationProtocols, SipTransportType, String, Int32, Boolean, RealTimeConnectionManager, String, IEnumerable&lt;SignalingHeader&gt;) constructor</p></td>
</tr>
<tr class="even">
<td><p>SipEndpointSettings class</p></td>
<td><p>New class</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728926(v=office.15)">SipEndpointSettings</a>.</p></td>
</tr>
<tr class="odd">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint(String) constructor</p>
<p>Parameter name change</p></td>
</tr>
<tr class="even">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint(String, RealTimeServerConnectionManager) constructor</p>
<p>Parameter name change</p></td>
</tr>
<tr class="odd">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint(String, RealTimeServerConnectionManager, SipPeerToPeerEndpointSettings) constructor</p></td>
</tr>
<tr class="even">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint(String, RealTimeServerConnectionManager, SipTransportType) constructor</p>
<p>Parameter name change</p></td>
</tr>
<tr class="odd">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint(String, RealTimeServerConnectionManager, SipTransportType, String) constructor</p>
<p>Parameter name change</p></td>
</tr>
<tr class="even">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint(String, RealTimeServerConnectionManager, SipTransportType, IEnumerable&lt;SignalingHeader&gt;) constructor</p></td>
</tr>
<tr class="odd">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint(String, RealTimeServerConnectionManager, SipTransportType, String, Int32, IEnumerable&lt;SignalingHeader&gt;) constructor</p></td>
</tr>
<tr class="even">
<td><p>SipPeerToPeerEndpointSettings class</p></td>
<td><p>New class</p>
<p>See <a href="https://msdn.microsoft.com/library/jj728825(v=office.15)">SipPeerToPeerEndpointSettings</a>.</p></td>
</tr>
<tr class="odd">
<td><p>StartListeningOptions class</p></td>
<td><p>New class</p></td>
</tr>
</tbody>
</table>

