---
title: 'How to: Filter an outgoing message from a local user to a chat room'
TOCTitle: 'How to: Filter an outgoing message'
ms:assetid: 4d753a01-94e0-4973-8a2c-641880f5550b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937334(v=office.15)
ms:contentKeyID: 50877167
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Filter an outgoing message from a local user to a chat room

Learn how to use Microsoft Lync 2013 SDK to create a client-side ethical/security filter for messages that a Microsoft Lync 2013 is posting to a Lync 2013 Persistent Chat room.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p>
<p><strong>In this article</strong><br />
Filter overview<br />
Prerequisites<br />
Initial application state<br />
Register for room events<br />
Handle the IsSendingMessage event<br />
Code examples: Ethical message filter<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-filter-room-c2544b54">Filter room messages before they are posted</a><br />
</p></td>
</tr>
</tbody>
</table>

## Filter overview

Some organizations require that a message to be posted to a room comply with content and formatting constraints. For example, a securities brokerage might want to make sure that any trade instructions communicated in a chat room message do not contain numeric errors that might cause a disadvantageous trade. To make this message filtering possible, the Lync platform exposes an event that is raised when a message posting operation has started but is pending review by a logical message filter. The filter catches the event, runs filter logic on the message, updates the message as necessary, and then posts the message or cancels it.

## Prerequisites

The prerequisites for filtering outgoing chat room messages are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

Understanding the following concepts is essential to adding Persistent Chat to an application.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Topic</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="chat-rooms.md">Chat rooms</a></p></td>
<td><p>Explains what a followed room is and how you use it in your application.</p></td>
</tr>
<tr class="even">
<td><p><a href="room-manager.md">Room manager</a></p></td>
<td><p>Explains the role of the room manager in finding Persistent Chat rooms.</p></td>
</tr>
<tr class="odd">
<td><p><a href="chat-room-messages.md">Chat room messages</a></p></td>
<td><p>Explains how room messages are encapsulated in the Lync 2013 API.</p></td>
</tr>
<tr class="even">
<td><p><a href="create-an-add-in-for-the-persistent-chat-window.md">Create an add-in for the Persistent Chat window</a></p></td>
<td><p>Learn about designing a Persistent Chat room add-in that displays messages that a UCMA bot has posted to the hosting chat room and then filters the pending message posts of the local user.</p></td>
</tr>
</tbody>
</table>

## Initial application state

Before you start the procedures in this topic, your application must declare and initialize a [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance and the client must be signed in. For more information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

You must also have an instance of [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\)) where the user has permission to read and post messages. For information about getting a room, see [How to: Find a chat room](how-to-find-a-chat-room.md). Your application must declare a button and a text box for rich-text format (RTF) content. The RTF text box accepts the message string to post and the button starts to post the message.

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

The following example declares the class fields that are referenced later in this topic.

```csharp
        /// <summary>
        /// The LyncClient class instance that encapsulates the Lync client platform
        /// </summary>
        private LyncClient _client=null;

        /// <summary>
        /// The Room instance that a user joins from the list of rooms that are queried, searched for, or gotten from the followed rooms list
        /// </summary>
        private Room _room = null;

        /// <summary>
        /// The Uri of the local user who can post a message to a chat room
        /// </summary>
        private string _senderUri = "";
```

## Register for room events

When you have obtained a [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\)) instance selected by a user, register for a set of room events so that you can receive a notification of a local user’s pending message post or messages posted to the room by other users.

### To register for room events

1.  Unregister for events on the previously selected room that is referenced by the \_room class field.

2.  Set the \_room class field to the newly selected room.

3.  Register for chat room events.

4.  Turn on room message filtering for the selected room.

5.  Read room properties and update the UI with the room title, description, and unread message count.

The following example registers for room events and reads room properties.

```csharp
        /// <summary>
        /// Registers for message, state, and participant related events on a room.
        /// </summary>
        private void FillRoomProperties(Room room)
        {
            if (_room != null)
            {
                //Un-Register for event raised when a new message is posted to the room or the user has read a message.
                _room.UnreadMessageCountChanged -= room_UnreadMessageCountChanged;

                //Un-Register for the event raised when users have posted messages to the room.
                _room.MessagesReceived -= room_MessagesReceived;

                //Register for the event raised when the local user is posting a message and before the message is posted.
                _room.IsSendingMessage -= room_IsSendingMessage;
            }

            _room = room;

            //Clear the messages from a previous room choice out of the message list box
            listBoxMessages.Items.Clear();

            //Register for event raised when a new message is posted to the room or the user has read a message.
            _room.UnreadMessageCountChanged += new EventHandler<UnreadMessageCountChangedEventArgs>(room_UnreadMessageCountChanged);

            //Register for the event raised when users have posted messages to the room.
            _room.MessagesReceived += new EventHandler<RoomMessagesEventArgs>(room_MessagesReceived);

            //Enable the outgoing message filter.
            _room.EnableOutgoingMessageFilter();

            //Register for the event raised when the local user is posting a message and before the message is posted.
            _room.IsSendingMessage += new EventHandler<RoomMessageEventArgs>(room_IsSendingMessage);

            if (_room.Properties != null)
            {
                if (_room.Properties[RoomProperty.Description] != null)
                {
                    RoomDescription_label.Text = _room.Properties[RoomProperty.Description].ToString();
                }
            }
            txtUnreadMessageCountChanged.Text = _room.UnreadRoomMessageCount.ToString();
        }
```

