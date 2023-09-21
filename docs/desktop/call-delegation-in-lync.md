---
title: Call delegation in Lync
TOCTitle: Call delegation in Lync
ms:assetid: c76261ef-2134-4a3e-b671-14d724101118
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933187(v=office.15)
ms:contentKeyID: 50877328
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Call delegation in Lync

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the Microsoft Lync 2013 SDK class that lets your application handle audio calls delegated to the local Lync 2013 user.



**Applies to**: Lync 2013 | Lync Server 2013

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

The API entry point for delegated calls is the [Microsoft.Lync.Model.DelegatorClient](https://msdn.microsoft.com/library/jj266028\(v=office.15\)) class. **DelegatorClient** inherits [Microsoft.Lync.Model.Client](https://msdn.microsoft.com/library/jj266014\(v=office.15\)) and provides a [Microsoft.Lync.Model.Conversation.ConversationManager](https://msdn.microsoft.com/library/jj266018\(v=office.15\)) object that raises the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A <strong>DelegatorClient</strong> object exposes a <a href="https://msdn.microsoft.com/library/jj266459(v=office.15)">Microsoft.Lync.Model.ContactManager</a> object. Although the <strong>DelegatorClient</strong> represents the delegator user, the obtained <strong>ContactManger</strong> represents the local user and exposes the local user’s groups and contacts, not the delegator’s groups and contacts.</p></td>
</tr>
</tbody>
</table>

The [LyncClient.DelegatorClients](https://msdn.microsoft.com/library/jj277686\(v=office.15\)) property returns a collection of delegator client objects. The collection contains a **DelegatorClient** object for each call delegator who has delegated calls to the local user. Read the [Client.Uri](https://msdn.microsoft.com/library/jj293482\(v=office.15\)) property on each **DelegatorClient** to get the URI of the Lync 2013 user who delegated calls to the local user. You should use this URI to get the [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) object for the call delegator. Be sure to get the name of the delegator user from this **Contact** object so that you can display a note on your conversation window UI that informs the local user who they are answering delegated calls for.

When a call comes in on behalf one of the delegating users, the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event is raised on the [Microsoft.Lync.Model.Conversation.ConversationManager](https://msdn.microsoft.com/library/jj266018\(v=office.15\)) object provided by the corresponding **DelegatorClient** object. Be sure to register for this event on all instances of the delegator **ConversationManager**.

When you obtain the [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) object for the delegated call, treat the call as a normal incoming audio call. You can accept or reject the call and then perform all of the audio call operations that you would for a non-delegated audio call. For information about handling conversations, see [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

## See also

  - [Beyond the basics: Lync conversations](beyond-the-basics-lync-conversations.md)

  - [How to: Handle delegated Lync audio calls](how-to-handle-delegated-lync-audio-calls.md)

