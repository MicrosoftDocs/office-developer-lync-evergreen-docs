---
title: Sharing resources in a conversation
TOCTitle: Sharing resources in a conversation
ms:assetid: 45c3e50a-ac07-4e31-84d1-f944efb9d9e7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937307(v=office.15)
ms:contentKeyID: 50877138
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Sharing resources in a conversation

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about programmatically sharing a computer monitor, desktop, or running program with another Microsoft Lync 2013 user in a conversation window by using classes in Microsoft Lync 2013 SDK.

**Last modified:** April 16, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p>
<p><strong>In this article</strong><br />
Resource sharing overview<br />
Working with shareable resources<br />
Working with sharing conversation modality objects<br />
Next steps<br />
Additional resources</p></td>
<td></td>
</tr>
</tbody>
</table>

## Resource sharing overview

Microsoft Lync 2013 SDK lets you start system resource sharing and manage user control of a shared resource on the sharing stage of a Microsoft Lync 2013 conversation window. The only way for a user to see shared resources in a conversation is to open a Lync 2013 conversation window on the desktop. The Lync 2013 API does not provide a control that you can drop into your application UI. However, you can use the API to build programmatic control over the sharing stage of the conversation window.

The [Microsoft.Lync.Model.Conversation.Sharing](https://msdn.microsoft.com/en-us/library/jj274504\(v=office.15\)) namespace contains the classes and enumerations that you use in resource sharing. Figure 1 shows a running process shared on the Lync 2013 sharing stage and visible to all conversation participants.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A shared resource is visible on the sharing stage for all conversation participants to view. A user must be aware that sensitive information can be seen by other participants when a resource such as a desktop, running process, or display is shared. When another user is granted control of a locally shared resource, the controlling user has the same access to the content within the resource that the owner does.</p></td>
</tr>
</tbody>
</table>

Figure 1. Lync client sharing stage with running process

  
![Lync Client sharing stage with shared process](images/JJ937307.UC_OCS15ConLyncClient_ResourceSharingfigure1(Office.15).jpg "Lync Client sharing stage with shared process")

In general, you program by using the following kinds of Lync 2013 API objects:

  - Shareable resource objects such as a running process or desktop.

  - Sharing conversation modality objects.

  - Conversation participant objects.

Each of these objects expose methods, events, and properties that you use to manage the resource sharing process. Most of the code that you write for resource sharing handles events on the sharing modalities.

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
<td><p>The Lync 2013 API does not support resource sharing when Lync 2013 is running in UI suppression mode.</p></td>
</tr>
</tbody>
</table>

## Working with shareable resources

A shareable resource can be the local desktop, any display attached to the local workstation, or a running process such as Notepad.exe. Although a computer can have any number of shareable resources, only one of these resources can be shared in a conversation at a time. In addition, only one conversation participant can share a resource at a time. A shared resource that is under the control of the resource owner is not considered controlled. It is only when the control of the resource is given to another user that the resource is considered controlled. The shared conversation resource can be controlled by one user at a time. Resource control amounts to giving the controlling user access to the local mouse and keyboard in the context of the shared resource. For example, if a running process has a UI with a **Close** button, the controlling user can click the button with the controlled mouse and close the process.

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
<td><p>A resource sharer is a conversation presenter who is sharing a local resource with other conversation participants. A resource viewer is a presenter or attender who is viewing a resource shared by a different conversation participant.</p></td>
</tr>
</tbody>
</table>

### Maintaining a list of locally shareable resources

A locally shareable collection of resources includes the desktop, monitors, and any UI-based processes that are running when a conversation is started and the conversation application sharing modality is connected. You are not notified when new processes are started after the application sharing modality is connected. To refresh a shareable resource list, you must read the [ShareableResources](https://msdn.microsoft.com/en-us/library/jj278380\(v=office.15\)) property.

## Working with sharing conversation modality objects

When a resource control action is available, the methods that you invoke to take an available action are exposed on the [ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) object. The conversation and each conversation participant own an application sharing modality. There are restrictions on which actions you can invoke on a given application sharing modality. Similarly, application sharing modality events are exposed on the conversation and participant application sharing modalities but not all modality events are raised on all of these modalities. In addition, not all application sharing modality operations are valid for all of the application sharing modality objects in a conversation.

This section tells you which modality events you should register for on which application sharing modality objects in the conversation and which operations are valid for each application sharing modality object.

This modality event handling code is invoked for the following kinds of modality state changes:

  - The availability of a resource control action is changed.

  - The user who controls a shared resource is changed.

  - A user is requesting control of a resource that is shared locally.

  - The locally shared resource is swapped for a different local shareable resource or a local resource is no longer shared.

  - The sharing modality connection state changes as a conversation starts or ends.

  - The local user shares, grants, or revokes control of a locally shared resource.

### Application sharing modality methods

The following tables show all of the methods that can be called on the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) object. The first table shows methods that start resource sharing. The second and third tables show methods that are related to controlling a shared resource.

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
<td><p>Pay attention to the third column of the following tables. You must invoke the methods on the correct <a href="https://msdn.microsoft.com/en-us/library/jj275536(v=office.15)">ApplicationSharingModality</a> object.</p></td>
</tr>
</tbody>
</table>

The methods in the following table let you share resources. Control of locally shared resources can be managed by using the control-related application sharing methods.

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
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275900(v=office.15)">BeginShareDesktop</a></p></td>
<td><p>Shares the user’s desktop and replaces the currently shared resource on the shared content stage regardless of the intent of the owner of the current resource.</p></td>
<td><p>Conversation modality</p></td>
</tr>
<tr class="even">
<td><p><strong>BeginShareMonitor</strong></p></td>
<td><p>Shares a display and replaces the currently shared resource on the shared content stage regardless of the intent of the owner of the current resource.</p></td>
<td><p>Conversation modality</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275502(v=office.15)">BeginShareResources</a></p></td>
<td><p>Shares a resource and replaces the currently shared resource on the shared content stage regardless of the intent of the owner of the current resource.</p></td>
<td><p>Conversation modality</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276997(v=office.15)">CanShare</a></p></td>
<td><p>Checks to see whether the specified resource type can be shared before you try to share resources of the specified type.</p></td>
<td><p>Conversation modality</p></td>
</tr>
</tbody>
</table>

## Next steps

  - [How to: Accept or decline a request to control a shared resource](how-to-accept-or-decline-a-request-to-control-a-shared-resource.md)

  - [How to: Grant and revoke control of a shared resource](how-to-grant-and-revoke-control-of-a-shared-resource.md)

  - [How to: Request and release control of a shared resource](how-to-request-and-release-control-of-a-shared-resource.md)

## Additional resources

  - [Core concepts: Desktop, application, and display sharing in Lync SDK](core-concepts-desktop-application-and-display-sharing-in-lync-sdk.md)

  - [Beyond the basics: Desktop, application, and display sharing](beyond-the-basics-desktop-application-and-display-sharing.md)

