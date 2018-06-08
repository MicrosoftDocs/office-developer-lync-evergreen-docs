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

![What's new topic](images/JJ937254.mod_icon_whatsnew_long(Office.15).png "What's new topic")

Learn about the sample applications that are installed on your computer when you install Microsoft Lync 2013 SDK.

**Last modified:** December 07, 2015

***Applies to:** Lync 2013 | Lync Server 2013*

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
<td><p>Populates a page with a <a href="https://msdn.microsoft.com/en-us/library/hh346137(v=office.15)">MyNoteBox</a> control and displays the signed-in user’s display name and personal note in a text entry control.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyNoteBoxDesktop\MyNoteBoxDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyNoteBoxSilverlight\MyNoteBoxSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>MyPresenceChooser</p></td>
<td><p>Populates a window with a <a href="https://msdn.microsoft.com/en-us/library/hh379434(v=office.15)">MyPresenceChooser</a> control that lets a user choose a presence activity. The resulting availability state is displayed in a text block on the page.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyPresenceChooserDesktop\MyPresenceChooserDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyPresenceChooserDesktop\MyPresenceChooserSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>MyStatusArea</p></td>
<td><p>Populates a window with a <a href="https://msdn.microsoft.com/en-us/library/hh363503(v=office.15)">MyStatusArea</a> control that lets a user choose a presence activity and enter a personal note. Three text blocks on the page are bound to <strong>MyStatusArea</strong> control properties for the user display name, availability state, and personal note. The text value of these text blocks are automatically updated when the corresponding properties of the <strong>MyStatusControl</strong> change.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyStatusAreaDesktop\MyStatusAreaDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\MyStatusAreaDesktop\MyStatusAreaSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>PresenceIndicator</p></td>
<td><p>Populates a list on a page with three <a href="https://msdn.microsoft.com/en-us/library/hh345947(v=office.15)">PresenceIndicator</a> instances. The user can hover a mouse pointer over any of the presence indicators to display a contact card for a user. The <a href="https://msdn.microsoft.com/en-us/library/hh363511(v=office.15)">Source</a> property for each control instance is set by the sample application.</p>
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
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347493(v=office.15)">LyncClient</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365096(v=office.15)">Contact</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347850(v=office.15)">Self</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh348201(v=office.15)">ContactAvailability</a> enumeration</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347693(v=office.15)">ContactInformationChanged</a> event</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh348218(v=office.15)">GetContactInformation</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380629(v=office.15)">BeginPublishContactInformation</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380283(v=office.15)">BeginSignIn</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347837(v=office.15)">BeginSignOut</a> method</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\PresencePublication\PresencePublication.sln</p></td>
</tr>
</tbody>
</table>

### Contact samples

The contact samples in the following table show how to interact with Lync contacts by using the objects of the Lync 2013 API and controls from the [Microsoft.Lync.Controls](https://msdn.microsoft.com/en-us/library/hh346685\(v=office.15\)) namespace.

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
<td><p>Loads three <a href="https://msdn.microsoft.com/en-us/library/hh379168(v=office.15)">ContactCard</a> controls into a list on a page in a Silverlight or WPF application.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\<br />
microsamples.zip\ContactCardDesktop\ContactCardDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\<br />
microsamples.zip\ContactCardDesktop\ContactCardSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>ContactList control</p></td>
<td><p>Populates a page with the <a href="https://msdn.microsoft.com/en-us/library/hh363781(v=office.15)">ContactList</a> control and then lists the SIP URI values for the contacts in the list.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactListDesktop\ContactListDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactListDesktop\ContactListSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>CustomContactList control</p></td>
<td><p>Populates a page with a <a href="https://msdn.microsoft.com/en-us/library/hh346321(v=office.15)">CustomContactList</a> control and several child <a href="https://msdn.microsoft.com/en-us/library/hh346017(v=office.15)">CustomContactListItem</a> objects. The child objects are created and added at runtime by using C# code in a code-behind source file.</p>
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
<td><p>Populates a page with a <a href="https://msdn.microsoft.com/en-us/library/hh379436(v=office.15)">ContactSearch</a> control and searches for used-by user name or skill.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\<br />
microsamples.zip\ContactSearchDesktop\ContactSearchDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContactSearchSilverlight\ContactSearchSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Contact search with input box and search results</p></td>
<td><p>Populates a page with a <a href="https://msdn.microsoft.com/en-us/library/hh379719(v=office.15)">ContactSearchInputBox</a> control and a <a href="https://msdn.microsoft.com/en-us/library/hh379201(v=office.15)">ContactSearchResultList</a> control. The <strong>ContactSearchInputBox</strong> is bound to the <strong>ContactSearchResultList</strong> so that the resulting list displays search results based on what the user types in the search input box.</p>
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
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347493(v=office.15)">LyncClient</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365092(v=office.15)">ContactManager</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365036(v=office.15)">Microsoft.Lync.Model.Group.Group</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365096(v=office.15)">Contact</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380174(v=office.15)">GetContactByUri</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347703(v=office.15)">BeginAddContact</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380136(v=office.15)">BeginRemoveContact</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh348218(v=office.15)">GetContactInformation</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\DisplayFrequentAndFavoriteContacts\DisplayFrequentAndFavoriteContacts.sln</p></td>
</tr>
<tr class="odd">
<td><p>Add and remove a custom group</p></td>
<td><p>Lists the groups in your contact list and lets you add or remove a group. The sample uses the <a href="https://msdn.microsoft.com/en-us/library/hh347910(v=office.15)">Groups</a> property, the <a href="https://msdn.microsoft.com/en-us/library/hh365068(v=office.15)">BeginAddGroup</a> method, and the <a href="https://msdn.microsoft.com/en-us/library/hh380622(v=office.15)">BeginRemoveGroup</a> method.</p>
<p>Path: <em>%PROGRAMFILES(X86)%\</em>Microsoft Lync\SDK\Samples<br />
\microsamples.zip\AddCustomGroup\AddCustomGroup.sln</p></td>
</tr>
<tr class="even">
<td><p>MoveContactBetweenGroups</p></td>
<td><p>Lists all custom groups in a user’s contact list and lets a user move a contact from one custom group to another. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347493(v=office.15)">LyncClient</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365092(v=office.15)">ContactManager</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365096(v=office.15)">Contact</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365036(v=office.15)">Group</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347703(v=office.15)">BeginAddContact</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380136(v=office.15)">BeginRemoveContact</a> method</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%\</em>Microsoft Lync\SDK\Samples<br />
\microsamples.zip\MoveContactBetweenGroups\MoveContactBetweenGroups.sln</p></td>
</tr>
<tr class="odd">
<td><p>Add and remove a contact from a group</p></td>
<td><p>Adds and removes contacts from the Other Contacts group. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365092(v=office.15)">ContactManager</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365036(v=office.15)">Group</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365096(v=office.15)">Contact</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380174(v=office.15)">GetContactByUri</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347703(v=office.15)">BeginAddContact</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380136(v=office.15)">BeginRemoveContact</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh348218(v=office.15)">GetContactInformation</a> method</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\AddRemoveContacts\AddRemoveContacts.sln</p></td>
</tr>
</tbody>
</table>

### Conversation samples

The conversation samples in the following table show how to interact with Lync conversations by using the objects of the Lync 2013 API and Lync Controls from the [Microsoft.Lync.Controls](https://msdn.microsoft.com/en-us/library/hh346685\(v=office.15\)) namespace.

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
<td><p>Shows how to display Lync conversation-starting controls in a list. The <a href="https://msdn.microsoft.com/en-us/library/hh363511(v=office.15)">Source</a> property for each control is set to the URI of a user. The controls used in the sample include: <a href="https://msdn.microsoft.com/en-us/library/hh379340(v=office.15)">StartInstantMessagingButton</a>, <a href="https://msdn.microsoft.com/en-us/library/hh378744(v=office.15)">StartAudioCallButton</a>, <a href="https://msdn.microsoft.com/en-us/library/hh379584(v=office.15)">StartVideoCallButton</a>, <a href="https://msdn.microsoft.com/en-us/library/hh363609(v=office.15)">ShareDesktopButton</a>, <a href="https://msdn.microsoft.com/en-us/library/hh363240(v=office.15)">SendFileButton</a>, <a href="https://msdn.microsoft.com/en-us/library/hh379649(v=office.15)">SendEmailButton</a>, and <a href="https://msdn.microsoft.com/en-us/library/hh363440(v=office.15)">ScheduleMeetingButton</a>.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ButtonsDesktop\ButtonsDesktop.sln</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ButtonsSilverlight\ButtonsSilverlight.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>AcceptConversation</p></td>
<td><p>Displays a window that registers for the <a href="https://msdn.microsoft.com/en-us/library/hh365100(v=office.15)">ConversationAdded</a> event and then notifies the user when a conversation invitation is received. If the user chooses to ignore the invitation, the window ends the new conversation. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347493(v=office.15)">LyncClient</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365042(v=office.15)">ConversationManager</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380466(v=office.15)">Conversation</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380311(v=office.15)">Modality</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh365100(v=office.15)">ConversationAdded</a> event</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh348014(v=office.15)">End</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\AcceptConversation\AcceptConversation.sln</p></td>
</tr>
<tr class="odd">
<td><p>StartConversation</p></td>
<td><p>Start an IM conversation using the <a href="https://msdn.microsoft.com/en-us/library/hh365042(v=office.15)">ConversationManager</a> class. Messages are sent using plain text.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\StartConversation\StartConversation.sln</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>StartFormattedConversation</p></td>
<td><p>Start an IM conversation using the <a href="https://msdn.microsoft.com/en-us/library/hh365042(v=office.15)">ConversationManager</a> class. Messages are sent in the MIME type selected by the user.</p>
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
<td><p>This sample uses the <a href="https://msdn.microsoft.com/en-us/library/hh348066(v=office.15)">Automation</a> class in the Lync 2013 API to start a new conversation with one or more Lync contacts. Features include the following:</p>
<ul>
<li><p>The sample uses the <a href="https://msdn.microsoft.com/en-us/library/hh348066(v=office.15)">Automation</a> API in Lync to start a new conversation with a set of Lync contacts.</p></li>
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
<td><p>This sample uses the <a href="https://msdn.microsoft.com/en-us/library/hh365247(v=office.15)">Microsoft.Lync.Model.Conversation</a> and <a href="https://msdn.microsoft.com/en-us/library/hh365346(v=office.15)">Microsoft.Lync.Model.Conversation.AudioVideo</a> namespaces from the Microsoft Lync 2013 API to implement a conversation window. The sample:</p>
<ul>
<li><p>Implements a fully functional audio/video conversation window.</p></li>
<li><p>Shows how to register and handle conversation manager and audio/video conversation events.</p></li>
<li><p>Uses the most common features of <a href="https://msdn.microsoft.com/en-us/library/hh380466(v=office.15)">Conversation</a>, <a href="https://msdn.microsoft.com/en-us/library/hh380301(v=office.15)">AVModality</a>, <a href="https://msdn.microsoft.com/en-us/library/hh348053(v=office.15)">AudioChannel</a>, and <a href="https://msdn.microsoft.com/en-us/library/hh365204(v=office.15)">VideoChannel</a>.</p></li>
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
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh347493(v=office.15)">LyncClient</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/hh380466(v=office.15)">Conversation</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj265940(v=office.15)">ContentSharingModality</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj274917(v=office.15)">ShareableContent</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj274699(v=office.15)">PowerPointContent</a> class</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj265981(v=office.15)">ShareableContentState</a> enumeration</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj275157(v=office.15)">BeginCreateContent</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj274944(v=office.15)">BeginCreateContentFromFile</a> method</p></li>
<li><p><a href="https://msdn.microsoft.com/en-us/library/jj275631(v=office.15)">Upload</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples<br />
\microsamples.zip\ContentSharingModality</p></td>
</tr>
</tbody>
</table>

## Reference samples

The following samples provide complete application examples using the Lync 2013 API. These examples illustrate the use of Lync 2013 API in real-world scenarios.

### Conversation translator

This sample uses the [Microsoft.Lync.Model.Conversation](https://msdn.microsoft.com/en-us/library/hh365247\(v=office.15\)) namespace from the Lync Model API to intercept instant messages and provide translation using Bing Web Services.

Features include the following:

  - The sample provides an example architecture for registering for and handling asynchronous Lync 2013 API events in Silverlight.

  - Register for two Conversation related events: [ParticipantAdded](https://msdn.microsoft.com/en-us/library/hh347719\(v=office.15\)) and [InstantMessageReceived](https://msdn.microsoft.com/en-us/library/hh380696\(v=office.15\)).

  - Use the [BeginSendMessage](https://msdn.microsoft.com/en-us/library/hh380302\(v=office.15\)) method and callback.

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

## See also

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

