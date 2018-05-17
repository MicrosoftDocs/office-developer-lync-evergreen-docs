---
title: Call delegation in Lync
TOCTitle: Call delegation in Lync
ms:assetid: c76261ef-2134-4a3e-b671-14d724101118
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933187(v=office.15)
ms:contentKeyID: 50877328
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Call delegation in Lync

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the Microsoft Lync 2013 SDK class that lets your application handle audio calls delegated to the local Lync 2013 user.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Lync 2013 call delegation<br />
Delegated call object model<br />
Additional resources</p></td>
</tr>
</tbody>
</table>


## Lync 2013 call delegation

The two components of Lync 2013 call delegation are the Lync user who delegates calls and the Lync user who is delegated to receive audio calls. A user can be delegated to receive delegated calls from multiple delegators. When a delegated call is answered by a delegated user, the normal Lync 2013 conversation window is opened on the delegated user’s display. The conversation window displays text that indicates the call is answered on behalf of a delegator and includes the delegator’s name. The Microsoft Lync 2013 API object model lets you create delegated call behavior in your application so that your code can emulate the behavior of the client.

## Delegated call object model

The API entry point for delegated calls is the [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md) class. **DelegatorClient** inherits [Microsoft.Lync.Model.Client](client-class-microsoft-lync-model_2.md) and provides a [Microsoft.Lync.Model.Conversation.ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) object that raises the [ConversationManager.ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event.


> [!TIP]
> <P>A <STRONG>DelegatorClient</STRONG> object exposes a <A href="contactmanager-class-microsoft-lync-model_2.md">Microsoft.Lync.Model.ContactManager</A> object. Although the <STRONG>DelegatorClient</STRONG> represents the delegator user, the obtained <STRONG>ContactManger</STRONG> represents the local user and exposes the local user’s groups and contacts, not the delegator’s groups and contacts.</P>



The [LyncClient.DelegatorClients](lyncclient-delegatorclients-property-microsoft-lync-model_2.md) property returns a collection of delegator client objects. The collection contains a **DelegatorClient** object for each call delegator who has delegated calls to the local user. Read the [Client.Uri](client-uri-property-microsoft-lync-model_2.md) property on each **DelegatorClient** to get the URI of the Lync 2013 user who delegated calls to the local user. You should use this URI to get the [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) object for the call delegator. Be sure to get the name of the delegator user from this **Contact** object so that you can display a note on your conversation window UI that informs the local user who they are answering delegated calls for.

When a call comes in on behalf one of the delegating users, the [ConversationManager.ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event is raised on the [Microsoft.Lync.Model.Conversation.ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) object provided by the corresponding **DelegatorClient** object. Be sure to register for this event on all instances of the delegator **ConversationManager**.

When you obtain the [Microsoft.Lync.Model.Conversation.Conversation](conversation-class-microsoft-lync-model-conversation_2.md) object for the delegated call, treat the call as a normal incoming audio call. You can accept or reject the call and then perform all of the audio call operations that you would for a non-delegated audio call. For information about handling conversations, see [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

## Additional resources

  - [Beyond the basics: Lync conversations](beyond-the-basics-lync-conversations.md)

  - [How to: Handle delegated Lync audio calls](how-to-handle-delegated-lync-audio-calls.md)

