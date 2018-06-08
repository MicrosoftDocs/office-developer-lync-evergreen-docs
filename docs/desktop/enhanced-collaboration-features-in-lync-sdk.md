---
title: Enhanced collaboration features in Lync SDK
TOCTitle: Enhanced collaboration features
ms:assetid: 639b64a2-edb4-47dd-b3d1-dc3cd2397e53
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933067(v=office.15)
ms:contentKeyID: 50877197
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Enhanced collaboration features in Lync SDK

![What's new topic](images/JJ937254.mod_icon_whatsnew_long(Office.15).png "What's new topic")

Microsoft Lync 2013 SDK includes new collaboration classes and shows how to use the new classes to add features to an application.

**Last modified:** February 18, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Enhanced collaboration features<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Enhanced collaboration features

The following table describes the new collaboration features in Microsoft Lync 2013 SDK.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Feature</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Meeting video management</p></td>
<td><p>The new meeting video management feature gives you control of the meeting video view while in gallery mode. If you are a meeting attendee or meeting presenter, you can use the Lync 2013 API to pin as many as three participant video streams in the gallery view.</p>
<p>As a meeting presenter, you can use the Lync 2013 API to lock as many as three participant video streams into the gallery views of all meeting participants. A locked video stream overrides video pinning choices made by meeting participants. This allows a meeting presenter, such as a lecturer, to be shown on the video gallery of all meeting attendees regardless of individual pinning choices.</p>
<p>For information about meeting video management, see <a href="get-started-with-lync-meetings.md">Get started with Lync meetings</a>.</p></td>
</tr>
<tr class="even">
<td><p>Resource sharing</p></td>
<td><p>The Lync 2013 API gives you the ability to start and control sharing such resources as a running program, your desktop, or one of your display monitors in either a peer-to-peer conversation or an online meeting.</p>
<p>The shared resource is shown on the content sharing stage of the Microsoft Lync 2013 conversation window for all conversation or meeting participants who have accepted an invitation to share resources. The conversation window content sharing stage is not available when Lync is running in UI suppression mode. For this reason, the new feature can only be used on clients that have disabled UI suppression.</p>
<p>Not only can you share resources with other people, but you can use the Lync 2013 API to grant and revoke control of the resources as well as request and surrender control of resources shared by other people in the conversation or meeting.</p>
<p>For information about resource sharing, see <a href="get-started-with-desktop-application-and-display-sharing.md">Get started with desktop, application, and display sharing</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Data collaboration</p></td>
<td><p>Data collaboration means sharing information in a meeting in such a way that all participants can annotate the shared information. This kind of collaboration works as though everyone was standing in front of a common physical whiteboard in a classroom or meeting room. The Lync 2013 API lets you start multiple whiteboard sessions in a conversation or meeting. Use the API to rotate these sessions onto the content stage for discussion and annotation. When a collaboration discussion is finished, use the API to clear the annotations or save a local image of each annotated whiteboard.</p>
<p>You can also upload and share multiple PowerPoint slide decks in a conversation or meeting. Like the whiteboard, a PowerPoint slide deck can be annotated by participants. Use the API to clear the annotations made to the slide deck. If the signed-in user is a meeting presenter, you can use the API to scroll all meeting participants through the slide deck. If the user is an attendee, use the API to scroll the local view of the slide deck and then return to the meeting presenter’s view.</p>
<p>For information about resource sharing, see <a href="get-started-with-content-sharing.md">Get started with content sharing</a>.</p></td>
</tr>
</tbody>
</table>

## See also

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

