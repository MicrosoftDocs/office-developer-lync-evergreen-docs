---
title: Lync state affects Lync Controls
TOCTitle: Lync state affects Lync Controls
ms:assetid: e927e77f-6809-41ca-affe-7baf139e8bae
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933218(v=office.15)
ms:contentKeyID: 50877365
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync state affects Lync Controls

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn how the state of Microsoft Lync 2013 affect Microsoft Lync 2013 Controls.

**Last modified:** February 22, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Lync state overview<br />
PresenceIndicator control<br />
MyStatusArea control<br />
MyPresenceChooser control<br />
MyNoteBox control<br />
StartInstantMessagingButton control<br />
StartVideoCallButton control<br />
ScheduleMeetingButton control<br />
StartAudioCallButton control<br />
SendEmailButton control<br />
SendFileButton control<br />
ShareDesktopButton control<br />
ContactCard control<br />
ContactList control<br />
CustomContactList control<br />
CustomContactListItem control<br />
ContactSearch control<br />
ContactSearchButtonInputBox control<br />
ContactSearchResultList control<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Lync state overview

Microsoft Lync Controls depend on Microsoft Lync 2013 for presence and contact information. At any moment Lync 2013 can be in a number of different states. For example, Lync 2013 can be signed in or signed out, or unable to connect to the WAN or the presence server. All of these states affect Lync Controls. The following sections describe how each control responds to the different states.

Lync Controls do not show state errors and other error notices; these appear in the Lync 2013 UI.

Branch office resiliency refers to the ability of Lync Controls to handle connectivity failures. Lync Controls enter branch office resiliency mode when full connectivity to Lync Server 2013, the WAN, or the datacenter is not available.

The term disabled describes a control’s state when Lync 2013 is not running. For example, in a PresenceIndicator control the contact name changes to "Unknown Contact" and a contact card does not appear.

## PresenceIndicator control

The following table describes how the PresenceIndicator control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 is not running.</p></td>
<td><p>PresenceIndicator control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed out.</p></td>
<td><p>PresenceIndicator control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing in.</p></td>
<td><p>PresenceIndicator control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed in.</p></td>
<td><p>PresenceIndicator control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing out.</p></td>
<td><p>PresenceIndicator control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Lync is not a Lync 2013 client.</p></td>
<td><p>PresenceIndicator control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switched user.</p></td>
<td><p>All cached information is cleared and new information appears.</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 connectivity is lost.</p></td>
<td><p>PresenceIndicator control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>URI is invalid.</p></td>
<td><p>Presence is set to &quot;unknown contact&quot; state.</p></td>
</tr>
<tr class="even">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>Presence state changes to unknown and the control and all subcontrols remain enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Normal mode.</p></td>
<td><p>Presence state is updated for the currently signed-in user.</p></td>
</tr>
<tr class="even">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
</tbody>
</table>

## MyStatusArea control

The following table describes how the MyStatusArea control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>MyStatusArea control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 is not running.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed out.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing in.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed in.</p></td>
<td><p>MyStatusArea control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing out.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync is not a Lync 2013 client.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switched user.</p></td>
<td><p>All cached information is cleared and new information appears.</p></td>
</tr>
<tr class="even">
<td><p>UI suppression is activated.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>MyStatusArea control is disabled.</p></td>
</tr>
</tbody>
</table>

## MyPresenceChooser control

The following table describes how the MyPresenceChooser control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>MyPresenceChooser control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 is not running.</p></td>
<td><p>MyPresenceChooser control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed out.</p></td>
<td><p>MyPresenceChooser control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing in.</p></td>
<td><p>MyPresenceChooser control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed in.</p></td>
<td><p>MyPresenceChooser control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing out.</p></td>
<td><p>MyPresenceChooser control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync is not a Lync 2013 client.</p></td>
<td><p>MyPresenceChooser control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switched user.</p></td>
<td><p>All cached information is cleared and new information appears.</p></td>
</tr>
<tr class="even">
<td><p>UI suppression is activated.</p></td>
<td><p>MyPresenceChooser control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>MyPresenceChooser control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>MyPresenceChooser control is enabled.</p></td>
</tr>
</tbody>
</table>

## MyNoteBox control

The following table describes how the MyNoteBox control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>MyNoteBox control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 is not running.</p></td>
<td><p>MyNoteBox control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed out.</p></td>
<td><p>MyNoteBox control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing in.</p></td>
<td><p>MyNoteBox control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is signed in.</p></td>
<td><p>MyNoteBox control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is signing out.</p></td>
<td><p>MyNoteBox control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync is not a Lync 2013 client.</p></td>
<td><p>MyNoteBox control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switched user.</p></td>
<td><p>All cached information is cleared and new information appears.</p></td>
</tr>
<tr class="even">
<td><p>UI suppression is activated.</p></td>
<td><p>MyNoteBox control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>MyNoteBox control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>MyNoteBox control is enabled.</p></td>
</tr>
</tbody>
</table>

