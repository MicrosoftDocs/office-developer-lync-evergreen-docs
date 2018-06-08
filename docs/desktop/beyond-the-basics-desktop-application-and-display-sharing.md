---
title: 'Beyond the basics: Desktop, application, and display sharing'
TOCTitle: Desktop, application, and display sharing
ms:assetid: 6ef40736-5396-4f20-9eae-00450ad1a0ff
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933065(v=office.15)
ms:contentKeyID: 50877195
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Beyond the basics: Desktop, application, and display sharing

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about advanced features of Microsoft Lync 2013 SDK that let you complete the resource sharing experience of Lync 2013 users in your application.

**Last modified:** February 22, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Advanced resource sharing programming<br />
Resource control methods<br />
Resource control events<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Advanced resource sharing programming

While the process of starting to share a local shareable resource is simple, managing the control of a shared resource involves handling events and calling methods on both the conversation application sharing modality and application sharing modalities of individual conversation participants.

## Resource control methods

The following table shows the control actions that a resource sharer can take. A resource viewer cannot take these actions.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Method</p></th>
<th><p>Purpose</p></th>
<th><p>Valid for which modality?</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275295(v=office.15)">ApplicationSharingModality.BeginAcceptControlRequest</a></p></td>
<td><p>Accepts another user’s request to control a locally shared resource.</p></td>
<td><p>Requesting participant modality</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276339(v=office.15)">ApplicationSharingModality.BeginDeclineControlRequest</a></p></td>
<td><p>Declines another user’s request to control a locally shared resource.</p></td>
<td><p>Requesting participant modality</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj274501(v=office.15)">ApplicationSharingModality.BeginGrantControl</a></p></td>
<td><p>Grants control of a locally shared resource to another user.</p>
<div class="alert">
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
<td><p>Granting control to another user does not create an offer that the user can decline. When you have granted control, the other user is automatically in control and must release the control back to you. You can also revoke control.</p></td>
</tr>
</tbody>
</table>
</div></td>
<td><p>Modality of participant to be granted control</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277377(v=office.15)">ApplicationSharingModality.BeginRevokeControl</a></p></td>
<td><p>Revokes control of a resource that was granted or requested by another user.</p></td>
<td><p>Resource controlling participant modality</p></td>
</tr>
</tbody>
</table>

The following table shows the control actions that a resource viewer can take. A resource sharer cannot take these actions.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Method</p></th>
<th><p>Purpose</p></th>
<th><p>Valid for which modality?</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276953(v=office.15)">ApplicationSharingModality.BeginRequestControl</a></p></td>
<td><p>Requests control of a resource that is owned by another user.</p></td>
<td><p>Local participant modality</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293551(v=office.15)">ApplicationSharingModality.BeginReleaseControl</a></p></td>
<td><p>Releases control of a resource that a user has either been granted control of or requested control of. This method cannot be called on an application sharing modality by the owner of a shared resource.</p></td>
<td><p>Local participant modality</p></td>
</tr>
</tbody>
</table>

## Resource control events

The events that are raised on the application sharing modalities in the conversation must be handled to make your application responsive to changes in the state of sharing objects in a conversation. The following table describes the purpose of each of these modality events and which objects (local participant, other participants, or the conversation) to register event callback methods on.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Event</p></th>
<th><p>Purpose</p></th>
<th><p>Which object to register on</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj278080(v=office.15)">Modality.ModalityStateChanged</a></p></td>
<td><p>Raised when an application sharing modality has connected or disconnected in the conversation. You cannot share resources when the modality is disconnected.</p></td>
<td><p>Application sharing modality of all participants, the conversation modality.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293249(v=office.15)">Modality.ActionAvailabilityChanged</a></p></td>
<td><p>Raised when an action such as granting control of a locally shared resource becomes available or is no longer available. This event is typically used to enable or disable resource control action-related buttons in a UI.</p></td>
<td><p>Application sharing modality of all participants, the conversation modality.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277299(v=office.15)">ApplicationSharingModality.ControlRequestReceived</a></p></td>
<td><p>Raised when another user wants to control a resource shared locally by the local user.</p></td>
<td><p>Conversation modality</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293289(v=office.15)">ApplicationSharingModality.ControllerChanged</a></p></td>
<td><p>Raised when the control of the shared resource changes from one user to another.</p></td>
<td><p>Conversation modality</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293494(v=office.15)">ApplicationSharingModality.ParticipationStateChanged</a></p></td>
<td><p>Raised when the local participant requests or releases control of a resource, or grants or revokes control of a locally shared resource.</p></td>
<td><p>Conversation modality</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276856(v=office.15)">ApplicationSharingModality.LocalSharedResourcesChanged</a></p></td>
<td><p>Raised when the local user begins to share a resource or switches from one shared resource to another shared resource.</p></td>
<td><p>Conversation modality</p></td>
</tr>
</tbody>
</table>

## In this section

  - [Application sharing modality event handling](application-sharing-modality-event-handling.md)

## See also

  - [Beyond the basics in Lync 2013 SDK](beyond-the-basics-in-lync-2013-sdk.md)

  - [Core concepts: Desktop, application, and display sharing in Lync SDK](core-concepts-desktop-application-and-display-sharing-in-lync-sdk.md)

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

