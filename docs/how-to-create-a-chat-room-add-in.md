---
title: 'How to: Create a chat room add-in'
TOCTitle: 'How to: Create a chat room add-in'
ms:assetid: d30b7a11-afae-4d3b-8f63-9eb79d246559
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn391640(v=office.15)
ms:contentKeyID: 56293550
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Create a chat room add-in

Learn how to create a chat room add-in that displays Microsoft Unified Communications Managed API (UCMA) bot messages and filters a local user’s messages before they are posted to the chat room.

**Last modified:** June 07, 2013

***Applies to:** Lync 2013*

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Code example: Chat room message filter<br />
<br />
Prerequisites<br />
Associate an add-in with a chat room<br />
Creating a Silverlight add-in<br />
Getting the hosting chat room<br />
Next steps<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><br />
<a href="http://code.msdn.microsoft.com/lync-2013-filter-room-c2544b54">Lync 2013: Filter room messages before they are posted</a></p></td>
</tr>
</tbody>
</table>

## Prerequisites

Before you create a chat room add-in, you need to meet the following prerequisites:

  - Microsoft Lync 2013 is installed and running on the development computer.

  - You have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK is installed on the development computer.

  - The Persistent chat role is enabled on the Lync Server 2013 topology that you sign in to.

  - You have the permission to associate an add-in with a chat room.

  - Microsoft Visual Studio or an express version of Microsoft Visual Studio is installed on your development computer.

### Core concepts to know

Understanding the following concepts is essential to creating a chat room add-in.

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
<td><p><a href="chat-room-add-in-application-in-lync-sdk.md">Chat room add-in application in Lync SDK</a></p></td>
<td><p>Learn about the Microsoft Lync 2013 Persistent Chat room add-in feature through the scenarios in which the add-in is used and the classes and methods that are used to create an add-in.</p></td>
</tr>
<tr class="even">
<td><p><a href="chat-rooms.md">Chat rooms</a></p></td>
<td><p>Explains what a followed room is and how you use it in your application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="room-manager.md">Room manager</a></p></td>
<td><p>Explains the role of the room manager in finding Persistent Chat rooms.</p></td>
</tr>
<tr class="even">
<td><p><a href="chat-room-messages.md">Chat room messages</a></p></td>
<td><p>Explains how room messages are encapsulated in the Lync 2013 API.</p></td>
</tr>
<tr class="odd">
<td><p><a href="create-an-add-in-for-the-persistent-chat-window.md">Create an add-in for the Persistent Chat window</a></p></td>
<td><p>Learn about designing a Persistent Chat room add-in that displays messages that a UCMA bot has posted to the hosting chat room and then filters the pending message posts of the local user.</p></td>
</tr>
</tbody>
</table>

## Associate an add-in with a chat room

