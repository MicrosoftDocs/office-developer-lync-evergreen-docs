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

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about making your application UI responsive to the events raised by Microsoft Lync 2013 API application sharing modality in Lync 2013 conversations.


_**Applies to:** Lync 2013 | Lync Server 2013_

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

The events on the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md) class inform you about changes to available resources, resource control requests, sharing participant state changes, and currently sharing participant.


> [!IMPORTANT]
> <P>Application sharing events are raised for all shareable resources, including the user’s desktop and any display attached to the computer. The set of running applications, desktop, and monitors is known as locally shareable resources.</P>



## Application sharing modality events

Handling all application sharing events in your Lync 2013 API-enabled application is critical to the functionality of application sharing. All the events described in this topic are raised on the conversation [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md) object, not on an application sharing modality owned by an individual participant.

### Application sharing modality state and property changed events

The application sharing modality [Modality.ModalityStateChanged](modality-modalitystatechanged-event-microsoft-lync-model-conversation_2.md) event lets you know when the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md) in a conversation is connected and resource sharing can begin. You can monitor the progress of the modality connection operation by handling this event.

To give a user an optimal sharing experience, you should not connect the modality until the local user has selected a resource to share. In the [Modality.ModalityStateChanged](modality-modalitystatechanged-event-microsoft-lync-model-conversation_2.md), start sharing the selected resource if the new state of the modality is [ModalityState](modalitystate-enumeration-microsoft-lync-model-conversation_2.md)**.Connected**. For information about sharing a resource, see [How to: Get a shareable resource and share it in a conversation](how-to-get-a-shareable-resource-and-share-it-in-a-conversation.md).

### Shared resources collection changed

Most of the locally shareable resources on a computer are processes that can be started and stopped by the user at any time. On the other hand, the desktop and attached displays are usually available when the conversation is connected. Use the [ApplicationSharingModality.LocalSharedResourcesChanged](applicationsharingmodality-localsharedresourceschanged-event-microsoft-lync-model-conversation-sharing_2.md) event to catch a notification of a new process or removed process to update the shareable resource list in your UI.

### Resource sharer changed

In a multi-party conversation that has more than one presenter, the current resource sharer changes whenever a presenter shares a resource. Use this event to get and display the name of the participant who is now sharing a resource.


> [!TIP]
> <P>To share a resource, a user uploads and presents a resource that he or she owns. To control a resource, a user requests or is granted control of a resource that is shared by another user.</P>



### Resource controller changed

Your application should always show the name of the current resource controller. Although you can read the [ApplicationSharingModality.Controller](applicationsharingmodality-controller-property-microsoft-lync-model-conversation-sharing_2.md) property to get the participant that is controlling the resource on the sharing stage, you can simply react to the [ApplicationSharingModality.ControllerChanged](applicationsharingmodality-controllerchanged-event-microsoft-lync-model-conversation-sharing_2.md) event to get notification when resource control is changed.

### Resource control request received

The owner of a resource can give permission to another participant to control a resource. Permission can be granted when requested by another user or permission can be offered to another user without a prior request. For information about handling control requests, see [How to: Accept or decline a request to control a shared resource](how-to-accept-or-decline-a-request-to-control-a-shared-resource.md).

## Additional resources

  - [Beyond the basics: Desktop, application, and display sharing](beyond-the-basics-desktop-application-and-display-sharing.md)

