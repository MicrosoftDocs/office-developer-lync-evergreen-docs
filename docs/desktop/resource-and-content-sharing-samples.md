---
title: Resource and content sharing samples
TOCTitle: Resource and content sharing samples
ms:assetid: fb44c4b7-23f1-4af9-991b-0be413915f5e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933233(v=office.15)
ms:contentKeyID: 50877378
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Resource and content sharing samples

![Code sample topic](images/JJ937254.mod_icon_codesample_long(Office.15).png "Code sample topic")

Learn about the resource sharing and content sharing quick-start samples that are installed with Microsoft Lync 2013 SDK.

**Last modified:** January 14, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Resource sharing samples<br />
Content sharing samples<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Resource sharing samples

The following sample application demonstrates how to share resources in a conversation and then manage user’s control of a shared resource.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Application</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-start-a-927aa595">ShareResources</a></p></td>
<td><p>Demonstrates all of the Lync 2013 API objects used in resource sharing.</p></td>
</tr>
</tbody>
</table>

## Content sharing samples

The following sample application demonstrates how to share whiteboards, PowerPoint slide decks, and native file attachments in a conversation.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Application</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-control-3b9df73f">ContentModalitySample</a></p></td>
<td><p>Shows how to create a conversation and then share a whiteboard and a PowerPoint slide deck. If a PowerPoint slide deck is shared, the sample lets a user scroll forward and backward in the slide deck. The sample uses the following classes, methods, and enumerations:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj274980(v=office.15)">Microsoft.Lync.Model.LyncClient</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj276988(v=office.15)">Microsoft.Lync.Model.Conversation.Conversation</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj266998(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj277217(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ShareableContent</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj277028(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.PowerPointContent</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj267322(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ShareableContentState</a> enumeration</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj277556(v=office.15)">ContentSharingModality.BeginCreateContent</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj277389(v=office.15)">ContentSharingModality.BeginCreateContentFromFile</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj278338(v=office.15)">ShareableContent.Upload</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\ContentSharingModality</p></td>
</tr>
</tbody>
</table>

## Additional resources

  - [Code samples: Lync SDK](code-samples-lync-sdk.md)

