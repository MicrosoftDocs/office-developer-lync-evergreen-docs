---
title: Conversation manager
TOCTitle: Conversation manager
ms:assetid: 5833aa16-a953-4806-92ff-c380d6eafb01
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937321(v=office.15)
ms:contentKeyID: 50877152
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Conversation manager

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about how the Microsoft Lync 2013 SDK **ConversationManager** class lets you start new conversations and online meetings.

**Last modified:** December 11, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
ConversationManager class<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## ConversationManager class

The [Microsoft.Lync.Model.Conversation.ConversationManager](https://msdn.microsoft.com/en-us/library/jj266018\(v=office.15\)) class encapsulates the collection of conversations that are starting, currently active, or terminating on the Lync 2013 client. The **ConversationManager** class is used to start new conversations, join conversations, or join online meetings. It is the source of conversation or meeting invitations when the local user is invited to join conversations that are started by another user. **ConversationManager** is the factory object that creates a new [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) object for each conversation that the local user participates in, whether initiated locally or invited remotely. Obtain the **ConversationManager** object by reading the [Client.ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)) property.

There are several actions that add a conversation to the conversation collection from the [ConversationManager.Conversations](https://msdn.microsoft.com/en-us/library/jj276776\(v=office.15\)) property. These actions include the following:

  - The user starts a new conversation from the Lync 2013 client itself.

  - The user starts a new conversation by using any of the conversation-initiating Lync Controls that might be populated in your WPF or Silverlight application.

  - Another user invites the local user to a conversation or online meeting.

  - The [ConversationManager.AddConversation](https://msdn.microsoft.com/en-us/library/jj276176\(v=office.15\)) method is called in your application.

  - The [ConversationManager.JoinConference](https://msdn.microsoft.com/en-us/library/jj276639\(v=office.15\)) method is called in your application.

  - The **AutomationBeginStartConversation(String, Int32, AsyncCallback, Object)** method is called in your application.

  - The [Automation.BeginMeetNow](https://msdn.microsoft.com/en-us/library/jj277161\(v=office.15\)) method is called in your application.

All of these actions raise the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event. It is important to be able to distinguish the origin of the conversation starting action to determine the action your event callback method will take. You must infer the originating action by examining the two properties of the event state. These event state properties are:

  - The [ConversationManagerEventArgs.Conversation](https://msdn.microsoft.com/en-us/library/jj276980\(v=office.15\)) property, which returns the new **Conversation** object.

  - The [Modality.State](https://msdn.microsoft.com/en-us/library/jj276637\(v=office.15\)) property, which is read from the **InstantMessageModality** object that you obtain from the new **Conversation**.

If the originating action is a Lync 2013 API method call, you should have cached the [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) object obtained synchronously from the method call. Compare the cached Conversation object to the [ConversationManagerEventArgs.Conversation](https://msdn.microsoft.com/en-us/library/jj276980\(v=office.15\)) property. If the comparison shows that these values reference the same **Conversation** object, the event is the result of a method call in your application.

If the originating action is not a Lync 2013 API method call, then a comparison to any cached **Conversation** object results in inequality. In this case, you must determine whether the new conversation is the result of an invitation from another user or started locally by using a Lync Control or the client itself. The state of the new conversation IM modality is always [ModalityState.Notified](https://msdn.microsoft.com/en-us/library/gg255331\(v=office.15\)) when the new conversation is the result of an invitation.

If you are interested in reacting to any of these kinds of conversation-starting events, you must register an event handler for the event. If the event is raised because the user started a conversation using a Lync Control or the client, you can ignore the new conversation because it is being hosted in a conversation window by the Lync 2013 client itself. An exception to this rule is the scenario where you want to dock all conversation windows in container controls within your application.

The conversation invitation action and all Lync 2013 API method call actions raise the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event and must be handled by your application.

## Additional resources

  - [Core concepts: Lync conversations](core-concepts-lync-conversations.md)

  - [How to: Join a Lync conversation](how-to-join-a-lync-conversation.md)

  - [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md)

  - [How to: Start an automation audio conversation](how-to-start-an-automation-audio-conversation.md)

  - [How to: Start a meet-now meeting](how-to-start-a-meet-now-meeting.md)

