---
title: Create an add-in for the Persistent Chat window
TOCTitle: Create an add-in for the Persistent Chat window
ms:assetid: 6a00d2b7-b48f-4679-93cd-a0221b1c20ea
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933071(v=office.15)
ms:contentKeyID: 50877202
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Create an add-in for the Persistent Chat window

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about designing a Lync 2013 Persistent Chat room add-in that displays messages that a Microsoft Unified Communications Managed API (UCMA) bot has posted to the hosting chat room and then filters the pending message posts of the local user.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Add-in overview<br />
Chat room add-in registration<br />
Initial application state<br />
Getting the hosting Persistent Chat room<br />
Handling message events<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Add-in overview

A Persistent Chat room add-in is a Microsoft Silverlight browser application. It's hosted in the add-in pane of the Lync 2013 Persistent Chat room window. An add-in application uses the [LyncClient.GetHostingRoom](https://msdn.microsoft.com/library/jj276700\(v=office.15\)) method to return an entry point to the room. The room entry point lets an add-in obtain room message history, post new messages, intercept local messages to be posted, and obtain the room roster for display.

The example in this topic obtains the hosting [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\)) of the chat window. After getting the room, the add-in registers for room messaging events to catch messages posted to the room by other user in addition to filtering messages to be sent by the local user.

Figure 1 shows a simple chat room add-in that displays reformatted messages from a bot and filters and formats messages to be posted to the host chat room by the locally signed-in user. The add-in is hosted in the add-in pane of Lync 2013.

Figure 1. Simple chat room add-in

  
![A simple chat room add-in](images/JJ933129.UC_OCS15ConLyncClient_HowToCreateAChatRoomAddonfigure1(Office.15).png "A simple chat room add-in")

## Chat room add-in registration

Your add-in must be registered on a Persistent Chat server and associated with a Persistent Chat room. The add-in is opened in the Persistent Chat room window when a user double-clicks a Persistent Chat room from the contact list. You can also register a Persistent Chat room by using a server-side tool such as the [Group Chat Administration Tool](http://www.microsoft.com/downloads/details.aspx?familyid=a50cf7a4-6e8c-48a3-8c54-2449106f1627%26amp%3bdisplaylang=e%26displaylang=en). For information about registering and associating an add-in with a chat room using Microsoft Lync Server 2010 Group Chat SDK, see [ChatRoomManagementServices.BeginRegisterAddIn Method](http://msdn.microsoft.com/library/hh379125.aspx).

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>You should associate your new add-in with a private chat room so that you can test the add-in. When your add-in is ready for public use, associate it with a public chat room.</p>
<p>A private chat room is only visible to its members. This means that the private chat room cannot be found by using a chat room query.</p></td>
</tr>
</tbody>
</table>

## Initial application state

Before you complete the steps in this topic, your application must have an instance of [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\)) where the user has permission to read messages.

### Code example

The following example references the namespaces that are used in the following Windows Forms examples.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Room;
using System.Collections;
```

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
<td><p>Your add-in project must reference the Microsoft.Lync.Model.dll and Microsoft.Lync.Model.Utilities.dll from the <em>%programfiles%</em>\Microsoft Office \Office15\LyncSDK\Assemblies\Silverlight folder.</p></td>
</tr>
</tbody>
</table>

The following example declares the class fields that are referenced in the following sections of this topic.

```csharp
        /// <summary>
        /// The hosting Persistent Chat room
        /// </summary>
        private readonly Room _room;
```

## Getting the hosting Persistent Chat room

The hosting chat room is the entry point to all Lync functionality that you can code in an add-in. To get the room, call the [LyncClient.GetHostingRoom](https://msdn.microsoft.com/library/jj276700\(v=office.15\)) method. The best place to get the hosting chat room is in the add-in constructor.

### Code example

The following example gets the hosting room, enables outgoing message filtering, and registers for messaging events.

```csharp
        /// <summary>
        /// Constructor of the add-in page
        /// </summary>
        public MainPage()
        {
            InitializeComponent();
 
            try
            {
                //Get the hosting chat room
                _room = (Room)LyncClient.GetHostingRoom();
                if (_room != null)
                {

                    //Tell Lync platform that outgoing messages are to filtered and formatted 
                    //If outgoing message filtering is not enabled then enable it
                    if (_room.IsOutgoingMessageFilterEnabled == false)
                    {
                        _room.EnableOutgoingMessageFilter();
                    }

                    //Register for message events 
                    _room.IsSendingMessage += new EventHandler<RoomMessageEventArgs>(_room_IsSendingMessage);
                    _room.MessagesReceived += new EventHandler<RoomMessagesEventArgs>(_room_MessagesReceived);
 
                }
            }
            catch (LyncClientException lyncClientException)
            {
                Debug.WriteLine(lyncClientException);
            }
        }