## StartInstantMessagingButton control

The following table describes how the StartInstantMessagingButton control responds to changes in the Lync 2013 state. If instant messaging is not available, StartInstantMessagingButton control is disabled.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>StartInstantMessagingButton control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>StartInstantMessagingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>StartInstantMessagingButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>StartInstantMessagingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>StartInstantMessagingButton control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>StartInstantMessagingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>URI is invalid.</p></td>
<td><p>StartInstantMessagingButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is not a Lync Server 2013 client.</p></td>
<td><p>StartInstantMessagingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>If cached information is available it appears. All capability settings are respected. All conferencing capabilities are disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>URI resolution is updated. All capability settings are respected. Conferencing capabilities are enabled.</p></td>
</tr>
</tbody>
</table>

## StartVideoCallButton control

The following table describes how the StartVideoCallButton control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>StartVideoCallButton control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>StartVideoCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>StartVideoCallButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>StartVideoCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>StartVideoCallButton control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>StartVideoCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>URI is invalid.</p></td>
<td><p>StartVideoCallButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>StartVideoCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>If cached information is available it appears. All capability settings are respected. All conferencing capabilities are disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>URI resolution is updated. Conferencing capabilities are enabled.</p></td>
</tr>
</tbody>
</table>

## ScheduleMeetingButton control

The following table describes how the ScheduleMeetingButton control responds to changes in the Lync 2013 state. If instant messaging is not available, ScheduleMeetingButton control is disabled.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>ScheduleMeetingButton control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>ScheduleMeetingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>ScheduleMeetingButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>ScheduleMeetingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>ScheduleMeetingButton control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>ScheduleMeetingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>URI is invalid.</p></td>
<td><p>ScheduleMeetingButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>ScheduleMeetingButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>ScheduleMeetingButton control is enabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>URI resolution is updated. All capability settings are respected. Conferencing capabilities are enabled.</p></td>
</tr>
</tbody>
</table>

## StartAudioCallButton control

The following table describes how the StartAudioCallButton control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>StartAudioCallButton control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>StartAudioCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>StartAudioCallButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>StartAudioCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>StartAudioCallButton control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>StartAudioCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>URI is invalid.</p></td>
<td><p>StartAudioCallButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>StartAudioCallButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>If cached information is available it appears. All capability settings are respected. All conferencing capabilities are disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>URI resolution is updated. Conferencing capabilities are enabled.</p></td>
</tr>
</tbody>
</table>

## SendEmailButton control

The following table describes how the SendEmailButton control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>SendEmailButton control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>SendEmailButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>SendEmailButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>SendEmailButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>SendEmailButton control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>SendEmailButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>URI is invalid.</p></td>
<td><p>SendEmailButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>SendEmailButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>SendEmailButton control is enabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>URI resolution is updated. Conferencing capabilities are enabled.</p></td>
</tr>
</tbody>
</table>

## SendFileButton control

The following table describes how the SendFileButton control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>SendFileButton control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>SendFileButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>SendFileButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>SendFileButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>SendFileButton control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>SendFileButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>URI is invalid.</p></td>
<td><p>SendFileButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>SendFileButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>If cached information is available it appears. All capability settings are respected. All conferencing capabilities are disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>URI resolution is updated. Conferencing capabilities are enabled.</p></td>
</tr>
</tbody>
</table>

## ShareDesktopButton control

The following table describes how the ShareDesktopButton control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>ShareDesktopButton control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>ShareDesktopButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>ShareDesktopButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>ShareDesktopButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>ShareDesktopButton control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>ShareDesktopButton control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>ShareDesktopButton control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="even">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>If cached information is available it appears. All capability settings are respected. All conferencing capabilities are disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Normal mode.</p></td>
<td><p>URI resolution is updated. Conferencing capabilities are enabled.</p></td>
</tr>
</tbody>
</table>

## ContactCard control

