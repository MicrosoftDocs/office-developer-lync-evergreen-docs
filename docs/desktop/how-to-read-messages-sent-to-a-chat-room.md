---
title: 'How to: Read messages sent to a chat room'
TOCTitle: 'How to: Read messages sent to a chat room'
ms:assetid: bd1b54d9-aef0-4e03-a0fd-2bdf86af242d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933154(v=office.15)
ms:contentKeyID: 50877293
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Read messages sent to a chat room

Learn how Microsoft Lync 2013 SDK lets you code an application window to display chat room messages as they are posted to a Microsoft Lync 2013 chat room.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Message overview<br />
Prerequisites<br />
Initial application state<br />
Register for room events<br />
Handle the MessagesReceived event<br />
Code examples: GetMessages<br />
Next steps<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-join-a-affa75e9">Join a Persistent Chat room and get messages posted to the room</a><br />
</p></td>
</tr>
</tbody>
</table>

## Message overview

The topic continues the scenario introduced in [Create a custom Persistent Chat client](create-a-custom-persistent-chat-client.md). The code in following samples updates the chat room window messages list with the contents of new messages posted to the chat room.

## Prerequisites

The prerequisites for reading message posted to a chat room are as follows:

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
<td><p>Explains what a followed room is and how you use it in an application.</p></td>
</tr>
<tr class="even">
<td><p><a href="room-manager.md">Room manager</a></p></td>
<td><p>Explains the role of the room manager in finding Persistent Chat rooms.</p></td>
</tr>
<tr class="odd">
<td><p><a href="chat-room-messages.md">Chat room messages</a></p></td>
<td><p>Explains how room messages are encapsulated in the Lync 2013 API.</p></td>
</tr>
</tbody>
</table>

## Initial application state

Before you start the following procedure, your application must declare and initialize a [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance and the client must be signed in. For more information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

You must also have an instance of [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/en-us/library/jj266467\(v=office.15\)) where the user has permission to read messages. For information about getting a room, see [How to: Find a chat room](how-to-find-a-chat-room.md). Your application must declare a list, which displays messages posted to the room.

### Code examples

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

When you have obtained a [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/en-us/library/jj266467\(v=office.15\)) instance selected by a user, register for a set of room events so that you can receive notification of messages posted to the room by other users or a message that is posted to the room by the local user.

### To register for room events

1.  Unregister for events on the previously selected room that is referenced by the \_room class field.

2.  Set the \_room class field to the newly selected room.

3.  Register for chat room events.

4.  Read room properties and update the UI with the room title, description, and unread message count.

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

            }

            _room = room;

            //Clear the messages from a previous room choice out of the message list box
            listBoxMessages.Items.Clear();

            //Register for event raised when a new message is posted to the room or the user has read a message.
            _room.UnreadMessageCountChanged += new EventHandler<UnreadMessageCountChangedEventArgs>(room_UnreadMessageCountChanged);

            //Register for the event raised when users have posted messages to the room.
            _room.MessagesReceived += new EventHandler<RoomMessagesEventArgs>(room_MessagesReceived);

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

## Handle the MessagesReceived event

