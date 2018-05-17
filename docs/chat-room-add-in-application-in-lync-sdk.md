---
title: Chat room add-in application in Lync SDK
TOCTitle: Chat room add-in application
ms:assetid: 916f5a99-c845-47d2-88a2-41837f4bc6a1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933129(v=office.15)
ms:contentKeyID: 50877259
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Chat room add-in application in Lync SDK

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the Microsoft Lync 2013 Persistent Chat room add-in feature through the scenarios in which the add-in is used and the classes and methods that are used to create an add-in.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p>
<p><strong>In this article</strong><br />
Chat room add-in overview<br />
Typical usage scenario<br />
Persistent Chat room API types<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Chat room add-in overview

A Persistent Chat room add-in is a Microsoft Silverlight browser application that is hosted in an HTML page. The HTML page is hosted in an extension pane that is located on the right side of the Persistent Chat window message area. An add-in can intercept the message text that the local user usually posts directly to the chat room message area. You can use it to create your own message display experience.

The add-in is used for the following chat room messaging related tasks:

  - Filter messages that are created by the locally joined user before the messages are sent to the chat room.

  - Apply formatting to the local user’s message text before the message is sent to the chat room. The formatting process can check the spelling and grammar, but you must write your own logic.

  - Replace the text of a pending message post with different text.

  - Format and display bot-generated messages in the add-in.

The add-in uses the Microsoft Lync 2013 API to connect to the hosting chat room. Once connected, the add-in can get the full message history of the chat room, post new messages to the chat room, and intercept the local user’s messages before they are posted to the chat room. You can embed a browser control in the add-in to display HTML from any source such as msn.com. If you don’t want to render HTML, you can build a UI with XAML. The add-in can make any web service calls that a WPF or Silverlight window makes. This means that you can get content from sources such as Bing and display in the add-in. Since an add-in can get message text before it is posted, you can use the text in a Bing web service call and display relevant search results directly in the add-in. The pending message can be posted or cancelled.

Figure 1 shows an example that obtains access to the hosting [Microsoft.Lync.Model.Room.Room](room-class-microsoft-lync-model-room_2.md) represented by the persistent chat window. After getting the **Room** instance, the add-in registers for room messaging events in order to catch messages posted to the room by participating user in addition to pending posts originated by the local user.

Figure 1. A simple chat room add-in

  
![A simple chat room add-in](images/JJ933129.UC_OCS15ConLyncClient_HowToCreateAChatRoomAddonfigure1(Office.15).png "A simple chat room add-in")

## Typical usage scenario

The chat room add-in is used by a brokerage firm whose traders need current information about currency exchange rates or stock prices. Because this information changes quickly, an employee must be able to see and react to the changes as they occur. A Persistent Chat room is a good venue for this because it lets employees take action on changes by messaging other people in the chat room when a currency trade is optimal. To make this work, the brokerage programmer creates a bot that monitors changes to stock prices or currency exchange rates from an outside source.

The bot is joined to the chat room and messages the room when a value changes. To reduce bandwidth use, the bot is programmed to send messages that are composed of coded headers and data and packaged as a story. These coded bot messages are not ordinarily human-readable and would make little sense to the chat room users. To convert these coded messages into readable text, the programmer creates a Persistent Chat room add-in and associates it with a chat room. When a user joins the chat room, the add-in is hosted in the chat room add-in pane. As the bot sends trading messages to the room, the add-in catches the messages, reformats them into human readable text, and displays the results in the add-in pane.

The add-in can also be used to act on a price or exchange rate change. In this scenario, the add-in has an input area that the trader uses to create a trading bid that is formatted into a message sent to the room for other users to see and act on. If a trader makes an entry error and tries to send a trade message whose parameters are out of a predefined range, the add-in intercepts the message and cancels it before it is sent to the chat room.

