---
title: Conversation window docking
TOCTitle: Conversation window docking
ms:assetid: 5ad30515-ac94-4db7-b87a-742c1a772d60
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933053(v=office.15)
ms:contentKeyID: 50877182
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Conversation window docking

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the Lync 2013 conversation window docking feature that lets you host a conversation window inside a container control in your application by using Microsoft Lync 2013 SDK.

**Last modified:** January 11, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Why dock a Lync conversation window?<br />
Hosting container controls<br />
Window docking events<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Why dock a Lync conversation window?

An application can implement any of the Lync Controls that start an IM or audio/video conversation with a click of a button. In addition, an application can start a Lync 2013 conversation programmatically as long as a user’s SIP address is provided. In these cases, an application can dock the Lync conversation window that encapsulates the conversation. A docked conversation window is confined inside an application UI container control and allows a user to participate in the new conversation without leaving the application. When a conversation window is docked in a container control, the dimensions of the conversation window can be controlled programmatically.

## Hosting container controls

The Lync conversation window is designed to be docked inside a Windows Form or Windows Form container control. To dock a conversation window in a WPF application, add a **WindowsFormsHost** control to the window. Add a container control such as a Panel control inside the **WindowsFormsHost** control and then dock the conversation window in the panel.

**Figure 1** shows a conversation window that is docked inside a **WindowsFormsHost** control-hosted **Panel** control. For comparison, an undocked conversation window for another conversation is shown on the right side of the WPF window. The docked conversation is now a component of the parent window and cannot be independently resized. The system buttons and window title are removed from docked conversations.

The dimensions of a container control are set at design time and should be larger than the default dimensions of the Lync conversation window. When the conversation window is docked in the container, it expands to fill the control. If the container is too small to fit the default conversation window, the conversation window pops out of the container. A Lync 2013 API event is raised when the docked conversation window discovers that the parent container control is too small to contain the conversation window. Five seconds after the event is raised, the conversation window undocks. You can prevent undocking by resizing the container control to fit the conversation window.

After a conversation window was docked in a container control that is large enough to hold the conversation window, a user can manually resize the container control to make it larger. When this happens, the conversation window does not respond to the size change. To make the conversation window fill the container control again, you must dock the conversation window again even though it has not undocked. This means that you must catch size changing events on the container control so that you can respond to the container resize.

It is a good idea to dock the conversation window inside a container control whose parent is a scrollable control. If you design your window in this manner, changes in the dimension of the conversation window do not require changes in the dimension of your application window. Instead, scroll bars appear on the parent container control.

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
<td><p>If the container control is nested in a scrollable control, the container control must still be redimensioned when the user adds a visual element to the conversation window. If the new container dimensions exceed its design time dimensions, horizontal and vertical scroll bars appear as appropriate.</p></td>
</tr>
</tbody>
</table>

Figure 1. Side-by-side view of a docked conversation window and an undocked conversation window

  
![Side by side view of a docked conversation window](images/JJ933086.LyncClientSDK_ConversationWindowDocking(Office.15).jpg "Side by side view of a docked conversation window")

## Window docking events

The conversation window exposes two events related to docking. The first event is raised when the parent container control is too small to contain the conversation window. The second event is raised when there is new activity in the conversation window and the form that hosts the container control does not have the focus.

### NeedsSizeChange event

The [ConversationWindow.NeedsSizeChange](https://msdn.microsoft.com/en-us/library/jj277925\(v=office.15\)) event is raised when a conversation participant has changed the size of the conversation window by adding a visual element such as a video window or the content sharing stage. The event is raised whether the parent container control is large enough to contain the new size of the conversation window or not. If the surface area of the parent container control is not large enough to contain the resized conversation window, then the conversation window automatically undocks five seconds after the event is raised. To avoid undocking the conversation window, use the event callback method to resize the container control by setting its dimensions to either the minimum size or recommended size specified in the event data.

This event provides three sets of dimensions that you select among to set the new size of a container control. The three dimension sets include the following types:

  - Minimum size. This is the minimum size of a container control that can dock the newly resized conversation window.

  - Maximum size. This is the largest possible dimension of the conversation window, given the connected conversation modalities.

  - Recommended size. This is the optimal container control dimension.

The example found in [How to: Dock a conversation window in Lync SDK](how-to-dock-a-conversation-window-in-lync-sdk.md) uses the minimum size values to redimension the hosting Panel control. The maximum size and recommended sizes are not used in the sample.

### NeedsAttention event

This event can be raised when an application window does not have the focus and has docked a conversation window. The conversation window needs attention after a visual element of the conversation window is added, a new invitation prompt is displayed, or an IM message has arrived. The [ConversationWindow.NeedsAttention](https://msdn.microsoft.com/en-us/library/jj276832\(v=office.15\)) event is raised to signal the parent window that it must start flashing its border to warn the user.

## Additional resources

  - [Beyond the basics: Lync conversations](beyond-the-basics-lync-conversations.md)

  - [How to: Dock a conversation window in Lync SDK](how-to-dock-a-conversation-window-in-lync-sdk.md)

