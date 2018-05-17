---
title: 'Core concepts: Lync conversations'
TOCTitle: Lync conversations
ms:assetid: 1c805dc1-5f85-4c8a-a0c3-a620433739db
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937273(v=office.15)
ms:contentKeyID: 50877090
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Core concepts: Lync conversations

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the foundational Microsoft Lync 2013 SDK objects that make up the programmable components of a Microsoft Lync 2013 conversation.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Conversation overview<br />
Core concepts in conversations<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>


## Conversation overview

The Lync platform provides a conversation manager class that combines the features of conversation factory class with a view of the collection of conversations that are active on the platform at any time. The conversation manager exposes events that inform you when the local user is invited to a conversation and lets you respond by accepting or declining such invitations.

A Lync conversation is encapsulated by a conversation class. This conversation class has properties, methods, and events that give you great control over the conversation. Use the methods to do such things as invite additional people to the conversation, remove people from the conversation, add audio or video to an ongoing IM conversation, start resource sharing (desktop, program, or display), or even manage the content sharing stage of the conversation.

These modes of conversation, from IM through content sharing, are encapsulated by a set of conversation modality classes. All of these modality classes inherit a common modality parent, but have unique properties, methods, and events that are suited for the specific demands of the modality they encapsulate. Use the modality classes to control the flow of modality-specific information through a conversation. You can hold, forward, and transfer audio conversations just like you would on a PBX. These actions are performed on a conversation’s audio/video modality.

## Core concepts in conversations

The concepts described in the following topics are essential for understanding how to add Lync features to an application.

## In this section

  - [Conversation manager](conversation-manager.md)

  - [Conversation modalities](conversation-modalities.md)

  - [Conversation participants](conversation-participants.md)

  - [Conversation window automation in Lync SDK](conversation-window-automation-in-lync-sdk.md)

## Additional resources

  - [Get started with Lync conversations](get-started-with-lync-conversations.md)

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

  - [Beyond the basics: Lync conversations](beyond-the-basics-lync-conversations.md)

