---
title: Understanding Lync Controls
TOCTitle: Understanding Lync Controls
ms:assetid: a6786758-e4e5-4c22-b348-ac3cb81b3e49
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933133(v=office.15)
ms:contentKeyID: 50877275
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Understanding Lync Controls

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Use Microsoft Lync Controls to integrate Microsoft Lync 2013 features such as search, presence, instant messaging (IM) calls, and voice calls into .NET applications and Microsoft Silverlight browser applications.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Implement features with Lync Controls<br />
Application options<br />
Lync Controls<br />
Additional resources</p></td>
<td><div class="caption">
Watch the video: Add Lync Controls to a Web Application
</div>
<br />
&gt; [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/c3d4ed0f-b3c8-43c4-af53-36425f014575]</td>
</tr>
</tbody>
</table>


## Implement features with Lync Controls

With Lync Controls, application developers can implement many of the features that are supported by Lync 2013:

  - Integrate Lync Controls into a Web browser application that runs a Silverlight browser application.

  - Use Microsoft Windows Presentation Foundation (WPF) to integrate Lync Controls into a .NET application.

  - Display presence status for colleagues, customers, and vendors.

  - Launch IM, voice, and video calls in Lync 2013, and perform application and file sharing in calls.

  - Search for members within an organization's address list or site.

  - Display contact information for colleagues, customers, and vendors.

  - Display the user’s current presence status selection and note string entry.


> [!NOTE]
> <P>Use Lync Controls to launch calls in the Lync 2013 conversation window. Inbound calls are handled by Lync 2013.</P>




> [!NOTE]
> <P>If UI suppression is turned on, Lync Controls are disabled as if you have signed out of your Lync 2013 session. For more information, see <A href="ui-suppression.md">UI suppression</A>.</P>




> [!NOTE]
> <P>Security settings for Microsoft Lync 2013 SDK applications require you to add the host URL for Lync Control Silverlight applications to the Trusted sites list in Microsoft Internet Explorer. For more information about adding to the Trusted sites list, see <A href="http://windows.microsoft.com/en-us/windows-vista/change-internet-explorer-security-settings">Change Internet Explorer Security Settings</A>.</P>



## Application options

To add Lync Controls to an existing Silverlight application, add project references for the Lync Control DLLs and add XAML code to create the Lync Controls. Only Microsoft Internet Explorer 7 and later versions support Lync 2013 Silverlight controls. For more information, see [How to: Add enhanced presence to a Web application](how-to-add-enhanced-presence-to-a-web-application.md).

## Lync Controls

