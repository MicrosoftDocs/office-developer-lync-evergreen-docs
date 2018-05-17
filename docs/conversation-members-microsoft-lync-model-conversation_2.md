---
title: Conversation members (Microsoft.Lync.Model.Conversation)
TOCTitle: Conversation members
ms:assetid: AllMembers.T:Microsoft.Lync.Model.Conversation.Conversation_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation_di_3_uc_ocs14mreflyncwpf_members(v=office.15)
ms:contentKeyID: 48599088
ms.date: 07/28/2014
mtps_version: v=office.15
---

# Conversation members

Include protected members  
Include inherited members  

Describes a conversation. It includes details such as the conversation participants, modalities (InstantMessaging, AudioVideo), state, etc., and implements actions such as merge, park, terminate or other conversation actions.

The [Conversation](conversation-class-microsoft-lync-model-conversation_2.md) type exposes the following members.

## Properties

<table>
<thead>
<tr class="header">
<th> </th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversation-conversationmanager-property-microsoft-lync-model-conversation_2.md">ConversationManager</a></td>
<td>Gets the parent conversation manager of this conversation.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversation-modalities-property-microsoft-lync-model-conversation_2.md">Modalities</a></td>
<td>Gets the collection of conversation modalities (activities</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversation-participants-property-microsoft-lync-model-conversation_2.md">Participants</a></td>
<td>Gets the participant collection.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversation-properties-property-microsoft-lync-model-conversation_2.md">Properties</a></td>
<td>Gets a collection of conversation properties.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversation-selfparticipant-property-microsoft-lync-model-conversation_2.md">SelfParticipant</a></td>
<td>Gets the local participant object.</td>
</tr>
<tr class="even">
<td><img src="images/JJ275421.pubproperty(Office.15).gif" title="Public property" alt="Public property" /></td>
<td><a href="conversation-state-property-microsoft-lync-model-conversation_2.md">State</a></td>
<td>Gets the current conversation state.</td>
</tr>
</tbody>
</table>


Top

## Methods

<table>
<thead>
<tr class="header">
<th> </th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-addparticipant-method-contact-microsoft-lync-model-conversation_2.md">AddParticipant(Contact)</a></td>
<td>Adds a contact to a conversation and returns the contact as a participant.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-addparticipant-method-contactendpoint-microsoft-lync-model-conversation_2.md">AddParticipant(ContactEndpoint)</a></td>
<td>Adds one of a contact's endpoints to a conversation and returns the contact as a participant.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginadmitparticipants-method-microsoft-lync-model-conversation_2.md">BeginAdmitParticipants</a></td>
<td>Used to admit a set of participants into conference.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-begindenyparticipants-method-microsoft-lync-model-conversation_2.md">BeginDenyParticipants</a></td>
<td>Used to Deny a set of participants access into a conference.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginmerge-method-microsoft-lync-model-conversation_2.md">BeginMerge</a></td>
<td>Merges another conversation into this one.modalityTypes specifies what modalities to be merged in.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginmuteparticipants-method-microsoft-lync-model-conversation_2.md">BeginMuteParticipants</a></td>
<td>Used to mute a set of participants in a conference.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginpark-method-microsoft-lync-model-conversation_2.md">BeginPark</a></td>
<td>Parks voice at the Call Park Server and terminates all other modalities.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginsendcontextdata-method-microsoft-lync-model-conversation_2.md">BeginSendContextData</a></td>
<td>This is used to send application context type and data to the conversation. The application Id has to be registered on the caller side. The context data will be sent in raw foramts</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginsendinitialcontext-method-microsoft-lync-model-conversation_2.md">BeginSendInitialContext</a></td>
<td>Sends an application hyperlink and application Id as initial conversation context.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginsetproperty-method-microsoft-lync-model-conversation_2.md">BeginSetProperty</a></td>
<td>Sets a property associated with this conversation. This is an asynchronous operation, hence the conversationCallback, if specified, will be called back.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-beginunmuteparticipants-method-microsoft-lync-model-conversation_2.md">BeginUnmuteParticipants</a></td>
<td>Used to unmute a set of participants in a conference.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-caninvoke-method-microsoft-lync-model-conversation_2.md">CanInvoke</a></td>
<td>Returns a flag indicating whether a specific action is available.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-cansetproperty-method-microsoft-lync-model-conversation_2.md">CanSetProperty</a></td>
<td>Test whether the property can be set to the conversation.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/2ch65xad">CreateObjRef</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-end-method-microsoft-lync-model-conversation_2.md">End</a></td>
<td>Terminates the conversation for all participants.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endadmitparticipants-method-microsoft-lync-model-conversation_2.md">EndAdmitParticipants</a></td>
<td>Used to admit a set of participants into conference.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-enddenyparticipants-method-microsoft-lync-model-conversation_2.md">EndDenyParticipants</a></td>
<td>Used to Deny a set of participants access into a conference.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endmerge-method-microsoft-lync-model-conversation_2.md">EndMerge</a></td>
<td>Merges another conversation into this one.modalityTypes specifies what modalities to be merged in.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endmuteparticipants-method-microsoft-lync-model-conversation_2.md">EndMuteParticipants</a></td>
<td>Used to mute a set of participants in a conference.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endpark-method-microsoft-lync-model-conversation_2.md">EndPark</a></td>
<td>Parks voice at the Call Park Server and terminates all other modalities.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endsendcontextdata-method-microsoft-lync-model-conversation_2.md">EndSendContextData</a></td>
<td>This is used to send application context type and data to the conversation. The application Id has to be registered on the caller side. The context data will be sent in raw foramts</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endsendinitialcontext-method-microsoft-lync-model-conversation_2.md">EndSendInitialContext</a></td>
<td>This is used to send application context to the conversation. ContextTypes and contextDatas are mapped together, So they must have the same length.If the contextTypes include application GUID, the caller must have been registered using the same GUID.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endsetproperty-method-microsoft-lync-model-conversation_2.md">EndSetProperty</a></td>
<td>Sets a property associated with this conversation. This is an asynchronous operation, hence the conversationCallback, if specified, will be called back.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-endunmuteparticipants-method-microsoft-lync-model-conversation_2.md">EndUnmuteParticipants</a></td>
<td>Used to unmute a set of participants in a conference.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/bsc2ak47">Equals</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="conversation-finalize-method-microsoft-lync-model-conversation_1.md">Finalize</a></td>
<td>(Overrides <strong>UCWFullFinalize()</strong>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-getapplicationdata-method-microsoft-lync-model-conversation_2.md">GetApplicationData</a></td>
<td>Gets the contextual conversation application data using the given GUID. Only the registered application with the same GUID may call this.</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/zdee4b3y">GetHashCode</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/c6y7316f">GetLifetimeService</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/dfwy45w9">GetType</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/zwt5tzck">InitializeLifetimeService</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/57ctke0a">MemberwiseClone()</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.protmethod(Office.15).gif" title="Protected method" alt="Protected method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/ms131262">MemberwiseClone(Boolean)</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/w4302s1f">MarshalByRefObject</a>.)</td>
</tr>
<tr class="even">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="conversation-removeparticipant-method-microsoft-lync-model-conversation_2.md">RemoveParticipant</a></td>
<td>Removes a participant from the collection.</td>
</tr>
<tr class="odd">
<td><img src="images/Hh347903.pubmethod(Office.15).gif" title="Public method" alt="Public method" /></td>
<td><a href="http://msdn2.microsoft.com/en-us/library/7bxwbwt2">ToString</a></td>
<td>(Inherited from <a href="http://msdn2.microsoft.com/en-us/library/e5kfa45b">Object</a>.)</td>
</tr>
</tbody>
</table>


Top

## Events

<table>
<thead>
<tr class="header">
<th> </th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-actionavailabilitychanged-event-microsoft-lync-model-conversation_2.md">ActionAvailabilityChanged</a></td>
<td>Raised when an action availability changes.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-contextdatareceived-event-microsoft-lync-model-conversation_2.md">ContextDataReceived</a></td>
<td>Raised to notify of the 3rd party applications of incoming info.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-contextdatasent-event-microsoft-lync-model-conversation_2.md">ContextDataSent</a></td>
<td>Raised to notify of the 3rd party applications of outgoing info.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-conversationcontextlinkclicked-event-microsoft-lync-model-conversation_2.md">ConversationContextLinkClicked</a></td>
<td>Raised when a contextual conversation launch link is clicked by the user.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-initialcontextreceived-event-microsoft-lync-model-conversation_2.md">InitialContextReceived</a></td>
<td>Raised to notify of the 3rd party applications of incoming calls .</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-initialcontextsent-event-microsoft-lync-model-conversation_2.md">InitialContextSent</a></td>
<td>Raised to notify of the 3rd party applications of outgoing calls .</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-participantadded-event-microsoft-lync-model-conversation_2.md">ParticipantAdded</a></td>
<td>Raised when a participant add operation completes.</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-participantremoved-event-microsoft-lync-model-conversation_2.md">ParticipantRemoved</a></td>
<td>Raised when a participant remove operation completes.</td>
</tr>
<tr class="odd">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-propertychanged-event-microsoft-lync-model-conversation_2.md">PropertyChanged</a></td>
<td>Raised when a property value changes</td>
</tr>
<tr class="even">
<td><img src="images/JJ266306.pubevent(Office.15).gif" title="Public event" alt="Public event" /></td>
<td><a href="conversation-statechanged-event-microsoft-lync-model-conversation_2.md">StateChanged</a></td>
<td>Raised when the conversation state changes.</td>
</tr>
</tbody>
</table>


Top

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