## Handle the IsSendingMessage event

The outgoing message filtering logic is triggered in the [Room.IsSendingMessage](https://msdn.microsoft.com/library/jj294015\(v=office.15\)) event. Your filter logic can take one of three actions:

  - Post the pending message that has no changes to the message text.

  - Replace some or all of the text in the message string before posting the message. This replacement can range from applying the results of a spelling checker algorithm, applying company messaging policy, applying standard message formatting, or translating the string from one language to another by calling methods on the Bing Translation service.
    
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
    <td><p>The text changes should be made for the message text in both plain text and RTF formats. If the same text replacement is not made to both formats, the resulting message shows inconsistent text across the two formats.</p></td>
    </tr>
    </tbody>
    </table>

  - Cancel the message posting operation. In this case, no message is posted to the chat room.
    
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
    <td><p>The Lync 2013 API platform has a timeout mechanism that posts a pending room message after 4 seconds if the <a href="https://msdn.microsoft.com/library/jj265991(v=office.15)">Room.SendFilteredMessage</a> is not called by your application. This means that if no filtering action is taken by your application within 4 seconds, the message is posted to the room.</p></td>
    </tr>
    </tbody>
    </table>

### To filter a message

1.  Get the [Microsoft.Lync.Model.Room.RoomMessage](https://msdn.microsoft.com/library/jj276207\(v=office.15\)) instance that encapsulates the pending message post.

2.  Get the plain-text message string and the RTF message string from the [RoomMessage.MessageDictionary](https://msdn.microsoft.com/library/jj275293\(v=office.15\)) property.

3.  Apply custom filtering logic to each string.

4.  Replace the original strings in the [RoomMessage.MessageDictionary](https://msdn.microsoft.com/library/jj275293\(v=office.15\)) with the updated message strings.

5.  Call the [Room.SendFilteredMessage](https://msdn.microsoft.com/library/jj265991\(v=office.15\)) method with the enumeration of [Microsoft.Lync.Model.Room.RoomMessageFilteringAction](https://msdn.microsoft.com/library/jj275314\(v=office.15\)) that applies your selected action.

### Code examples

The following example filters a pending message in the [Room.IsSendingMessage](https://msdn.microsoft.com/library/jj294015\(v=office.15\)) event.

```csharp
        private void room_IsSendingMessage(object sender, RoomMessageEventArgs e)
        {

            try
            {
                _filteredMessage = e.Message;

                string filteredMessageContentsPlain = _filteredMessage.MessageDictionary[RoomMessageFormat.PlainText].ToString();
                string filteredMessageContentsRtf = _filteredMessage.MessageDictionary[RoomMessageFormat.Rtf].ToString();

                 
                //Parse pending message text for valid stock trade numerical values.
                string message = CustomStockTradeFilterLogic(filteredMessageContentsPlain);

                //Parse pending message text for valid stock trade numerical values.
                string RtfMessage = CustomStockTradeFilterLogic(filteredMessageContentsRtf);

                //If both the plain text and Rtf versions of the message pass the custom stock trade filter unchanged then
                //post the original message
                if (message.ToLower() == filteredMessageContentsPlain.ToLower() && RtfMessage.ToLower() == filteredMessageContentsRtf.ToLower())
                {
                    _room.SendFilteredMessage(_filteredMessage, RoomMessageFilteringAction.Passed);
                }
                else
                {
                    //If either the plain text or Rtf message strings fail the stock trade filter then
                    //cancel the message post. Neither message string is posted.
                    if (message == "Trade Canceled" || RtfMessage == "Trade Canceled")
                    {

                        //This filtering action cancels an entire message and all message strings that are contained
                        //within the message dictionary.
                        _room.SendFilteredMessage(_filteredMessage, RoomMessageFilteringAction.Canceled);
                    }

                    else
                    {
                        //Update the message dictionary with the plain text and Rtf string updates.

                        //It is not required that you replace both strings. You may replace one or the other
                        _filteredMessage.MessageDictionary[RoomMessageFormat.PlainText] = message;
                        _filteredMessage.MessageDictionary[RoomMessageFormat.Rtf] = RtfMessage;
                        _room.SendFilteredMessage(_filteredMessage, RoomMessageFilteringAction.Replaced);
                    }
                }

            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }

        }
```

The following example takes the pending message text as a parameter, parses the message for custom content rules, makes corrections in the string, warns a user if corrections are made, and passes the updated string back to the [Room.IsSendingMessage](https://msdn.microsoft.com/library/jj294015\(v=office.15\)) event handler.

```csharp
        /// <summary>
        /// Replaces trade quantities and/or securities prices when either value is outside of
        /// acceptable trading parameters
        /// </summary>
        /// <param name="OriginalMessage">string. Original message to be posted.</param>
        /// <returns>string. Updated message string</returns>
        private string CustomStockTradeFilterLogic(string OriginalMessage)
        {
            string updatedMessage = OriginalMessage;

            //Custom message parsing and text replacement would run here
            //---------------- text replacement algorithm ----------------------

            if (updatedMessage != OriginalMessage)
            {
                Console.WriteLine("Your trade: " + OriginalMessage + " has been modified. The new trade is: " + updatedMessage);
            }
            return updatedMessage;
        }
```

## Code examples: Ethical message filter

    <UserControl x:Class="FilterMessageAddIn.FilterMessageAddIn"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d"
        d:DesignHeight="300" d:DesignWidth="400" xmlns:sdk="http://schemas.microsoft.com/winfx/2006/xaml/presentation/sdk">
    
        <Grid x:Name="LayoutRoot" Background="White" ShowGridLines="True">
            <Grid.RowDefinitions>
                <RowDefinition Height="28*" />
                <RowDefinition Height="119*" />
                <RowDefinition Height="153*" />
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="143*" />
                <ColumnDefinition Width="257*" />
            </Grid.ColumnDefinitions>
            <TextBlock Name="PendingPost" Text="TextBlock" Grid.Column="1" Grid.Row="1" Height="131"  VerticalAlignment="Top" HorizontalAlignment="Left" Width="245" Grid.RowSpan="1" />
            <TextBlock Name="UpdatedPost" Text="TextBlock" Height="122" Grid.Row="2" Grid.Column="1"   Margin="0,20,0,0" VerticalAlignment="Top" HorizontalAlignment="Left" Width="245" />
            <sdk:Label Name="PendingPost_Label" Height="18" Width="121" Content="Pending Post" Margin="12,12,0,0" VerticalAlignment="Top" HorizontalAlignment="Left" Grid.RowSpan="1" Grid.Column="0" Grid.Row="1" /> 
            <sdk:Label Name="UpdatedPost_Label"  Grid.Column="0"  Grid.Row="2"  Height="28"  HorizontalAlignment="Left"  VerticalAlignment="Top" Width="120" Content="Updated Post"  Margin="12,20,10,114"/>
            <sdk:Label Name="FilterAction" Grid.Column="0"   Grid.ColumnSpan="1"  Grid.Row="2"  Height="28" HorizontalAlignment="Left" Margin="0,74,0,0"  VerticalAlignment="Top" Width="147" />
            <sdk:Label Name="FilterText_label" Content="Filter Text" Height="21" HorizontalAlignment="Left" Margin="12,12,0,0"  VerticalAlignment="Top" Width="140"  />
            <TextBox Grid.Column="1" Grid.Row="0" Grid.RowSpan="1" Height="23" HorizontalAlignment="Left" Margin="1,1,0,0" Name="FilterTextString" VerticalAlignment="Top" Width="120" />
        </Grid>
    </UserControl>

The following example is the interaction logic for the window declared in the previous example.

```csharp
using System;
using System.Windows.Controls;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Room;

namespace FilterMessageAddIn
{
    public partial class FilterMessageAddIn : UserControl
    {
        /// <summary>
        /// The hosting group chat room
        /// </summary>
        Room _HostingRoom;

        /// <summary>
        /// Class constructor
        /// </summary>
        public FilterMessageAddIn()
        {
            InitializeComponent();

            //Get the group chat room that is hosting this add-in
            _HostingRoom = LyncClient.GetHostingRoom();
            if (_HostingRoom != null)
            {
                //If the hosting room outgoing message filter is not enabled then enable it.
                if (_HostingRoom.IsOutgoingMessageFilterEnabled == false)
                {
                    _HostingRoom.EnableOutgoingMessageFilter();
                }

                //Register for outgoing message post events.
                _HostingRoom.IsSendingMessage += new EventHandler<RoomMessageEventArgs>(_HostingRoom_IsSendingMessage);
            }
        }

        /// <summary>
        /// Invoked when a local user is posting a message to the hosting chat room
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _HostingRoom_IsSendingMessage(object sender, RoomMessageEventArgs e)
        {

            /// <summary>
            /// The message filtering action taken by the application after filter/format logic is run
            /// </summary>
            RoomMessageFilteringAction messageAction;

            //Get the pending message
            RoomMessage messageToFilter = e.Message;

            //Extract the plain-text version of the message.
            string pendingPostText = e.Message.MessageDictionary[RoomMessageFormat.PlainText].ToString();
             
            //Update UI with the text of the pending message.
            this.Dispatcher.BeginInvoke(new ShowPendingMessageDelegate(ShowPendingMessage), new object[] { pendingPostText });

            //Check message string to see if the message contains the sub-string entered on the add-in UI
            if (FilterMessagePost(pendingPostText, FilterTextString.Text))
            {
                //The message string contains the sub-string so the message action is canceled. 
                //Update the UI with the message filtering action and do not update the UpdatedMessage text block.
                this.Dispatcher.BeginInvoke(new ShowFilterMessageActionDelegate(ShowFilterMessageAction), new object[] { RoomMessageFilteringAction.Canceled });
                messageAction = RoomMessageFilteringAction.Canceled;
            }
            else
            {

                //The message string DOES NOT contain the filter sub-string.

                //If the pending message starts with "do not reformat" in any letter case then 
                //update the UI with the message filter action, update the UI updated message box with the original message text,
                //and set the message filtering action to Passed
                if (pendingPostText.ToUpper().StartsWith("DO NOT REFORMAT:"))
                {
                    this.Dispatcher.BeginInvoke(new ShowUpdatedMessageDelegate(ShowUpdatedMessage), new object[] { pendingPostText });
                    this.Dispatcher.BeginInvoke(new ShowFilterMessageActionDelegate(ShowFilterMessageAction), new object[] { RoomMessageFilteringAction.Passed });
                    messageAction = RoomMessageFilteringAction.Passed;

                }
                else
                {
                    //Reformat the original message text by setting all characters to upper case.
                    //Update the UI with the message filter action, update the UI updated message box with the reformatted message text
                    //and set the message filtering action to Replaced
                    this.Dispatcher.BeginInvoke(new ShowUpdatedMessageDelegate(ShowUpdatedMessage), new object[] { FormatMessagePost(pendingPostText) });
                    this.Dispatcher.BeginInvoke(new ShowFilterMessageActionDelegate(ShowFilterMessageAction), new object[] { RoomMessageFilteringAction.Replaced });
                    messageAction = RoomMessageFilteringAction.Replaced;
                }
            }

            //Update the pending message with the updated message text UI text block
            messageToFilter.MessageDictionary[RoomMessageFormat.PlainText] = UpdatedPost.Text;

            //Send the filtered message with whatever message filtering action was set in the previous code.
            _HostingRoom.SendFilteredMessage(messageToFilter, messageAction);
        }

        /// <summary>
        /// Message filter method searches the pending message text for the sub-string entered
        /// on the main UI. If the substring is found, true is returned.  Otherwse, false is returned.
        /// true = message is filtered and must be canceled.
        /// false = message passes filter and can be posted.
        /// </summary>
        /// <param name="pendingMessagString"></param>
        /// <returns></returns>
        private Boolean FilterMessagePost(string pendingMessagString, string messageFilter)
        {
            if (pendingMessagString.Contains(messageFilter))
            {
                //Cancel message.
                return true;
            }
            //Post message.
            return false;
        }
        
        /// <summary>
        /// Message text formatter. sets all message text to upper case.
        /// This simplistic example works well for plain-text messages. If your application will 
        /// format rtf or Html messages, be sure to apply equivalent formatting logic to all formats of a message's text before 
        /// posting.
        /// </summary>
        /// <param name="pendingMessageString"></param>
        /// <returns></returns>
        private string FormatMessagePost(string pendingMessageString)
        {
            return pendingMessageString.ToUpper();
        }

        private delegate void ShowPendingMessageDelegate(string pendingMessage);

        /// <summary>
        /// Updates the main UI pending message block
        /// </summary>
        /// <param name="pendingMessage"></param>
        private void ShowPendingMessage(string pendingMessage)
        {
            PendingPost.Text = pendingMessage;
        }

        private delegate void ShowUpdatedMessageDelegate(string updatedMessage);
        /// <summary>
        /// Updates the main UI updated message text block with the reformatted message text.
        /// </summary>
        /// <param name="updatedMessage"></param>
        private void ShowUpdatedMessage(string updatedMessage)
        {
            UpdatedPost.Text = updatedMessage;
        }

        private delegate void ShowFilterMessageActionDelegate(RoomMessageFilteringAction action);
        /// <summary>
        /// Updates the main UI filter action label content with the action to be applied to the
        /// pending message post.
        /// </summary>
        /// <param name="action"></param>
        private void ShowFilterMessageAction(RoomMessageFilteringAction action)
        {
            FilterAction.Content = action.ToString();
        }
      
    }
}
```

## See also

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