Before your add-in can be opened in a chat window, you need to register the add-in with the Lync Server 2013. The add-in is opened in the persistent chat room window when a user double-clicks a persistent chat room from the contact list. You can also register a persistent chat room by using a server-side tool such as the [Group Chat Administration Tool](http://www.microsoft.com/downloads/details.aspx?familyid=a50cf7a4-6e8c-48a3-8c54-2449106f1627%26amp%3bdisplaylang=e%26displaylang=en). For information about associating an add-in with a chat room using the Microsoft Lync Server 2013 Persistent Chat SDK, see [ChatRoomManagementServices.BeginUpdateChatRoom](http://msdn.microsoft.com/en-us/library/microsoft.rtc.collaboration.persistentchat.management.chatroommanagementservices.beginupdatechatroom.aspx).

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
<p>A private chat room is only visible to its members. This means that the private chat room cannot be found by using a chat room query to search for a chat room.</p></td>
</tr>
</tbody>
</table>

## Creating a Silverlight add-in

Use Microsoft Visual Studio to create the solution and project files for the add-in. You can open the solution in Microsoft Expression Web if you want to create an enhanced user experience.

### To create a Silverlight add-in

1.  Start Microsoft Visual Studio and click **New Project…** on the start page.

2.  In the New Project dialog, select Templates -\> Visual C\# -\> Silverlight.

3.  Select the **Lync Silverlight Application** template in the middle pane of the New Project dialog. This template populates the references folder with the assembly that contains the namespace you use to get chat room features.

4.  Set the **name**, **location**, and **solution name** for your solution and click the **OK** button.

5.  In the **New Silverlight Application** dialog, un-check **Host the Silverlight application in a new Web site**.

6.  In the **Options** group, select Silverlight 5 from the **Silverlight Version** list and click the **OK** button.

The solution file is now ready to update. The MainPage.xaml file declares a user control that nests a grid, stack panel, and the PresenceIndicator control. This control is in the stack panel to show you how to embed Lync Controls in your Silverlight application.

## Getting the hosting chat room

The hosting chat room is the entry point to all Lync functionality that you can code in an add-in. To get the room, call the [LyncClient.GetHostingRoom](https://msdn.microsoft.com/en-us/library/jj276700\(v=office.15\)) method. The best place to get the hosting chat room is in the add-in constructor.

### To get the hosting chat room

1.  In the constructor for your page, add a try/catch block for the [Microsoft.Lync.Model.LyncClientException](https://msdn.microsoft.com/en-us/library/jj294075\(v=office.15\)) class.

2.  Get the [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/en-us/library/jj266467\(v=office.15\)) object that encapsulates the hosting chat room by calling the static **\[M:Microsoft.Lync,Model.LyncClient.GetHostingRoom\]** method.

3.  Enable message filtering by calling the [Room.EnableOutgoingMessageFilter](https://msdn.microsoft.com/en-us/library/jj275520\(v=office.15\)) method.

4.  Register for the [Room.IsSendingMessage](https://msdn.microsoft.com/en-us/library/jj294015\(v=office.15\)) event so you can catch and filter messages before they are posted by the local user.

5.  Register for the [Room.MessagesReceived](https://msdn.microsoft.com/en-us/library/jj277819\(v=office.15\)) event so you can catch new messages after they are posted to the hosting chat room.

The following example gets the hosting room, enables outgoing message filtering, and registers for messaging events.

``` csharp
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
            catch (SystemException systemException)
            {
                if (IsLyncException(systemException))
                {
                    // Log the exception thrown by the Lync Model API.
                    Console.WriteLine("Error: " + systemException);
                }
                else
                {
                    // Rethrow the SystemException which did not come from the Lync Model API.
                    throw;
                }
            }
 
        }
```

## Code example: Chat room message filter

The following example uses XAML to declare the add-in UI. The controls include an entry field that the user types a filter string into, and text blocks that show the original message post and the post after the add-in has reformatted it.

``` xaml
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
        <sdk:Label Name="PendingPost_Label" Height="18 " Width="121" Content="Pending Post" Margin="12,12,0,0" VerticalAlignment="Top" HorizontalAlignment="Left" Grid.RowSpan="1" Grid.Column="0" Grid.Row="1" /> 
        <sdk:Label Name="UpdatedPost_Label"  Grid.Column="0"  Grid.Row="2"  Height="28"  HorizontalAlignment="Left"  VerticalAlignment="Top" Width="120" Content="Updated Post"  Margin="12,20,10,114"/>
        <sdk:Label Name="FilterAction" Grid.Column="0"   Grid.ColumnSpan="1"  Grid.Row="2"  Height="28" HorizontalAlignment="Left" Margin="0,74,0,0"  VerticalAlignment="Top" Width="147" />
        <sdk:Label Name="FilterText_label" Content="Filter Text" Height="21" HorizontalAlignment="Left" Margin="12,12,0,0"  VerticalAlignment="Top" Width="140"  />
        <TextBox Grid.Column="1" Grid.Row="0" Grid.RowSpan="1" Height="23" HorizontalAlignment="Left" Margin="1,1,0,0" Name="FilterTextString" VerticalAlignment="Top" Width="120" />
    </Grid>
</UserControl>
```

The following example interacts with the XAML user control of a Silverlight chat room add-in. When the user posts a message to the hosting chat room, this add-in catches the message before it is posted. If the message contains the filter string that is entered in the filter text box, the message post is canceled. Otherwise, the message is posted to the room

``` csharp
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

            try
            {
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
            catch (ClientNotFoundException cnf)
            {
                System.Diagnostics.Debug.WriteLine("The Lync client is not running:" + cnf.Message);
            }
            catch (LyncClientException lce)
            {
                System.Diagnostics.Debug.WriteLine("Lync client exception on open add-in:" + lce.Message);
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

## Next steps

Now that you have created a chat room add-in, learn about how to make your add-in interact with the hosting chat room.

  - [How to: Read messages sent to a chat room](how-to-read-messages-sent-to-a-chat-room.md)

  - [How to: Filter an outgoing message from a local user to a chat room](how-to-filter-an-outgoing-message-from-a-local-user-to-a-chat-room.md)

## Additional resources

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

  - [How to: Send a meeting access key to a Persistent Chat room](how-to-send-a-meeting-access-key-to-a-persistent-chat-room.md)

