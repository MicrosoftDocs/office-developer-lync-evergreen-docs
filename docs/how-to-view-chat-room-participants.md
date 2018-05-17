---
title: 'How to: View chat room participants'
TOCTitle: 'How to: View chat room participants'
ms:assetid: 0af3879c-4a06-4955-9621-aaabbbbc1aee
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937256(v=office.15)
ms:contentKeyID: 50877074
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: View chat room participants

Learn how to display and maintain a roster of Microsoft Lync 2013 users who have joined a Lync 2013 chat room.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Initial application state<br />
Register for room events<br />
Fill the participant list<br />
Handle participant list events<br />
Code examples: Chat room participant list<br />
Next steps<br />
Additional resources</p></td>
<td><p><img src="images/JJ937288.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-get-the-d10a83bc">Get the participants in a followed chat room</a><br />
</p></td>
</tr>
</tbody>
</table>


## Prerequisites

The prerequisites for displaying a chat room roster are as follow:

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

Before you complete the procedures in this topic, your application must declare and initialize a [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md) instance and the Lync client must be signed in. For more information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

You must also have an instance of [Microsoft.Lync.Model.Room.Room](room-class-microsoft-lync-model-room_2.md) where the user is a member. For information about getting a room, see [How to: Find a chat room](how-to-find-a-chat-room.md). Your application must declare a list to display room participants. You cannot use the Lync 2013 API to add or remove a user from the membership list of a room.

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

The following example declares the class fields that are referenced in the following sections of this topic.

``` csharp
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

When you have obtained the [Microsoft.Lync.Model.Room.Room](room-class-microsoft-lync-model-room_2.md) instance selected by a user, register for a set of chat room events so that you can receive notification of chat room participant roster changes.

### To register for room events

1.  Unregister for events on the previously selected room that is referenced by the \_room class field.

2.  Set the \_room class field to the newly selected chat room.

3.  Register for chat room events.

4.  Fill a UI list with the names of active chat room participants.

The following example registers for chat room participant roster events and gets the chat room participant roster.

``` csharp
        /// <summary>
        /// Registers for message, state, and participant related events on a room.
        /// </summary>
        private void FillRoomProperties(Room room)
        {
            if (_room != null)
            {
                //un-Register for the events on the previous selected room.
                _room.ParticipantAdded -= room_ParticipantAdded;

                //un-Register for the events on the previous selected room.
                _room.ParticipantRemoved -= room_ParticipantRemoved;

            }

            _room = room;

            //Register for the event raised when a user joins the room.
            _room.ParticipantAdded += new EventHandler<RoomParticipantsEventArgs>(room_ParticipantAdded);

            //Register for the event raised when a user leaves the room.
            _room.ParticipantRemoved += new EventHandler<RoomParticipantsEventArgs>(room_ParticipantRemoved);

            FillRoomRoster(_room);

        }
```

## Fill the participant list

The [Room.Participants](room-participants-property-microsoft-lync-model-room_2.md) property returns the current list of active chat room participants. Use this property to fill a list of participant names. The **IList\<**[Microsoft.Lync.Model.Room.RoomUser](roomuser-class-microsoft-lync-model-room_2.md)**\>** type is returned by the property. The [RoomUser.Uri](roomuser-uri-property-microsoft-lync-model-room_2.md) property returns a participant’s SIP address as a string. To get the participant display name, complete the following tasks with each [Microsoft.Lync.Model.Room.RoomUser](roomuser-class-microsoft-lync-model-room_2.md) in the list.

### To fill the participant list with participant names

1.  Verify that the [RoomUser.Uri](roomuser-uri-property-microsoft-lync-model-room_2.md) property is not null.

2.  Call the [ContactManager.GetContactByUri](contactmanager-getcontactbyuri-method-microsoft-lync-model_2.md) method and pass the SIP address in the first argument.
    
    An instance of [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) is returned.

3.  Get the display name of the participant by calling the [Contact.GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md) method, passing the [ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md)**.DisplayName** enumerator.
    
    The display name of the contact is returned.

4.  Add the participant’s name to the list.

### Code examples

The following example updates the participant list in the UI with the names of all active room participants. To call this method, pass [Room.Participants](room-participants-property-microsoft-lync-model-room_2.md) in the argument.

``` csharp
        /// <summary>
        /// Fills a list box with the display names of active room participants.
        /// </summary>
        /// <param name="users"></param>
        private void UpdateParticipantList(IList<RoomUser> users)
        {
            RoomRoster_Listbox.Items.Clear();

            //Iterate on list of room users
            foreach (RoomUser roomUser in users)
            {
                //Get the display name of a room user.
                if (roomUser.Uri != null)
                {
                    string displayName = _client.ContactManager.GetContactByUri(roomUser.Uri).GetContactInformation(ContactInformationType.DisplayName).ToString();

                    //Add the display name to the list box if it is not already in the list box.
                    if (!RoomRoster_Listbox.Items.Contains(displayName))
                    {
                        RoomRoster_Listbox.Items.Add(displayName);
                    }
                }
            }
        }
