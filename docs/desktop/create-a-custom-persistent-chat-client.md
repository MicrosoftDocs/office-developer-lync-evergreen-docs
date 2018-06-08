---
title: Create a custom Persistent Chat client
TOCTitle: Create a custom Persistent Chat client
ms:assetid: 70542183-dd35-454a-beac-6617dd1e0498
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933074(v=office.15)
ms:contentKeyID: 50877204
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Create a custom Persistent Chat client

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the components of a typical custom Lync 2013 Persistent Chat window that is built by using Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Persistent Chat room client scenario<br />
Chat room details<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Persistent Chat room client scenario

A typical scenario where you use the classes in the [Microsoft.Lync.Model.Room](https://msdn.microsoft.com/en-us/library/jj277187\(v=office.15\)) namespace is to create a chat room client in your own application. The design of your chat room UI is completely up to you. However, it should contain several basic UI features. These features include the following:

  - A selectable chat room list whose source is the Lync contact list.

  - A set of text controls that display the chat room title and room description.

  - A list of previously posted messages that can be refreshed according to a user’s needs.

  - A set of controls that let a user select the range of messages that are used to refresh the message list.

  - A registered event listener that refreshes the message display with each new message posted to the room.

  - An entry control that accepts a string to be posted to the chat room as a message.

Optional chat room features can include a chat room roster that shows a list of other participating users and a rich-text entry control that lets a user format the message text before sending it.

Figure 1 shows the Persistent Chat window that is discussed in this topic. The elements that you must have to create a Persistent Chat window appear in this window. The elements in the chat room window include the following:

1.  The Persistent Chat rooms that a user is following in the contact list.
    
    All displayed messages have been posted to the selected chat room and the selected chat room is the destination of any message posted by the user.

2.  Participants in the chat room that is selected in the chat room list.

3.  The description of the selected chat room.

4.  The number of unread messages posted to the selected chat room.

5.  The messages that have been posted to the chat room by any member of the room.
    
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
    <td><p>This example uses a ListBox control, which ignores RTF formatting codes in messages posted to a room. For more information, see <a href="http://msdn.microsoft.com/en-us/library/system.windows.forms.listbox.aspx">ListBox Class</a>.</p></td>
    </tr>
    </tbody>
    </table>

6.  A text field that accepts a message ID that is used to get a set of messages previously posted to the selected room.

7.  A text field that accepts an integer value for the maximum number of messages to retrieve with each request for messages.

8.  A button to start a message get request that uses the values from the two previous text fields.

9.  An RTF text box that accepts a string that will be posted to the room as a new message.

10. A button that posts a new message to the room.

Figure 1. Simple Persistent Chat window

  
![Simple Group Chat Client](images/JJ933074.UC_OCS15ConLyncClient_HowToCreateachatclient(Office.15).png "Simple Group Chat Client")

This topic does not explore the code details for the UI controls that appear in figure 1. The following topics show how to write code for the controls that are used in figure 1.

## Chat room details

After you create the UI control elements that appear in figure 1, the topics in the following table show how to add the content for the controls with values obtained from a [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/en-us/library/jj266467\(v=office.15\)) instance, post messages to a chat room, and respond to events from the chat room.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Topic</p></th>
<th><p>Persistent Chat feature</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="how-to-find-a-chat-room.md">How to: Find a chat room</a></p></td>
<td><p>Describes how to fill the followed room list that uses chat rooms from a user’s contact list. This topic also shows how to get chat rooms that are not in the user’s contact list.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-view-chat-room-participants.md">How to: View chat room participants</a></p></td>
<td><p>Describes how to display a roster of chat room members that are in the chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-send-a-message-to-a-chat-room.md">How to: Send a message to a chat room</a></p></td>
<td><p>Describes how to post a message to a chat room.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-read-messages-sent-to-a-chat-room.md">How to: Read messages sent to a chat room</a></p></td>
<td><p>Describes how to display the messages as they are posted to a chat room.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-filter-an-outgoing-message-from-a-local-user-to-a-chat-room.md">How to: Filter an outgoing message from a local user to a chat room</a></p></td>
<td><p>Describes how to catch messages before a local user can post a message and then pass the message on, reformat the message text, or cancel the message.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Beyond the basics: Persistent Chat](beyond-the-basics-persistent-chat.md)

