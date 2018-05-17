---
title: Event-driven code in Lync SDK
TOCTitle: Event-driven code
ms:assetid: 2c4828f4-989c-4ad4-94c0-2edfb3ae0952
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937285(v=office.15)
ms:contentKeyID: 50877106
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Event-driven code in Lync SDK

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the asynchronous nature of programming with Microsoft Lync 2013 SDK.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Event-based programming<br />
Additional resources</p></td>
</tr>
</tbody>
</table>


## Event-based programming

With few exceptions, the methods that you call on the classes in the Lync 2013 API begin operations that generate a SIP dialog between the Lync client and a Microsoft Lync Server 2013 front-end computer. A SIP dialog is a set of client requests and server responses using the SIP protocol. Server response time depends on network bandwidth usage and server load. For this reason, the API method must be asynchronous with response data exposed by a set of events on the calling object. To give a user a responsive application UI, the client thread where the method is called should not be blocked while awaiting the asynchronous response from the server. This requirement is met because the Lync 2013 API gives you asynchronous methods and state change notifications by using events.

In addition to locally initiated operations that return results, Lync Server 2013 sends information that result from an operation started by another user. For example, another user can request an operation that sends an IM to other users in a conversation. The incoming SIP IM text can only be obtained and rendered in your UI if your application is listening for IM text by registering for the **InstantMessageReceived** event.

