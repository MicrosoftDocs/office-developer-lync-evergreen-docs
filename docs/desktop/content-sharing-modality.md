---
title: Content sharing modality
TOCTitle: Content sharing modality
ms:assetid: ccbe213b-9a51-4a5b-b637-cf7abbd81e64
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933194(v=office.15)
ms:contentKeyID: 50877338
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Content sharing modality

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the Microsoft Lync 2013 conversation modality that is used to administer meeting content in a Lync conversation.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
What is shared content in Lync 2013?<br />
Typical content sharing usage scenario<br />
Content sharing objects<br />
Working with the content sharing modality object<br />
Working with presentable content<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## What is shared content in Lync 2013?

Shared content is any object that can be uploaded to a Microsoft Lync 2013 conversation to be presented on the sharing stage. Shared content objects include the following types:

  - Whiteboards

  - PowerPoint slide decks

  - Native file objects

These content sharing objects enable conversation participants to actively participate in a conversation by annotating whiteboard and PowerPoint content on the sharing stage in the conversation. Annotated content is visible to all participants and can be saved locally to preserve feedback to ideas presented in the conversation.

Native file types include such types as Word files, text files, and image files. Executable files cannot be uploaded to a content bin. Native files cannot be opened on the sharing stage but conversation participants can download native files that have been uploaded by other participants. A downloaded file can be modified and then uploaded to the same conversation as long as it's given a unique title. For example, Sam uploads a Word document to a conversation with the title "Project proposal." Mary and George are in the conversation and they both download a copy of "Project proposal." Each participant adds comments to their copy of the proposal and uploads the commented Word document as "Project proposal – Mary" and "Project proposal – George."

Resource sharing is different than content sharing because a *view* of an object such as a desktop, monitor, or process resource is shared and not the object itself. A token representing the resource view is uploaded and referred to when a participant moves the resource view to the content stage or requests control of the resource.

A shared resource such as a desktop or monitor display area can be placed on the content sharing stage but cannot be annotated and can only be controlled by one participant at a time.

## Typical content sharing usage scenario

Microsoft Lync 2013 SDK makes it possible for you to enable your application to manage a meeting from end to end. That is, you can start a meeting, invite other people, upload presentable content, move uploaded content on to and off of the sharing stage, and then remove content from the meeting. You can design a UI that meets your unique requirements. For example, you might need to create a UI that hides many of the complexities of Lync 2013 so that a person can start a meeting with a single mouse-click. In a conference room setting, there are typically one or more large wall displays that show a meeting sharing stage and live meeting video. You can configure a desktop display that shows a custom meeting manager and lets you control meeting content in a private view.

Figure 1 shows a Windows Form that implements a simple meeting console. The console is used to start a new meeting and then manage the sharing stage of the meeting window that is shown on an auditorium display.

Figure 1. Custom meeting console

  
![Content bin manager application UI](images/JJ933194.UC_OCS15ConLyncClient_ContentBinManagerfigure3(Office.15).png "Content bin manager application UI")

## Content sharing objects

To build a console like the one shown in figure 1, your development is centered on five objects out of the Lync 2013 API object model. You also handle a series of events and get other API objects by reading properties and handling events on these objects. These five objects include the following:

  - [LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\))  
    This is the API platform and the entry point for further coding.

  - [ConversationManager](https://msdn.microsoft.com/library/jj266018\(v=office.15\))  
    This is a factory class that creates new conversation objects.

  - [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\))  
    This class represents a single meeting.

  - [ContentSharingModality](https://msdn.microsoft.com/library/jj266998\(v=office.15\))  
    This class is the part of a meeting that handles all the presentable content work that your console application does.

  - [ShareableContent](https://msdn.microsoft.com/library/jj277217\(v=office.15\))  
    An object of this class encapsulates a single presentable content item such as a PowerPoint deck.

For more information about signing in to and out of Lync 2013 by using the [LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) object, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md). For information about conversations, see [Core concepts: Lync conversations](core-concepts-lync-conversations.md).

## Working with the content sharing modality object

In most cases, you use the [Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality](https://msdn.microsoft.com/library/jj266998\(v=office.15\)) that you get from the [Conversation.Modalities](https://msdn.microsoft.com/library/jj275560\(v=office.15\)) property of a conversation object. This modality exposes all the methods and properties that are needed to manage presentable content. To respond to an invitation to view shared presentable content, you need to get the [ContentSharingModality](https://msdn.microsoft.com/library/jj266998\(v=office.15\)) that is owned by the meeting participant who is inviting the local participant.

[Microsoft.Lync.Model.Conversation.Sharing.ContentSharingModality](https://msdn.microsoft.com/library/jj266998\(v=office.15\)) inherits the methods, properties, and events of [Microsoft.Lync.Model.Conversation.Modality](https://msdn.microsoft.com/library/jj274796\(v=office.15\)) but adds additional class members that are scoped specifically to presentable content management. These presentable content-specific members allow you to create [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/library/jj277217\(v=office.15\)) objects that represent presentable content, monitor the content bin for activity such as adding or removing content, and moving content to and from the sharing stage.

The [ContentSharingModality.ContentCollection](https://msdn.microsoft.com/library/jj267301\(v=office.15\)) property represents the content bin of the meeting. The property returns a collection of [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/library/jj277217\(v=office.15\)) objects that any meeting presenter can update. For example, assume a meeting has been started by Bob. Bob invites John and Nancy. Both John and Nancy are promoted to the presenter role and have joined the meeting from remote endpoints. If John starts sharing a new whiteboard, both Bob and Nancy can annotate the white board, clear annotations, or save the annotations locally. This is possible because John’s whiteboard is added to the local **ContentCollection** of all meeting participants.

## Working with presentable content

A presentable content item, whether a whiteboard, a PowerPoint deck, or a native file, is represented by a [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/library/jj277217\(v=office.15\)) class object. Although this is the common class for all types of presentable content, you can only call the class methods that are appropriate for the underlying content type. For example, the [ShareableContent.BeginDownloadFile](https://msdn.microsoft.com/library/jj278158\(v=office.15\)) method can only be called on a [Microsoft.Lync.Model.Conversation.Sharing.ShareableContent](https://msdn.microsoft.com/library/jj277217\(v=office.15\)) object when the type of that object is **ShareableContentTypeNativefile()**.

## See also

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [What you can do with content sharing](what-you-can-do-with-content-sharing.md)

  - [Beyond the basics: Content sharing](beyond-the-basics-content-sharing.md)

