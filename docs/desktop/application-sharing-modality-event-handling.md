---
title: Application sharing modality event handling
TOCTitle: Application sharing modality event handling
ms:assetid: dbb279cf-2f89-4ad1-bc5a-b89841e64a8e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933210(v=office.15)
ms:contentKeyID: 50877353
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Application sharing modality event handling

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about making your application UI responsive to the events raised by Microsoft Lync 2013 API application sharing modality in Lync 2013 conversations.

**Last modified:** January 09, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Event handling overview<br />
Application sharing modality events<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Event handling overview

The events on the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) class inform you about changes to available resources, resource control requests, sharing participant state changes, and currently sharing participant.

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
<td><p>Application sharing events are raised for all shareable resources, including the user’s desktop and any display attached to the computer. The set of running applications, desktop, and monitors is known as locally shareable resources.</p></td>
</tr>
</tbody>
</table>

## Application sharing modality events

Handling all application sharing events in your Lync 2013 API-enabled application is critical to the functionality of application sharing. All the events described in this topic are raised on the conversation [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) object, not on an application sharing modality owned by an individual participant.

### Application sharing modality state and property changed events

The application sharing modality [Modality.ModalityStateChanged](https://msdn.microsoft.com/en-us/library/jj278080\(v=office.15\)) event lets you know when the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) in a conversation is connected and resource sharing can begin. You can monitor the progress of the modality connection operation by handling this event.

To give a user an optimal sharing experience, you should not connect the modality until the local user has selected a resource to share. In the [Modality.ModalityStateChanged](https://msdn.microsoft.com/en-us/library/jj278080\(v=office.15\)), start sharing the selected resource if the new state of the modality is [ModalityState](https://msdn.microsoft.com/en-us/library/jj293265\(v=office.15\))**.Connected**. For information about sharing a resource, see [How to: Get a shareable resource and share it in a conversation](how-to-get-a-shareable-resource-and-share-it-in-a-conversation.md).

### Shared resources collection changed

Most of the locally shareable resources on a computer are processes that can be started and stopped by the user at any time. On the other hand, the desktop and attached displays are usually available when the conversation is connected. Use the [ApplicationSharingModality.LocalSharedResourcesChanged](https://msdn.microsoft.com/en-us/library/jj276856\(v=office.15\)) event to catch a notification of a new process or removed process to update the shareable resource list in your UI.

### Resource sharer changed

In a multi-party conversation that has more than one presenter, the current resource sharer changes whenever a presenter shares a resource. Use this event to get and display the name of the participant who is now sharing a resource.

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
<td><p>To share a resource, a user uploads and presents a resource that he or she owns. To control a resource, a user requests or is granted control of a resource that is shared by another user.</p></td>
</tr>
</tbody>
</table>

### Resource controller changed

Your application should always show the name of the current resource controller. Although you can read the [ApplicationSharingModality.Controller](https://msdn.microsoft.com/en-us/library/jj266020\(v=office.15\)) property to get the participant that is controlling the resource on the sharing stage, you can simply react to the [ApplicationSharingModality.ControllerChanged](https://msdn.microsoft.com/en-us/library/jj293289\(v=office.15\)) event to get notification when resource control is changed.

### Resource control request received

The owner of a resource can give permission to another participant to control a resource. Permission can be granted when requested by another user or permission can be offered to another user without a prior request. For information about handling control requests, see [How to: Accept or decline a request to control a shared resource](how-to-accept-or-decline-a-request-to-control-a-shared-resource.md).

## See also

  - [Beyond the basics: Desktop, application, and display sharing](beyond-the-basics-desktop-application-and-display-sharing.md)

