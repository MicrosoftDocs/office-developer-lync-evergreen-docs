---
title: Conversation modalities
TOCTitle: Conversation modalities
ms:assetid: 9e6fc969-9c15-42ab-96c5-7df87c2e95ee
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933146(v=office.15)
ms:contentKeyID: 50877282
ms.date: 07/24/2014
mtps_version: v=office.15
description: Explore Microsoft Lync 2013's conversation modes, including desktop sharing, virtual whiteboard, and more. Learn about modality operations and classes.
---

# Conversation modalities

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about how Microsoft Lync 2013 SDK represents the communication modes in a Microsoft Lync 2013 conversation.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Conversation modes<br />
Invoking modality operations<br />
Conversation modality owners<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Conversation modes

A Lync 2013 conversation can let people converse in any combination of several modes, including modes that let a user share their desktop, a running program, a virtual whiteboard, or an Office document such as a PowerPoint slide deck. Each of these modes share features and operations that are encapsulated by the base [Microsoft.Lync.Model.Conversation.Modality](https://msdn.microsoft.com/library/jj274796\(v=office.15\)) class. These include the modality state, hosting endpoint, and owning participant. Common modality operations include invitation acceptance, invitation rejection, modality connection, and modality rejection.

Each specific conversation mode, such as the IM mode or the audio-video mode, is encapsulated by a class that inherits the base [Microsoft.Lync.Model.Conversation.Modality](https://msdn.microsoft.com/library/jj274796\(v=office.15\)) class and then exposes properties, methods, and events that are specific to the modality. For example, the [Microsoft.Lync.Model.Conversation.InstantMessageModality](https://msdn.microsoft.com/library/jj266036\(v=office.15\)) class exposes the [InstantMessageModality.BeginSendMessage(String, AsyncCallback, Object)](https://msdn.microsoft.com/library/jj275538\(v=office.15\)) method so that you can send IM messages on the modality. The following table lists the conversation modality classes in the Lync 2013 API.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Class</p></th>
<th><p>Conversation mode</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj274796(v=office.15)">Modality</a></p></td>
<td><p>The base modality class.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj266036(v=office.15)">InstantMessageModality</a></p></td>
<td><p>The instant message modality class. Inherits from <strong>Modality</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj274580(v=office.15)">AVModality</a></p></td>
<td><p>The audio-video modality. This modality is used for audio conversations, audio-video conversations, audio conferences (online meetings), and audio-video conferences. Inherits from <strong>Modality</strong>.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj275536(v=office.15)">ApplicationSharingModality</a></p></td>
<td><p>The application sharing modality. This modality is used to share a user’s desktop, computer display, or running program. Inherits from <strong>Modality</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj266998(v=office.15)">ContentSharingModality</a></p></td>
<td><p>The content sharing modality. This modality is used to upload and annotate virtual whiteboards, PowerPoint slide decks, and meeting attachments.</p></td>
</tr>
</tbody>
</table>

## Invoking modality operations

The success of operations such as sending IM messages, holding and retrieving audio calls, transferring, and forwarding calls depend on the state of a modality at the time the operation is attempted. Some operations are not allowed on modalities even when the state of the modality is valid. For example, because **InstantMessageModality** inherits the methods of **Modality**, it is syntactically correct to call the [Modality.BeginTransfer](https://msdn.microsoft.com/library/jj293455\(v=office.15\)) method on it. However, doing so raises an **UnauthorizedAccessException**. Instead of requiring that a developer learn about all of the scenarios where an operation is not allowed on a modality, Microsoft Lync 2013 SDK provides the [Modality.CanInvoke](https://msdn.microsoft.com/library/jj267958\(v=office.15\)) method. If you pass the modality action that you are going to try, the method returns true if the action is available. **CanInvoke** checks the state and type of the modality for you and then returns false if you cannot perform the action.

## Conversation modality owners

A **Conversation** object exposes a modality collection that always includes every modality in the previous table. The modalities in this collection represent the SIP and medial dialog between the local user’s endpoint and either another user or a meeting focus. The conversation also exposes a collection of [Microsoft.Lync.Model.Conversation.Participant](https://msdn.microsoft.com/library/jj267311\(v=office.15\)) objects. These participant objects represent the other people who are participating in the conversation. Each **Participant** object exposes a complete collection of modalities. The modalities in a participant’s collection represent the relationship between the local user and the participant who owns the modality object. These modalities are normally used to start modality operations that affect only the local user and the participant on the other end of the relationship.

By default, **InstantMessageModality** is in a **F:Microsoft.Lync.Model.Conversation.ModalityState.Connected** state when a conversation is created. This means that you can send and receive IM text as soon as a conversation starts. The exception to this rule is where one or more of the conversation endpoints is incapable of rendering or capturing IM text. For example, an audio conversation between a Lync 2013 client and a person using a public switched telephone network (PSTN) telephone. As long as all endpoints in a conversation support a given modality, you can activate the modality by calling the [Modality.BeginConnect](https://msdn.microsoft.com/library/jj268193\(v=office.15\)) method. When connected, you can use the conversation mode encapsulated by the modality.

## See also

  - [Core concepts: Lync conversations](core-concepts-lync-conversations.md)

  - [How to: Join a Lync conversation](how-to-join-a-lync-conversation.md)

  - [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md)

  - [How to: Start an automation audio conversation](how-to-start-an-automation-audio-conversation.md)

  - [How to: Start a meet-now meeting](how-to-start-a-meet-now-meeting.md)