```

## Handle participant list events

Keep the UI room participant list current by handling the events in this section.

### Code examples

The following examples handle the [Room.ParticipantAdded](room-participantadded-event-microsoft-lync-model-room_2.md) and [Room.ParticipantRemoved](room-participantremoved-event-microsoft-lync-model-room_2.md) events.

``` csharp
        /// <summary>
        /// Handles the Room.ParticipantAdded event. The event is raised when a room member starts participating in a room.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void room_ParticipantAdded(object sender, RoomParticipantsEventArgs e)
        {
            try
            {
                //Invoke a method on the UI thread that updates the room participant list.
                RoomRoster_Listbox.Invoke(new FillRoomRosterCallback(this.FillRoomRoster), (Room)sender);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Exception in Room.ParticpantAdded : " + ex.Message);
            }

        }

        /// <summary>
        /// Handles the Room.ParticipantRemoved event. The event is raised when a room member stops participating in a room
        /// by signing out of Lync
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void room_ParticipantRemoved(object sender, RoomParticipantsEventArgs e)
        {
            try
            {
                //Invoke a method on the UI thread that updates the room participant list.
                RoomRoster_Listbox.Invoke(new FillRoomRosterCallback(this.FillRoomRoster), (Room)sender);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Exception in Room.ParticpantRemoved : " + ex.Message);
            }

        }
```

The following example is invoked on the UI thread by the platform thread when a participant collection event is raised.

``` csharp
        //Delegate that is invoked by the Room Manager followed room collection events
        private delegate void FillRoomRosterCallback(Room room);

        /// <summary>
        /// Invoked by platform thread when a participant is added or removed from a room
        /// </summary>
        /// <param name="room"></param>
        private void FillRoomRoster(Room room)
        {
            //Participants property count is zero if a user is not in the room.
            //If a user is not in a room, the first message that the user sends to a room 
            //causes the user to enter the room.
            if (room.Participants.Count > 0)
            {
                UpdateParticipantList(room.Participants);
            }
        }
```

## Code examples: Chat room participant list

The following example declares a Windows Form that displays the list of participants in a selected chat room from a signed-in user’s followed room list.

``` csharp
namespace GetParticipants
{
    partial class GetParticipants
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
            this.Participants_ListBox = new System.Windows.Forms.ListBox();
            this.Participants_Label = new System.Windows.Forms.Label();
            this.FollowedRoom_Numeric = new System.Windows.Forms.NumericUpDown();
            this.FollowedRoomTitle_Label = new System.Windows.Forms.Label();
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
            // Participants_ListBox
            // 
            this.Participants_ListBox.FormattingEnabled = true;
            this.Participants_ListBox.HorizontalScrollbar = true;
            this.Participants_ListBox.Location = new System.Drawing.Point(9, 153);
            this.Participants_ListBox.Name = "Participants_ListBox";
            this.Participants_ListBox.Size = new System.Drawing.Size(233, 160);
            this.Participants_ListBox.TabIndex = 40;
            // 
            // Participants_Label
            // 
            this.Participants_Label.AutoSize = true;
            this.Participants_Label.Location = new System.Drawing.Point(9, 128);
            this.Participants_Label.Name = "Participants_Label";
            this.Participants_Label.Size = new System.Drawing.Size(62, 13);
            this.Participants_Label.TabIndex = 41;
            this.Participants_Label.Text = "Participants";
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
            this.FollowedRoomTitle_Label.Size = new System.Drawing.Size(80, 13);
            this.FollowedRoomTitle_Label.TabIndex = 43;
            this.FollowedRoomTitle_Label.Text = "Followed Room";
            // 
            // GetParticipants
            // 
            this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(253, 326);
            this.Controls.Add(this.FollowedRoomTitle_Label);
            this.Controls.Add(this.FollowedRoom_Numeric);
            this.Controls.Add(this.Participants_Label);
            this.Controls.Add(this.Participants_ListBox);
            this.Controls.Add(this.label13);
            this.Controls.Add(this.panel1);
            this.Name = "GetParticipants";
            this.Text = "Get Room Participants";
            this.Load += new System.EventHandler(this.GetParticipants_Load);
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
        private System.Windows.Forms.ListBox Participants_ListBox;
        private System.Windows.Forms.Label Participants_Label;
        private System.Windows.Forms.NumericUpDown FollowedRoom_Numeric;
        private System.Windows.Forms.Label FollowedRoomTitle_Label;
    }
}
```

The following example interacts with the Windows Form declared by the previous example. This example fills a list with the participants in a selected chat room and then updates the list as the room roster changes.

``` csharp
using System;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Room;

