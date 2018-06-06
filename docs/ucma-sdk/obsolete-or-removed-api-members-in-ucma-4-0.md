---
title: Obsolete or removed API members in UCMA 4.0
TOCTitle: Obsolete or removed API members in UCMA 4.0
ms:assetid: 49725ca6-fa2b-4986-8ae3-2c66417a8301
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465992(v=office.15)
ms:contentKeyID: 57102830
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Obsolete or removed API members in UCMA 4.0


_**Applies to:** Lync 2013_

**In this article**  
Microsoft.Rtc.Collaboration namespace  
Microsoft.Rtc.Collaboration.AudioVideo namespace  
Microsoft.Rtc.Collaboration.ComponentModel namespace  
Microsoft.Rtc.Collaboration.ConferenceManagement namespace  
Microsoft.Rtc.Collaboration.ContactsGroups namespace  
Microsoft.Rtc.Collaboration.Presence namespace  
Microsoft.Rtc.Signaling namespace  

The following tables list the API members that are obsolete or have been removed between Microsoft Unified Communications Managed API (UCMA) 3.0 and UCMA 4.0. The changes are grouped by namespace.

## Microsoft.Rtc.Collaboration namespace

The following members of the [Microsoft.Rtc.Collaboration](https://msdn.microsoft.com/en-us/library/hh384297\(v=office.15\)) namespace are obsolete or removed in UCMA 4.0.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Obsolete or removed member</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ApplicationEndpoint class</p></td>
<td><p>SetProxyInformation(String, Int32) method</p></td>
<td><p>Obsolete. User SetProxyInformation(ConnectionContext) instead.</p></td>
</tr>
<tr class="even">
<td><p>ApplicationEndpointSettings class</p></td>
<td><p>ProvisioningDataAutoRefreshDisabled property</p></td>
<td><p>Removed</p></td>
</tr>
<tr class="odd">
<td><p>Call class</p></td>
<td><p>Forward(String) method</p></td>
<td><p>Now internal</p></td>
</tr>
<tr class="even">
<td><p>Call class</p></td>
<td><p>Forward(String, CallForwardOptions) method</p></td>
<td><p>Now internal</p></td>
</tr>
<tr class="odd">
<td><p>ClientPlatformSettings class</p></td>
<td><p>AddressFamiliesEnabled property</p></td>
<td><p>Use OutboundConnectionConfiguration.DefaultAddressFamilyHint instead.</p></td>
</tr>
<tr class="even">
<td><p>Conference class</p></td>
<td><p>AdmissionPolicy property</p></td>
<td><p>Use Conference.ConferenceAccessLevel instead.</p></td>
</tr>
<tr class="odd">
<td><p>ConferenceFailureException class</p></td>
<td><p>Diagnostics property</p></td>
<td><p>Removed</p></td>
</tr>
<tr class="even">
<td><p>ConferenceInvitationState enumeration</p></td>
<td><p>Outgoing member</p></td>
<td><p>Removed</p></td>
</tr>
<tr class="odd">
<td><p>ConferenceSession class</p></td>
<td><p>IsLocked property</p></td>
<td><p>This property will be removed from future versions. Use the AccessLevel property instead.</p></td>
</tr>
<tr class="even">
<td><p>ConferenceSessionProperties class</p></td>
<td><p>IsLocked property</p></td>
<td><p>Use the AccessLevel property instead.</p></td>
</tr>
<tr class="odd">
<td><p>InstantMessagingFlow class</p></td>
<td><p>BeginSendMessage(ContentType, Byte[], AsyncCallback, Object) method</p></td>
<td><p>Removed. Use BeginSendInstantMessage instead.</p></td>
</tr>
<tr class="even">
<td><p>InstantMessagingFlow class</p></td>
<td><p>BeginSendMessage(String, AsyncCallback, Object) method</p></td>
<td><p>Removed. Use BeginSendInstantMessage instead.</p></td>
</tr>
<tr class="odd">
<td><p>InstantMessagingFlow class</p></td>
<td><p>EndSendMessage(IAsyncResult) method</p></td>
<td><p>Removed. Use EndSendInstantMessage instead.</p></td>
</tr>
<tr class="even">
<td><p>LocalEndpoint class</p></td>
<td><p>AddressFamiliesEnabled property</p></td>
<td><p>Use OutboundConnectionDefaultAddressFamilyHint instead.</p></td>
</tr>
<tr class="odd">
<td><p>LocalEndpoint class</p></td>
<td><p>RemotePresence property</p></td>
<td><p>Use the RemotePresenceView class (in the Microsoft.Rtc.Collaboration.Presence namespace) or PresenceServices property instead.</p></td>
</tr>
<tr class="even">
<td><p>LocalEndpoint class</p></td>
<td><p>ProvisioningDataAutoRefreshDisabled property</p></td>
<td><p>Removed. If data provisioning is enabled it will be refreshed automatically.</p></td>
</tr>
<tr class="odd">
<td><p>LocalEndpointSettings class</p></td>
<td><p>AddressFamiliesEnabled property</p></td>
<td><p>Use OutboundConnectionConfiguration.DefaultAddressFamilyHint instead.</p></td>
</tr>
<tr class="even">
<td><p>LocalEndpointSettings class</p></td>
<td><p>LocalEndpointSettings(String, String, Int32) constructor</p></td>
<td><p>Removed</p></td>
</tr>
<tr class="odd">
<td><p>ServerPlatformSettings class</p></td>
<td><p>AddressFamiliesEnabled property</p></td>
<td><p>Use OutboundConnectionConfiguration.DefaultAddressFamilyHint instead.</p></td>
</tr>
<tr class="even">
<td><p>ServerPlatformSettings class</p></td>
<td><p>AllowedDomains property</p></td>
<td><p>Use TrustedDomains instead.</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.AudioVideo namespace

The following members of the [Microsoft.Rtc.Collaboration.AudioVideo](https://msdn.microsoft.com/en-us/library/hh365775\(v=office.15\)) namespace are obsolete or removed in UCMA 4.0.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Obsolete or removed member</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AudioVideoMcuParticipantEndpointProperties class</p></td>
<td><p>IsMuted property</p></td>
<td><p>Obsolete. Use IsAudioMuted or IsVideoMuted.</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>MuteAllMode property</p></td>
<td><p>Obsolete. Use AudioMuteAllMode.</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>SelfUnmuteAssignment property</p></td>
<td><p>Obsolete. Use AudioSelfMuteAllMode.</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>BeginEnableAnnouncements(IEnumerable&lt;ParticipantEndpoint&gt;, AsyncCallback, Object) method</p></td>
<td><p>Removed. Use the methods that are available through the AudioVideoCall.AudioVideoMcuRouting property.</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuSession class</p></td>
<td><p>EndEnableAnnouncements(IAsyncResult) method</p></td>
<td><p>Removed. Use the methods that are available through the AudioVideoCall.AudioVideoMcuRouting property.</p></td>
</tr>
<tr class="even">
<td><p>AudioVideoMcuSessionProperties class</p></td>
<td><p>MuteAllMode property</p></td>
<td><p>Obsolete. Use the AudioMuteAllMode property.</p></td>
</tr>
<tr class="odd">
<td><p>AudioVideoMcuSessionProperties class</p></td>
<td><p>SelfUnmuteAssignment property</p></td>
<td><p>Obsolete. Use the AudioSelfUnmuteAssignment property.</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.ComponentModel namespace

The following members of the [Microsoft.Rtc.Collaboration.ComponentModel](https://msdn.microsoft.com/en-us/library/hh384699\(v=office.15\)) namespace are obsolete or removed in UCMA 4.0.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Obsolete or removed member</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>InviteReceivedEventArgs class</p></td>
<td><p>IsForked property</p></td>
<td><p>Removed. Use the IsImmediateAutoAcceptNeeded property or the IsAutoAcceptEventNeeded event exposed in classes derived from Call and ConferenceInvitation to determine whether auto-acceptance is needed.</p></td>
</tr>
<tr class="even">
<td><p>MediaProvider class</p></td>
<td><p>HandleMessage(CallDialogContext, MessageReceivedEventArgs) method</p></td>
<td><p>Removed. Use the HandleMessage(CallDialogContext, CallMessageReceivedEventArgs) method.</p></td>
</tr>
<tr class="odd">
<td><p>MediaProvider class</p></td>
<td><p>Voice802_1p property</p></td>
<td><p>Removed.</p></td>
</tr>
<tr class="even">
<td><p>OfferAnswerContext class</p></td>
<td><p>OfferAnswerContext(CallDialogContext, MediaRelayToken, SdpOfferAnswerReason) constructor</p></td>
<td><p>Removed. Use the OfferAnswerContext(CallDialogContext, MediaRelayToken, SdpOfferAnswerReason, NetworkStackHint) constructor.</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.ConferenceManagement namespace

The following members of the [Microsoft.Rtc.Collaboration.ConferenceManagement](https://msdn.microsoft.com/en-us/library/hh381081\(v=office.15\)) namespace are obsolete or removed in UCMA 4.0.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Obsolete or removed member</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ConferenceScheduleInformation</p></td>
<td><p>AdmissionPolicy property</p></td>
<td><p>Removed. Use ConferenceScheduleInformation.AccessLevel. </p></td>
</tr>
<tr class="even">
<td><p>ConferenceSummary</p></td>
<td><p>AdmissionPolicy property</p></td>
<td><p>Removed. Use ConferenceSummary.AccessLevel. </p></td>
</tr>
<tr class="odd">
<td><p>PhoneAccessNumber class</p></td>
<td><p>ConferenceAdmissionPolicy enumeration</p></td>
<td><p>Removed</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.ContactsGroups namespace

The following members of the [Microsoft.Rtc.Collaboration.ContactsGroups](https://msdn.microsoft.com/en-us/library/hh381542\(v=office.15\)) namespace are obsolete or removed in UCMA 4.0.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Obsolete or removed member</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Contact class</p></td>
<td><p>IsSubscribed property</p></td>
<td><p>Removed</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Collaboration.Presence namespace

The following members of the [Microsoft.Rtc.Collaboration.Presence](https://msdn.microsoft.com/en-us/library/hh350235\(v=office.15\)) namespace are obsolete or removed in UCMA 4.0.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Obsolete or removed member</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LocationProfilesConfiguration class</p></td>
<td><p>Entire class</p></td>
<td><p>Obsolete. Use the LocationProfileConfiguration property on the ProvisioningData class.</p></td>
</tr>
<tr class="even">
<td><p>NormalizationRulesInstance class</p></td>
<td><p>Entire class</p></td>
<td><p>Obsolete</p></td>
</tr>
<tr class="odd">
<td><p>ProvisioningData class</p></td>
<td><p>Xml property</p></td>
<td><p>Removed. Access the individual provisioning groups instead of the full XML blob.</p></td>
</tr>
</tbody>
</table>


## Microsoft.Rtc.Signaling namespace

The following members of the [Microsoft.Rtc.Signaling](https://msdn.microsoft.com/en-us/library/hh365949\(v=office.15\)) namespace are obsolete or removed in UCMA 4.0.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Obsolete or removed member</p></th>
<th><p>Comments</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Participant class</p></td>
<td><p>SyncRoot property</p></td>
<td><p>Removed</p></td>
</tr>
<tr class="even">
<td><p>RealTimeConnectionManager class</p></td>
<td><p>AddressFamiliesEnabled property</p></td>
<td><p>Use OutboundConnectionDefaultAddressFamilyHint instead.</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeConnectionManager class</p></td>
<td><p>GetDestinationTuple(SipTransportType, String, Int32, String) method</p></td>
<td><p>Removed</p></td>
</tr>
<tr class="even">
<td><p>RealTimeEndpoint class</p></td>
<td><p>RealTimeEndpoint(String, SipTransportType, String, Boolean, Int32, String, Boolean, Boolean) constructor</p></td>
<td><p>Removed. Use RealTimeEndpoint(String, RealTimeConnectionManager, RealTimeEndpointSettings). </p></td>
</tr>
<tr class="odd">
<td><p>RealTimeEndpoint class</p></td>
<td><p>RealTimeEndpoint(String, String, Boolean) constructor</p></td>
<td><p>Removed. Use RealTimeEndpoint(String, RealTimeConnectionManager, RealTimeEndpointSettings). </p></td>
</tr>
<tr class="even">
<td><p>RealTimeEndpoint class</p></td>
<td><p>RealTimeEndpoint(String, String) constructor</p></td>
<td><p>Removed. Use RealTimeEndpoint(String, RealTimeConnectionManager, RealTimeEndpointSettings). </p></td>
</tr>
<tr class="odd">
<td><p>RealTimeEndpoint class</p></td>
<td><p>DisableReferredBySigning property</p></td>
<td><p>Removed. Use CallEstablishOptions.Transferor property to sign Referred-By headers in INVITE requests.</p></td>
</tr>
<tr class="even">
<td><p>RealTimeEndpoint class</p></td>
<td><p>IsDialogResiliencySupported supported</p></td>
<td><p>Removed. Use RealTimeEndpoint.ApplyRouteSetRecoverySettings() or RealTimeEndpoint.RouteSetRecoveryMode instead.</p></td>
</tr>
<tr class="odd">
<td><p>RealTimeEndpoint class</p></td>
<td><p>ProcessNotifyReceived(Object, TransactionCreatedEventArgs) method</p></td>
<td><p>Removed.</p></td>
</tr>
<tr class="even">
<td><p>RealTimeEndpoint class</p></td>
<td><p>SyncRoot property</p></td>
<td><p>Removed. </p></td>
</tr>
<tr class="odd">
<td><p>RealTimeServerConnectionManager class</p></td>
<td><p>ListeningPort property</p></td>
<td><p>Property is now read-only.</p></td>
</tr>
<tr class="even">
<td><p>RealTimeServerTlsConnectionManager class</p></td>
<td><p>GetDestinationTuple(SipTransportType, String, Int32, String) method</p></td>
<td><p>Removed. Use GetDestinationTuple(SipTransportType, String, Int32, AddressFamilyHint, String)</p></td>
</tr>
<tr class="odd">
<td><p>RegistrationStateChangedEventArgs class</p></td>
<td><p>ResponseData property</p></td>
<td><p>Removed. Use MessageData instead, casting it to the correct type.</p></td>
</tr>
<tr class="even">
<td><p>SignalingSession class</p></td>
<td><p>SignalingSession(RealTimeEndpoint, String, String, RealTimeAddress) constructor</p></td>
<td><p>Removed. Use SignalingSession(RealTimeEndpoint, RealTimeEndpointSettings) instead.</p></td>
</tr>
<tr class="odd">
<td><p>SignalingSession class</p></td>
<td><p>SignalingSession(RealTimeEndpoint, String, String, RealTimeAddress, String) constructor</p></td>
<td><p>Removed. Use SignalingSession(RealTimeEndpoint, RealTimeEndpointSettings) instead.</p></td>
</tr>
<tr class="even">
<td><p>SignalingSession class</p></td>
<td><p>BeginSetConnection(String, Int32, SipTransportType, AsyncCallback, Object) method</p></td>
<td><p>Removed. Use the ConnectionContext property of the SignalingSessionEstablishOptions instead.</p></td>
</tr>
<tr class="odd">
<td><p>SignalingSession class</p></td>
<td><p>EndSetConnection(IAsyncResult) method</p></td>
<td><p>Removed. Use the ConnectionContext property of the SignalingSessionEstablishOptions instead.</p></td>
</tr>
<tr class="even">
<td><p>SignalingSession class</p></td>
<td><p>Grid property</p></td>
<td><p>Removed. There is no alternative as the functionality is no longer supported.</p></td>
</tr>
<tr class="odd">
<td><p>SignalingSession class</p></td>
<td><p>SetConnection(String, Int32, SipTransportType) method</p></td>
<td><p>Removed. Use the ConnectionContext property of the SignalingSessionEstablishOptions instead.</p></td>
</tr>
<tr class="even">
<td><p>SipPeerToPeerEndpoint class</p></td>
<td><p>SipPeerToPeerEndpoint() constructor</p></td>
<td><p>Obsolete. Create an ownerUri and ConnectionManager and use another constructor overload.</p></td>
</tr>
<tr class="odd">
<td><p>SipUriParser class</p></td>
<td><p>GridUriParameter property</p></td>
<td><p>Removed. There is no alternative as the functionality is no longer supported.</p></td>
</tr>
</tbody>
</table>

