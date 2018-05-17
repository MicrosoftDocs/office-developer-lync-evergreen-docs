---
title: Lync conversation samples
TOCTitle: Lync conversation samples
ms:assetid: e0c1202c-fef8-42da-b3bb-c79df4650f36
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933212(v=office.15)
ms:contentKeyID: 50877355
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync conversation samples

![Code sample topic](images/JJ937254.mod_icon_codesample_long(Office.15).png "Code sample topic")

Learn about the conversation-related quick-start samples that are installed with Microsoft Lync 2013 SDK.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Conversation samples<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Conversation samples

The quick-start samples in the following table show how to interact with Lync conversations by using Lync 2013 API objects and controls from the [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md) namespace.

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
<td><p>Shows how to display Lync conversation-starting controls in a list. The <a href="contactbase-source-property-microsoft-lync-controls_1.md">ContactBase.Source</a> property for each control is set to the URI of a user. The controls used in the sample include: <a href="startinstantmessagingbutton-class-microsoft-lync-controls_1.md">Microsoft.Lync.Controls.StartInstantMessagingButton</a>, <a href="startaudiocallbutton-class-microsoft-lync-controls_1.md">Microsoft.Lync.Controls.StartAudioCallButton</a>, <a href="startvideocallbutton-class-microsoft-lync-controls_1.md">Microsoft.Lync.Controls.StartVideoCallButton</a>, <a href="sharedesktopbutton-class-microsoft-lync-controls_1.md">Microsoft.Lync.Controls.ShareDesktopButton</a>, <a href="sendfilebutton-class-microsoft-lync-controls.md">Microsoft.Lync.Controls.SendFileButton</a>, <a href="sendemailbutton-class-microsoft-lync-controls_1.md">Microsoft.Lync.Controls.SendEmailButton</a>, and <a href="schedulemeetingbutton-class-microsoft-lync-controls_1.md">Microsoft.Lync.Controls.ScheduleMeetingButton</a>.</p>
<ul>
<li><p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\ButtonsDesktop</p></li>
<li><p>Silverlight sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\ButtonsSilverlight</p></li>
</ul>
<p>Download the sample from Code Gallery at the following locations:</p>
<ul>
<li><p>WPF sample location: <a href="http://code.msdn.microsoft.com/lync-2013-start-new-9d1d6e20">Lync 2013: Start new conversations from a WPF application</a></p></li>
<li><p>Silverlight sample location: <a href="http://code.msdn.microsoft.com/lync-2013-start-new-6e1ca269">Lync 2013: Start new conversations from a Silverlight application</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-accept-requests-2ae187c4">AcceptConversation</a></p></td>
<td><p>Displays a window that registers for the <a href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md">ConversationManager.ConversationAdded</a> event and then notifies the user when a conversation invitation is received. If the user chooses to ignore the invitation, the window ends the new conversation. The sample uses the following classes and methods:</p>
<ul>
<li><p><a href="lyncclient-class-microsoft-lync-model_2.md">Microsoft.Lync.Model.LyncClient</a> class</p></li>
<li><p><a href="conversationmanager-class-microsoft-lync-model-conversation_2.md">Microsoft.Lync.Model.Conversation.ConversationManager</a> class</p></li>
<li><p><a href="conversation-class-microsoft-lync-model-conversation_2.md">Microsoft.Lync.Model.Conversation.Conversation</a> class</p></li>
<li><p><a href="modality-class-microsoft-lync-model-conversation_2.md">Microsoft.Lync.Model.Conversation.Modality</a> class</p></li>
<li><p><a href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md">ConversationManager.ConversationAdded</a> event</p></li>
<li><p><a href="conversation-end-method-microsoft-lync-model-conversation_2.md">Conversation.End</a> method</p></li>
</ul>
<p>WPF sample location: <em>%PROGRAMFILES(X86)%</em>\Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\AcceptConversation</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p>WPF sample location: <a href="http://code.msdn.microsoft.com/lync-2013-accept-requests-2ae187c4">Lync 2013: Accept requests using the AcceptConversation method</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-start-an-im-27951440">StartConversation</a></p></td>
<td><p>Uses the <a href="automation-class-microsoft-lync-model-extensibility_2.md">Automation</a> class in the Lync Model API to start a new conversation with one Lync contact. Features include:</p>
<ul>
<li><p>Uses the Automation API in Lync to start a new conversation with new Lync contacts.</p></li>
<li><p>The conversation can start with IM modalities.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES%\</em>Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\StartConversation or <em>%PROGRAMFILES(X86)%\</em>Microsoft Office 2013\LyncSDK\Samples\microsamples.zip\StartConversation</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p><a href="http://code.msdn.microsoft.com/lync-2013-start-an-im-27951440">Lync 2013: Start an IM conversation by using automation</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-translate-a-a849e513">ConversationTranslator</a></p></td>
<td><p>Uses the <a href="microsoft-lync-model-conversation-namespace_2.md">Microsoft.Lync.Model.Conversation</a> namespace from the Lync Model API to intercept instant messages and provide translation by using Bing Web Services. Features include:</p>
<ul>
<li><p>Provides sample architecture for registering for and handling asynchronous Lync SDK events in Silverlight.</p></li>
<li><p>Register for two Conversation related events:</p>
<ul>
<li><p><strong>ParticipantAdded</strong>.</p></li>
<li><p><strong>InstantMessageReceived</strong>.</p></li>
</ul></li>
<li><p>Use the <strong>InstantMessageModality.BeginSendMessage()</strong> method and callback.</p></li>
<li><p>Uses the Bing Translator Web Service.</p></li>
</ul>
<p>Path: %PROGRAMFILES%\Microsoft Lync\SDK\Samples\ConversationTranslator or %PROGRAMFILES(X86)%\Microsoft Lync\SDK\Samples\ConversationTranslator</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p><a href="http://code.msdn.microsoft.com/lync-2013-translate-a-a849e513">Lync 2013: Translate a conversation from one language to another in real time</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-start-a-new-4775ec38">MeetNow</a></p></td>
<td><p></p>
<p>Starts a MeetNow conference by using the <strong>BeginMeetNow()</strong> method from the Lync <a href="automation-class-microsoft-lync-model-extensibility_2.md">Automation</a> class. Features include:</p>
<ul>
<li><p>Start a MeetNow conference using the Lync <a href="automation-class-microsoft-lync-model-extensibility_2.md">Automation</a> class.</p></li>
</ul>
<p>Path: %PROGRAMFILES%\Microsoft Lync\SDK\Samples\MeetNow or %PROGRAMFILES(X86)%\Microsoft Lync\SDK\Samples\MeetNow</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p><a href="http://code.msdn.microsoft.com/lync-2013-start-a-new-4775ec38">Lync 2013: Start a new conference using the BeginMeetNow method</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-join-meeting-1f65c20a">JoinMeetingFromLobby</a></p></td>
<td><p>Joins a running meeting and notifies user if they are in the meeting lobby. Features include:</p>
<ul>
<li><p>Starts a JoinMeeting conference by using Lync <a href="automation-class-microsoft-lync-model-extensibility_2.md">Automation</a> class.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES%\</em>Microsoft Lync\SDK\Samples\JoinMeetingFromLobby or <em>%PROGRAMFILES(X86)%\</em>Microsoft Lync\SDK\Samples\JoinMeetingFromLobby</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p><a href="http://code.msdn.microsoft.com/lync-2013-join-meeting-1f65c20a">Lync 2013: Join meeting from lobby using the Automation class</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-use-automation-cd6dfa46">Automation</a> conversation</p></td>
<td><p>This sample uses the <a href="automation-class-microsoft-lync-model-extensibility_2.md">Automation</a> class in the Lync 2013 API to start a new conversation with one or more Lync contacts. Features include:</p>
<ul>
<li><p>Uses the <a href="automation-class-microsoft-lync-model-extensibility_2.md">Automation</a> API in Lync to start a new conversation with a set of Lync contacts.</p></li>
<li><p>The conversation can be started with one or more modalities at the same time.</p></li>
<li><p>Shows how to set up specific settings for each conversation modality.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES%\</em>Microsoft Lync\SDK\Samples\Automation or <em>%PROGRAMFILES(X86)%</em>\Microsoft Lync\SDK\Samples\Automation</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p><a href="http://code.msdn.microsoft.com/lync-2013-use-automation-cd6dfa46">Lync 2013: Use Automation class to start a new conversation with Lync contacts</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Conversation Window Docker</p></td>
<td><p>This application demonstrates the ability to dock a conversation window within another WPF application. Features include:</p>
<ul>
<li><p>Docks a conversation window into a WPF application.</p></li>
<li><p>Demonstrates how to use a <a href="http://go.microsoft.com/fwlink/?linkid=198548%26clcid=0x409">WindowsFormsHost</a> to dock a conversation window.</p></li>
<li><p>Shows how to handle the different events raised by a conversation window.</p></li>
<li><p>Shows how to flash the window when the conversation window requires attention.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES%\</em>Microsoft Lync\SDK\Samples\DockingConversationWindowSample or <em>%PROGRAMFILES(X86)%</em>\Microsoft Lync\SDK\Samples\DockingConversationWindowSample</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p><a href="http://code.msdn.microsoft.com/lync-2013-start-and-dock-00a29819">Lync 2013: Start and dock an IM chat using StartInstantMessagingButton control</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Audio/Video Conversation</p></td>
<td><p>This sample Uses the <a href="microsoft-lync-model-conversation-namespace_2.md">Microsoft.Lync.Model.Conversation</a> and <a href="microsoft-lync-model-conversation-audiovideo-namespace_2.md">Microsoft.Lync.Model.Conversation.AudioVideo</a> namespaces from the Lync 2013 API to implement a conversation window. Features include:</p>
<ul>
<li><p>Implements a fully functional audio/video conversation window.</p></li>
<li><p>Shows how to register and handle conversation manager and audio/video conversation events.</p></li>
<li><p>Uses the most common features of <a href="conversation-class-microsoft-lync-model-conversation_2.md">Conversation</a>, <a href="avmodality-class-microsoft-lync-model-conversation-audiovideo_2.md">AVModality</a>, <a href="audiochannel-class-microsoft-lync-model-conversation-audiovideo_2.md">AudioChannel</a>, and <a href="videochannel-class-microsoft-lync-model-conversation-audiovideo_2.md">VideoChannel</a>.</p></li>
</ul>
<p>Path: <em>%PROGRAMFILES%\</em>Microsoft Lync\SDK\Samples\AudioVideoConversation or <em>%PROGRAMFILES(X86)%</em>\Microsoft Lync\SDK\Samples\AudioVideoConversation</p>
<p>Download the sample from Code Gallery at the following location:</p>
<ul>
<li><p><a href="http://code.msdn.microsoft.com/lync-2013-use-the-lync-68eabecb">Lync 2013: Use the Lync 2013 API to create a conversation window</a></p></li>
</ul></td>
</tr>
</tbody>
</table>


## Additional resources

  - [Code samples: Lync SDK](code-samples-lync-sdk.md)

