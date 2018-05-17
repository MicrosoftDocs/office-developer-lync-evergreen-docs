---
title: Expanded code samples
TOCTitle: Expanded code samples
ms:assetid: 0b432c67-2179-4240-84d3-dc5acc966098
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937259(v=office.15)
ms:contentKeyID: 50877078
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Expanded code samples

![What's new topic](images/JJ933179.mod_icon_whatsnew_long(Office.15).png "What's new topic")

Learn about the sample applications that are installed on your computer when you install Microsoft Lync 2013 SDK.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Code samples overview  
Quick-start samples  
Reference samples  
Additional resources  

<table>
<tbody>
<tr class="odd">
<td></td>
</tr>
</tbody>
</table>


## Code samples overview

The sample collection includes quick-start samples that let you get started quickly with Lync development by demonstrating one Microsoft Lync 2013 API feature at a time. There is also a set of end-to-end samples that show how to put all the API features together to create a complete unified communication solution. You can download these samples from the MSDN samples code gallery. Links to individual code gallery samples are found in the How to topics where a corresponding sample is available to download.

## Quick-start samples

The quick-start samples are grouped by API feature area. Many of these samples demonstrate Lync API features that have been in the API since the initial release of Lync, such as the presence-related samples that show how to use Lync Controls to display and update presence. The new Lync SDK features are demonstrated by the Persistent Chat, resource sharing, and content sharing samples.

### Presence samples

The quick-start samples in the following table show how to publish and get presence for a contact by using presence controls or objects in the Lync 2013 API object model.

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
<td><p>MyNotebox</p></td>
<td><p>Populates a page with a <a href="mynotebox-class-microsoft-lync-controls_1.md">MyNoteBox</a> control and displays the signed-in user’s display name and personal note in a text entry control.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyNoteBoxDesktop\MyNoteBoxDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyNoteBoxSilverlight\MyNoteBoxSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>MyPresenceChooser</p></td>
<td><p>Populates a window with a <a href="mypresencechooser-class-microsoft-lync-controls_1.md">MyPresenceChooser</a> control that lets a user choose a presence activity. The resulting availability state is displayed in a text block on the page.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyPresenceChooserDesktop\MyPresenceChooserDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyPresenceChooserDesktop\MyPresenceChooserSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>MyStatusArea</p></td>
<td><p>Populates a window with a <a href="mystatusarea-class-microsoft-lync-controls_1.md">MyStatusArea</a> control that lets a user choose a presence activity and enter a personal note. Three text blocks on the page are bound to <strong>MyStatusArea</strong> control properties for the user display name, availability state, and personal note. The text value of these text blocks are automatically updated when the corresponding properties of the <strong>MyStatusControl</strong> change.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyStatusAreaDesktop\MyStatusAreaDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyStatusAreaDesktop\MyStatusAreaSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>PresenceIndicator</p></td>
<td><p>Populates a list on a page with three <a href="presenceindicator-class-microsoft-lync-controls_1.md">PresenceIndicator</a> instances. The user can hover a mouse pointer over any of the presence indicators to display a contact card for a user. The <a href="contactbase-source-property-microsoft-lync-controls_1.md">Source</a> property for each control instance is set by the sample application.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PresenceIndicatorDesktop\PresenceIndicatorDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PresenceIndicatorDesktop\PresenceIndicatorSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Presence publication</p></td>
<td><p>Retrieve and publish information of the Self contact (the currently signed-in user) by using classes, enumerations, events, and methods of the Lync 2013 API. It also shows how to sign in to Lync using the credentials of the active user. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="lyncclient-class-microsoft-lync-model.md">LyncClient</a> class</p></li>
<li><p><a href="contact-class-microsoft-lync-model.md">Contact</a> class</p></li>
<li><p><a href="self-class-microsoft-lync-model.md">Self</a> class</p></li>
<li><p><a href="contactavailability-enumeration-microsoft-lync-model.md">ContactAvailability</a> enumeration</p></li>
<li><p><a href="contact-contactinformationchanged-event-microsoft-lync-model.md">ContactInformationChanged</a> event</p></li>
<li><p><a href="contact-getcontactinformation-method-microsoft-lync-model.md">GetContactInformation</a> method</p></li>
<li><p><a href="self-beginpublishcontactinformation-method-microsoft-lync-model.md">BeginPublishContactInformation</a> method</p></li>
<li><p><a href="lyncclient-beginsignin-method-microsoft-lync-model.md">BeginSignIn</a> method</p></li>
<li><p><a href="lyncclient-beginsignout-method-microsoft-lync-model.md">BeginSignOut</a> method</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PresencePublication\PresencePublication.sln</p></td>
</tr>
</tbody>
</table>


### Contact samples

The contact samples in the following table show how to interact with Lync contacts by using the objects of the Lync 2013 API and controls from the [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md) namespace.

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
<td><p>ContactCard control list</p></td>
<td><p>Loads three <a href="contactcard-class-microsoft-lync-controls_1.md">ContactCard</a> controls into a list on a page in a Silverlight or WPF application.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\<br />
microsamples.zip\ContactCardDesktop\ContactCardDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\<br />
microsamples.zip\ContactCardDesktop\ContactCardSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>ContactList control</p></td>
<td><p>Populates a page with the <a href="contactlist-class-microsoft-lync-controls_1.md">ContactList</a> control and then lists the SIP URI values for the contacts in the list.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactListDesktop\ContactListDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactListDesktop\ContactListSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>CustomContactList control</p></td>
<td><p>Populates a page with a <a href="customcontactlist-class-microsoft-lync-controls_1.md">CustomContactList</a> control and several child <a href="customcontactlistitem-class-microsoft-lync-controls_1.md">CustomContactListItem</a> objects. The child objects are created and added at runtime by using C# code in a code-behind source file.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\CustomContactListAndcustomContactListItemDesktop<br />
\CustomContactListAndcustomContactListItemDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\CustomContactListAndcustomContactListItemSilverlight<br />
\CustomContactListAndcustomContactListItemSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>ContactSearch control</p></td>
<td><p>Populates a page with a <a href="contactsearch-class-microsoft-lync-controls_1.md">ContactSearch</a> control and searches for used-by user name or skill.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\<br />
microsamples.zip\ContactSearchDesktop\ContactSearchDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactSearchSilverlight\ContactSearchSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Contact search with input box and search results</p></td>
<td><p>Populates a page with a <a href="contactsearchinputbox-class-microsoft-lync-controls_1.md">ContactSearchInputBox</a> control and a <a href="contactsearchresultlist-class-microsoft-lync-controls_1.md">ContactSearchResultList</a> control. The <strong>ContactSearchInputBox</strong> is bound to the <strong>ContactSearchResultList</strong> so that the resulting list displays search results based on what the user types in the search input box.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactSearchInputBoxAndContactSearchResultListDesktop<br />
\ContactSearchInputBoxAndContactSearchResultListDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactSearchInputBoxAndContactSearchResultListSilverlight<br />
\ContactSearchInputBoxAndContactSearchResultListSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Display frequent and favorite contacts</p></td>
<td><p>Populates a page with a list of favorite contacts and a list of frequent contacts. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="lyncclient-class-microsoft-lync-model.md">LyncClient</a> class</p></li>
<li><p><a href="contactmanager-class-microsoft-lync-model.md">ContactManager</a> class</p></li>
<li><p><a href="group-class-microsoft-lync-model-group.md">Microsoft.Lync.Model.Group.Group</a> class</p></li>
<li><p><a href="contact-class-microsoft-lync-model.md">Contact</a> class</p></li>
<li><p><a href="contactmanager-getcontactbyuri-method-microsoft-lync-model.md">GetContactByUri</a> method</p></li>
<li><p><a href="group-beginaddcontact-method-microsoft-lync-model-group.md">BeginAddContact</a> method</p></li>
<li><p><a href="group-beginremovecontact-method-microsoft-lync-model-group.md">BeginRemoveContact</a> method</p></li>
<li><p><a href="contact-getcontactinformation-method-microsoft-lync-model.md">GetContactInformation</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\DisplayFrequentAndFavoriteContacts\DisplayFrequentAndFavoriteContacts.sln</p></td>
</tr>
<tr class="odd">
<td><p>Add and remove a custom group</p></td>
<td><p>Lists the groups in your contact list and lets you add or remove a group. The sample uses the <a href="contactmanager-groups-property-microsoft-lync-model.md">Groups</a> property, the <a href="contactmanager-beginaddgroup-method-microsoft-lync-model.md">BeginAddGroup</a> method, and the <a href="contactmanager-beginremovegroup-method-microsoft-lync-model.md">BeginRemoveGroup</a> method.</p>
<p>Path: <em>%PROGRAMFILES(X86)%\</em>Microsoft Lync\SDK\Samples<br />
\microsamples.zip\AddCustomGroup\AddCustomGroup.sln</p></td>
</tr>
<tr class="even">
<td><p>MoveContactBetweenGroups</p></td>
<td><p>Lists all custom groups in a user’s contact list and lets a user move a contact from one custom group to another. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="lyncclient-class-microsoft-lync-model.md">LyncClient</a> class</p></li>
<li><p><a href="contactmanager-class-microsoft-lync-model.md">ContactManager</a> class</p></li>
<li><p><a href="contact-class-microsoft-lync-model.md">Contact</a> class</p></li>
<li><p><a href="group-class-microsoft-lync-model-group.md">Group</a> class</p></li>
<li><p><a href="group-beginaddcontact-method-microsoft-lync-model-group.md">BeginAddContact</a> method</p></li>
<li><p><a href="group-beginremovecontact-method-microsoft-lync-model-group.md">BeginRemoveContact</a> method</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%\</em>Microsoft Lync\SDK\Samples<br />
\microsamples.zip\MoveContactBetweenGroups\MoveContactBetweenGroups.sln</p></td>
</tr>
<tr class="odd">
<td><p>Add and remove a contact from a group</p></td>
<td><p>Adds and removes contacts from the Other Contacts group. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="contactmanager-class-microsoft-lync-model.md">ContactManager</a> class</p></li>
<li><p><a href="group-class-microsoft-lync-model-group.md">Group</a> class</p></li>
<li><p><a href="contact-class-microsoft-lync-model.md">Contact</a> class</p></li>
<li><p><a href="contactmanager-getcontactbyuri-method-microsoft-lync-model.md">GetContactByUri</a> method</p></li>
<li><p><a href="group-beginaddcontact-method-microsoft-lync-model-group.md">BeginAddContact</a> method</p></li>
<li><p><a href="group-beginremovecontact-method-microsoft-lync-model-group.md">BeginRemoveContact</a> method</p></li>
<li><p><a href="contact-getcontactinformation-method-microsoft-lync-model.md">GetContactInformation</a> method</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\AddRemoveContacts\AddRemoveContacts.sln</p></td>
</tr>
</tbody>
</table>


### Conversation samples

The conversation samples in the following table show how to interact with Lync conversations by using the objects of the Lync 2013 API and Lync Controls from the [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md) namespace.

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
<td><p>ButtonsDesktop</p></td>
<td><p>Shows how to display Lync conversation-starting controls in a list. The <a href="contactbase-source-property-microsoft-lync-controls_1.md">Source</a> property for each control is set to the URI of a user. The controls used in the sample include: <a href="startinstantmessagingbutton-class-microsoft-lync-controls_1.md">StartInstantMessagingButton</a>, <a href="startaudiocallbutton-class-microsoft-lync-controls_1.md">StartAudioCallButton</a>, <a href="startvideocallbutton-class-microsoft-lync-controls_1.md">StartVideoCallButton</a>, <a href="sharedesktopbutton-class-microsoft-lync-controls_1.md">ShareDesktopButton</a>, <a href="sendfilebutton-class-microsoft-lync-controls_1.md">SendFileButton</a>, <a href="sendemailbutton-class-microsoft-lync-controls_1.md">SendEmailButton</a>, and <a href="schedulemeetingbutton-class-microsoft-lync-controls_1.md">ScheduleMeetingButton</a>.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ButtonsDesktop\ButtonsDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ButtonsSilverlight\ButtonsSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>AcceptConversation</p></td>
<td><p>Displays a window that registers for the <a href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation.md">ConversationAdded</a> event and then notifies the user when a conversation invitation is received. If the user chooses to ignore the invitation, the window ends the new conversation. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="lyncclient-class-microsoft-lync-model.md">LyncClient</a> class</p></li>
<li><p><a href="conversationmanager-class-microsoft-lync-model-conversation.md">ConversationManager</a> class</p></li>
<li><p><a href="conversation-class-microsoft-lync-model-conversation.md">Conversation</a> class</p></li>
<li><p><a href="modality-class-microsoft-lync-model-conversation.md">Modality</a> class</p></li>
<li><p><a href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation.md">ConversationAdded</a> event</p></li>
<li><p><a href="conversation-end-method-microsoft-lync-model-conversation.md">End</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\AcceptConversation\AcceptConversation.sln</p></td>
</tr>
<tr class="odd">
<td><p>StartConversation</p></td>
<td><p>Start an IM conversation using the <a href="conversationmanager-class-microsoft-lync-model-conversation.md">ConversationManager</a> class. Messages are sent using plain text.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\StartConversation\StartConversation.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>StartFormattedConversation</p></td>
<td><p>Start an IM conversation using the <a href="conversationmanager-class-microsoft-lync-model-conversation.md">ConversationManager</a> class. Messages are sent in the MIME type selected by the user.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\StartFormattedConversation\StartFormattedConversation.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>DockingConversationWindowSample</p></td>
<td><p>Start and dock an IM conversation using the StartInstantMessagingButton control.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\DockingConversationWindowSample\DockingConversationWindowSample.csproj</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>MeetNow</p></td>
<td><p>Start a meet-now conference using automation</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MeetNow\MeetNow.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>JoinMeetingFromLobby</p></td>
<td><p>Joins a running meeting and notifies the users if they are in the meeting lobby.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\JoinMeetingFromLobby\JoinMeetingFromLobby.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Automation conversation</p></td>
<td><p>This sample uses the <a href="automation-class-microsoft-lync-model-extensibility.md">Automation</a> class in the Lync 2013 API to start a new conversation with one or more Lync contacts. Features include the following:</p>
<ul>
<li><p>The sample uses the <a href="automation-class-microsoft-lync-model-extensibility.md">Automation</a> API in Lync to start a new conversation with a set of Lync contacts.</p></li>
<li><p>The conversation can be started with one or more modalities at the same time.</p></li>
<li><p>The sample shows how to set up specific settings for each conversation modality.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\Automation\Automation.csproj</p></td>
</tr>
<tr class="odd">
<td><p>Conversation Window Docker</p></td>
<td><p>This application demonstrates the ability to dock a conversation window within another WPF application. The sample:</p>
<ul>
<li><p>Docks a conversation window into a WPF application.</p></li>
<li><p>Demonstrates how to use a <a href="http://go.microsoft.com/fwlink/?linkid=198548%26clcid=0x409">WindowsFormsHost</a> to dock a conversation window.</p></li>
<li><p>Shows how to handle the different events raised by a conversation window.</p></li>
<li><p>Shows how to flash the window when the conversation window requires attention.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\DockingConversationWindowSample\DockingConversationWindowSample.csproj</p></td>
</tr>
<tr class="even">
<td><p>Audio/Video Conversation</p></td>
<td><p>This sample uses the <a href="microsoft-lync-model-conversation-namespace.md">Microsoft.Lync.Model.Conversation</a> and <a href="microsoft-lync-model-conversation-audiovideo-namespace.md">Microsoft.Lync.Model.Conversation.AudioVideo</a> namespaces from the Microsoft Lync 2013 API to implement a conversation window. The sample:</p>
<ul>
<li><p>Implements a fully functional audio/video conversation window.</p></li>
<li><p>Shows how to register and handle conversation manager and audio/video conversation events.</p></li>
<li><p>Uses the most common features of <a href="conversation-class-microsoft-lync-model-conversation.md">Conversation</a>, <a href="avmodality-class-microsoft-lync-model-conversation-audiovideo.md">AVModality</a>, <a href="audiochannel-class-microsoft-lync-model-conversation-audiovideo.md">AudioChannel</a>, and <a href="videochannel-class-microsoft-lync-model-conversation-audiovideo.md">VideoChannel</a>.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\AudioVideoConversation\AudioVideoConversation.csproj</p></td>
</tr>
</tbody>
</table>


### Persistent Chat samples

The following sample applications demonstrate how to add chat room features to a Microsoft Lync 2013 SDK-enabled application.

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
<td><p>GetMessages</p></td>
<td><p>The GetMessages sample application shows how to get messages that have been posted to a Persistent Chat room and then display any new message that are posted to the chat room. In addition, the sample shows how to get the chat rooms that are in a user’s contact list and keep that room collection synchronized with the contact list.</p>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PersistentChat_GetMessages\PersistentChat_GetMessages.sln</p></td>
</tr>
<tr class="even">
<td><p>FollowedRoomList</p></td>
<td><p>The FollowedRoomList sample application shows how to get the Persistent Chat rooms that are in a user’s contact list and then keep that room collection synchronized with the contact list. For information about how to find Persistent Chat rooms that are not in a user’s contact list, see &quot;RoomQuery&quot; application later in this topic.</p>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PersistentChat_FollowedRoomList\PersistentChat_FollowedRoomList.sln</p></td>
</tr>
<tr class="odd">
<td><p>RoomQuery</p></td>
<td><p>The RoomQuery sample application shows how to get a collection of Persistent Chat rooms that are not in a user’s contact list. For information about finding Persistent Chat rooms that are in a user’s contact list, see &quot;FollowedRoomList&quot; application earlier in this topic.</p>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PersistentChat_RoomQuery\PersistentChat_RoomQuery.sln</p></td>
</tr>
<tr class="even">
<td><p>PostMessage</p></td>
<td><p>The PostMessage sample application shows how to post a plain-text message to a Persistent Chat room in a user’s contact list and verify that the message posted successfully. In addition, the sample shows how to get a chat room from the contact list.</p>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PersistentChat_PostMessage\PersistentChat_PostMessage.sln</p></td>
</tr>
<tr class="odd">
<td><p>GetParticipants</p></td>
<td><p>The GetParticipants sample application shows how to get a list of Persistent Chat room participants. In addition, the sample shows how to get a chat room from the contact list.</p>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PersistentChat_GetParticipants\PersistentChat_GetParticipants.sln</p></td>
</tr>
<tr class="even">
<td><p>FilterMessageAddIn</p></td>
<td><p>The FilterMessageAddIn sample application shows how to get a hosting group for a Persistent Chat room, catch outgoing messages before they are posted to the hosting chat room, run filtering and formatting logic on the messages, and then send the resulting message to the hosting chat room.</p>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PersistentChat_FilterMessageAddin\PersistentChat_FilterMessageAddIn.sln</p></td>
</tr>
</tbody>
</table>


### Content sharing samples

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
<td><p>ContentModalitySample</p></td>
<td><p>Shows how to create a conversation and then share a whiteboard and a PowerPoint slide deck. If a PowerPoint slide deck is shared, the sample lets a user scroll forward and backward in the slide deck. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="lyncclient-class-microsoft-lync-model.md">LyncClient</a> class</p></li>
<li><p><a href="conversation-class-microsoft-lync-model-conversation.md">Conversation</a> class</p></li>
<li><p><a href="contentsharingmodality-class-microsoft-lync-model-conversation-sharing.md">ContentSharingModality</a> class</p></li>
<li><p><a href="shareablecontent-class-microsoft-lync-model-conversation-sharing.md">ShareableContent</a> class</p></li>
<li><p><a href="powerpointcontent-class-microsoft-lync-model-conversation-sharing.md">PowerPointContent</a> class</p></li>
<li><p><a href="shareablecontentstate-enumeration-microsoft-lync-model-conversation-sharing.md">ShareableContentState</a> enumeration</p></li>
<li><p><a href="contentsharingmodality-begincreatecontent-method-microsoft-lync-model-conversation-sharing.md">BeginCreateContent</a> method</p></li>
<li><p><a href="contentsharingmodality-begincreatecontentfromfile-method-microsoft-lync-model-conversation-sharing.md">BeginCreateContentFromFile</a> method</p></li>
<li><p><a href="shareablecontent-upload-method-microsoft-lync-model-conversation-sharing.md">Upload</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContentSharingModality</p></td>
</tr>
</tbody>
</table>


## Reference samples

The following samples provide complete application examples using the Lync 2013 API. These examples illustrate the use of Lync 2013 API in real-world scenarios.

### Conversation translator

This sample uses the [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace.md) namespace from the Lync Model API to intercept instant messages and provide translation using Bing Web Services.

Features include the following:

  - The sample provides an example architecture for registering for and handling asynchronous Lync 2013 API events in Silverlight.

  - Register for two Conversation related events: [ParticipantAdded](conversation-participantadded-event-microsoft-lync-model-conversation.md) and [InstantMessageReceived](instantmessagemodality-instantmessagereceived-event-microsoft-lync-model-conversation.md).

  - Use the [BeginSendMessage](instantmessagemodality-beginsendmessage-method-microsoft-lync-model-conversation.md) method and callback.

  - Uses the Bing Translator Web Service.

Path: *%PROGRAMFILES(X86)%*\\Microsoft Office 2013\\LyncSDK\\Samples  
\\ConversationTranslator\\ConversationTranslator.csproj

### Proposal tracker

The ProposalTracker application demonstrates the use of Microsoft Lync Controls in a Silverlight application. The application is a demonstration, representing a tool used by a fictitious company called Fabrikam, Inc. It tracks a list of proposals and sales people in the company.

Features include the following:

  - Demonstrates how to use the following Lync Controls in a Silverlight application:
    
      - MyStatusArea control
    
      - PresenceIndicator control
    
      - ContactCard control
    
      - ContactList control
    
      - CustomContactList control
    
      - ContactSearchInputBox control
    
      - ContactSearchResultList control

  - Demonstrates how to use ContextualConversation between two conversation windows with the companion application MiniProposalTracker, which runs in a Lync Conversation Window Extension.

Path: *%PROGRAMFILES(X86)%*\\Microsoft Office 2013\\LyncSDK\\Samples  
\\ProposalTracker\\ProposalTracker.sln

## Additional resources

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

