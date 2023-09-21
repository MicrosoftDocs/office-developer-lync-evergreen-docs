---
title: Get started with Lync conversations
TOCTitle: Lync conversations
ms:assetid: db65193e-57ea-44a1-b949-06ae2b655d8b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933207(v=office.15)
ms:contentKeyID: 50877350
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Get started with Lync conversations

Learn about programming Microsoft Lync 2013 conversations with Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013



<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><a href="get-started-with-lync-conversations.md#Start" class="uri"><img src="images/JJ933215.mod_icon_getstartbox(Office.15).gif"/></a>   <a href="get-started-with-lync-conversations.md#Do" class="uri"><img src="images/JJ933215.mod_icon_dobox(Office.15).gif"/></a>   <a href="get-started-with-lync-conversations.md#Learn" class="uri"><img src="images/JJ933215.mod_icon_startbox(Office.15).gif"/></a></p></td>
</tr>
</tbody>
</table>

## What is a Lync 2013 conversation?

A Microsoft Lync 2013 conversation is a dialog in IM text, audio, video, or desktop sharing modalities between two or more Lync users. When only two people are in the conversation, the conversation involves only two computer endpoints. This is known as a peer-to-peer conversation. When more than two people are in the conversation, the conversation endpoints include the Lync Server 2013 endpoint that aggregates the conversation modalities so that all participants can see and hear the contributions of other participants.

The Lync 2013 API exposes classes that encapsulate the endpoints, modalities, and participants in a conversation. These classes let you create an application that can give a user the same immersive experience that is available by using the Lync 2013 client.

<a name="Start"></a> 

## Get started with Lync 2013 conversations

The prerequisites for working with Lync 2013 conversations are as follows:

  - Microsoft Lync 2013 SDK

  - Visual Studio 2010 or Visual Studio 2012

  - Microsoft Lync 2013

### Lync 2013 conversation essentials

To understand how to work with Lync 2013 conversations, it's important to become familiar with the concepts in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="conversation-manager.md">Conversation manager</a></p></td>
<td><p>Describes the role of the <a href="https://msdn.microsoft.com/library/jj266018(v=office.15)">ConversationManager</a> object in starting and joining conversations.</p></td>
</tr>
<tr class="even">
<td><p><a href="conversation-modalities.md">Conversation modalities</a></p></td>
<td><p>Describes how conversation modes are encapsulated by <a href="https://msdn.microsoft.com/library/jj274796(v=office.15)">Modality</a> objects.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversation-participants.md">Conversation participants</a></p></td>
<td><p>Describes how <a href="https://msdn.microsoft.com/library/jj267311(v=office.15)">Microsoft.Lync.Model.Conversation.Participant</a> objects represent Lync 2013 users in a conversation.</p></td>
</tr>
</tbody>
</table>
<a name="Do"></a> 

## What can you do with Lync 2013 conversations?

Microsoft Lync 2013 SDK gives you the ability to start conversations in all Lync 2013 modalities, join conversations, extend the conversation experience by embedding application specific information in extensions to conversation windows, and perform call transfer operations such as holding, transferring, and forwarding audio/video Lync 2013 calls.

