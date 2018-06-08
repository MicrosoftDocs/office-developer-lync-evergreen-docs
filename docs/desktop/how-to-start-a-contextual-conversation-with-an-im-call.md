---
title: 'How to: Start a contextual conversation with an IM call'
TOCTitle: 'How to: Start a contextual conversation with an IM call'
ms:assetid: dc333a91-1502-4be7-bc7f-18b489f2193c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933211(v=office.15)
ms:contentKeyID: 50877354
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# How to: Start a contextual conversation with an IM call

Learn how to use the Microsoft Lync Control [ContextualInformation](https://msdn.microsoft.com/en-us/library/hh363342\(v=office.15\)) property to add the sender’s context to an instant messaging (IM) conversation, using Microsoft Silverlight or Microsoft Windows Presentation Foundation (WPF).

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Contextual conversation overview<br />
Prerequisites<br />
Create the walkthrough application<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Contextual conversation overview

Use contextual conversation to increase productivity by capturing the message sender’s context and setting up the receiver’s context. Adding context to the message in this way streamlines communication by allowing call participants to get on the same page quicker. Context is transmitted as a data structure that is composed of one or more pieces of contextual information. Context can be delivered as a conversation subject line or as application data. In its simplest form, it consists of a subject string, a contextual link that appears on the recipient’s conversation invite, or both. Contextual data can also include an application ID with associated application data. For more information, see [Contextual Lync conversations](contextual-lync-conversations.md).

## Prerequisites

For a list of prerequisites, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

## Create the walkthrough application

The following procedure works for Silverlight and WPF applications.

  - For information about contextual application registration, see [Register contextual conversation packages](register-contextual-conversation-packages.md).

  - For information about contextual conversation walkthrough applications, see [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md).

### To create the contextual conversation walkthrough application

1.  Create the application.
    
    For information about creating Silverlight and WPF applications, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md). The following instructions assume this is a unified communications WPF application, but the information can be used with other application types.

2.  In Window1.xaml, add the following XAML.
    
    Note that the empty braces in the [ApplicationId](http://go.microsoft.com/fwlink/?linkid=207179%26clcid=0x409) property escape the following ‘{’.
    
    ```xaml
    <StackPanel>
      <StackPanel.Resources>
        <controls:ConversationContextualInfo 
          x:Key="contextualInfo" 
          ApplicationId="{}{21224942-AC24-4D0D-B0C7-6107D79448DF}"
          ApplicationData="your application data here"
    
          Subject="Try out this customized subject!"
        />
      </StackPanel.Resources>
        <controls:StartInstantMessagingButton 
          x:Name="startInstantMessaging"
          Source="sip:barbara@contoso.com"
          ContextualInformation="{StaticResource contextualInfo}"
        />
    </StackPanel>
    ```

3.  Edit the [Source](https://msdn.microsoft.com/en-us/library/hh363511\(v=office.15\)) property on the [StartInstantMessagingButton](https://msdn.microsoft.com/en-us/library/hh379340\(v=office.15\)) control to provide a valid value.

4.  Install and register the application on the sending and receiving computers.
    
    For information about contextual application registration, see [Register contextual conversation packages](register-contextual-conversation-packages.md).

5.  Build and run the application.

6.  Click the StartInstantMessagingButton control.

7.  Enter message text in the conversation window and then press **ENTER**.

8.  On the receiving computer, use the [GetApplicationData](http://go.microsoft.com/fwlink/?linkid=210831%26clcid=0x409) method to retrieve the data or trap one of the [Conversation](http://go.microsoft.com/fwlink/?linkid=210832%26clcid=0x409) object events.

## See also

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

  - [Contextual Lync conversations](contextual-lync-conversations.md)

