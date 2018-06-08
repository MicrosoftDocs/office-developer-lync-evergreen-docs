---
title: Lync meet-now meeting object model
TOCTitle: Lync meet-now meeting object model
ms:assetid: 9266704b-1bd4-43e5-9b89-dffda681f638
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933116(v=office.15)
ms:contentKeyID: 50877249
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync meet-now meeting object model

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the part of the Microsoft Lync 2013 SDK object model that lets you programmatically start meetings and manage meeting access, the meeting lobby, and meeting presenters.

**Last modified:** April 16, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Getting a Lync 2013 meeting object<br />
Lync SDK meeting object model<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Getting a Lync 2013 meeting object

The Lync 2013 API object model exposes the meeting-specific properties of the Conversation object that represents a Lync 2013 meeting.

A meeting can be a meet-now meeting that is started by using the [Automation.BeginMeetNow](https://msdn.microsoft.com/en-us/library/jj277161\(v=office.15\)) method or a multi-party audio conversation, which is described in [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md). The [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) object is the entry point to the meeting object model. Get this object from a meet-now meeting [Microsoft.Lync.Model.Extensibility.ConversationWindow](https://msdn.microsoft.com/en-us/library/jj293606\(v=office.15\)) object by reading the [ConversationWindow.Conversation](https://msdn.microsoft.com/en-us/library/jj275546\(v=office.15\)) property or getting the Conversation object directly from the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event when the conversation is added by the [ConversationManager.AddConversation](https://msdn.microsoft.com/en-us/library/jj276176\(v=office.15\)) method.

## Lync SDK meeting object model

The following table lists the meeting object model classes in the order that you get them, starting from the meeting object model entry point.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Namespace</p></th>
<th><p>Class</p></th>
<th><p>Purpose</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj278382(v=office.15)">Microsoft.Lync.Model.Extensibility</a></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293816(v=office.15)">Automation</a></p></td>
<td><p>Exposes the <a href="https://msdn.microsoft.com/en-us/library/jj277161(v=office.15)">BeginMeetNow</a> method.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293606(v=office.15)">ConversationWindow</a></p></td>
<td><p>Encapsulates a meeting Lync 2013 conversation window and gives programmatic access to the window and underlying meeting <a href="https://msdn.microsoft.com/en-us/library/jj276988(v=office.15)">Conversation</a> object.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276168(v=office.15)">Microsoft.Lync.Model.Conversation</a></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266018(v=office.15)">ConversationManager</a></p></td>
<td><p>The factory object used to create a new multi-party audio conference programmatically. Use this factory when in UI suppression mode and you are creating a complete meeting UI in your application.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276988(v=office.15)">Conversation</a></p></td>
<td><p>Encapsulates the meeting and exposes methods, properties, and events that you use to manage the meeting programmatically.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267311(v=office.15)">Participant</a></p></td>
<td><p>Encapsulates a meeting attendee. Use this object to mute and unmute a participant, pin or lock participant video, promote or demote, or offer shared resource control.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266982(v=office.15)">ConversationProperty</a></p></td>
<td><p>Enumerates the meeting properties that you can read or write to. The ConferenceAccessInformation enumerator is used to return the <strong>ConferenceAccessInformation</strong> object.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266047(v=office.15)">ConferenceAccessInformation</a></p></td>
<td><p>Encapsulates the meeting access key that you send to users who will &quot;dial in&quot; to an audio conference meeting.</p></td>
</tr>
<tr class="even">
<td><p></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294117(v=office.15)">ConferenceAccessType</a></p></td>
<td><p>Enumerates the conference access rules that you can set on a meeting.</p></td>
</tr>
<tr class="odd">
<td><p></p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277580(v=office.15)">ParticipantProperty</a></p></td>
<td><p>Enumerates the properties that you can read or write for a meeting participant.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Core concepts: Lync meetings](core-concepts-lync-meetings.md)