namespace GetParticipants
{
    public partial class GetParticipants : Form
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
        public GetParticipants()
        {
            InitializeComponent();
        }

        /// <summary>
        /// Main form load event handler
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void GetParticipants_Load(object sender, EventArgs e)
        {
            try
            {
                //Get the lync client platform, the entry point for all group chat room related code.
                _client = LyncClient.GetClient();

                if (_client.RoomManager.State == RoomManagerState.Disabled)
                {
                    MessageBox.Show("Persistent Chat Server is not reachable. Quitting");
                }

                //Register for sign in/sign out events on the client
                _client.StateChanged += new EventHandler<ClientStateChangedEventArgs>(client_StateChanged);

                //If the client is signed in then load the followed room list
                if (_client.State == ClientState.SignedIn)
                {
                    //Set the numeric updown control maximum property to the number of 
                    //followed rooms in the followed room collection on the room manager.
                    FollowedRoom_Numeric.Maximum = _client.RoomManager.FollowedRooms.Count;
                    FollowedRoom_Numeric.Minimum = 1;
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
            //If the client has signed out then un-register for events on the room manager
            if (e.NewState == ClientState.SignedOut)
            {
                //Refresh the participant list with zero participants
                this.Invoke(new RefreshParticipantListDelegate(RefreshParticipantList));
            }

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

            //The _FollowedRoom is null when the form opens and a user has not
            //selected a room index from the control.
            if (_FollowedRoom != null)
            {
                //Unregister for participant events on the last room selected
                _FollowedRoom.ParticipantAdded -= _FollowedRoom_ParticipantAdded;
                _FollowedRoom.ParticipantRemoved -= _FollowedRoom_ParticipantRemoved;
            }
            //RoomManager.FollowedRooms property is null when the LyncClient.State == ClientState.SignedOut.
            //A user can sign out of Lync while this sample is running. If this happens, then the
            //FollowedRoom property is set to null
            if (_client.RoomManager.FollowedRooms == null)
            {
                return;
            }
            //Get the Room from the followed rooms collection at the index specified by the user
            _FollowedRoom = _client.RoomManager.FollowedRooms[Convert.ToInt32(upDown.Value - 1)];

            //Update the room title label on the form with the Title property of the selected room.
            FollowedRoomTitle_Label.Text = _FollowedRoom.Properties[RoomProperty.Title].ToString();

            //Register for participant events on the room
            _FollowedRoom.ParticipantAdded += _FollowedRoom_ParticipantAdded;
            _FollowedRoom.ParticipantRemoved += _FollowedRoom_ParticipantRemoved;

            //Refresh the participant list with the current participants of the selected room.
            RefreshParticipantList();
        }

        /// <summary>
        /// Handles the event raised when a user removes a room from their contact list.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _FollowedRoom_ParticipantRemoved(object sender, RoomParticipantsEventArgs e)
        {
            //Invoke the room participant list refresh delegate on the UI thread.
            Participants_ListBox.Invoke(new RefreshParticipantListDelegate(RefreshParticipantList));
        }

        /// <summary>
        /// Handles the event raised when a user adds a room to their contact list.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _FollowedRoom_ParticipantAdded(object sender, RoomParticipantsEventArgs e)
        {
           
            //Invoke the room participant list refresh delegate on the UI thread.
            Participants_ListBox.Invoke(new RefreshParticipantListDelegate(RefreshParticipantList));
        }

        private delegate void RefreshParticipantListDelegate();

        /// <summary>
        /// Refreshes the room participant list box on the UI
        /// </summary>
        private void RefreshParticipantList()
        {
            //Clear the contents of the room participant list box
            Participants_ListBox.Items.Clear();

            //verify that the FollowedRooms property is not null. 
            //When LyncClient.State == ClientState.SignedOut, FollowedRooms is null
            if (_client.RoomManager.FollowedRooms == null)
            {
                return;
            }

            //Declare a Contact that represents a room participant so that contact properties
            //can be read.
            Contact aParticipant;

            //Iterate on the collection of RoomUsers (particpiants)
            foreach (RoomUser user in _FollowedRoom.Participants)
            {
                //Get a Contact object by passing the room user's Uri to the contact manager.
                aParticipant = _client.ContactManager.GetContactByUri(user.Uri);
                if (_client.Self.Contact.Uri == user.Uri)
                {
                    //This is the local user
                    //Add the display name of the room user to the room participant list box.
                    Participants_ListBox.Items.Add("Self: " + aParticipant.GetContactInformation(ContactInformationType.DisplayName).ToString());

                }
                else
                {
                    //Add the display name of the room user to the room participant list box.
                    Participants_ListBox.Items.Add(aParticipant.GetContactInformation(ContactInformationType.DisplayName).ToString());
                }
            }
        }
    }
}
```

## Next steps

  - [Create a custom Persistent Chat client](create-a-custom-persistent-chat-client.md)

## Additional resources

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