Although the scope of your add-in should be limited to the messaging features previously described, you can add lightweight features that let a user interact with non-Lync applications. To stay with the securities brokerage scenario, a developer can create an add-in that accepts a broker’s trade order and transmits it directly to the trade order processing application. In this case, the trader reacts to current market information that is sent by a middle-tier bot and displayed in the add-in. The trader can generate a trade order in the add-in or post a message to the chat room by calling the [Room.BeginSendMessage](room-beginsendmessage-method-microsoft-lync-model-room_2.md) method in the context of the new market information.

## Persistent Chat room API types

The following table lists the classes and enumerations in the [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md) namespace that make the previously described scenario possible. An add-in uses these classes to catch incoming messages, intercept locally created messages before they are posted to a room, and obtains all previously posted messages.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>API type</p></th>
<th><p>Add-in feature</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lyncclient-gethostingroom-method-microsoft-lync-model.md">GetHostingRoom</a></p></td>
<td><p>Available in the Silverlight version of Microsoft.Lync.Model.dll, this method gets the hosting <a href="room-class-microsoft-lync-model-room_2.md">Room</a> object.</p></td>
</tr>
<tr class="even">
<td><p><a href="room-class-microsoft-lync-model-room_2.md">Room</a></p></td>
<td><p>Represents the chat room that hosts your add-in. Use this class to register for chat room message events, get chat room message history, and see all chat room participants.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommessage-class-microsoft-lync-model-room_2.md">RoomMessage</a></p></td>
<td><p>Represents one message that was sent to a chat room. Properties of the class include the URI of the chat room, URI of the message sender, message ID, and the message text.</p></td>
</tr>
<tr class="even">
<td><p><a href="roommessagedictionary-class-microsoft-lync-model-room_2.md">RoomMessageDictionary</a></p></td>
<td><p>This is the actual message text in multiple formats including plain-text and rich text format (RTF). The <strong>RoomMessageDictionary</strong> class has many of the features of the <strong>IDictionary</strong> interface and encapsulates message text and formatting enumerators. Read the <a href="roommessage-messagedictionary-property-microsoft-lync-model-room_2.md">MessageDictionary</a> property to get the <strong>RoomMessageDictionary</strong> for one message.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommessageeventargs-class-microsoft-lync-model-room_2.md">RoomMessageEventArgs</a></p></td>
<td><p>This class encapsulates a single message composed by the local user. It is the event state of the <a href="room-issendingmessage-event-microsoft-lync-model-room_2.md">IsSendingMessage</a> event that is raised when the local user has typed a message in the message posting area and pressed the <strong>Enter</strong> key. The event is raised before the message is posted to the chat room. This gives your add-in an opportunity to format or filter the message.</p></td>
</tr>
<tr class="even">
<td><p><a href="roommessagefilteringaction-enumeration-microsoft-lync-model-room_2.md">RoomMessageFilteringAction</a></p></td>
<td><p>This enumerates the actions that an add-in can take with an outgoing message whose post to the chat room is pending. An add-in can cancel a posting, replace the message by using a formatted version of the message and then post the message, or post the message unchanged.</p></td>
</tr>
<tr class="odd">
<td><p><a href="roommessageseventargs-class-microsoft-lync-model-room_2.md">RoomMessagesEventArgs</a></p></td>
<td><p>This class encapsulates the messages that were sent to a chat room. The set includes both message sent by the local user and other users joined to the chat room. Your add-in gets an instance of this class from the <a href="room-messagesreceived-event-microsoft-lync-model-room_2.md">MessagesReceived</a> event that is raised when one or more messages are received. When a bot created in the previous scenario sends a message to the chat room, your add-in catches this event.</p></td>
</tr>
</tbody>
</table>


## Additional resources

  - [Core concepts: Persistent Chat](core-concepts-persistent-chat.md)

  - [Chat rooms](chat-rooms.md)

  - [Room manager](room-manager.md)

  - [Chat room messages](chat-room-messages.md)

  - [Create an add-in for the Persistent Chat window](create-an-add-in-for-the-persistent-chat-window.md)