The following table describes how the ContactCard control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>ContactCard control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 available but not signed in.</p></td>
<td><p>ContactCard control is disabled. The contact and presence are shown as unknown.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 signed in.</p></td>
<td><p>ContactCard control enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 signed out.</p></td>
<td><p>ContactCard control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is not available.</p></td>
<td><p>ContactCard control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>URI is invalid.</p></td>
<td><p>Presence is set to unknown and ContactCard control is enabled.</p></td>
</tr>
<tr class="even">
<td><p>Presence server outage.</p></td>
<td><p>Presence information is set to unknown and communication methods are enabled.</p></td>
</tr>
<tr class="odd">
<td><p>WAN outage.</p></td>
<td><p>Presence is set to unknown and the ContactCard control remains enabled.</p></td>
</tr>
<tr class="even">
<td><p>Datacenter outage.</p></td>
<td><p>Presence is set to unknown and the ContactCard control remains enabled.</p></td>
</tr>
<tr class="odd">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
</tbody>
</table>

## ContactList control

The following table describes how the ContactList control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>ContactList control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>ContactList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out</p></td>
<td><p>ContactList control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>ContactList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>ContactList control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>ContactList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>ContactList control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="even">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>ContactList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>ContactList control is enabled and repopulated.</p></td>
</tr>
</tbody>
</table>

## CustomContactList control

The following table describes how the CustomContactList control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>CustomContactList control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 client available, not signed in.</p></td>
<td><p>CustomContactList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Signed in.</p></td>
<td><p>CustomContactList control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Signed out.</p></td>
<td><p>CustomContactList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 client not available.</p></td>
<td><p>CustomContactList control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
<tr class="even">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>Presence state moves to Presence unknown for all users.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Normal mode.</p></td>
<td><p>Presence state is updated for subcontrols.</p></td>
</tr>
</tbody>
</table>

## CustomContactListItem control

The following table describes how the CustomContactListItem control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>CustomContactListItem control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 client available, not signed in.</p></td>
<td><p>CustomContactListItem control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Signed in.</p></td>
<td><p>CustomContactListItem control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Signed out.</p></td>
<td><p>CustomContactListItem control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 client not available.</p></td>
<td><p>CustomContactListItem control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>URI is invalid.</p></td>
<td><p>Entity is disabled.</p></td>
</tr>
<tr class="even">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>Presence state moves to Presence unknown.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>Presence state is updated.</p></td>
</tr>
</tbody>
</table>

## ContactSearch control

The following table describes how the ContactSearch control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>ContactSearch control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>ContactSearch control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>ContactSearch control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>ContactSearch control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>ContactSearch control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>ContactSearch control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>ContactSearch control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 connectivity is lost.</p></td>
<td><p>ContactSearch control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
<tr class="even">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>Presence state reverts to unknown for all users. Hover, contact card, and menus remain enabled. Results continue to be shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Normal mode.</p></td>
<td><p>Add button is enabled, presence is refreshed.</p></td>
</tr>
</tbody>
</table>

## ContactSearchInputBox control

The following table describes how the ContactSearchInputBox control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>ContactSearchInputBox control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>ContactSearchInputBox control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out</p></td>
<td><p>ContactSearchInputBox control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>ContactSearchInputBox control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>ContactSearchInputBox control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>ContactSearchInputBox control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>ContactSearchInputBox control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="even">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>No action taken.</p></td>
</tr>
<tr class="even">
<td><p>Entering Normal mode.</p></td>
<td><p>No action taken.</p></td>
</tr>
</tbody>
</table>

## ContactSearchResultList control

The following table describes how the ContactSearchResultList control responds to changes in the Lync 2013 state.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync 2013 state</p></th>
<th><p>ContactSearchResultList control state</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013 not running.</p></td>
<td><p>ContactSearchResultList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed out.</p></td>
<td><p>ContactSearchResultList control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing in.</p></td>
<td><p>ContactSearchResultList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 running, signed in.</p></td>
<td><p>ContactSearchResultList control is enabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 running, signing out.</p></td>
<td><p>ContactSearchResultList control is disabled.</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 is not an Lync Server 2013 client.</p></td>
<td><p>ContactSearchResultList control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2013 switches user.</p></td>
<td><p>All cached information cleared and new information is shown.</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 connectivity is lost.</p></td>
<td><p>ContactSearchResultList control is disabled.</p></td>
</tr>
<tr class="odd">
<td><p>UI suppression is activated.</p></td>
<td><p>Lync Controls are disabled when UI suppression is activated.</p></td>
</tr>
<tr class="even">
<td><p>Entering Branch Office Resiliency mode.</p></td>
<td><p>Presence state reverts to unknown for all users. In-line expansion, hover, contact card, and menus remain enabled. Results continue to be shown.</p></td>
</tr>
<tr class="odd">
<td><p>Entering Normal mode.</p></td>
<td><p>Add button is enabled, presence is refreshed.</p></td>
</tr>
</tbody>
</table>

## Additional resources

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [Lync Controls reference](lync-controls-reference.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

