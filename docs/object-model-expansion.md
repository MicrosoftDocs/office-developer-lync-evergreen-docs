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

![What's new topic](images/JJ933179.mod_icon_whatsnew_long(Office.15).png "What's new topic")

The Microsoft Lync 2013 API includes new types to enable the features described in [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md).


_**Applies to:** Lync 2013 | Lync Server 2013_

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
<td><p><a href="followedroomschangedeventargs-class-microsoft-lync-model-room_2.md">FollowedRoomsChangedEventArgs</a></p></td>
<td><p>The state of the event raised when the membership of collection of user-followed chat rooms has changed.</p></td>
</tr>
<tr class="even">
<td><p><a href="joinroomfailexception-class-microsoft-lync-model_2.md">JoinRoomFailException</a></p></td>
<td><p>Encapsulates the state of the exception raised when a user fails to join a chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="joinroomunauthorizedexception-class-microsoft-lync-model_2.md">JoinRoomUnauthorizedException</a></p></td>
<td><p>Encapsulates the state of the exception raised when a user attempts to join a chat room that he or she is not authorized to join.</p></td>
</tr>
<tr class="even">
<td><p><a href="room-class-microsoft-lync-model-room_2.md">Room</a></p></td>
<td><p>Encapsulates a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roomjoinstate-enumeration-microsoft-lync-model-room_2.md">RoomJoinState</a></p></td>
<td><p>Enumerates the Persistent Chat room joining operation states.</p></td>
</tr>
<tr class="even">
<td><p><a href="roomjoinstatechangedeventargs-class-microsoft-lync-model-room_2.md">RoomJoinStateChangedEventArgs</a></p></td>
<td><p>Encapsulates the state of the RoomJoinStateChanged event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommanager-class-microsoft-lync-model-room_2.md">RoomManager</a></p></td>
<td><p>Persistent Chat room manager that provides room query functionality.</p></td>
</tr>
<tr class="even">
<td><p><a href="roommanagerstate-enumeration-microsoft-lync-model-room_2.md">RoomManagerState</a></p></td>
<td><p>Enumerates the room manager state.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommanagerstatechangedeventargs-class-microsoft-lync-model-room_2.md">RoomManagerStateChangedEventArgs</a></p></td>
<td><p>Exposes the new state of a room manager.</p></td>
</tr>
<tr class="even">
<td><p><a href="roommessage-class-microsoft-lync-model-room_2.md">RoomMessage</a></p></td>
<td><p>Defines a room message sent to a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommessagedictionary-class-microsoft-lync-model-room_2.md">RoomMessageDictionary</a></p></td>
<td><p>A key/value pairing of a message format enumerator and actual message text.</p></td>
</tr>
<tr class="even">
<td><p><a href="roommessageeventargs-class-microsoft-lync-model-room_2.md">RoomMessageEventArgs</a></p></td>
<td><p>Encapsulates the state of the event raised when a local user sends a message to a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommessageseventargs-class-microsoft-lync-model-room_2.md">RoomMessagesEventArgs</a></p></td>
<td><p>Encapsulates the state of the MessagesReceived event and contains a collection of the messages sent to a room.</p></td>
</tr>
<tr class="even">
<td><p><a href="roommessagefilteringaction-enumeration-microsoft-lync-model-room_2.md">RoomMessageFilteringAction</a></p></td>
<td><p>Enumerates the action taken by a chat room add-in for a room message.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommessageformat-enumeration-microsoft-lync-model-room_2.md">RoomMessageFormat</a></p></td>
<td><p>Enumerates the possible format types of a room message.</p></td>
</tr>
<tr class="even">
<td><p><a href="roommessagetype-enumeration-microsoft-lync-model-room_2.md">RoomMessageType</a></p></td>
<td><p>Enumerates the possible types of a room message.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roomparticipantseventargs-class-microsoft-lync-model-room_2.md">RoomParticipantsEventArgs</a></p></td>
<td><p>Encapsulates the state of the ParticpiantsAdded and ParticipantsRemoved events and contains a collection of the room participants added or removed.</p></td>
</tr>
<tr class="even">
<td><p><a href="roomproperty-enumeration-microsoft-lync-model-room_2.md">RoomProperty</a></p></td>
<td><p>Enumerates the room properties.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roompropertychangedeventargs-class-microsoft-lync-model-room_2.md">RoomPropertyChangedEventArgs</a></p></td>
<td><p>Encapsulates the event data of the Room.PropertyChanged event and provides the new value of the changed property.</p></td>
</tr>
<tr class="even">
<td><p><a href="roompropertydictionary-class-microsoft-lync-model-room_2.md">RoomPropertyDictionary</a></p></td>
<td><p>A dictionary that contains the properties of a Persistent Chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roomsearchmodetype-enumeration-microsoft-lync-model-room_2.md">RoomSearchModeType</a></p></td>
<td><p>Enumerates the possible room search mode types.</p></td>
</tr>
<tr class="even">
<td><p><a href="roomtype-enumeration-microsoft-lync-model-room_2.md">RoomType</a></p></td>
<td><p>Enumerates the room type.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roomuser-class-microsoft-lync-model-room_2.md">RoomUser</a></p></td>
<td><p>Defines a user in a Persistent Chat room.</p></td>
</tr>
<tr class="even">
<td><p><a href="roomuserchangedeventargs-class-microsoft-lync-model-room_2.md">RoomUserChangedEventArgs</a></p></td>
<td><p>Encapsulates the state of the event raised when the ability of a group chat room user to send messages changes.</p></td>
</tr>
<tr class="odd">
<td><p><a href="unreadmessagecountchangedeventargs-class-microsoft-lync-model-room_2.md">UnreadMessageCountChangedEventArgs</a></p></td>
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
<td><p><a href="applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md">ApplicationSharingModality</a></p></td>
<td><p>Represents the application sharing modality of a conversation modality collection.</p></td>
</tr>
<tr class="even">
<td><p><a href="cansharedetail-enumeration-microsoft-lync-model-conversation-sharing_2.md">CanShareDetail</a></p></td>
<td><p>Enumerates the detail of why sharing a particular resource is allowed or not allowed.</p></td>
</tr>
<tr class="odd">
<td><p><a href="controllerchangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ControllerChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ControllerChanged event. A controller is a user who takes control of a shared resource.</p></td>
</tr>
<tr class="even">
<td><p><a href="controlrequestreceivedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ControlRequestReceivedEventArgs</a></p></td>
<td><p>Represents the event data of a ControlRequestReceivedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sharingresource-class-microsoft-lync-model-conversation-sharing_2.md">SharingResource</a></p></td>
<td><p>Encapsulates a shareable resource such as a desktop, application, or display.</p></td>
</tr>
<tr class="even">
<td><p><a href="sharingresourcelist-class-microsoft-lync-model-conversation-sharing_2.md">SharingResourceList</a></p></td>
<td><p>Encapsulates a collection of shareable resources.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sharingresourcetype-enumeration-microsoft-lync-model-conversation-sharing_2.md">SharingResourceType</a></p></td>
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
<td><p><a href="activecontentchangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ActiveContentChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ActiveContentChanged event.</p></td>
</tr>
<tr class="even">
<td><p><a href="activepresenterchangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ActivePresenterChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ActivePresenterChangedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contentcollectionchangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ContentCollectionChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ContentCollectionChanged event.</p></td>
</tr>
<tr class="even">
<td><p><a href="contentsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md">ContentSharingModality</a></p></td>
<td><p>Creates and manages a collection of shareable content items.</p></td>
</tr>
<tr class="odd">
<td><p><a href="participationstate-enumeration-microsoft-lync-model-conversation-sharing_2.md">ParticipationState</a></p></td>
<td><p>Enumerates the application sharing participation states.</p></td>
</tr>
<tr class="even">
<td><p><a href="participationstatechangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ParticipationStateChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ParticipationStateChangedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="powerpointcontent-class-microsoft-lync-model-conversation-sharing_2.md">PowerPointContent</a></p></td>
<td><p>Represents a PowerPoint slide deck that is shared on the meeting content stage.</p></td>
</tr>
<tr class="even">
<td><p><a href="shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md">ShareableContent</a></p></td>
<td><p>The ShareableContent class is the common class for all types of content</p></td>
</tr>
<tr class="odd">
<td><p><a href="shareablecontentaction-enumeration-microsoft-lync-model-conversation-sharing_2.md">ShareableContentAction</a></p></td>
<td><p>Enumerates supported content actions.</p></td>
</tr>
<tr class="even">
<td><p><a href="shareablecontentactionavailabilitychangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ShareableContentActionAvailabilityChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ShareableContentActionAvailabilityChangedEvent event.</p></td>
</tr>
<tr class="odd">
<td><p><a href="shareablecontentcollection-class-microsoft-lync-model-conversation-sharing_2.md">ShareableContentCollection</a></p></td>
<td><p>Maintains a collection of all shareable content objects.</p></td>
</tr>
<tr class="even">
<td><p><a href="shareablecontentproperty-enumeration-microsoft-lync-model-conversation-sharing_2.md">ShareableContentProperty</a></p></td>
<td><p>Enumerates the content properties.</p></td>
</tr>
<tr class="odd">
<td><p><a href="shareablecontentpropertychangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ShareableContentPropertyChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ShareableContentPropertyChangedEvent event.</p></td>
</tr>
<tr class="even">
<td><p><a href="shareablecontentstate-enumeration-microsoft-lync-model-conversation-sharing_2.md">ShareableContentState</a></p></td>
<td><p>Enumerates the states of a <a href="shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md">ShareableContent</a> object.</p></td>
</tr>
<tr class="odd">
<td><p><a href="shareablecontentstatechangedeventargs-class-microsoft-lync-model-conversation-sharing_2.md">ShareableContentStateChangedEventArgs</a></p></td>
<td><p>Represents the event data of a ShareableContentStateChangedEvent.</p></td>
</tr>
<tr class="even">
<td><p><a href="shareablecontenttype-enumeration-microsoft-lync-model-conversation-sharing_2.md">ShareableContentType</a></p></td>
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
<td><p><a href="alertlevel-class-microsoft-lync-model_2.md">AlertLevel</a></p></td>
<td><p>Presence-based alert policy.</p></td>
</tr>
<tr class="even">
<td><p><a href="alertlevelchangedeventargs-class-microsoft-lync-model_2.md">AlertLevelChangedEventArgs</a></p></td>
<td><p>Encapsulates the new state of an AlertLevel instance.</p></td>
</tr>
<tr class="odd">
<td><p><a href="alertmodetypes-enumeration-microsoft-lync-model_2.md">AlertModeTypes</a></p></td>
<td><p>Enumerates the modes of alert events.</p></td>
</tr>
<tr class="even">
<td><p><a href="alertprivacytype-enumeration-microsoft-lync-model_2.md">AlertPrivacyType</a></p></td>
<td><p>A privacy level for the level of alert.</p></td>
</tr>
<tr class="odd">
<td><p><a href="presencecapability-class-microsoft-lync-model_2.md">PresenceCapability</a></p></td>
<td><p>Encapsulates a presence capability as published by a contact.</p></td>
</tr>
<tr class="even">
<td><p><a href="presencecapabilitytype-enumeration-microsoft-lync-model_2.md">PresenceCapabilityType</a></p></td>
<td><p>Enumerates the published communications capabilities of a contact.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contexttype-enumeration-microsoft-lync-model-conversation_2.md">ContextType</a></p></td>
<td><p>Enumerates the types of context data that can be sent in a conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="conferenceaccesstype-enumeration-microsoft-lync-model-conversation_2.md">ConferenceAccessType</a></p></td>
<td><p>Enumerates the types of user access that can be assigned to a conference.</p></td>
</tr>
<tr class="odd">
<td><p><a href="exchangeecpurlchangedeventargs-class-microsoft-lync-model_2.md">ExchangeECPUrlChangedEventArgs</a></p></td>
<td><p>Encapsulates the new state of the Exchange ECP URL, which is raised when the Exchange ECP URL changes.</p></td>
</tr>
<tr class="even">
<td><p><a href="notificationtypes-enumeration-microsoft-lync-model_2.md">NotificationTypes</a></p></td>
<td><p>Enumerates the notification types that are related to the level of alert.</p></td>
</tr>
<tr class="odd">
<td><p><a href="notificationurgencytype-enumeration-microsoft-lync-model_2.md">NotificationUrgencyType</a></p></td>
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
<td><p><a href="lyncclient-gethostingroom-method-microsoft-lync-model.md">GetHostingRoom</a></p></td>
<td><p>When called from a Persistent Chat room add-in, gets the <a href="room-class-microsoft-lync-model-room_2.md">Room</a> object of the hosting chat room.</p></td>
</tr>
<tr class="even">
<td><p><a href="conferenceaccesstype-enumeration-microsoft-lync-model-conversation_2.md">ConferenceAccessType</a></p></td>
<td><p>Enumerates the conference admission types.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversationwindow-class-microsoft-lync-model-extensibility_2.md">ConversationWindow</a></p></td>
<td><p>New properties and events: <a href="conversationwindow-properties-property-microsoft-lync-model-extensibility_2.md">Properties</a>, <a href="conversationwindow-state-property-microsoft-lync-model-extensibility_2.md">State</a>, <a href="conversationwindow-informationchanged-event-microsoft-lync-model-extensibility_2.md">InformationChanged</a>, and <a href="conversationwindow-statechanged-event-microsoft-lync-model-extensibility_2.md">StateChanged</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="credentialrequestedtype-enumeration-microsoft-lync-model_2.md">CredentialRequestedType</a></p></td>
<td><p>New enumerators: <a href="credentialrequestedtype-enumeration-microsoft-lync-model.md">LyncAutodiscover</a> and <a href="credentialrequestedtype-enumeration-microsoft-lync-model.md">SipAuthBroker</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</a></p></td>
<td><p>New enumerator to support contact capability details. <a href="contactinformationtype-enumeration-microsoft-lync-model.md">CapabilityDetails</a></p></td>
</tr>
<tr class="even">
<td><p><a href="modalityaction-enumeration-microsoft-lync-model-conversation_2.md">ModalityAction</a></p></td>
<td><p>New enumerators to support resource and meeting content sharing.</p></td>
</tr>
<tr class="odd">
<td><p><a href="modalitytypes-enumeration-microsoft-lync-model-conversation_2.md">ModalityTypes</a></p></td>
<td><p>New enumerators to support resource and meeting content sharing.</p></td>
</tr>
<tr class="even">
<td><p><a href="self-class-microsoft-lync-model_2.md">Self</a></p></td>
<td><p>New members: <a href="self-getalertlevelfornotification-method-microsoft-lync-model_2.md">GetAlertLevelForNotification</a>, <a href="self-alertlevelchanged-event-microsoft-lync-model_2.md">AlertLevelChanged</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="utilities-class-microsoft-lync-model_2.md">Utilities</a></p></td>
<td><p>New property: <a href="utilities-exchangeecpurl-property-microsoft-lync-model_2.md">ExchangeECPUrl</a>. New Event: <a href="utilities-exchangeecpurlchanged-event-microsoft-lync-model_2.md">Utilities.ExchangeECPUrlChanged</a>.</p></td>
</tr>
</tbody>
</table>


## Additional resources

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