```

## Handling message events

The content of the text boxes on the UI come from the [Microsoft.Lync.Model.Room.RoomMessage](https://msdn.microsoft.com/library/jj276207\(v=office.15\)) objects obtained from the message events that the add-in registered for in the previous example. The bot message text comes from the messages obtained from the [Room.MessagesReceived](https://msdn.microsoft.com/library/jj277819\(v=office.15\)) event while an outgoing message that is pending a filter action is obtained from the [Room.IsSendingMessage](https://msdn.microsoft.com/library/jj294015\(v=office.15\)) event.

The add-in puts the original pending message post text in the **Pending Message Text** text box and the final message text that is posted in the **Updated Message Text** text box. In this sample add-in, the user is not asked to approve any message text changes. The updated message is immediately posted after it passes through the filter and formatting is applied to the text.

A message filtering mechanism in an add-in can take one of three possible actions on each message. These actions are described in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Action</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj275314(v=office.15)">RoomMessageFilteringAction</a><strong>.Passed</strong></p></td>
<td><p>The pending message is posted to the room without modification.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj275314(v=office.15)">RoomMessageFilteringAction</a><strong>.Replaced</strong></p></td>
<td><p>The pending message is posted to the room after a modification to the message text, which can include replacement of text or reformatting of the original text. If you want to spell-check a message before posting, you can use an add-in perform the check.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj275314(v=office.15)">RoomMessageFilteringAction</a><strong>.Canceled</strong></p></td>
<td><p>The message posting is canceled and the message is not posted to the chat room.</p></td>
</tr>
</tbody>
</table>

To cancel a pending message, an add-in parses pending message text for some condition and if met, calls the [Room.SendFilteredMessage](https://msdn.microsoft.com/library/jj265991\(v=office.15\)) method. The **RoomMessage** to be canceled is in the first argument and the [RoomMessageFilteringAction](https://msdn.microsoft.com/library/jj275314\(v=office.15\))**.Canceled** enumerator is passed in the second argument.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>If you call the <a href="https://msdn.microsoft.com/library/jj265991(v=office.15)">Room.SendFilteredMessage</a> method multiple times while passing the same <a href="https://msdn.microsoft.com/library/jj276207(v=office.15)">Microsoft.Lync.Model.Room.RoomMessage</a> object, a <a href="https://msdn.microsoft.com/library/jj294075(v=office.15)">Microsoft.Lync.Model.LyncClientException</a> is raised on the second and following calls.</p></td>
</tr>
</tbody>
</table>

### Code example: Bot message parsing

The following example handles the [Room.MessagesReceived](https://msdn.microsoft.com/library/jj277819\(v=office.15\)) event. Each message in the collection of new messages contains the message sender’s URI. If the URI string contains the unique part of a UCMA bot’s URI, the example treats the message as a bot message. In this example, a bot message might contain information about US currency. If the text of the message contains the United States currency symbol, the message must be parsed and displayed in the add-in UI.

```csharp
        /// <summary>
        /// Handles event that is raised when other users send messages to the room. The method
        /// identifies any UCMA bot messages and then displays bot messages that contain
        /// a currency symbol for the US dollar.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _room_MessagesReceived(object sender, RoomMessagesEventArgs e)
        {
            //Iterate on all new messages posted to the hosting chat room
            foreach (RoomMessage roomMessage in e.Messages)
            {
                //If the sender of this message is a bot then get the message sent by the bot
                if (roomMessage.SenderUri.Contains("UCMABot"))
                {
                    //If this is a message about the US dollar then get the message plain text
                    if (roomMessage.MessageDictionary[RoomMessageFormat.PlainText].ToString().Contains("USD"))
                    {
                        //Parse the text of the message and display the resulting text in the add-in text box
                        string parsedMessage = ParseBOTmessage(roomMessage.MessageDictionary[RoomMessageFormat.PlainText].ToString());
 
                         //Invoke delegate on UI thread to update the BOT text box
                        Deployment.Current.Dispatcher.BeginInvoke(delegate { UpdateBotMessageBox(parsedMessage); });
                    }
                }
            }
        }
