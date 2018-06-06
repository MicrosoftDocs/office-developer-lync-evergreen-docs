---
title: Conversation window automation in Lync SDK
TOCTitle: Conversation window automation
ms:assetid: fdbbd783-9d3a-4120-8932-8d48f5c854ae
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933260(v=office.15)
ms:contentKeyID: 50877407
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Conversation window automation in Lync SDK

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about Microsoft Lync 2013 conversation window automation in Microsoft Lync 2013 SDK and how conversation window automation lets you integrate Lync 2013 into an application with very little code and in a short time.

**Last modified:** April 16, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
What is conversation window automation?<br />
Conversation window automation objects<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-join-meeting-1f65c20a">Join meeting from lobby using the Automation class</a></p></td>
</tr>
</tbody>
</table>

## What is conversation window automation?

Conversation window automation is a feature that lets you programmatically start a new Lync 2013 conversation window that hosts a conversation in any of the conversation modes supported by the Lync client. You provide a list of Lync user SIP addresses along with the desired conversation modes in the automation method call and a conversation window opens in the desired conversation mode and with the invited users. Automation lets you create a parent/child relationship between a container control in your application as parent and the conversation window as child. This relationship docks the conversation window in your application as though it was an organic part of your application.

A conversation window can be made context-aware at the time it is started. That is, the conversation window can be extended to provide conversation participants with contextual information from the launching application. For example, if your application is an accounts payable (AP) system and you start a conversation window from within an AP screen for a given payable transaction, the details of the transaction can be shown in the conversation window so that users have context for conversing.

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
<td><p>The mechanism that extends the conversation window with contextual information has two parts. The first part is the extension tabs on the conversation window UI that are built into the conversation window. The second part is a Silverlight browser extension application that you must write. This extension application is hosted in the conversation window on an extension tab. The extension application must be able to call into your application for context data and call into the Lync API for access to the object that encapsulates the conversation itself. For information about writing extension applications, see <a href="how-to-create-a-conversation-window-extension-application-in-lync-sdk.md">How to: Create a Conversation Window Extension application in Lync SDK</a>.</p></td>
</tr>
</tbody>
</table>

## Conversation window automation objects

The [Microsoft.Lync.Model.Extensibility](https://msdn.microsoft.com/en-us/library/jj278382\(v=office.15\)) namespace contains the five classes and three enumerations that are responsible for exposing the automation feature. The [Automation](https://msdn.microsoft.com/en-us/library/jj293816\(v=office.15\)) class is the entry point into the automation feature and provides the method that starts the conversation window and returns a reference to the new conversation window. The [ConversationWindow](https://msdn.microsoft.com/en-us/library/jj293606\(v=office.15\)) class represents a started conversation window. The enumerations and other classes of the namespace support the conversation modality options and docking feature in automation.

## Additional resources

  - [Core concepts: Lync conversations](core-concepts-lync-conversations.md)

  - [How to: Join a Lync conversation](how-to-join-a-lync-conversation.md)

  - [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md)

  - [How to: Start an automation audio conversation](how-to-start-an-automation-audio-conversation.md)

  - [How to: Start a meet-now meeting](how-to-start-a-meet-now-meeting.md)

