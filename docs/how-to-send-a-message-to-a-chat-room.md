---
title: 'How to: Send a message to a chat room'
TOCTitle: 'How to: Send a message to a chat room'
ms:assetid: 8d68c4e8-fb3e-4929-9ecd-e1161e5bfc8c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933112(v=office.15)
ms:contentKeyID: 50877245
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Send a message to a chat room

Learn how to post regular and story messages to a Microsoft Lync 2013 Persistent Chat room by using methods in Microsoft Lync 2013 SDK.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

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
Prepare to post messages<br />
Post a message to a chat room<br />
Code examples: Chat room message poster<br />
Next steps<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-post-messages-to-b823afd1">Post messages to a Persistent Chat room that the user has joined</a><br />
</p></td>
</tr>
</tbody>
</table>

## Message overview

This topic shows you the code that you add to a simple Persistent Chat window so that a user can post a message to a chat room. A user can post a regular message or an alert message to a chat room and the message can be plain text, rich-text (RTF), or sent in both formats.

A message can be sent to a chat room even if the user is not an active participant in the chat room. There are two requirements to post messages to a chat room:

  - The user must be a member of the chat room.

  - If the chat room is an [RoomType](https://msdn.microsoft.com/en-us/library/jj266029\(v=office.15\))**.Auditorium** chat room, the user must be a presenter in the auditorium.

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
<td><p>The user must join a chat room before they can post messages to the chat room. The user is added to the participant list and a <a href="https://msdn.microsoft.com/en-us/library/jj277204(v=office.15)">Room.ParticipantAdded</a> event is raised on any other client that is registered for the event and whose user is an active participant in the chat room.</p>
<p>A user is automatically joined to a followed chat room when the user signs in to Microsoft Lync 2013. In this case, the <strong>ParticipantAdded</strong> event is raised on other clients when the member-user signs in to Lync 2013.</p></td>
</tr>
</tbody>
</table>

In some scenarios, it is important that a message that is posted to a chat room comply with content and formatting constraints imposed by the organization that administers the Persistent Chat server. For example, a multi-national IT company might want to make sure that a user’s message does not contain language that can offend another chat room user. To make this message filtering possible, the Lync platform exposes an event that is raised when a message posting operation has started but is pending review by a logical message filter. The filter catches the event, runs filter logic on the message, updates the message as necessary, and then posts the message or cancels it. For information about how to build a message filter, see [How to: Filter an outgoing message from a local user to a chat room](how-to-filter-an-outgoing-message-from-a-local-user-to-a-chat-room.md).

## Prerequisites

The prerequisites for posting a message to a chat room are as follows:

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
</tbody>
</table>

## Initial application state

Before you start the procedures in this topic, your application must declare and initialize a [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance and the client must be signed in. For more information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

You must also have an instance of [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/en-us/library/jj266467\(v=office.15\)) where the user has permission to post messages. For information about getting a chat room, see [How to: Find a chat room](how-to-find-a-chat-room.md). Your application must declare a button and an RTF text box. The RTF text box accepts the message string to post and the button posts the message.

### Code example

The following example references the namespaces that are used in the following Windows Forms examples.

``` csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Room;
using System.Collections;
```

The following example declares the class fields that are referenced later in this topic.

``` csharp
        /// <summary>
        /// The LyncClient class instance that encapsulates the Lync client platform
        /// </summary>
        private LyncClient _client=null;

        /// <summary>
        /// The Room instance that a user joins from the list of chat rooms that are queried, searched for, or gotten from the followed chat rooms list
        /// </summary>
        private Room _room = null;

        /// <summary>
        /// The Uri of the local user who can post a message to a chat room
        /// </summary>
        private string _senderUri = "";

        /// <summary>
        /// The default color of the message send button. Used to restore the color after a local user
        /// message post is successful
        /// </summary>
        private System.Drawing.Color originalSendButtonColor;
```

The following example constructs the simple chat window UI and saves the original background color of the send button.

``` csharp
        /// <summary>
        /// Simple chat window constructor
        /// </summary>
        public SimpleChat()
        {
            InitializeComponent();
 
            // Save the original color of the message post button.
            originalSendButtonColor = btnSendMessage.BackColor;
          
        }
```

## Prepare to post messages

When you have obtained a [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/en-us/library/jj266467\(v=office.15\)) instance selected by a user, register for a set of chat room events so that you can receive notification of messages posted to the chat room by other users or a message that is posted to the chat room by the local user.

### To prepare to post messages

1.  Unregister for events on the previously selected chat room that is referenced by the \_room class field.

2.  Set the \_room class field to the newly selected chat room.

3.  Register for chat room events.

4.  Read chat room properties and update the UI with the chat room title, description, unread message count, and chat room roster.

The following example registers for chat room events, reads chat room properties, and gets the chat room participant roster.

``` csharp
        /// <summary>
        /// Registers for message, state, and participant related events on a chat room.
        /// </summary>
        private void FillRoomProperties(Room room)
        {
            if (_room != null)
            {
                //Un-Register for event raised when a new message is posted to the chat room or the user has read a message.
                _room.UnreadMessageCountChanged -= room_UnreadMessageCountChanged;

                //Un-Register for the event raised when users have posted messages to the chat room.
                _room.MessagesReceived -= room_MessagesReceived;

            }

            _room = room;

            //Clear the messages from a previous chat room choice out of the message list box
            listBoxMessages.Items.Clear();

            //Register for event raised when a new message is posted to the chat room or the user has read a message.
            _room.UnreadMessageCountChanged += new EventHandler<UnreadMessageCountChangedEventArgs>(room_UnreadMessageCountChanged);

            //Register for the event raised when users have posted messages to the chat room.
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

## Post a message to a chat room

After you have prepared to post messages to a chat room by following the steps in the previous procedure, you are ready to accept a user’s text input and post new messages to the selected chat room.

### To post a message to a chat room

1.  Declare and instantiate an instance of **IDictionary\<**[Microsoft.Lync.Model.Room.RoomMessageFormat](https://msdn.microsoft.com/en-us/library/jj277588\(v=office.15\))**, string\>** that you add formatted message strings to.
    
    The dictionary is passed into the message posting method as the first argument.

2.  Add both versions of the message to the dictionary declared in the previous step.
    
    1.  Add the key/value pair of [RoomMessageFormat](https://msdn.microsoft.com/en-us/library/jj277588\(v=office.15\))**.PlainText** / plain-text-formatted string (the message text) to the dictionary declared in the previous step.
    
    2.  Add the key/value pair of [RoomMessageFormat](https://msdn.microsoft.com/en-us/library/jj277588\(v=office.15\))**.Rtf** / Rtf formatted version of the message string to the dictionary declared in the previous step.

3.  Join the chat room if the current [Room.JoinedState](https://msdn.microsoft.com/en-us/library/jj267006\(v=office.15\)) is [Microsoft.Lync.Model.Room.RoomJoinState](https://msdn.microsoft.com/en-us/library/jj276163\(v=office.15\))**.NotJoined**.

4.  If the message is a regular message, call the [Room.BeginSendMessage](https://msdn.microsoft.com/en-us/library/jj293980\(v=office.15\)) overload of the method.
    
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
    <td><p>The following code example passes <a href="https://msdn.microsoft.com/en-us/library/jj265996(v=office.15)">RoomMessageType</a><strong>.Regular</strong> as the second argument without asking a user for input. Normally, you would put a choice control on your window that lets a user select one of the four message types.</p>
    <p>When the text of the message is long enough to justify displaying the message as a story in the Lync 2013 Persistent Chat window, set the <strong>RoomMessageType</strong> to <a href="https://msdn.microsoft.com/en-us/library/jj265996(v=office.15)">RoomMessageType</a><strong>.Story</strong>.</p></td>
    </tr>
    </tbody>
    </table>

5.  If the user wants to send a story instead of a regular message and has provided a story title, call the **RoomBeginSendStoryMessage(IDictionary\<RoomMessageFormat, String\>, String, AsyncCallback, Object)** method.

6.  Handle the [Room.MessagesReceived](https://msdn.microsoft.com/en-us/library/jj277819\(v=office.15\)) event.

7.  Iterate over the collection of new messages and find a message whose sender URI matches the local user’s URI and message text matches the newly posted message.
    
    If a match is found, the message was posted to the chat room.

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
<td><p>If posting a plain-text message only, call <a href="https://msdn.microsoft.com/en-us/library/jj293980(v=office.15)">Room.BeginSendMessage</a>, passing the plain-text message string in the first argument instead of the <strong>IDictionary</strong> instance.</p></td>
</tr>
</tbody>
</table>

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
<td><p>The following list describes two ways that you can confirm whether a local user’s message was posted to a chat room.</p>
<ul>
<li><p>Code a <strong>try/catch</strong> block around the <a href="https://msdn.microsoft.com/en-us/library/jj267662(v=office.15)">Room.EndSendMessage</a> method that you call inside a callback method passed into the <a href="https://msdn.microsoft.com/en-us/library/jj293980(v=office.15)">Room.BeginSendMessage</a> method. If an exception is not raised and the user is a member of the chat room with permission to post, the post succeeded.</p></li>
<li><p>Handle the <a href="https://msdn.microsoft.com/en-us/library/jj277819(v=office.15)">Room.MessagesReceived</a> event. If one of the messages in the collection of new messages posted to the chat room originated with the local user, the post succeeded.</p></li>
</ul></td>
</tr>
</tbody>
</table>

### Code examples

The following example gets the user’s message text and then posts the plain-text formatted version of the message to a chat room.

``` csharp
        /// <summary>
        /// Handles the event raised when the user clicks the Send button
        /// </summary>
        /// <param name="followedRoom">Room. The chat room to post to</param>
        /// <param name="messageTitle">string. The title of the story</param>
        /// <param name="messageBody">string. The message body</param>
        private void SendAMessage(Room followedRoom, string messageTitle, string messageBody)
        {
            //Send a message if the user has selected a room
            if (followedRoom == null || _client.State != ClientState.SignedIn)
            {
                Console.WriteLine("Message was not sent");
                return;
            }
            try
            {
                //If the user is not joined to the room then try to join the room
                if (followedRoom.JoinedState != RoomJoinState.Success)
                {
                    followedRoom.BeginJoin((ar) => { followedRoom.EndJoin(ar); }, null);
                }

                //If the user is connected (joined) to the room then send the message
                if (followedRoom.JoinedState == RoomJoinState.Success)
                {
                    //Post the story

                    IDictionary<RoomMessageFormat, string> roomMessageDictionary = new Dictionary<RoomMessageFormat, string>();
                    roomMessageDictionary.Add(RoomMessageFormat.PlainText, messageBody);

                    // If the user added a story title, then send message as a story.
                    if (messageTitle.Length > 0)
                    {
                        followedRoom.BeginSendStoryMessage(roomMessageDictionary, messageTitle, (ar) =>
                        {
                            try
                            {
                                followedRoom.EndSendStoryMessage(ar);
                                Console.WriteLine( "Message Sent" );
                            }
                            catch (OperationException oe)
                            {
                                Console.WriteLine("Lync client failed to send the message: " + oe.Message);
                            }
                            catch (Exception ex)
                            {
                                Console.WriteLine("Exception on send message: " + ex.Message);
                            }
                        }, null);
                    }

                    // if the user did not provide a story title, then send as regular message.
                    else
                    {
                        followedRoom.BeginSendMessage(roomMessageDictionary, RoomMessageType.Regular, (ar) =>
                        {
                            try
                            {
                                followedRoom.EndSendMessage(ar);
                                Console.WriteLine("Message Sent");
                            }
                            catch (OperationException oe)
                            {
                                Console.WriteLine("Lync client failed to send the message: " + oe.Message);
                            }
                            catch (Exception ex)
                            {
                                Console.WriteLine("Exception on send message: " + ex.Message);
                            }
                        }, null);
                    }
                }
            }
            catch (JoinRoomFailException)
            {
                Console.WriteLine("Failed to join room");
            }
            catch (JoinRoomUnauthorizedException)
            {
                Console.WriteLine("Not authorized to join room");
            }
            catch (OperationException oe)
            {
                Console.WriteLine("Operation Exception on post message " + oe.Message);
            }
            catch (Exception ex)
            {
                Console.WriteLine("Exception on post message " + ex.Message);
            }
        }
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
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267662(v=office.15)">Room.EndSendMessage</a> raises an exception if the sent message contains an invalid RTF string.</p></td>
</tr>
</tbody>
</table>

## Code examples: Chat room message poster

The following example declares a form that accepts a followed room collection index and a string and then posts the string as a message to the followed room at the index position in the collection.

``` csharp
namespace PostMessage
{
    partial class PostMessage
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
            this.label13 = new System.Windows.Forms.Label();
            this.FollowedRoom_Numeric = new System.Windows.Forms.NumericUpDown();
            this.FollowedRoomTitle_Label = new System.Windows.Forms.Label();
            this.Send_Button = new System.Windows.Forms.Button();
            this.SendMessageResult_Label = new System.Windows.Forms.Label();
            this.Message_TextBox = new System.Windows.Forms.TextBox();
            this.panel1.SuspendLayout();
            ((System.ComponentModel.ISupportInitialize)(this.FollowedRoom_Numeric)).BeginInit();
            this.SuspendLayout();
            // 
            // panel1
            // 
            this.panel1.Controls.Add(this.LyncClientState_Label);
            this.panel1.Controls.Add(this.label1);
            this.panel1.Location = new System.Drawing.Point(9, 5);
            this.panel1.Name = "panel1";
            this.panel1.Size = new System.Drawing.Size(233, 23);
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
            this.label1.Location = new System.Drawing.Point(18, 4);
            this.label1.Name = "label1";
            this.label1.Size = new System.Drawing.Size(87, 13);
            this.label1.TabIndex = 0;
            this.label1.Text = "Lync Client State";
            // 
            // label13
            // 
            this.label13.AutoSize = true;
            this.label13.Location = new System.Drawing.Point(6, 60);
            this.label13.Name = "label13";
            this.label13.Size = new System.Drawing.Size(80, 13);
            this.label13.TabIndex = 39;
            this.label13.Text = "Followed Room";
            // 
            // FollowedRoom_Numeric
            // 
            this.FollowedRoom_Numeric.Location = new System.Drawing.Point(93, 60);
            this.FollowedRoom_Numeric.Name = "FollowedRoom_Numeric";
            this.FollowedRoom_Numeric.Size = new System.Drawing.Size(62, 20);
            this.FollowedRoom_Numeric.TabIndex = 42;
            this.FollowedRoom_Numeric.ValueChanged += new System.EventHandler(this.FollowedRoom_Numeric_ValueChanged);
            // 
            // FollowedRoomTitle_Label
            // 
            this.FollowedRoomTitle_Label.AutoSize = true;
            this.FollowedRoomTitle_Label.Location = new System.Drawing.Point(9, 104);
            this.FollowedRoomTitle_Label.Name = "FollowedRoomTitle_Label";
            this.FollowedRoomTitle_Label.Size = new System.Drawing.Size(0, 13);
            this.FollowedRoomTitle_Label.TabIndex = 43;
            // 
            // Send_Button
            // 
            this.Send_Button.Location = new System.Drawing.Point(249, 137);
            this.Send_Button.Name = "Send_Button";
            this.Send_Button.Size = new System.Drawing.Size(75, 23);
            this.Send_Button.TabIndex = 45;
            this.Send_Button.Text = "Send";
            this.Send_Button.UseVisualStyleBackColor = true;
            this.Send_Button.Click += new System.EventHandler(this.SendButton_Click);
            // 
            // SendMessageResult_Label
            // 
            this.SendMessageResult_Label.AutoSize = true;
            this.SendMessageResult_Label.Location = new System.Drawing.Point(9, 235);
            this.SendMessageResult_Label.Name = "SendMessageResult_Label";
            this.SendMessageResult_Label.Size = new System.Drawing.Size(83, 13);
            this.SendMessageResult_Label.TabIndex = 46;
            this.SendMessageResult_Label.Text = "Message Status";
            // 
            // Message_TextBox
            // 
            this.Message_TextBox.Location = new System.Drawing.Point(0, 139);
            this.Message_TextBox.Multiline = true;
            this.Message_TextBox.Name = "Message_TextBox";
            this.Message_TextBox.Size = new System.Drawing.Size(229, 77);
            this.Message_TextBox.TabIndex = 47;
            // 
            // PostMessage
            // 
            this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(334, 262);
            this.Controls.Add(this.Message_TextBox);
            this.Controls.Add(this.SendMessageResult_Label);
            this.Controls.Add(this.Send_Button);
            this.Controls.Add(this.FollowedRoomTitle_Label);
            this.Controls.Add(this.FollowedRoom_Numeric);
            this.Controls.Add(this.label13);
            this.Controls.Add(this.panel1);
            this.Name = "PostMessage";
            this.Text = "Post a Message";
            this.Load += new System.EventHandler(this.PostMessage_Load);
            this.panel1.ResumeLayout(false);
            this.panel1.PerformLayout();
            ((System.ComponentModel.ISupportInitialize)(this.FollowedRoom_Numeric)).EndInit();
            this.ResumeLayout(false);
            this.PerformLayout();

        }

        #endregion

        private System.Windows.Forms.Panel panel1;
        private System.Windows.Forms.Label LyncClientState_Label;
        private System.Windows.Forms.Label label1;
        private System.Windows.Forms.Label label13;
        private System.Windows.Forms.NumericUpDown FollowedRoom_Numeric;
        private System.Windows.Forms.Label FollowedRoomTitle_Label;
        private System.Windows.Forms.Button Send_Button;
        private System.Windows.Forms.Label SendMessageResult_Label;
        private System.Windows.Forms.TextBox Message_TextBox;
    }
}
```

The following example interacts with the form declared in the previous example. This example gets a followed room based on user index value selection and then sends any typed text to the selected room.

``` csharp
using System;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Room;

namespace PostMessage
{
    public partial class PostMessage : Form
    {

        /// <summary>
        /// The LyncClient class instance that encapsulates the Lync client platform
        /// </summary>
        private LyncClient _client=null;

        /// <summary>
        /// The Room selected by a user when a numeric value changes on the NumericUpDown control
        /// </summary>
        private Room _FollowedRoom;

        /// <summary>
        /// Simple chat window constructor
        /// </summary>
        public PostMessage()
        {
            InitializeComponent();
        }

        /// <summary>
        /// Main form load event handler
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void PostMessage_Load(object sender, EventArgs e)
        {
            try
            {
                //Get the lync client platform, the entry point for all group chat room related code.
                _client = LyncClient.GetClient();

                //Register for sign in/sign out events on the client
                _client.StateChanged += new EventHandler<ClientStateChangedEventArgs>(client_StateChanged);

                //If the client is signed in then load the followed room list
                if (_client.State == ClientState.SignedIn)
                {
                    //Set the numeric updown control maximum property to the number of 
                    //followed rooms in the followed room collection on the room manager.
                    if (_client.RoomManager.State == RoomManagerState.Enabled)
                    {
                        if (_client.RoomManager.FollowedRooms != null)
                        {
                            FollowedRoom_Numeric.Maximum = _client.RoomManager.FollowedRooms.Count;
                            FollowedRoom_Numeric.Minimum = 1;
                        }
                    }
                    else
                    {
                        MessageBox.Show("Persistent Chat Server is not reachable. Qutting");
                        this.Close();
                    }
                }

                //Set the lync client state label to show the current state of the client
                RefreshClientStateLabel();
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }

        /// <summary>
        /// Handles the client state change event
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        public void client_StateChanged(object sender, ClientStateChangedEventArgs e)
        {
            //If the client has signed in then register for room mananger events
            if (e.NewState == ClientState.SignedIn)
            {
                //Set the NumericUpdown maximum to the count of rooms in the followed room list
                FollowedRoom_Numeric.Maximum = _client.RoomManager.FollowedRooms.Count;
                FollowedRoom_Numeric.Minimum = 1;
            }

            //Update the form label with the current state of the client
            this.Invoke(new RefreshClientStateLabelDelegate(RefreshClientStateLabel));
        }

        private delegate void RefreshClientStateLabelDelegate();

        /// <summary>
        /// Updates the client state label on the form to the current state of the client
        /// </summary>
        public void RefreshClientStateLabel()
        {
            if (_client == null)
            {
                LyncClientState_Label.Text = "Null";
            }
            else
            {
                LyncClientState_Label.Text = _client.State.ToString();
            }
        }

        /// <summary>
        /// Handles the event raised when a user changes the numeric value of the
        /// followed room index NumericUpDown control
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void FollowedRoom_Numeric_ValueChanged(object sender, EventArgs e)
        {
            //Get the control
            NumericUpDown upDown = (NumericUpDown)sender;

            //RoomManager.FollowedRooms property is null when the LyncClient.State == ClientState.SignedOut.
            //A user can sign out of Lync while this sample is running. If this happens, then the
            //FollowedRoom property is set to null
            if (_client.RoomManager.FollowedRooms != null && _client.RoomManager.FollowedRooms.Count > 0)
            {
                //Get the Room from the followed rooms collection at the index specified by the user
                _FollowedRoom = _client.RoomManager.FollowedRooms[Convert.ToInt32(upDown.Value - 1)];

                //Update the room title label on the form with the Title property of the selected room.
                FollowedRoomTitle_Label.Text = _FollowedRoom.Properties[RoomProperty.Title].ToString();

            }
        }

        /// <summary>
        /// Handles the event raised when the user clicks the Send button
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SendButton_Click(object sender, EventArgs e)
        {
            //Clear the previous message send result.
            SendMessageResult_Label.Text = "";

            //Send a message if the user has selected a room
            if (_FollowedRoom == null || _client.State != ClientState.SignedIn)
            {
                SendMessageResult_Label.Text = "Message was not sent";
                return;
            }
            try
            {
                //If the user is not joined to the room then try to join the room
                if (_FollowedRoom.JoinedState != RoomJoinState.Success)
                {
                    _FollowedRoom.EndJoin(_FollowedRoom.BeginJoin(null, null));
                }

                //If the user is connected (joined) to the room then send the message
                if (_FollowedRoom.JoinedState == RoomJoinState.Success)
                {
                    //Post the message
                    _FollowedRoom.BeginSendMessage(Message_TextBox.Text, RoomMessageType.Regular, SendMessageCallback, null);
                }
            }
            catch (JoinRoomFailException)
            {
                SendMessageResult_Label.Text = "Failed to join room";
            }
            catch (JoinRoomUnauthorizedException)
            {
                SendMessageResult_Label.Text = "Not authorized to join room";
            }
            catch (OperationException oe)
            {
                SendMessageResult_Label.Text = "Operation Exception on post message " + oe.Message;
            }
            catch (Exception ex)
            {
                SendMessageResult_Label.Text = "Exception on post message " + ex.Message;
            }
        }

        /// <summary>
        /// Invoked by platform when the message post operation is finished.
        /// </summary>
        /// <param name="ar"></param>
        private void SendMessageCallback(IAsyncResult ar)
        {
            try
            {
                _FollowedRoom.EndSendMessage(ar);
                SendMessageResult_Label.Invoke(new UpdateMessagePostResultsDelegate(UpdateMessagePostResults), new object[] { "Sent" });
            }
            catch (OperationException oe)
            {
                SendMessageResult_Label.Invoke(new UpdateMessagePostResultsDelegate(UpdateMessagePostResults), new object[] { "Lync client failed to send the message: " + oe.Message });
            }
            catch (Exception ex)
            {
                SendMessageResult_Label.Invoke(new UpdateMessagePostResultsDelegate(UpdateMessagePostResults), new object[] { "Exception on send message: " + ex.Message });
            }
        }

        private delegate void UpdateMessagePostResultsDelegate(string Results);

        private void UpdateMessagePostResults(string Results)
        {
            SendMessageResult_Label.Text = Results;
        }
    }
}
```

## Next steps

  - [How to: Find a chat room](how-to-find-a-chat-room.md)

  - [How to: Read messages sent to a chat room](how-to-read-messages-sent-to-a-chat-room.md)

## Additional resources

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