Use the following Lync Controls to implement Lync 2013 features in applications.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Lync Control</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="presenceindicator-control.md">PresenceIndicator control</a></p></td>
<td><p>The <a href="presenceindicator-class-microsoft-lync-controls_1.md">PresenceIndicator</a> control displays one of several icons that indicate the presence of a given user.</p></td>
</tr>
<tr class="even">
<td><p><a href="mystatusarea-control.md">MyStatusArea control</a></p></td>
<td><p>Use the <a href="mystatusarea-class-microsoft-lync-controls_1.md">MyStatusArea</a> control in Microsoft Lync Control applications to display the note string, an availability icon/photo, a textblock with the user’s name, and a textblock with the user’s location.</p></td>
</tr>
<tr class="odd">
<td><p><a href="mypresencechooser-control.md">MyPresenceChooser control</a></p></td>
<td><p>Use the <a href="mypresencechooser-class-microsoft-lync-controls_1.md">MyPresenceChooser</a> control in Microsoft Lync Control applications to display and change the user’s current presence status selection.</p></td>
</tr>
<tr class="even">
<td><p><a href="mynotebox-control.md">MyNoteBox control</a></p></td>
<td><p>Use the <a href="mynotebox-class-microsoft-lync-controls_1.md">MyNoteBox</a> control in Microsoft Lync Control applications to display and change the current user’s personal note.</p></td>
</tr>
<tr class="odd">
<td><p><a href="startinstantmessagingbutton-control.md">StartInstantMessagingButton control</a></p></td>
<td><p>Use the <a href="startinstantmessagingbutton-class-microsoft-lync-controls_1.md">StartInstantMessagingButton</a> control in Microsoft Lync Control applications to enable the user to open a Microsoft Lync 2013 conversation window and start an IM conversation between the user who activated the control and another user specified by the Source property.</p></td>
</tr>
<tr class="even">
<td><p><a href="startvideocallbutton-control.md">StartVideoCallButton control</a></p></td>
<td><p>Use the <a href="startvideocallbutton-class-microsoft-lync-controls_1.md">StartVideoCallButton</a> control in Microsoft Lync 2013 SDK applications to launch a video conversation between the user who activated the control and another user specified by the Source property.</p></td>
</tr>
<tr class="odd">
<td><p><a href="schedulemeetingbutton-control.md">ScheduleMeetingButton control</a></p></td>
<td><p>Use the <a href="schedulemeetingbutton-class-microsoft-lync-controls_1.md">ScheduleMeetingButton</a> control in Microsoft Lync Control applications to open a Microsoft Outlook meeting invite dialog box.</p></td>
</tr>
<tr class="even">
<td><p><a href="startaudiocallbutton-control.md">StartAudioCallButton control</a></p></td>
<td><p>Use the <a href="startaudiocallbutton-class-microsoft-lync-controls_1.md">StartAudioCallButton</a> control in Microsoft Lync Control applications to enable the user to open a Microsoft Lync 2013 conversation window and start a voice conversation between the user who activated the control and another user.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sendemailbutton-control.md">SendEmailButton control</a></p></td>
<td><p>Use the <a href="sendemailbutton-class-microsoft-lync-controls_1.md">SendEmailButton</a> control in Microsoft Lync Control applications to start Microsoft Outlook and compose an email to a selected contact.</p></td>
</tr>
<tr class="even">
<td><p><a href="sendfilebutton-control.md">SendFileButton control</a></p></td>
<td><p>Use the <a href="sendfilebutton-class-microsoft-lync-controls.md">SendFileButton</a> control in Microsoft Lync Control applications to launch a conversation with a specified contact and open a file selection dialog where the user can select a file to transfer to the contact.</p></td>
</tr>
<tr class="odd">
<td><p><a href="sharedesktopbutton-control.md">ShareDesktopButton control</a></p></td>
<td><p>Use the <a href="sharedesktopbutton-class-microsoft-lync-controls_1.md">ShareDesktopButton</a> control in Microsoft Lync 2013 SDK applications to launch desktop sharing between the user who activated the control and another user or group specified by the Source property.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-control.md">ContactCard control</a></p></td>
<td><p>Use the <a href="contactcard-class-microsoft-lync-controls_1.md">ContactCard</a> control to show basic or detailed contact and organization information for contacts.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-control.md">ContactList control</a></p></td>
<td><p>Use the <a href="contactlist-class-microsoft-lync-controls_1.md">ContactList</a> control to display the Microsoft Lync 2013 contacts list and give users the ability to launch voice, instant messaging (IM), or email conversations with any of their contacts.</p></td>
</tr>
<tr class="even">
<td><p><a href="customcontactlist-control.md">CustomContactList control</a></p></td>
<td><p>Use the <a href="customcontactlist-class-microsoft-lync-controls_1.md">CustomContactList</a> control to provide an arbitrary and non-hierarchical display of contacts and groups for specific contexts.</p></td>
</tr>
<tr class="odd">
<td><p><a href="customcontactlistitem-control.md">CustomContactListItem control</a></p></td>
<td><p>Use the <a href="customcontactlistitem-class-microsoft-lync-controls_1.md">CustomContactListItem</a> control with the CustomContactList control to show basic or detailed contact and organization information for contacts.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactsearch-control.md">ContactSearch control</a></p></td>
<td><p>Use the <a href="contactsearch-class-microsoft-lync-controls_1.md">ContactSearch</a> control in Microsoft Lync Control applications to display the ContactSearchInputBox and ContactSearchResultList controls together in the same location on a page.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactsearchinputbox-control.md">ContactSearchInputBox control</a></p></td>
<td><p>Use the <a href="contactsearchinputbox-class-microsoft-lync-controls_1.md">ContactSearchInputBox</a> control to enable users to search their organization for people based on name, phone number, or skill.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactsearchresultlist-control.md">ContactSearchResultList control</a></p></td>
<td><p>Use the <a href="contactsearchresultlist-class-microsoft-lync-controls_1.md">ContactSearchResultList</a> control to display the result of a search performed by the ContactSearchInputBox control.</p></td>
</tr>
</tbody>
</table>


## Additional resources

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [Lync Controls reference](lync-controls-reference.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

