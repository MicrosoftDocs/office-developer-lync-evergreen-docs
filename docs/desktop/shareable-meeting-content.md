---
title: Shareable meeting content
TOCTitle: Shareable meeting content
ms:assetid: 1a12549b-68ba-4d56-ad33-ba07f8ac8250
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937271(v=office.15)
ms:contentKeyID: 50877087
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Shareable meeting content

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the nature of shareable content in a Microsoft Lync 2013 conversation and what content sharing feature that Microsoft Lync 2013 SDK lets you build into your application.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Working with shareable content<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

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
<td><p>The Lync 2013 API does not support content sharing when Lync 2013 is running in UI suppression mode.</p></td>
</tr>
</tbody>
</table>

## Working with shareable content

Microsoft Lync 2013 SDK lets you create collaboration features in your application that let users control the content sharing stage in a conversation. Programmable features include starting whiteboard sessions, uploading and sharing PowerPoint slide decks, saving or clearing annotations, choosing content presenters, and attaching files on the sharing stage of a Microsoft Lync 2013 conversation window. You can use the API to build programmatic control over the sharing stage of the conversation window.

Figure 1 shows the Lync 2013 conversation window with the content sharing stage management dialog. This dialog lets you add any of the displayed types to the conversation sharing stage. In addition, you can change the presenter of the shared content from this dialog. The Lync 2013 API gives you programmable types from the [Microsoft.Lync.Model.Conversation.Sharing](https://msdn.microsoft.com/en-us/library/jj274504\(v=office.15\)) namespace to add the features from this dialog to your application.

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
<td><p>You cannot create or upload a poll using the Lync 2013 API.</p></td>
</tr>
</tbody>
</table>

Figure 1. Content sharing stage content dialog

  
![Lync content stage content bin item manager](images/JJ937271.LyncClientSDK_ContentStageManager(Office.15).jpg "Lync content stage content bin item manager")

To learn about sharing a desktop, monitor, or program, see [Core concepts: Desktop, application, and display sharing in Lync SDK](core-concepts-desktop-application-and-display-sharing-in-lync-sdk.md).

Microsoft Lync 2013 SDK exposes a set of classes in the [Microsoft.Lync.Model.Conversation.Sharing](https://msdn.microsoft.com/en-us/library/jj274504\(v=office.15\)) namespace that let you create and manage the content sharing stages of multiple conversations from a single custom application. This feature is useful in many scenarios, especially where you are required to create a simplified content sharing UI for people who are not familiar with the Lync 2013 conversation window UI.

## See also

  - [Core concepts: Content sharing in Lync SDK](core-concepts-content-sharing-in-lync-sdk.md)

  - [What you can do with content sharing](what-you-can-do-with-content-sharing.md)

  - [Beyond the basics: Content sharing](beyond-the-basics-content-sharing.md)