The [Room.MessagesReceived](https://msdn.microsoft.com/en-us/library/jj277819\(v=office.15\)) event is raised when any room participant succeeds in posting to a room. The event data, [Microsoft.Lync.Model.Room.RoomMessagesEventArgs](https://msdn.microsoft.com/en-us/library/jj294006\(v=office.15\)), contains the message that is posted. Normally the event data message collection contains one message but this might not always be the case. For this reason, you should iterate on the full collection and process each message.

### To handle the MessagesReceived event

1.  Read the [RoomMessagesEventArgs.Messages](https://msdn.microsoft.com/en-us/library/jj267984\(v=office.15\)) property to get the collection of messages sent to a room.

2.  For each [Microsoft.Lync.Model.Room.RoomMessage](https://msdn.microsoft.com/en-us/library/jj276207\(v=office.15\)) object in the messages collection, read the [RoomMessage.SenderUri](https://msdn.microsoft.com/en-us/library/jj275022\(v=office.15\)) property to get the sender’s URI.
    
    1.  Get a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) instance that represents the user that is sending the message by calling the [ContactManager.GetContactByUri](https://msdn.microsoft.com/en-us/library/jj274481\(v=office.15\)) method and passing the sender’s URI in the first argument.
    
    2.  Get the display name of the user that is sending the message by calling the [Contact.GetContactInformation](https://msdn.microsoft.com/en-us/library/jj294012\(v=office.15\)) method, specifying the [ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\))**.DisplayName** property.
    
    3.  Read the [RoomMessage.MessageDictionary](https://msdn.microsoft.com/en-us/library/jj275293\(v=office.15\)) property to get the dictionary that contains the message in each format.
    
    4.  Get the plain text of the message by calling the [RoomMessageDictionary.TryGetValue](https://msdn.microsoft.com/en-us/library/jj277163\(v=office.15\)) method. The message text is returned in an out parameter string. Pass the [RoomMessageFormat](https://msdn.microsoft.com/en-us/library/jj277588\(v=office.15\))**.PlainTex**t enumerator into the method.
    
    5.  Get the message sent time and date by reading the [RoomMessage.SentTime](https://msdn.microsoft.com/en-us/library/jj277976\(v=office.15\)) property. A **DateTime** object is returned.

### Code examples

The following two examples demonstrate the tasks listed in the previous procedure. The first example is an event callback method that is invoked by the platform when a collection of new messages is posted to a room. The second example is a helper method that is invoked on the UI thread and updates the room message list control.

```csharp
/// <summary>
        /// This event is raised when any room member has posted a message to the room. This includes
        /// the local user.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void room_MessagesReceived(object sender, RoomMessagesEventArgs e)
        {
           
            //Get the collection of newly posted messages.
           IList<RoomMessage> receivedMessages = e.Messages;

            //Invoke a delegate on the UI thread that updates the message list with the contents of the new message.
           listBoxMessages.Invoke(new LoadPostedMessagesDelegate(LoadPostedMessages), new object[] { receivedMessages });

        }
```

The following example updates the message list for the chat room window. It gets the message send date and time, the message type, the message sender display name, and the plain text of the message.

```csharp
        /// <summary>
        /// Loads a list box with a collection of messages
        /// </summary>
        /// <param name="messages"></param>
        private void LoadPostedMessages(IList<RoomMessage> messages)
        {
                //Add a header row to the list box
                listBoxMessages.Items.Add("Messages retrieved: " + messages.Count.ToString());
                listBoxMessages.Items.Add("Sent Time\t\tType\tSender");

                //Declare Contact object to be initialized with the object returned from GetContactByUri
                Contact senderContact;

                foreach (RoomMessage message in messages)
                {
                    object messageObject = null;

                    //Get the sender as a Contact instance
                    senderContact = _client.ContactManager.GetContactByUri(message.SenderUri);

                    //Get the display name of the message sender
                    string senderName = senderContact.GetContactInformation(ContactInformationType.DisplayName).ToString();

                    //Get the plain text version of a message
                    message.MessageDictionary.TryGetValue(RoomMessageFormat.PlainText, out messageObject);
                    string messageContent = (string)messageObject;

                    //create an item in the list box composed of message sent time - TAB character - message type - sender display name
                    listBoxMessages.Items.Add(message.SentTime.ToString() + "\t" + message.MessageDictionary.Type + "\t" + senderName);

                    //Create an item in the list box composed of the TAB character and message string
                    listBoxMessages.Items.Add("\t" + messageContent);

                    //Create item composed of TAB TAB and line separator
                    listBoxMessages.Items.Add("\t\t------------------");

                    messageObject = null;
                   
                }
        }
```

## Code examples: GetMessages

The following example declares a Windows Form that displays the most recent 27 messages posted to a selected followed room. Previous messages are retrieved by clicking a command button on the right of the message list.

    namespace GetMessages
    {
        partial class GetMessages
        {
            /// <summary>
            /// Required designer variable.
            /// </summary>
            private System.ComponentModel.IContainer components = null;
    
            /// <summary>
            /// Clean up any resources being used.
            /// </summary>
            /// <param name="disposing">true if managed resources should be disposed; otherwise, false.</param>
            protected override void Dispose(bool disposing)
            {
                if (disposing && (components != null))
                {
                    components.Dispose();
                }
                base.Dispose(disposing);
            }
    
            #region Windows Form Designer generated code
    
            /// <summary>
            /// Required method for Designer support - do not modify
            /// the contents of this method with the code editor.
            /// </summary>
            private void InitializeComponent()
            {
                this.panel1 = new System.Windows.Forms.Panel();
                this.LyncClientState_Label = new System.Windows.Forms.Label();
                this.label1 = new System.Windows.Forms.Label();
                this.txtUnreadMessageCountChanged = new System.Windows.Forms.Label();
                this.label8 = new System.Windows.Forms.Label();
                this.RoomDescription_label = new System.Windows.Forms.Label();
                this.label5 = new System.Windows.Forms.Label();
                this.btnRetrieveAdditionalMessages = new System.Windows.Forms.Button();
                this.listBoxMessages = new System.Windows.Forms.ListBox();
                this.txtLastMessageID = new System.Windows.Forms.TextBox();
                this.NumberOfMessagesToGet_Text = new System.Windows.Forms.TextBox();
                this.label6 = new System.Windows.Forms.Label();
                this.label7 = new System.Windows.Forms.Label();
                this.FollowedRooms_listbox = new System.Windows.Forms.ListBox();
                this.label13 = new System.Windows.Forms.Label();
                this.panel1.SuspendLayout();
                this.SuspendLayout();
                // 
                // panel1
                // 
                this.panel1.Controls.Add(this.LyncClientState_Label);
                this.panel1.Controls.Add(this.label1);
                this.panel1.Location = new System.Drawing.Point(97, 3);
                this.panel1.Name = "panel1";
                this.panel1.Size = new System.Drawing.Size(200, 23);
                this.panel1.TabIndex = 1;
                // 
                // LyncClientState_Label
                // 
                this.LyncClientState_Label.AutoSize = true;
                this.LyncClientState_Label.Location = new System.Drawing.Point(111, 4);
                this.LyncClientState_Label.Name = "LyncClientState_Label";
                this.LyncClientState_Label.Size = new System.Drawing.Size(25, 13);
                this.LyncClientState_Label.TabIndex = 1;
                this.LyncClientState_Label.Text = "Null";
                // 
                // label1
                // 
                this.label1.AutoSize = true;
                this.label1.Location = new System.Drawing.Point(3, 5);
                this.label1.Name = "label1";
                this.label1.Size = new System.Drawing.Size(87, 13);
                this.label1.TabIndex = 0;
                this.label1.Text = "Lync Client State";
                // 
                // txtUnreadMessageCountChanged
                // 
                this.txtUnreadMessageCountChanged.AutoSize = true;
                this.txtUnreadMessageCountChanged.Location = new System.Drawing.Point(305, 86);
                this.txtUnreadMessageCountChanged.Name = "txtUnreadMessageCountChanged";
                this.txtUnreadMessageCountChanged.Size = new System.Drawing.Size(24, 13);
                this.txtUnreadMessageCountChanged.TabIndex = 8;
                this.txtUnreadMessageCountChanged.Text = "test";
                // 
                // label8
                // 
                this.label8.AutoSize = true;
                this.label8.Location = new System.Drawing.Point(180, 86);
                this.label8.Name = "label8";
                this.label8.Size = new System.Drawing.Size(119, 13);
                this.label8.TabIndex = 7;
                this.label8.Text = "Unread Message Count";
                // 
                // RoomDescription_label
                // 
                this.RoomDescription_label.AutoSize = true;
                this.RoomDescription_label.Location = new System.Drawing.Point(305, 63);
                this.RoomDescription_label.Name = "RoomDescription_label";
                this.RoomDescription_label.Size = new System.Drawing.Size(84, 13);
                this.RoomDescription_label.TabIndex = 6;
                this.RoomDescription_label.Text = "room description";
                // 
                // label5
                // 
                this.label5.AutoSize = true;
                this.label5.Location = new System.Drawing.Point(180, 63);
                this.label5.Name = "label5";
                this.label5.Size = new System.Drawing.Size(60, 13);
                this.label5.TabIndex = 5;
                this.label5.Text = "Description";
                // 
                // btnRetrieveAdditionalMessages
                // 
                this.btnRetrieveAdditionalMessages.Location = new System.Drawing.Point(545, 209);
                this.btnRetrieveAdditionalMessages.Name = "btnRetrieveAdditionalMessages";
                this.btnRetrieveAdditionalMessages.Size = new System.Drawing.Size(75, 49);
                this.btnRetrieveAdditionalMessages.TabIndex = 7;
                this.btnRetrieveAdditionalMessages.Text = "Retrieve Additional Messages";
                this.btnRetrieveAdditionalMessages.UseVisualStyleBackColor = true;
                this.btnRetrieveAdditionalMessages.Click += new System.EventHandler(this.btnRetrieveAdditionalMessages_Click);
                // 
                // listBoxMessages
                // 
                this.listBoxMessages.FormattingEnabled = true;
                this.listBoxMessages.HorizontalScrollbar = true;
                this.listBoxMessages.Location = new System.Drawing.Point(9, 123);
                this.listBoxMessages.Name = "listBoxMessages";
                this.listBoxMessages.Size = new System.Drawing.Size(517, 407);
                this.listBoxMessages.TabIndex = 8;
                // 
                // txtLastMessageID
                // 
                this.txtLastMessageID.Location = new System.Drawing.Point(545, 142);
                this.txtLastMessageID.Name = "txtLastMessageID";
                this.txtLastMessageID.Size = new System.Drawing.Size(100, 20);
                this.txtLastMessageID.TabIndex = 10;
                // 
                // txtNumMessages
                // 
                this.NumberOfMessagesToGet_Text.Location = new System.Drawing.Point(545, 183);
                this.NumberOfMessagesToGet_Text.Name = "txtNumMessages";
                this.NumberOfMessagesToGet_Text.Size = new System.Drawing.Size(100, 20);
                this.NumberOfMessagesToGet_Text.TabIndex = 11;
                this.NumberOfMessagesToGet_Text.Text = "27";
                // 
                // label6
                // 
                this.label6.AutoSize = true;
                this.label6.Location = new System.Drawing.Point(545, 126);
                this.label6.Name = "label6";
                this.label6.Size = new System.Drawing.Size(87, 13);
                this.label6.TabIndex = 12;
                this.label6.Text = "Last Message ID";
                // 
                // label7
                // 
                this.label7.AutoSize = true;
                this.label7.Location = new System.Drawing.Point(545, 167);
                this.label7.Name = "label7";
                this.label7.Size = new System.Drawing.Size(107, 13);
                this.label7.TabIndex = 13;
                this.label7.Text = "Number of Messages";
                // 
                // FollowedRooms_listbox
                // 
                this.FollowedRooms_listbox.FormattingEnabled = true;
                this.FollowedRooms_listbox.Location = new System.Drawing.Point(9, 48);
                this.FollowedRooms_listbox.Name = "FollowedRooms_listbox";
                this.FollowedRooms_listbox.Size = new System.Drawing.Size(165, 69);
                this.FollowedRooms_listbox.TabIndex = 38;
                this.FollowedRooms_listbox.SelectedValueChanged += new System.EventHandler(this.FollowedRoomsList_SelectedValueChanged);
                // 
                // label13
                // 
                this.label13.AutoSize = true;
                this.label13.Location = new System.Drawing.Point(6, 31);
                this.label13.Name = "label13";
                this.label13.Size = new System.Drawing.Size(85, 13);
                this.label13.TabIndex = 39;
                this.label13.Text = "Followed Rooms";
                // 
                // GetMessages
                // 
                this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);
                this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
                this.ClientSize = new System.Drawing.Size(656, 551);
                this.Controls.Add(this.RoomDescription_label);
                this.Controls.Add(this.txtUnreadMessageCountChanged);
                this.Controls.Add(this.label13);
                this.Controls.Add(this.label8);
                this.Controls.Add(this.FollowedRooms_listbox);
                this.Controls.Add(this.label7);
                this.Controls.Add(this.label5);
                this.Controls.Add(this.label6);
                this.Controls.Add(this.NumberOfMessagesToGet_Text);
                this.Controls.Add(this.txtLastMessageID);
                this.Controls.Add(this.listBoxMessages);
                this.Controls.Add(this.btnRetrieveAdditionalMessages);
                this.Controls.Add(this.panel1);
                this.Name = "GetMessages";
                this.StartPosition = System.Windows.Forms.FormStartPosition.CenterScreen;
                this.Text = "GetMessages";
                this.Load += new System.EventHandler(this.GetMessages_Load);
                this.panel1.ResumeLayout(false);
                this.panel1.PerformLayout();
                this.ResumeLayout(false);
                this.PerformLayout();
    
            }
    
            #endregion
    
            private System.Windows.Forms.Panel panel1;
            private System.Windows.Forms.Label LyncClientState_Label;
            private System.Windows.Forms.Label label1;
            private System.Windows.Forms.Label RoomDescription_label;
            private System.Windows.Forms.Label label5;
            private System.Windows.Forms.Button btnRetrieveAdditionalMessages;
            private System.Windows.Forms.ListBox listBoxMessages;
            private System.Windows.Forms.TextBox txtLastMessageID;
            private System.Windows.Forms.TextBox NumberOfMessagesToGet_Text;
            private System.Windows.Forms.Label label6;
            private System.Windows.Forms.Label label7;
            private System.Windows.Forms.Label txtUnreadMessageCountChanged;
            private System.Windows.Forms.Label label8;
            private System.Windows.Forms.ListBox FollowedRooms_listbox;
            private System.Windows.Forms.Label label13;
        }
    }

The following code interacts with the form declared in the previous example. This example contains the logic necessary to get followed rooms from a user’ contact list, get successive sets of posted messages from a followed room, and display new messages as they are posted.

    using System;
    using System.Collections.Generic;
    using System.Windows.Forms;
    using Microsoft.Lync.Model;
    using Microsoft.Lync.Model.Room;
    using System.Collections;
    
    namespace GetMessages
    {
        public partial class GetMessages : Form
        {
    
            /// <summary>
            /// The LyncClient class instance that encapsulates the Lync client platform
            /// </summary>
            private LyncClient _client=null;
    
            /// <summary>
            /// The Room instance that a user joins from the list of rooms that are queried, searched for, or gotten from the followed rooms list
            /// </summary>
            private Room _room = null;
    
            /// <summary>
            /// A Dictionary of Room instances that represent the chat rooms which a user is following.
            /// </summary>
            private Dictionary<string, Room> _followedRoomsList = new Dictionary<string, Room>();
    
            /// <summary>
            /// the number of messages that have been sent to a room which have not been read by a user
            /// </summary>
            private uint _unreadMessageCount = 0;
    
            /// <summary>
            /// Simple chat window constructor
            /// </summary>
            public GetMessages()
            {
                InitializeComponent();
              
            }
    
            private void GetMessages_Load(object sender, EventArgs e)
            {
                
                try
                {
                    //Get the client. The entry point to all further sample application functionality.
                    _client = LyncClient.GetClient();
    
                    if (_client.RoomManager.State == RoomManagerState.Disabled)
                    {
                        MessageBox.Show("Persistent Chat Server is not reachable. Quitting");
                    }
    
                    //Register for state change on the client (sign in, sign out)
                    _client.StateChanged += new EventHandler<ClientStateChangedEventArgs>(client_StateChanged);
    
                    //Register for accidental loss of network connectivity event
                    _client.ClientDisconnected += new EventHandler(client_ClientDisconnected);
    
                    //If the user is signed in to Lync, get the group chat rooms that are on the Lync contact list and register
                    //for events raised when a user adds another room to the contact list or removes a room from the contact list.
                    if (_client.State == ClientState.SignedIn)
                    {
                        //Check the state of the room manager. If the room manager is not enabled, then the Lync client is not signed in.
                        //Room manager is enabled by the platform after the Lync client has signed in
                        if (_client.RoomManager.State == RoomManagerState.Enabled && _client.RoomManager.FollowedRooms != null)
                        {
                            //Load all followed rooms that are currently in the users contact list.
                            LoadInitialFollowedRoomList();
    
                            //Register for event that is raised when another room is added to the user's contact list.
                            _client.RoomManager.FollowedRoomAdded += RoomManager_FollowedRoomAdded;
    
                            //Register for event that is raised when a room is removed from the user's contact list.
                            _client.RoomManager.FollowedRoomRemoved += RoomManager_FollowedRoomRemoved;
                        }
                    }
                    RefreshSelectedRoomProperties();
                }
                catch (Exception ex)
                {
                    MessageBox.Show(ex.Message);
                }
            }
    
            #region Followed Room related Methods
            /// <summary>
            /// Room removed event handler. Removes a room from the followed room list box on the UI.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void RoomManager_FollowedRoomRemoved(object sender, FollowedRoomsChangedEventArgs e)
            {
                this.Invoke(new UpdateFollowedRoomListDelegate(RemoveAFollowedRoomFromList), new object[] { e.Room });
            }
    
            /// <summary>
            /// Room added to contact list event handler. Adds a room to the followed room list box on the UI.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void RoomManager_FollowedRoomAdded(object sender, FollowedRoomsChangedEventArgs e)
            {
                this.Invoke(new UpdateFollowedRoomListDelegate(AddAFollowedRoomToList), new object[] { e.Room });
            }
    
            private delegate void UpdateFollowedRoomListDelegate(Room roomToAdd);
            private void AddAFollowedRoomToList(Room roomToAdd)
            {
    
                //Add a room to the Dictionary<string,Microsoft.Lync.Model.Room.Room>() 
                //Dictionary entry key is room title and value is room instance
                _followedRoomsList.Add(roomToAdd.Properties[RoomProperty.Title].ToString(), roomToAdd);
    
                //Add a followed room title to the UI list box of followed room titles.
                //User selects a room title from the list box and the corresponding Room instance is obtained
                //from the _followedRoomsList dictonary.
                FollowedRooms_listbox.Items.Add(roomToAdd.Properties[RoomProperty.Title].ToString());
    
            }
    
            /// <summary>
            /// Removes a room from the followed room list on the UI
            /// </summary>
            /// <param name="roomToRemove"></param>
            private void RemoveAFollowedRoomFromList(Room roomToRemove)
            {
                //If the followed room is in the followed room dictionary, remove the room from
                //both the dictionary and the followed room list on the UI
                if (_followedRoomsList.ContainsKey(roomToRemove.Properties[RoomProperty.Title].ToString()))
                {
                    _followedRoomsList.Remove(roomToRemove.Properties[RoomProperty.Title].ToString());
                    FollowedRooms_listbox.Items.Remove(roomToRemove.Properties[RoomProperty.Title].ToString());
                }
            }
    
            /// <summary>
            /// Loads a UI list box with the room title strings of all group chat rooms that
            /// the user has "followed"... added to the contact list.
            /// These followed rooms are locally cached by the Lync client platform.
            /// </summary>
            private void LoadInitialFollowedRoomList()
            {
                try
                {
                    //Update a UI label with the current state of the Lync client platform (signed out, signing in, signed in... etc)
                    LyncClientState_Label.Text = _client.State.ToString();
    
                    //Check the state of the room manager. If the room manager is not enabled, then the Lync client is not signed in.
                    //Room manager is enabled by the platform after the Lync client has signed in
                    if (_client.RoomManager.State == RoomManagerState.Enabled && _client.RoomManager.FollowedRooms != null)
                    {
    
                        //Iterate on the collection of Room instances that are followed by the user
                        foreach (Room followedRoom in _client.RoomManager.FollowedRooms)
                        {
                            //Add a room to the followed room UI list
                            AddAFollowedRoomToList(followedRoom);
                        }
                    }
    
                }
                catch (Exception ex)
                {
                    MessageBox.Show("Load Followed Room List Exception: " + ex.Message);
                }
    
            }
    
            /// <summary>
            /// Handles the event raised when a user selects a followed room from the list
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void FollowedRoomsList_SelectedValueChanged(object sender, EventArgs e)
            {
                ListBox box = (ListBox)sender;
                Room selectedRoom;
    
                //Make sure the user has selected a room.
                if (box.SelectedItem != null)
                {
                    //Get the Room object from the followed room dictionary that is filled when the form is opened.
                    if (_followedRoomsList.TryGetValue(box.SelectedItem.ToString(), out selectedRoom))
                    {
                        //Clear the room properties and unregister for events on the previously chosen room.
                        ClearRoomProperties(_room);
    
                        //Fill the room properties and register for events on the currently chosen room.
                        FillRoomProperties(selectedRoom);
                    }
                }
            }
    
            #endregion
    
            #region Message Related methods
            /// <summary>
            /// Gets a set of previously posted messages.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void btnRetrieveAdditionalMessages_Click(object sender, EventArgs e)
            {
                try
                {
                    //Empty the message list box of all messages
                    listBoxMessages.Items.Clear();
    
                    if (_room != null)
                    {
    
                        //A user can get messages from a room if they are a member of the room as defined by the room managers. 
                        //User must join a room to get messages from the room.
    
                        //If not joined to the room, attempt to join the room.
                        if (_room.JoinedState != RoomJoinState.Success)
                        {
                            _room.EndJoin(_room.BeginJoin(null, null));
                        }
    
                        //If joined to the room then request messages posted to the room.
                        if (_room.JoinedState == RoomJoinState.Success)
                        {
                            //Get the number of messages to return
                            uint count = Convert.ToUInt32(NumberOfMessagesToGet_Text.Text);
    
                            //Declare field that holds the id of the oldest message currently displayed
                            uint OldestMessageIdDisplayed = 0;
    
                            try
                            {
                                //If a non-numeric string is held in this text field, a FormatException is raised
                                //when the Convert method is called.
                                OldestMessageIdDisplayed = Convert.ToUInt32(txtLastMessageID.Text);
                            }
                            catch (FormatException) { }
    
                            //If an oldest current message Id is specified then get a set of messages that are older than the oldest current message.
                            if (OldestMessageIdDisplayed != 0)
                            {
                                //Retrieve messages with Ids up to (but not including) the message Id specified in the first argument
                                _room.BeginRetrieveAdditionalMessages(OldestMessageIdDisplayed, count, GetMessagesCallback, "Additional");
                            }
                            else
                            {
                                //Retrieve messages in chronological order from newest to oldest up to the number of messages specified in the first argument.
                                _room.BeginRetrieveLatestMessages(count, GetMessagesCallback, "Latest");
                            }
                        }
    
                    }
                }
                catch (JoinRoomUnauthorizedException)
                {
                    MessageBox.Show("Not authorized to join room");
                }
                catch (JoinRoomFailException)
                {
                    MessageBox.Show("Failed to join the room");
                }
                catch (Exception ex)
                {
                    MessageBox.Show(ex.Message);
                }
            }
    
            /// <summary>
            /// Invoked by platform thread when the message retrieve operation is completed.
            /// </summary>
            /// <param name="ar"></param>
            private void GetMessagesCallback(IAsyncResult ar)
            {
    
                //Declare a list to contain the collection of room messages returned by the operation
                IList<RoomMessage> messages;
                try
                {
    
                    //Call the EndRetrieveXXXMessages operation that corresponds to the
                    //BeginRetrieveXXXMessges method call that started the operation
                    if (ar.AsyncState.ToString() == "Latest")
                    {
                        //Get the collection of the latest messages sent to the room
                        messages = _room.EndRetrieveLatestMessages(ar);
                    }
                    else
                    {
                        //Get the collection of messages up to the specified message
                        messages = _room.EndRetrieveAdditionalMessages(ar);
                    }
    
                    //Invoke a delegate on the UI thread that loads the message collection in the message list box.                
                    listBoxMessages.Invoke(new LoadPostedMessagesDelegate(LoadPostedMessages), new object[] { messages, false });
                }
                catch (Exception ex)
                {
                    Console.WriteLine("Exception on EndRetrieveXXMessages " + ex.Message);
                }
            }
    
            private delegate void LoadPostedMessagesDelegate(IList<RoomMessage> messages, Boolean invokeByMessagesReceivedEvent);
            /// <summary>
            /// Loads a list box with a collection of messages
            /// </summary>
            /// <param name="messages"></param>
            private void LoadPostedMessages(IList<RoomMessage> messages, Boolean invokeByMessagesReceivedEvent)
            {
                if (invokeByMessagesReceivedEvent == false)
                {
                    //Add a header row to the list box with colunm names separated by TAB characters.
                    listBoxMessages.Items.Add("Messages retrieved: " + messages.Count.ToString());
                    listBoxMessages.Items.Add("Id\tSent Time\t\tSender");
    
                    //Store the message id of the oldest message in this collection. Subsequent calls to
                    //BeginGetAdditionalMessages() uses this Id to specify the oldest message that is already
                    //displayed in the message list.
                    if (messages.Count > 0)
                    {
                        txtLastMessageID.Text = messages[0].Id.ToString();
                    }
                }
                //Declare Contact object to be initialized with the object returned from GetContactByUri
                Contact senderContact;
    
                foreach (RoomMessage message in messages)
                {
                    object messageObject = null;
    
                    //Get the sender as a Contact instance
                    senderContact = _client.ContactManager.GetContactByUri(message.SenderUri);
    
                    //Get the display name of the message sender
                    string senderName = senderContact.GetContactInformation(ContactInformationType.DisplayName).ToString();
    
                    //Get the plain text version of a message
                    if (message.MessageDictionary.TryGetValue(RoomMessageFormat.PlainText, out messageObject))
                    {
                        string messageContent = (string)messageObject;
    
                        //create an item in the list box constructed of message sent time - TAB character - message type - sender display name
                        listBoxMessages.Items.Add(message.Id.ToString() +
                            "\t" + message.SentTime.ToString() +
                            "\t" + senderName +
                            "\t" + messageContent);
                    }
                    messageObject = null;
                }
            }
    
            /// <summary>
            /// Room event handler for the UnreadRoomMessageCount changed event. Raised when a user posts a message to a room. 
            /// This event handler can be used to cause your application to request the most recent messages.
            /// In this case, the event handler just updates a UI label that displays the number of unread messages.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void room_UnreadMessageCountChanged(object sender, UnreadMessageCountChangedEventArgs e)
            {
                uint count = e.NewUnreadMessageCount;
    
                txtUnreadMessageCountChanged.Invoke(new UpdateUnreadMessageCountDelegate(this.UpdateUnreadMessageCount), count);
    
            }
    
            private delegate void UpdateUnreadMessageCountDelegate(uint count);
            /// <summary>
            /// Updates a UI label with the current number of unread messages
            /// </summary>
            /// <param name="count"></param>
            private void UpdateUnreadMessageCount(uint count)
            {
                txtUnreadMessageCountChanged.Text = count.ToString();
            }
    
            /// <summary>
            /// This event is raised when any room member has posted a message to the room. This includes
            /// the local user.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void room_MessagesReceived(object sender, RoomMessagesEventArgs e)
            {
    
                //Get the collection of newly posted messages.
                IList<RoomMessage> receivedMessages = e.Messages;
    
                //Invoke a delegate on the UI thread that updates the message list with the contents of the new message.
                listBoxMessages.Invoke(new LoadPostedMessagesDelegate(LoadPostedMessages), new object[] { receivedMessages, true });
    
            }
    
            #endregion
    
            #region Room related methods
            private delegate void RefreshObjectsDelegate();
            /// <summary>
            /// Updates the client state label, unread message count, and message list
            /// when the state of the client changes.
            /// </summary>
            public void RefreshSelectedRoomProperties()
            {
                LyncClientState_Label.Text = _client.State.ToString();
                if (_client.State != ClientState.SignedIn)
                {
                    FollowedRooms_listbox.Items.Clear();
                    _followedRoomsList.Clear();
                }
                ClearRoomProperties(_room);
                if (_room != null)
                {
                    FillRoomProperties(_room);
                }
    
                if (_room == null)
                {
                    RoomDescription_label.Text = "null";
                    txtUnreadMessageCountChanged.Text = "null";
                }
            }
    
            /// <summary>
            /// Clears the messagebox and un-registers for events on a selected room
            /// </summary>
            /// <param name="room"></param>
            private void ClearRoomProperties(Room room)
            {
                //Clear the messages from a previous room choice out of the message listbox
                listBoxMessages.Items.Clear();
    
                if (room == null)
                {
                    return;
                }
    
                //Register for event raised when a new message is posted to the room or the user has read a message.
                room.UnreadMessageCountChanged -= room_UnreadMessageCountChanged;
    
                //Register for the event raised when users have posted messages to the room.
                room.MessagesReceived -= room_MessagesReceived;
            }
    
            /// <summary>
            /// Registers for message, state, and participant related events on a room.
            /// </summary>
            private void FillRoomProperties(Room room)
            {
    
                //If the LyncClient is signed in then any Room object is valid and can be queried for properties. 
                //If LyncClient is signed out, you may have a non-null Room object, but it's properties are null.
                if (_client.State == ClientState.SignedIn)
                {
                    _room = room;
    
                    //Register for event raised when a new message is posted to the room or the user has read a message.
                    _room.UnreadMessageCountChanged += room_UnreadMessageCountChanged;
    
                    //Register for the event raised when users have posted messages to the room.
                    _room.MessagesReceived += room_MessagesReceived;
    
                    if (_room.Properties[RoomProperty.Description] != null)
                    {
                        RoomDescription_label.Text = _room.Properties[RoomProperty.Description].ToString();
                    }
    
                    txtUnreadMessageCountChanged.Text = _room.UnreadRoomMessageCount.ToString();
    
                    uint numberOfMessagesToGet = 0;
                    try
                    {
                        numberOfMessagesToGet = Convert.ToUInt32(NumberOfMessagesToGet_Text.Text);
                    }
                    catch (FormatException) { }
    
                    //Get the most recent messages.
                    _room.BeginRetrieveLatestMessages(numberOfMessagesToGet, GetMessagesCallback, "Latest");
    
                }
            }
    
            #endregion
    
            #region Client related methods
            public void client_StateChanged(object sender, ClientStateChangedEventArgs e)
            {
                if (_client.State != ClientState.SignedIn)
                {
                    _room = null;
                }
                this.Invoke(new RefreshObjectsDelegate(RefreshSelectedRoomProperties));
            }
    
            public void client_ClientDisconnected(object sender, EventArgs e)
            {
                this.Invoke(new RefreshObjectsDelegate(RefreshSelectedRoomProperties));
            }
            #endregion
    
        }
    }

## Next steps

  - [How to: Send a message to a chat room](how-to-send-a-message-to-a-chat-room.md)

  - [How to: Find a chat room](how-to-find-a-chat-room.md)

## See also

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

