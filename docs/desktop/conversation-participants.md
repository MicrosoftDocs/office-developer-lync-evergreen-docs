---
title: Conversation participants
TOCTitle: Conversation participants
ms:assetid: a06cc993-fe0a-4ae5-8e35-b35a3ae4bb37
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933151(v=office.15)
ms:contentKeyID: 50877290
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Conversation participants

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about how Microsoft Lync 2013 SDK represents the people who are participating in a Microsoft Lync 2013 conversation.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Conversation participants<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Conversation participants

People who are participating in Lync 2013 are represented by [Microsoft.Lync.Model.Conversation.Participant](https://msdn.microsoft.com/en-us/library/jj267311\(v=office.15\)) objects in a collection obtained by reading the [Conversation.Participants](https://msdn.microsoft.com/en-us/library/jj293292\(v=office.15\)) property of a **Conversation**. A **Participant** object encapsulates the state of individuals in conversations. For example, the video stream pinned state for a user is exposed by the **Participant** object. Person-specific operations such as admitting or denying meeting access from a meeting lobby are done in the context of an individual **Participant** object. The **Participant** object exposes its own complete set of conversation modalities that encapsulate the IM, audio/video, or sharing interactions between individual conversation participants.

### Inviting participants to a conversation

You can invite a person to a conversation by getting his or her [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object or the [Microsoft.Lync.Model.ContactEndpoint](https://msdn.microsoft.com/en-us/library/jj276722\(v=office.15\)) of a telephone number to be dialed. There is an overload of the **Conversation.AddParticipant** method that is appropriate for the kind of entity that you are adding to the conversation. **Participant** objects are created by the API platform when you call the [Conversation.AddParticipant](https://msdn.microsoft.com/en-us/library/jj266479\(v=office.15\)) (Contact) method or the [Conversation.AddParticipant](https://msdn.microsoft.com/en-us/library/jj266479\(v=office.15\)) (ContactEndpoint) method. After a person or telephone number is added to a conversation and the [Conversation.ParticipantAdded](https://msdn.microsoft.com/en-us/library/jj275759\(v=office.15\)) event is raised, you invite the person by sending an initial IM on the conversation [Microsoft.Lync.Model.Conversation.InstantMessageModality](https://msdn.microsoft.com/en-us/library/jj266036\(v=office.15\)) modality or dial the added telephone number by connecting the conversation [Microsoft.Lync.Model.Conversation.AudioVideo.AVModality](https://msdn.microsoft.com/en-us/library/jj274580\(v=office.15\)).

## See also

  - [Core concepts: Lync conversations](core-concepts-lync-conversations.md)

  - [How to: Join a Lync conversation](how-to-join-a-lync-conversation.md)

  - [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md)

  - [How to: Start an automation audio conversation](how-to-start-an-automation-audio-conversation.md)

  - [How to: Start a meet-now meeting](how-to-start-a-meet-now-meeting.md)