The following table lists basic tasks for working with Lync 2013 conversations.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Task</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="how-to-join-a-lync-conversation.md">How to: Join a Lync conversation</a></p></td>
<td><p>Learn how to use Microsoft Lync 2013 SDK to code a feature that lets a user join a Lync 2013 conversation after receiving an invitation from another Lync 2013 user or a federated user.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-start-a-lync-im-conversation.md">How to: Start a Lync IM conversation</a></p></td>
<td><p>Learn how to use Microsoft Lync 2013 SDK to programmatically start a Lync 2013 conversation, invite a user, and send the first IM text.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-start-an-automation-audio-conversation.md">How to: Start an automation audio conversation</a></p></td>
<td><p>Learn how to use Microsoft Lync 2013 SDK to automate opening a new Lync 2013 conversation window to host an audio conversation with another Lync 2013 user.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-dock-a-conversation-window-in-lync-sdk.md">How to: Dock a conversation window in Lync SDK</a></p></td>
<td><p>Learn how to dock a Microsoft Lync 2013 conversation window inside a WPF window and respond to conversation window sizing and attention events to prevent the conversation window from undocking when its size changes.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-create-a-conversation-window-extension-application-in-lync-sdk.md">How to: Create a Conversation Window Extension application in Lync SDK</a></p></td>
<td><p>Learn how to create a simple Microsoft Silverlight application that sends and receives information in conversation context and use Microsoft Lync 2013 SDK to run it in a Microsoft Lync 2013 Conversation Window Extension (CWE).</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-install-a-cwe-application-in-lync-sdk.md">How to: Install a CWE application in Lync SDK</a></p></td>
<td><p>Learn how to create a registry (.reg) file that registers a Microsoft Lync 2013 Conversation Window Extension (CWE) on a computer so that the CWE can be opened in a Lync 2013 conversation window.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-start-an-extension-application-in-a-lync-conversation-window.md">How to: Start an extension application in a Lync conversation window</a></p></td>
<td><p>Learn how to set Microsoft Lync 2013 Conversation Window Extension properties, set CWE size and hosting location at runtime, and then start an IM conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-send-and-receive-context-information-in-a-lync-conversation.md">How to: Send and receive context information in a Lync conversation</a></p></td>
<td><p>Learn how to use Microsoft Lync 2013 SDK to send contextual data in a Microsoft Lync 2013 conversation when the Lync clients at all endpoints have been suppressed.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-start-a-lync-audio-conversation.md">How to: Start a Lync audio conversation</a></p></td>
<td><p>Learn how to start an audio conversation. This process involves creating a conversation with a local and remote participant and connecting to the remote participant using the participant’s audio/video (AV) modality. To complete this process, you must handle state change events on both the client’s <a href="https://msdn.microsoft.com/library/jj266018(v=office.15)">ConversationManager</a> instance and the conversation itself.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-park-and-unpark-a-lync-audio-conversation.md">How to: Park and unpark a Lync audio conversation</a></p></td>
<td><p>Learn how to use the call park feature, which can be used programmatically with Microsoft Lync 2013 SDK and provides a call hold and call park feature.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-forward-a-lync-audio-conversation.md">How to: Forward a Lync audio conversation</a></p></td>
<td><p>Learn how to programmatically forward a Microsoft Lync 2013 audio call.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-transfer-a-lync-audio-conversation.md">How to: Transfer a Lync audio conversation</a></p></td>
<td><p>Learn how to programmatically transfer a Microsoft Lync 2013 audio call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-hold-and-retrieve-a-lync-audio-conversation.md">How to: Hold and retrieve a Lync audio conversation</a></p></td>
<td><p>Learn how to programmatically hold and retrieve a Microsoft Lync 2013 audio call.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-handle-delegated-lync-audio-calls.md">How to: Handle delegated Lync audio calls</a></p></td>
<td><p>Learn how to programmatically handle a delegated Microsoft Lync 2013 audio call.</p></td>
</tr>
</tbody>
</table>
<a name="Learn"></a> 

## Beyond the basics: Learn more about Lync 2013 conversations

After you have added basic conversation features to your application, you have the experience necessary to add new features such as conversation window docking, extending the conversation window itself with context specific functionality, and call delegation so that Lync 2013 can take calls on behalf of another user.

The following table lists advanced concepts for working with Lync 2013 conversations.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Concept</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="conversation-window-docking.md">Conversation window docking</a></p></td>
<td><p>Learn about the Microsoft Lync 2013 conversation window docking feature that lets you host a conversation window inside a container control in your application.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-conversation-window-extension.md">Lync Conversation Window Extension</a></p></td>
<td><p>Learn about the Conversation Window Extension (CWE) feature of the Microsoft Lync 2013 client conversation window and how a CWE is opened, closed, and sized.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contextual-lync-conversations.md">Contextual Lync conversations</a></p></td>
<td><p>Learn about contextual conversations in Lync 2013 and about application scenarios, application development models, and contextual extension application package registration.</p></td>
</tr>
<tr class="even">
<td><p><a href="call-delegation-in-lync.md">Call delegation in Lync</a></p></td>
<td><p>Learn about the call delegation feature in Microsoft Lync 2013 SDK that allows a user to take Lync 2013 calls on behalf of another user.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Get started with Lync 2013 SDK](get-started-with-lync-2013-sdk.md)

  - [Core concepts: Lync conversations](core-concepts-lync-conversations.md)

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

  - [Beyond the basics: Lync conversations](beyond-the-basics-lync-conversations.md)

