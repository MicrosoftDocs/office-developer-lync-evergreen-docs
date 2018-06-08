---
title: 'Core concepts: Lync meetings'
TOCTitle: Lync meetings
ms:assetid: 4f8087f1-d1c5-4e88-8a27-a81eee0062a5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933042(v=office.15)
ms:contentKeyID: 50877170
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Core concepts: Lync meetings

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the foundational Microsoft Lync 2013 SDK objects that make up the programmable components of a Microsoft Lync 2013 online meeting.

**Last modified:** December 11, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
What is a Lync 2013 meet-now meeting?<br />
Lync SDK meet-now meeting object model<br />
In this section<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-start-a-new-4775ec38">Start a new conference using the BeginMeetNow method</a></p></td>
</tr>
</tbody>
</table>

## What is a Lync 2013 meet-now meeting?

From the perspective of the developer, a meet-now meeting is a multi-party capable audio conference that is started programmatically with a single method call. There is no need to configure a conference object with the modalities needed to start the meet-now meeting. The call to the [Automation.BeginMeetNow](https://msdn.microsoft.com/en-us/library/jj277161\(v=office.15\)) method starts an operation that activates an audio conference on Microsoft Lync Server 2013 that can be joined immediately. The [Automation.EndMeetNow](https://msdn.microsoft.com/en-us/library/jj278119\(v=office.15\)) method returns a [Microsoft.Lync.Model.Extensibility.ConversationWindow](https://msdn.microsoft.com/en-us/library/jj293606\(v=office.15\)) hosts the meet-now meeting and can be docked in your application. The **ConversationWindow** object gives you programmatic access to the meeting so that you can manage meeting access, presenters, and participant video.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The meet-now meeting is not supported in UI suppression mode.</p></td>
</tr>
</tbody>
</table>

## Lync SDK meet-now meeting object model

The topic in this section describes the Lync 2013 API object model that exposes the meeting-specific properties of the **Conversation** object and other meeting specific objects that encapsulate a meet-now Lync 2013 meeting.

## In this section

  - [Lync meet-now meeting object model](lync-meet-now-meeting-object-model.md)

## See also

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [What you can do with Lync meetings](what-you-can-do-with-lync-meetings.md)

  - [Beyond the basics: Lync meetings](beyond-the-basics-lync-meetings.md)

