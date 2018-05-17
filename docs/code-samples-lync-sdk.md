---
title: 'Code samples: Lync SDK'
TOCTitle: Code samples
ms:assetid: 991281a6-b3c0-4a89-bdb1-6f37b8863268
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933140(v=office.15)
ms:contentKeyID: 50877274
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Code samples: Lync SDK

![Code sample topic](images/JJ937254.mod_icon_codesample_long(Office.15).png "Code sample topic")

Learn about the quick-start samples and application reference samples that are installed with Microsoft Lync 2013 SDK.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
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


The two comprehensive reference samples provide a broader look at the API. Use a reference sample to see how to build an application that implements a complete scenario using combinations of Lync Controls and objects from the Lync 2013 API object model.

The SDK installation program places the samples in the *%PROGRAMFILES%\\*Microsoft Lync\\SDK\\Samples folder on 32-bit computers and the *%PROGRAMFILES(X86)%*\\Microsoft Lync\\SDK\\Samples folder on 64-bit computers.

## Quick-start samples

When you install Microsoft Lync 2013 SDK, you get a set of quick-start sample applications, including Windows Forms, Windows Presentation Foundation (WPF), and Silverlight projects. These quick-start samples focus on specific API features. Refer to these samples when you want to see how to complete a small task such as putting a contact list control on a page in your WPF application.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Feature category</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="presence-samples.md">Presence samples</a></p></td>
<td><p>The quick-start presence samples show how to publish and get presence for a contact by using presence controls or objects in the Lync 2013 API object model.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-contact-samples.md">Lync contact samples</a></p></td>
<td><p>The quick-start contact samples show how to interact with Lync contacts by using the objects of the Lync 2013 API and controls from the <a href="microsoft-lync-controls-namespace_1.md">Microsoft.Lync.Controls</a> namespace.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-conversation-samples.md">Conversation samples</a></p></td>
<td><p>The quick-start conversation samples show how to interact with Lync conversations by using Lync 2013 API objects and controls from the <a href="microsoft-lync-controls-namespace_1.md">Microsoft.Lync.Controls</a> namespace.</p></td>
</tr>
<tr class="even">
<td><p><a href="persistent-chat-samples.md">Persistent Chat samples</a></p></td>
<td><p>The Persistent Chat sample applications demonstrate how to add chat room features to your Microsoft Lync 2013 SDK-enabled application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="resource-and-content-sharing-samples.md">Resource sharing samples</a></p></td>
<td><p>The sharing sample applications demonstrate how to share resources and content in a conversation and then manage user’s control of a shared item.</p></td>
</tr>
</tbody>
</table>


## Reference samples

The following samples provide complete application examples using the Lync 2013 API. These examples show how to use the Lync 2013 API in real-world scenarios.

### Conversation translator

The [ConversationTranslator](http://code.msdn.microsoft.com/lync-2013-translate-a-a849e513) sample application uses the [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace.md) namespace from the Lync model API to intercept instant messages and provide translation using Bing Web Services.

Features:

  - The sample provides an example architecture for registering for and handling asynchronous Lync 2013 API events in Silverlight.

  - Register for two Conversation related events: [ParticipantAdded](conversation-participantadded-event-microsoft-lync-model-conversation.md) and [InstantMessageReceived](instantmessagemodality-instantmessagereceived-event-microsoft-lync-model-conversation.md).

  - Use the [BeginSendMessage](instantmessagemodality-beginsendmessage-method-microsoft-lync-model-conversation.md) method and callback.

  - Uses the Bing Translator Web Service.

Path: *%PROGRAMFILES(X86)%*\\Microsoft Lync\\SDK\\Samples\\micro\\ConversationTranslator

### Proposal tracker

The [ProposalTracker](http://code.msdn.microsoft.com/lync-2013-use-lync-60a934d7) sample application shows how to use Lync Controls in a Silverlight application. The application includes a tool that is used by a fictitious company called Fabrikam Inc. that tracks a list of proposals and sales people in the company.

Features:

  - Demonstrates how to use the following Lync Controls in a Silverlight application.
    
      - MyStatusArea Control
    
      - PresenceIndicator Control
    
      - ContactCard Control
    
      - ContactList Control
    
      - CustomContactList Control
    
      - ContactSearchInputBox Control
    
      - ContactSearchResultList Control

  - Demonstrates how to use ContextualConversation between two conversation windows with the companion application called MiniProposalTracker that runs in Lync Conversation Window Extension.

Path: *%PROGRAMFILES%\\*Microsoft Lync\\SDK\\Samples \\ProposalTracker or *%PROGRAMFILES(X86)%*\\Microsoft Lync\\SDK\\Samples \\ProposalTracker

## Additional resources

  - [Lync 2013 SDK general reference](lync-2013-sdk-general-reference.md)