For more information about event-based programming, see [Events (C\# Programming Guide)](http://msdn.microsoft.com/en-us/library/awbftdfh\(v=vs.80\).aspx).

### Event-invoking actions

Actions that raise events in the Lync 2013 API can be initiated by the local client application, a Lync 2013 client at a different endpoint, or Lync Server 2013. In some cases, the same event type can be invoked locally from actions taken by either the local endpoint or a remote client endpoint. Figure 1 shows the case in which the local user sends IM text to another user in a conversation. The [InstantMessageModality.InstantMessageReceived](instantmessagemodality-instantmessagereceived-event-microsoft-lync-model-conversation_2.md) event is invoked on both the local endpoint and the endpoint of the message recipient. Other kinds of remote user actions that can result in local events include adding a participant to a conversation, publishing updated contact card information, and changes in user availability. In general, events are invoked non-deterministically when they are not the result of a locally started operation.

The following figures show examples of actions taken on one endpoint that invoke events on another endpoint.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Conversation IM sent</p></th>
<th><p>Presence publication</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><div class="caption">
Figure 1. IM message send operation-related events
</div>
<br />
<img src="images/JJ937285.LyncClientSDK_EventProgramming_ConversationEvents(Office.15).jpg" title="AddConversation operation related events" alt="AddConversation operation related events" /></td>
<td><div class="caption">
Figure 2. Publish availability operation-related events
</div>
<br />
<img src="images/JJ937285.LyncClientSDK_EventProgramming_PublicationEvents(Office.15).jpg" title="Publication-related events" alt="Publication-related events" /></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> <P>If your application and the Lync 2013 client that the user has signed in are running on the same computer, they share a common endpoint. Any events raised for an endpoint are exposed to all processes that share the endpoint.</P>
> <P>All Lync 2013 API operations have corresponding Lync 2013 client operations. The results of these client operations are visible to your application through API events even though the operations were not initiated in your application. For example, a user can start a new conversation from the Lync client itself. The <STRONG>ConversationAdded</STRONG> event is raised even though your application did not call the <STRONG>AddConversation</STRONG> method. You may want to ignore the <STRONG>ConversationAdded</STRONG> event raised for the Lync client-originated conversation. This <STRONG>ConversationAdded</STRONG> event is distinguishable because the event data parameter of the event carries a reference to a <STRONG>Conversation</STRONG> object. Comparing this object to a <STRONG>Conversation</STRONG> object returned when <STRONG>AddConversation</STRONG> is called in your application lets you determine the source of the event. For more information about how to handle this event, see <A href="how-to-join-a-lync-conversation.md">How to: Join a Lync conversation</A>.</P>
> <P></P>
> <P>User presence publication operations generate events that are raised across all endpoints that share a common user. For example, if a user has signed in from a device by using Lync 2013 and also signed in on a different device by using your application, both endpoints are exposed to the same user publication events.</P>



### Event registration

From the [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md) class at the entry point of the API, through multiple class-object layers, to something as fine-grained as the [Microsoft.Lync.Model.Conversation.Sharing.SharingResource](sharingresource-class-microsoft-lync-model-conversation-sharing_2.md) that encapsulates a conversation participant’s shared desktop, you can access all Lync 2013 API child objects through parent object properties.

Lync entities such as contact lists and conversations are encapsulated by the Lync 2013 API as sets of nested class objects. For example, a conversation is encapsulated by a [Microsoft.Lync.Model.Conversation.Conversation](conversation-class-microsoft-lync-model-conversation_2.md) object. This object exposes properties, methods, and event. Conversation events are raised to notify you of changes to conversation state that you should respond to. A conversation is additionally broken down into a collection of [Microsoft.Lync.Model.Conversation.Modality](modality-class-microsoft-lync-model-conversation_2.md) objects that encapsulate the modes of communication in a conversation. A conversation is an interaction between two or more users. These users are encapsulated by a collection of [Microsoft.Lync.Model.Conversation.Participant](participant-class-microsoft-lync-model-conversation_2.md) objects. Both modality and participant objects expose their own sets of methods, properties, and events.

Each participant encapsulates a set of modalities that parallel the conversation modalities, but are scoped to the participant. A participant modality exposes the same set of properties, methods, and events as the conversation modality. However, all events raised on a participant modality pertain only to the participant who owns the modality.

A responsive Lync 2013 API-enabled application registers event callback methods for all of the events exposed by the conversation and conversation-related class objects. This registration is usually done in either of two locations. In the first case, registration can be done when a parent object is created that has a fully populated collection of child objects. Register for the parent events and then iterate on the child object collection and register for events on the children. The second case is where you get a parent object whose child object collection can be added to in the lifetime of the parent object.

An example of the second case is the [Microsoft.Lync.Model.Conversation.ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) object. When you get the [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md) object to enter the API and sign a user in, the **ConversationManager** has an empty collection of conversations. When the user is invited to a conversation, starts a conversation using the Lync client UI, or calls the **AddConversation** method, the [ConversationManager.ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event is raised when a conversation is created and added to the **ConversationManager** conversation collection. The event callback method that is called for this event should register for all conversation events and conversation modality events. The most important conversation event to register for is the [Conversation.ParticipantAdded](conversation-participantadded-event-microsoft-lync-model-conversation_2.md) event.

When a conversation is created, the new **Conversation** is added to the state of the **LyncClient** object. In a conversation object lifetime, API objects are added and removed from the conversation. As users join a conversation, [Microsoft.Lync.Model.Conversation.Participant](participant-class-microsoft-lync-model-conversation_2.md) objects are added to the [Microsoft.Lync.Model.Conversation.Conversation](conversation-class-microsoft-lync-model-conversation_2.md). The state of each **Participant** object contains a collection of [Microsoft.Lync.Model.Conversation.Modality](modality-class-microsoft-lync-model-conversation_2.md) objects that encapsulate individual communication modes in a conversation. A modality such as the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md) includes properties whose values yield such things as primitive strings or objects such as the [Microsoft.Lync.Model.Conversation.Sharing.SharingResource](sharingresource-class-microsoft-lync-model-conversation-sharing_2.md) that encapsulate a shared resource such as a desktop.


> [!IMPORTANT]
> <P>Although it seems appropriate to register for conversation events and call methods on a Conversation object as it is returned synchronously by the <A href="conversationmanager-addconversation-method-microsoft-lync-model-conversation_2.md">ConversationManager.AddConversation</A> method, it is never a good idea to do this. The conversation-creating SIP dialog with the server is incomplete at this point and the new conversation object is not fully provisioned. Registering events at this point can result in a race condition with the API platform and server. Your application can behave unpredictably as a result. Instead, register for conversation events in the <A href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md">ConversationManager.ConversationAdded</A> event handler. The conversation object is OK to use at this point.</P>



In the conversation object hierarchy, each child object is obtained by reading a collection property on the parent. In some cases, these collection properties contain a fixed number of children. In other cases, the number of children depend on the actions of conversation participants. In the first case, all **Conversation** objects are created that have a fixed collection of modalities. Modalities are never added or removed from the modalities collection. However, the states of individual modalities change and you must know about these changes. In the other case, **Conversation** objects are created that have no participants. As users are added to a conversation, **Participant** objects are added to the conversation participant collection. You have to know when a participant is added to the collection and when it is removed. Like the state of individual modalities, the state of individual **Participant** objects can change.

To react to all these changes and keep your UI up to date, you have to register for events on all these conversation objects. The best way to do this is to either iterate on all child objects in a collection at the time that the parent object is added or register for events on a new child object at the time that it is added to the parent collection.

## Additional resources

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [Asynchronous programming in Lync SDK](asynchronous-programming-in-lync-sdk.md)