```

The following example is a simple text parser that replaces a substring with a space character.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Note" alt="Note" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The bot message can be any string object such as an XML or JSON string.</p></td>
</tr>
</tbody>
</table>

            /// <summary>
            /// Parses a bot message and replaces square brackets with space characters. 
            /// The updated message is returned and displayed in the add-in UI
            /// </summary>
            /// <param name="messageToParse"></param>
            /// <returns></returns>
            private string ParseBOTmessage(string messageToParse)
            {
                messageToParse.Replace("[", " ");
                messageToParse.Replace("]", " ");
                return messageToParse;
            }

The following example updates the bot message text box on the UI thread.

```csharp
        /// <summary>
        /// Updates the BOT message text box
        /// </summary>
        /// <param name="NewMessage"></param>
        private void UpdateBotMessageBox(string NewMessage)
        {
            BotMessage_Textbox.Text += System.Environment.NewLine;
            BotMessage_Textbox.Text += NewMessage;
        }
```

### Code example: Message filtering

The following example handles the [Room.IsSendingMessage](https://msdn.microsoft.com/library/jj294015\(v=office.15\)) event. The event logic filters the message for an objectionable phrase. If the phrase is not found, the message is reformatted by replacing all uppercase letters with lowercase. Finally, the [Room.SendFilteredMessage](https://msdn.microsoft.com/library/jj265991\(v=office.15\)) method is called with the action determined by the filter logic.

```csharp
        /// <summary>
        /// Handles the event raised when the local user starts sending a message. the 
        /// method filters the message and if the message passes the filter, the message
        /// is reformatted and posted to the room.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _room_IsSendingMessage(object sender, RoomMessageEventArgs e)
        {
            RoomMessage roomMessage = e.Message;
            RoomMessageFilteringAction messageAction;
            string updatedMessage = string.Empty;
            //Filter message for an objectionable phrase.
            if (FilterMessage(e.Message.MessageDictionary[RoomMessageFormat.PlainText].ToString()))
            {
                //The message does not contain an objectionable phrase so it can be formatted and posted.
 
                //If the message formatting logic did not make any formatting changes to the original text then
                //post the message to the room as-is.
                updatedMessage = FormatMessage(e.Message.MessageDictionary[RoomMessageFormat.PlainText].ToString());
                //Invoke delgate on UI thread to update the BOT text box
                Deployment.Current.Dispatcher.BeginInvoke(delegate { UpdatePostMessageBox(updatedMessage); });
 
                if (updatedMessage == e.Message.MessageDictionary[RoomMessageFormat.PlainText].ToString())
                {
                    messageAction = RoomMessageFilteringAction.Passed;
                }
                else
                {
                    //If the message text was changed by the formatting method, replace the original text with 
                    //the re-formatted text
                    messageAction = RoomMessageFilteringAction.Replaced;
                }
            }
            else
            {
                //The message contains an objectionable phrase. Cancel the post to the room.
                messageAction = RoomMessageFilteringAction.Canceled;
            }
 
            //If there is a room to post to and a message to post then post the message with the
            //appropriate action.
            if (_room != null && roomMessage != null)
            {
                //If not cancelling the message then replace the possibly unchanged text.
                if (messageAction != RoomMessageFilteringAction.Canceled)
                {
                    roomMessage.MessageDictionary[RoomMessageFormat.PlainText] = updatedMessage;
                }
                //Complete the posting with the actions of canceled, replaced, or posted.
                _room.SendFilteredMessage(roomMessage, messageAction);
            }
        }
```

The following example redraws the updated message text box in the UI with the updated text to be posted.

            /// <summary>
            /// Replaces text in the updated message text box on the UI
            /// </summary>
            /// <param name="UpdatedMessage"></param>
            private void UpdatePostMessageBox(string UpdatedMessage)
            {
                UpdatedText_Textbox.Text = UpdatedMessage;
            }

The following example converts text of the message to all lowercase.

```csharp
        /// <summary>
        /// Applies formatting to a message string before posting
        /// </summary>
        /// <param name="MessageToFormat"></param>
        /// <returns></returns>
        private string FormatMessage(string MessageToFormat)
        {
            return MessageToFormat.ToLower();
        }
```

The following example checks the pending message string for the substring "bla\!". If the substring is found, the example returns false and the [Room.IsSendingMessage](https://msdn.microsoft.com/library/jj294015\(v=office.15\)) event handler cancels the pending post.

```csharp
        /// <summary>
        /// Message string filter. Looks for an instance of 
        /// </summary>
        /// <param name="MessageToFilter"></param>
        /// <returns></returns>
        private Boolean FilterMessage(string MessageToFilter)
        {
            if (MessageToFilter.Contains("bla!"))
            {
                return false;
            }
            return true;
        }
```

## See also

  - [Beyond the basics: Persistent Chat](beyond-the-basics-persistent-chat.md)

