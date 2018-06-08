---
title: Object model expansion
TOCTitle: Object model expansion
ms:assetid: f380d9ca-4030-4b85-8a16-1b488bb97db7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933254(v=office.15)
ms:contentKeyID: 50877400
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Object model expansion

![What's new topic](images/JJ937254.mod_icon_whatsnew_long(Office.15).png "What's new topic")

The Microsoft Lync 2013 API includes new types to enable the features described in [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md).



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Persistent Chat API<br />
Resource sharing API<br />
Meeting content API<br />
Other new types<br />
Changed types<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## New API types

The following sections list the API types that are new to Microsoft Lync 2013 SDK and support the new features.

### Persistent Chat API

The following table lists the new API types that support Persistent Chat. For more information about Persistent Chat in the Lync 2013 API, see [Get started with Persistent Chat](get-started-with-persistent-chat.md).

Persistent Chat types

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276739(v=office.15)">FollowedRoomsChangedEventArgs</a></p></td>
<td><p>The state of the event raised when the membership of collection of user-followed chat rooms has changed.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266481(v=office.15)">JoinRoomFailException</a></p></td>
<td><p>Encapsulates the state of the exception raised when a user fails to join a chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277941(v=office.15)">JoinRoomUnauthorizedException</a></p></td>
<td><p>Encapsulates the state of the exception raised when a user attempts to join a chat room that he or she is not authorized to join.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266467(v=office.15)">Room</a></p></td>
<td><p>Encapsulates a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276163(v=office.15)">RoomJoinState</a></p></td>
<td><p>Enumerates the Persistent Chat room joining operation states.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277183(v=office.15)">RoomJoinStateChangedEventArgs</a></p></td>
<td><p>Encapsulates the state of the RoomJoinStateChanged event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277050(v=office.15)">RoomManager</a></p></td>
<td><p>Persistent Chat room manager that provides room query functionality.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj274480(v=office.15)">RoomManagerState</a></p></td>
<td><p>Enumerates the room manager state.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277266(v=office.15)">RoomManagerStateChangedEventArgs</a></p></td>
<td><p>Exposes the new state of a room manager.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276207(v=office.15)">RoomMessage</a></p></td>
<td><p>Defines a room message sent to a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275495(v=office.15)">RoomMessageDictionary</a></p></td>
<td><p>A key/value pairing of a message format enumerator and actual message text.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277332(v=office.15)">RoomMessageEventArgs</a></p></td>
<td><p>Encapsulates the state of the event raised when a local user sends a message to a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294006(v=office.15)">RoomMessagesEventArgs</a></p></td>
<td><p>Encapsulates the state of the MessagesReceived event and contains a collection of the messages sent to a room.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275314(v=office.15)">RoomMessageFilteringAction</a></p></td>
<td><p>Enumerates the action taken by a chat room add-in for a room message.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277588(v=office.15)">RoomMessageFormat</a></p></td>
<td><p>Enumerates the possible format types of a room message.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj265996(v=office.15)">RoomMessageType</a></p></td>
<td><p>Enumerates the possible types of a room message.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266993(v=office.15)">RoomParticipantsEventArgs</a></p></td>
<td><p>Encapsulates the state of the ParticpiantsAdded and ParticipantsRemoved events and contains a collection of the room participants added or removed.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293288(v=office.15)">RoomProperty</a></p></td>
<td><p>Enumerates the room properties.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277944(v=office.15)">RoomPropertyChangedEventArgs</a></p></td>
<td><p>Encapsulates the event data of the Room.PropertyChanged event and provides the new value of the changed property.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266452(v=office.15)">RoomPropertyDictionary</a></p></td>
<td><p>A dictionary that contains the properties of a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277918(v=office.15)">RoomSearchModeType</a></p></td>
<td><p>Enumerates the possible room search mode types.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266029(v=office.15)">RoomType</a></p></td>
<td><p>Enumerates the room type.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293507(v=office.15)">RoomUser</a></p></td>
<td><p>Defines a user in a Persistent Chat room.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277692(v=office.15)">RoomUserChangedEventArgs</a></p></td>
<td><p>Encapsulates the state of the event raised when the ability of a group chat room user to send messages changes.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293547(v=office.15)">UnreadMessageCountChangedEventArgs</a></p></td>
<td><p>Encapsulates the state of the event raised when the count of unread messages in a room changes.</p></td>
</tr>
</tbody>
</table>

### Resource sharing API

The following table lists the new API types that support resource sharing. For more information about resource sharing in the Lync 2013 API, see [Get started with desktop, application, and display sharing](get-started-with-desktop-application-and-display-sharing.md).

Resource sharing types

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275536(v=office.15)">ApplicationSharingModality</a></p></td>
<td><p>Represents the application sharing modality of a conversation modality collection.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277269(v=office.15)">CanShareDetail</a></p></td>
<td><p>Enumerates the detail of why sharing a particular resource is allowed or not allowed.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj278391(v=office.15)">ControllerChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ControllerChanged event. A controller is a user who takes control of a shared resource.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293464(v=office.15)">ControlRequestReceivedEventArgs</a></p></td>
<td><p>Represents the event data of a ControlRequestReceivedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293621(v=office.15)">SharingResource</a></p></td>
<td><p>Encapsulates a shareable resource such as a desktop, application, or display.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277836(v=office.15)">SharingResourceList</a></p></td>
<td><p>Encapsulates a collection of shareable resources.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj278136(v=office.15)">SharingResourceType</a></p></td>
<td><p>Enumerates the application sharing resource type.</p></td>
</tr>
</tbody>
</table>

### Meeting content API

The following table lists the new API types that support meeting content management. For more information about meeting content sharing in the Lync 2013 API, see [Get started with content sharing](get-started-with-content-sharing.md).

Meeting content types

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276638(v=office.15)">ActiveContentChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ActiveContentChanged event.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275324(v=office.15)">ActivePresenterChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ActivePresenterChangedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267326(v=office.15)">ContentCollectionChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ContentCollectionChanged event.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266998(v=office.15)">ContentSharingModality</a></p></td>
<td><p>Creates and manages a collection of shareable content items.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267952(v=office.15)">ParticipationState</a></p></td>
<td><p>Enumerates the application sharing participation states.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266001(v=office.15)">ParticipationStateChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ParticipationStateChangedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277028(v=office.15)">PowerPointContent</a></p></td>
<td><p>Represents a PowerPoint slide deck that is shared on the meeting content stage.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277217(v=office.15)">ShareableContent</a></p></td>
<td><p>The ShareableContent class is the common class for all types of content</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267316(v=office.15)">ShareableContentAction</a></p></td>
<td><p>Enumerates supported content actions.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276320(v=office.15)">ShareableContentActionAvailabilityChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ShareableContentActionAvailabilityChangedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277561(v=office.15)">ShareableContentCollection</a></p></td>
<td><p>Maintains a collection of all shareable content objects.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293192(v=office.15)">ShareableContentProperty</a></p></td>
<td><p>Enumerates the content properties.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277679(v=office.15)">ShareableContentPropertyChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ShareableContentPropertyChangedEvent event.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267322(v=office.15)">ShareableContentState</a></p></td>
<td><p>Enumerates the states of a <a href="https://msdn.microsoft.com/en-us/library/jj277217(v=office.15)">ShareableContent</a> object.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294086(v=office.15)">ShareableContentStateChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ShareableContentStateChangedEvent.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275743(v=office.15)">ShareableContentType</a></p></td>
<td><p>Enumerates supported content types.</p></td>
</tr>
</tbody>
</table>

### Other new types

The following table lists the new API types that enhance existing features.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293442(v=office.15)">AlertLevel</a></p></td>
<td><p>Presence-based alert policy.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj278329(v=office.15)">AlertLevelChangedEventArgs</a></p></td>
<td><p>Encapsulates the new state of an AlertLevel instance.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276351(v=office.15)">AlertModeTypes</a></p></td>
<td><p>Enumerates the modes of alert events.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294064(v=office.15)">AlertPrivacyType</a></p></td>
<td><p>A privacy level for the level of alert.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277156(v=office.15)">PresenceCapability</a></p></td>
<td><p>Encapsulates a presence capability as published by a contact.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj274838(v=office.15)">PresenceCapabilityType</a></p></td>
<td><p>Enumerates the published communications capabilities of a contact.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275691(v=office.15)">ContextType</a></p></td>
<td><p>Enumerates the types of context data that can be sent in a conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294117(v=office.15)">ConferenceAccessType</a></p></td>
<td><p>Enumerates the types of user access that can be assigned to a conference.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275880(v=office.15)">ExchangeECPUrlChangedEventArgs</a></p></td>
<td><p>Encapsulates the new state of the Exchange ECP URL, which is raised when the Exchange ECP URL changes.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj278387(v=office.15)">NotificationTypes</a></p></td>
<td><p>Enumerates the notification types that are related to the level of alert.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj268211(v=office.15)">NotificationUrgencyType</a></p></td>
<td><p>Enumerates the urgency levels for the notification.</p></td>
</tr>
</tbody>
</table>

### Changed types

The types in the following table have been changed by adding additional members.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Description of change</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276700(v=office.15)">GetHostingRoom</a></p></td>
<td><p>When called from a Persistent Chat room add-in, gets the <a href="https://msdn.microsoft.com/en-us/library/jj266467(v=office.15)">Room</a> object of the hosting chat room.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294117(v=office.15)">ConferenceAccessType</a></p></td>
<td><p>Enumerates the conference admission types.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293606(v=office.15)">ConversationWindow</a></p></td>
<td><p>New properties and events: <a href="https://msdn.microsoft.com/en-us/library/jj275303(v=office.15)">Properties</a>, <a href="https://msdn.microsoft.com/en-us/library/jj266022(v=office.15)">State</a>, <a href="https://msdn.microsoft.com/en-us/library/jj266962(v=office.15)">InformationChanged</a>, and <a href="https://msdn.microsoft.com/en-us/library/jj274811(v=office.15)">StateChanged</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj268277(v=office.15)">CredentialRequestedType</a></p></td>
<td><p>New enumerators: <a href="https://msdn.microsoft.com/en-us/library/hh380166(v=office.15)">LyncAutodiscover</a> and <a href="https://msdn.microsoft.com/en-us/library/hh380166(v=office.15)">SipAuthBroker</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277212(v=office.15)">ContactInformationType</a></p></td>
<td><p>New enumerator to support contact capability details. <a href="https://msdn.microsoft.com/en-us/library/hh380506(v=office.15)">CapabilityDetails</a></p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266957(v=office.15)">ModalityAction</a></p></td>
<td><p>New enumerators to support resource and meeting content sharing.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj274831(v=office.15)">ModalityTypes</a></p></td>
<td><p>New enumerators to support resource and meeting content sharing.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277683(v=office.15)">Self</a></p></td>
<td><p>New members: <a href="https://msdn.microsoft.com/en-us/library/jj268279(v=office.15)">GetAlertLevelForNotification</a>, <a href="https://msdn.microsoft.com/en-us/library/jj275713(v=office.15)">AlertLevelChanged</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293806(v=office.15)">Utilities</a></p></td>
<td><p>New property: <a href="https://msdn.microsoft.com/en-us/library/jj276608(v=office.15)">ExchangeECPUrl</a>. New Event: <a href="https://msdn.microsoft.com/en-us/library/jj275769(v=office.15)">Utilities.ExchangeECPUrlChanged</a>.</p></td>
</tr>
</tbody>
</table>

## See also

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

