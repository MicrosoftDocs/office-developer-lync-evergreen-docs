---
title: 'How to: Find a chat room'
TOCTitle: 'How to: Find a chat room'
ms:assetid: 5cfc6e70-e254-457f-aae7-42b781224c4f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937327(v=office.15)
ms:contentKeyID: 50877162
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Find a chat room

Learn how to query for a Microsoft Lync 2013 Persistent Chat room by using methods in Microsoft Lync 2013 SDK.



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
Prerequisites<br />
Initial application state<br />
Get the room manager<br />
Get the chat rooms in a user’s contact list<br />
Query for a chat room<br />
Application state after completing all tasks<br />
Code examples: Persistent chat room query utility<br />
Next steps<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-display-a-list-192ef4d3">Display a list of persistent chat rooms that the user is following</a><br />
<br />
<a href="http://code.msdn.microsoft.com/lync-2013-query-for-a-cbc2e1f3">Query for a persistent chat room based on a partial name</a></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for finding a Persistent Chat room are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

Understanding the following concept is essential to adding Persistent Chat to an application.

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
<td><p><a href="room-manager.md">Room manager</a></p></td>
<td><p>Describes the role of the room manager object in querying for Persistent Chat rooms and getting a user’s followed chat rooms.</p></td>
</tr>
</tbody>
</table>

## Initial application state

Before you start the procedures in this topic, you must declare and initialize an instance of [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) for the application and the client must be signed in. For more information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

In addition to the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance, your application must declare a button, a text box, and a list. The text box accepts the title of the Persistent Chat room to query, the button starts the room query, and the list displays the results.

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

        /// <summary>
        /// A Dictionary of Room instances that represent the chat rooms which a user is following.
        /// </summary>
        private Dictionary<string, Room> _followedRoomsList = new Dictionary<string, Room>();

        /// <summary>
        /// A dictionary of all Room instances that are returned from a query for rooms whose title matches (or partially matches)
        /// a query string provided by the user.
        /// </summary>
        private Dictionary<string, Room> _roomQueryResults = new Dictionary<string, Room>();
```

## Get the room manager

The [Microsoft.Lync.Model.Room.RoomManager](https://msdn.microsoft.com/library/jj277050\(v=office.15\)) class lets you query or search for a chat room and get the collection of rooms that a user is following. You get a **RoomManager** instance and register for events on it before you can do any of the following tasks.

### To get the room manager

1.  Read the [Client.RoomManager](https://msdn.microsoft.com/library/jj276177\(v=office.15\)) property of the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance.

2.  Register for the [Client.StateChanged](https://msdn.microsoft.com/library/jj276368\(v=office.15\)) event.

3.  Register for the [LyncClient.ClientDisconnected](https://msdn.microsoft.com/library/jj277818\(v=office.15\)) event.

4.  Register for the [RoomManager.RoomManagerStateChanged](https://msdn.microsoft.com/library/jj274531\(v=office.15\)) event.

5.  Register for the [RoomManager.FollowedRoomAdded](https://msdn.microsoft.com/library/jj278058\(v=office.15\)) event.

6.  Register for the [RoomManager.FollowedRoomRemoved](https://msdn.microsoft.com/library/jj275522\(v=office.15\)) event.

If the [Client.State](https://msdn.microsoft.com/library/jj274837\(v=office.15\)) property returns the [ClientState](https://msdn.microsoft.com/library/jj275269\(v=office.15\))**.SignedIn** enumerator, then it calls the method described in the next section of this topic.

### Code example

The following example gets the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance and registers for events on the **LyncClient** and the **RoomManager**.

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
<td><p>The code in this example assumes that a user has signed in to Microsoft Lync 2013. For more information, see <a href="how-to-sign-a-user-in-to-lync.md">How to: Sign a user in to Lync</a>.</p></td>
</tr>
</tbody>
</table>

```csharp
        /// <summary>
        /// Gets the LyncClient instance that encapsulates the Lync client platform and registers
        /// for events on both LyncClient and the RoomManager. 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void btnGetLyncClient_Click(object sender, EventArgs e)
        {
            try
            {
                _client = LyncClient.GetClient();
                _client.StateChanged += new EventHandler<ClientStateChangedEventArgs>(client_StateChanged);
                _client.ClientDisconnected += new EventHandler(client_ClientDisconnected);
                _client.RoomManager.FollowedRoomAdded += new EventHandler<FollowedRoomsChangedEventArgs>(roomManager_FollowedRoomAdded);
                _client.RoomManager.FollowedRoomRemoved += new EventHandler<FollowedRoomsChangedEventArgs>(roomManager_FollowedRoomRemoved);
                _client.RoomManager.RoomManagerStateChanged += new EventHandler<RoomManagerStateChangedEventArgs>(roomManager_RoomManagerStateChanged);
                if (_client.State == ClientState.SignedIn)
                {
                    LoadInitialFollowedRoomList();
                }

            }
            catch(Exception ex)
            {
                MessageBox.Show(ex.Message);
            }
        }
```

## Get the chat rooms in a user’s contact list

To get the chat rooms that a user has added to the local contact list, you must make sure that the Lync 2013 client is signed in and the room manager is enabled. If these two conditions are met, read the [RoomManager.FollowedRooms](https://msdn.microsoft.com/library/jj276520\(v=office.15\)) property that returns a list of the rooms that the user is following.

### To get the user’s contact list chat rooms

1.  Check the state of the room manager. Proceed if the room manager is enabled.

2.  Check to see whether the [RoomManager.FollowedRooms](https://msdn.microsoft.com/library/jj276520\(v=office.15\)) property is null. If it's not null, proceed to the next step.

3.  Run a foreach loop over the collection of [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\)) objects returned by the **FollowedRooms** property.

4.  Read the [Room.Properties](https://msdn.microsoft.com/library/jj277330\(v=office.15\)) property enumerated by [RoomProperty](https://msdn.microsoft.com/library/jj293288\(v=office.15\))**.Title**.

5.  Add each room title string to the UI list so that a user can select a followed room to join.

6.  Add each room title and room to a dictionary where the room title is a key and the room is a value.
    
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
    <td><p>You can skip this step if you intend to iterate over the whole list of rooms returned by <a href="https://msdn.microsoft.com/library/jj276520(v=office.15)">RoomManager.FollowedRooms</a> to find a room whose title matches the title that a user selects from the UI list. The number of followed rooms in the list can be large, depending on how many rooms a user has added to his or her contact list.</p></td>
    </tr>
    </tbody>
    </table>

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
<td><p>The user is automatically joined to any chat room that is in the contact list at the time that the user signs in to Lync 2013. This means that if the user is a room member, the user can catch chat room message sending events as soon as the <a href="https://msdn.microsoft.com/library/jj274837(v=office.15)">Client.State</a> property returns <a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">ClientState</a><strong>.SignedIn</strong> and you have registered for the <a href="https://msdn.microsoft.com/library/jj277819(v=office.15)">Room.MessagesReceived</a> event on each followed room for which the user wants to receive a message notification.</p></td>
</tr>
</tbody>
</table>

### Handle followed room collection events

When the initial list of followed rooms is filled, you must handle two events on the room manager to keep the followed room list in synchronization with the user’s contact list. When the user adds a Persistent Chat room to the contact list, the [RoomManager.FollowedRoomAdded](https://msdn.microsoft.com/library/jj278058\(v=office.15\)) event is raised. When the user removes a room from the contact list, the [RoomManager.FollowedRoomRemoved](https://msdn.microsoft.com/library/jj275522\(v=office.15\)) event is raised. To handle either event, call a helper method that clears the followed room list and then refills the list from the current collection of followed rooms.

### Code example

The following example updates the application UI by using the current state of the client, gets the user’s URI, checks the state of the room manager, and adds the title of every room in the followed room collection to a list in the chat room UI.

```csharp
        /// <summary>
        /// Loads a UI list box with the room title strings of all Persistent Chat rooms that
        /// the user has "followed"... added to the contact list.
        /// These followed rooms are locally cached by the Lync client platform.
        /// </summary>
        private void LoadInitialFollowedRoomList()
        {
            try
            {

                //Check the state of the room manager. If the room manager is not enabled, then the Lync client is not signed in.
                //Room manager is enabled by the platform after the Lync client has signed in
                if (_client.RoomManager.State == RoomManagerState.Enabled &&  _client.RoomManager.FollowedRooms != null)
                {

                    //Iterate on the collection of Room instances that are followed by the user
                    foreach (Room followedRoom in _client.RoomManager.FollowedRooms)
                    {
                        //Add a room to the Dictionary<string,Microsoft.Lync.Model.Room.Room>() 
                        //Dictionary entry key is room title and value is room instance
                        _followedRoomsList.Add(followedRoom.Properties[RoomProperty.Title].ToString(), followedRoom);

                        //Add a followed room title to the UI list box of followed room titles.
                        //User selects a room title from the list box and the corresponding Room instance is obtained
                        //from the _followedRoomsList dictionary.
                        FollowedRooms_listbox.Items.Add(followedRoom.Properties[RoomProperty.Title].ToString());

                    }
                }

            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }

        }
```

The following examples handle the [RoomManager.FollowedRoomAdded](https://msdn.microsoft.com/library/jj278058\(v=office.15\)) and [RoomManager.FollowedRoomRemoved](https://msdn.microsoft.com/library/jj275522\(v=office.15\)) events.

```csharp
        /// <summary>
        /// Handles the event raised when a user adds a chat room to the contact list
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        public void roomManager_FollowedRoomAdded(object sender, FollowedRoomsChangedEventArgs e)
        {
            Room room=  e.Room;           

            //Invoke a delegate on the UI thread to re-fill the followed rooms list
            FollowedRooms_listbox.Invoke(new UpdatedFollowedRoomListCallback(this.UpdateFollowedRoomList), room);
        }
        /// <summary>
        /// Handles the event raised when a user removes a chat room from the contact list
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        public void roomManager_FollowedRoomRemoved(object sender, FollowedRoomsChangedEventArgs e)
        {
            Room room = e.Room;

            FollowedRooms_listbox.Invoke(new UpdatedFollowedRoomListCallback(this.UpdateFollowedRoomList), room);
        }
```

The following example adds a room title to the followed room list or removes the title, depending on which of the two previous event handlers invoked it.

```csharp
        //Delegate that is invoked by the Room Manager followed room collection events
        private delegate void UpdatedFollowedRoomListCallback(Room followedRoom);

        /// <summary>
        /// Updates the followed room list.
        /// This helper method is called when a room is added to the contact list or when a room is removed
        /// from the contact list.
        /// 
        /// If called on FollowedRoomAdded event, then the room is not in the list box and must
        /// be added to the list box.
        /// 
        /// If called on FollowedRoomRemoved event, then the room is in the list box and must be
        /// removed from the list box
        /// </summary>
        /// <param name="followedRoom"></param>
        private void UpdateFollowedRoomList(Room followedRoom)
        {
            if (_client.State == ClientState.SignedIn)
            {
                //If the followed room list box DOES NOT contain the title of the room in param 1 then 
                if (!FollowedRooms_listbox.Items.Contains(followedRoom.Properties[RoomProperty.Title].ToString()))
                {
                    //Add the room to the list box
                    FollowedRooms_listbox.Items.Add(followedRoom.Properties[RoomProperty.Title].ToString());

                    //Add the room title/room to the dictionary as key/value
                    _followedRoomsList.Add(followedRoom.Properties[RoomProperty.Title].ToString(), followedRoom);
                }

                 //The followed room IS IN the list box already
                else
                {
                    //Remove the room from the list box
                    FollowedRooms_listbox.Items.Remove(followedRoom.Properties[RoomProperty.Title].ToString());

                    //Remove the room from the dictionary
                    _followedRoomsList.Remove(followedRoom.Properties[RoomProperty.Title].ToString());
                }
            }
            else
            {
                //Client is signed out and the contact list is empty. Therefore, clear the followed room list
                FollowedRooms_listbox.Items.Clear();
            }
            
        }
```

## Query for a chat room

The next procedure assumes that a user wants to participate in a chat room that is not being followed. To get such a room, query for the desired room by a name or partial name provided by the user.

### To query for a chat room

1.  Clear the query results list from previous query results.

2.  Call the [RoomManager.BeginQueryRooms](https://msdn.microsoft.com/library/jj277979\(v=office.15\)) method and pass a full or partial room title to query for, the search mode, and a method to be called when the query is completed.
    
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
    <td><p>The regular search mode searches room titles while the extended search mode searches among room titles and room descriptions.</p></td>
    </tr>
    </tbody>
    </table>

3.  Get the query results by calling the [RoomManager.EndQueryRooms](https://msdn.microsoft.com/library/jj267955\(v=office.15\)) method.
    
    A list of rooms is returned from this method call.

4.  Iterate on the room list and add the title of each room to the list that you added to your UI.

5.  Add the title of a room and a reference to the room as a key/value pair to an IDictionary\<string, [Microsoft.Lync.Model.Room.Room](https://msdn.microsoft.com/library/jj266467\(v=office.15\))\> class field.
    
    When a user selects a room title from the list, you get the room out of the dictionary by getting the value by the title key string.

### Code example

The following example starts an asynchronous query for a chat room based on a name supplied by a user.

```csharp
        /// <summary>
        /// Query for a chat room based on a partial or full room title.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void btnSearchRoom_Click(object sender, EventArgs e)
        {
            //Clear the UI query results text box of the results for the previous query.
            QueryResults_Listbox.Items.Clear();
            try
            {

                //Start asynchronous room query with the string supplied by the user in the UI text entry field.
                _client.RoomManager.BeginQueryRooms(txtSearchRoom.Text, RoomSearchModeType.Regular, QueryRoomsCallback, null);

             
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }
            
        }
```

The following example declares private delegates that are invoked on the UI thread by platform thread callback methods.

```csharp
        private delegate void UpdateRoomUri_Textbox(string roomUri);
        public delegate void UpdateSearchRoomsResultCallback(string roomName);  
```

The following example is called by the platform when the chat room query operation is finished.

```csharp
       /// <summary>
        /// Handles the asynchronous callback from the Lync API platform when the room query operation is completed
        /// </summary>
        /// <param name="ar"></param>
        private void QueryRoomsCallback(IAsyncResult ar)
        {
            try
            {
                //Get the room list that is the result of the query.
                IList<Room> searchResult = _client.RoomManager.EndQueryRooms(ar);

                //Display the room title of the first room in the results list. 
                //QueryRoomsCallback is invoked on the platform thread which does not own the room Uri text box. The room Uri text box invokes a
                //delegate on the UI thread.
                roomUri_Textbox.Invoke(new UpdateRoomUri_Textbox(roomUri_TextboxUpdate), searchResult[0].Properties[RoomProperty.Uri].ToString());

                //Iterate on the list of chat rooms returned by the query and add each room title to a query results list box on the UI
                foreach (Room room in searchResult)
                {

                    //Invoke a delegate on the UI thread that updates a list box with the title of a chat room.
                    QueryResults_Listbox.Invoke(new UpdateSearchRoomsResultCallback(this.UpdateSearchRoomResults), room.Properties[RoomProperty.Title].ToString());

                    //Add the title of a room as dictionary key and the room itself as a dictionary value. 
                    _roomQueryResults.Add(room.Properties[RoomProperty.Title].ToString(), room);
                }
            }

            //An exception is raised if the chat room query did not return any rooms. No rooms are returned when the query string does
            //not match any chat room created on Persistent Chat server.
            catch (Exception ex)
            {
                //Display the exception message.
                MessageBox.Show("Exception on EndQueryRooms " + ex.Message);
            }
        }
```

The following examples comply with the delegate signatures in the previous delegate declarations. The example methods are invoked by the previous example and update UI controls to display the results of a room query.

```csharp
        /// <summary>
        /// Invoked to update a UI label text property with the Uri of a chat room to be joined.
        /// </summary>
        /// <param name="uri"></param>
        private void roomUri_TextboxUpdate(string uri)
        {
            roomUri_Textbox.Text = uri;
        }
        /// <summary>
        /// Invoked to update a UI list box with the title of a room
        /// </summary>
        /// <param name="roomTitle"></param>
        private void UpdateSearchRoomResults(string roomTitle)
        {
            QueryResults_Listbox.Items.Add(roomTitle);
        }
```

## Application state after completing all tasks

The user has joined a chat room and can start to read messages posted to the chat room, post messages to the chat room, and see a roster of participants in the room. You can verify this state by reading the [Room.JoinedState](https://msdn.microsoft.com/library/jj267006\(v=office.15\)) and [Room.Participants](https://msdn.microsoft.com/library/jj293558\(v=office.15\)) properties on the room obtained from the appropriate example dictionary. If the joined state is [RoomJoinState](https://msdn.microsoft.com/library/jj276163\(v=office.15\))**.Success** and the **Participants** property returns a collection of [Microsoft.Lync.Model.Room.RoomUser](https://msdn.microsoft.com/library/jj293507\(v=office.15\)) instances, the user can participate in the room. You should now receive the events that you registered to receive for all chat rooms.

  - For information about displaying a chat room roster, see [How to: View chat room participants](how-to-view-chat-room-participants.md).

  - For information about obtaining messages that are posted to the chat room, see [How to: Read messages sent to a chat room](how-to-read-messages-sent-to-a-chat-room.md).

  - For information about posting messages to a chat room, see [How to: Send a message to a chat room](how-to-send-a-message-to-a-chat-room.md).

  - For information about filtering and formatting messages that are pending a post to a chat room, see [How to: Filter an outgoing message from a local user to a chat room](how-to-filter-an-outgoing-message-from-a-local-user-to-a-chat-room.md).

## Code examples: Persistent chat room query utility

The following example declares a Windows Form that accepts a string as a partial room name and returns a list of Persistent Chat rooms whose title contains the search string.

    namespace RoomQuery
    {
        partial class RoomQuery
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
                this.QueriedRooms_ListBox = new System.Windows.Forms.ListBox();
                this.RoomQueryString_TextBox = new System.Windows.Forms.TextBox();
                this.label2 = new System.Windows.Forms.Label();
                this.StartQuery_Button = new System.Windows.Forms.Button();
                this.panel1.SuspendLayout();
                this.SuspendLayout();
                // 
                // panel1
                // 
                this.panel1.Controls.Add(this.LyncClientState_Label);
                this.panel1.Controls.Add(this.label1);
                this.panel1.Location = new System.Drawing.Point(21, 3);
                this.panel1.Name = "panel1";
                this.panel1.Size = new System.Drawing.Size(276, 23);
                this.panel1.TabIndex = 1;
                // 
                // lblLyncClient
                // 
                this.LyncClientState_Label.AutoSize = true;
                this.LyncClientState_Label.Location = new System.Drawing.Point(111, 4);
                this.LyncClientState_Label.Name = "lblLyncClient";
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
                // QueriedRooms_ListBox
                // 
                this.QueriedRooms_ListBox.FormattingEnabled = true;
                this.QueriedRooms_ListBox.Location = new System.Drawing.Point(21, 80);
                this.QueriedRooms_ListBox.Name = "QueriedRooms_ListBox";
                this.QueriedRooms_ListBox.Size = new System.Drawing.Size(276, 186);
                this.QueriedRooms_ListBox.TabIndex = 53;
                // 
                // RoomQueryString_TextBox
                // 
                this.RoomQueryString_TextBox.Location = new System.Drawing.Point(103, 48);
                this.RoomQueryString_TextBox.Name = "RoomQueryString_TextBox";
                this.RoomQueryString_TextBox.Size = new System.Drawing.Size(100, 20);
                this.RoomQueryString_TextBox.TabIndex = 54;
                // 
                // label2
                // 
                this.label2.AutoSize = true;
                this.label2.Location = new System.Drawing.Point(18, 51);
                this.label2.Name = "label2";
                this.label2.Size = new System.Drawing.Size(76, 13);
                this.label2.TabIndex = 55;
                this.label2.Text = "Room to query";
                // 
                // StartQuery_Button
                // 
                this.StartQuery_Button.Location = new System.Drawing.Point(222, 48);
                this.StartQuery_Button.Name = "StartQuery_Button";
                this.StartQuery_Button.Size = new System.Drawing.Size(75, 23);
                this.StartQuery_Button.TabIndex = 56;
                this.StartQuery_Button.Text = "Go";
                this.StartQuery_Button.UseVisualStyleBackColor = true;
                this.StartQuery_Button.Click += new System.EventHandler(this.StartQuery_Button_Click);
                // 
                // RoomQuery
                // 
                this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);
                this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
                this.ClientSize = new System.Drawing.Size(324, 292);
                this.Controls.Add(this.StartQuery_Button);
                this.Controls.Add(this.label2);
                this.Controls.Add(this.RoomQueryString_TextBox);
                this.Controls.Add(this.QueriedRooms_ListBox);
                this.Controls.Add(this.panel1);
                this.Name = "RoomQuery";
                this.Text = "Simple Group Chat";
                this.Load += new System.EventHandler(this.RoomQuery_Load);
                this.panel1.ResumeLayout(false);
                this.panel1.PerformLayout();
                this.ResumeLayout(false);
                this.PerformLayout();
    
            }
    
            #endregion
    
            private System.Windows.Forms.Panel panel1;
            private System.Windows.Forms.Label LyncClientState_Label;
            private System.Windows.Forms.Label label1;
            private System.Windows.Forms.ListBox QueriedRooms_ListBox;
            private System.Windows.Forms.TextBox RoomQueryString_TextBox;
            private System.Windows.Forms.Label label2;
            private System.Windows.Forms.Button StartQuery_Button;
        }
    }

The following example is the interaction logic for the Form declared in the previous example.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Room;
using System.Collections;

namespace RoomQuery
{
    public partial class RoomQuery : Form
    {

        /// <summary>
        /// The LyncClient class instance that encapsulates the Lync client platform
        /// </summary>
        private LyncClient _client=null;

        /// <summary>
        /// A dictionary of all Room instances that are returned from a query for rooms whose title matches (or partially matches)
        /// a query string provided by the user.
        /// </summary>
        private Dictionary<string, Room> _roomQueryResults = new Dictionary<string, Room>();

        /// <summary>
        /// Simple chat window constructor
        /// </summary>
        public RoomQuery()
        {
            InitializeComponent();
        }

        /// <summary>
        /// Form constructor
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void RoomQuery_Load(object sender, EventArgs e)
        {
            
            try
            {
                //Get the API entry point
                _client = LyncClient.GetClient();

                //Register for the state changed event on the lync client platform.
                _client.StateChanged += new EventHandler<ClientStateChangedEventArgs>(client_StateChanged);
                _client.ClientDisconnected += new EventHandler(client_ClientDisconnected);

                //Set the enable state of the query start button based on the state of the RoomManager.
                EnableDisableStartQueryButton();

                //Register for room manager state event. If room manager is disabled, disable the "Go" button on the UI so that
                //a user does not attempt to query the room manager for a room.
                if (_client.RoomManager.State == RoomManagerState.Disabled)
                {
                    MessageBox.Show("Persistent Chat Server is not reachable. Quitting");
                }
                _client.RoomManager.RoomManagerStateChanged += roomManager_RoomManagerStateChanged;

                //Display the current sign in state of the Lync client.
                RefreshClientStateLabel();
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }

            
        }

        /// <summary>
        /// Handles the event raised if the state of the RoomManager changes.
        /// Response to state change i
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void roomManager_RoomManagerStateChanged(object sender, RoomManagerStateChangedEventArgs e)
        {
            //Invoke a delegate on UI thread to enable or disable room query start button
            StartQuery_Button.Invoke(new EnableDisableStartQueryButtonDelegate(EnableDisableStartQueryButton));
        }

        private delegate void EnableDisableStartQueryButtonDelegate();

        
        /// <summary>
        /// Enables or disables the room query button based on the current state of the RoomManager
        /// </summary>
        private void EnableDisableStartQueryButton()
        {
            if (_client.RoomManager.State == RoomManagerState.Enabled)
            {
                StartQuery_Button.Enabled = true;
            }
            else
            {
                StartQuery_Button.Enabled = false;
            }
        }

        /// <summary>
        /// Handles the client state change event
        /// Updates the client state label on the UI
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        public void client_StateChanged(object sender, ClientStateChangedEventArgs e)
        {
            //Invoke delegate on UI thread that updates client state label
            this.Invoke(new RefreshClientStateLabelDelegate(RefreshClientStateLabel));

            //Invoke a delegate on UI thread to enable or disable room query start button
            StartQuery_Button.Invoke(new EnableDisableStartQueryButtonDelegate(EnableDisableStartQueryButton));

        }

        public void client_ClientDisconnected(object sender, EventArgs e)
        {
            //Invoke delegate on UI thread that updates client state label
            this.Invoke(new RefreshClientStateLabelDelegate(RefreshClientStateLabel));
        }

        private delegate void RefreshClientStateLabelDelegate();
        /// <summary>
        /// Updates client state label based on current state of the client
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
        /// Handles the click event on the StartRoomQuery button
        /// If the RoomManager.State is not RoomManagerState.Enbled, the application logic
        /// disables the StartRoomQuery button.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void StartQuery_Button_Click(object sender, EventArgs e)
        {
            //Clear the current contents of the room listbox
             QueriedRooms_ListBox.Items.Clear();

            //Start asynchronous room query operation with the room name or partial room name 
            //entered by the user.
             _client.RoomManager.BeginQueryRooms(RoomQueryString_TextBox.Text, RoomSearchModeType.Regular, RoomQueryCallback, null);
        }

        /// <summary>
        /// Invoked by the platform when the room query operation finishes. 
        /// </summary>
        /// <param name="ar"></param>
        private void RoomQueryCallback(System.IAsyncResult ar)
        {
            //Get the results of the query.
           IList<Room> roomResults = _client.RoomManager.EndQueryRooms(ar);

            //Load the resulting room collection into the room list on the UI
           foreach (Room r in roomResults)
           {
               //If this room is not already in the results dictionary then add it to the dictionary.
               if (!_roomQueryResults.ContainsKey(r.Properties[RoomProperty.Title].ToString()))
               {
                   //Room title and room are key/value pair. Added to dictionary to be retrieved based on 
                   //room title when user selects a room title from the UI list.
                   _roomQueryResults.Add(r.Properties[RoomProperty.Title].ToString(), r);

                   //Invoke a delegate on the UI thread to add a room to the room list on the UI
                   QueriedRooms_ListBox.Invoke(new AddToQueriedRoomsListDelegate(this.AddToQueriedRoomsList), r.Properties[RoomProperty.Title].ToString());
               }
           }
        }

        private delegate void AddToQueriedRoomsListDelegate(string roomTitle);

        /// <summary>
        /// Adds the title of a room to the room list on the UI
        /// </summary>
        /// <param name="roomTitle"></param>
        private void AddToQueriedRoomsList(string roomTitle)
        {
            QueriedRooms_ListBox.Items.Add(roomTitle);
        }
    }
}
```

## Next steps

  - [How to: Send a message to a chat room](how-to-send-a-message-to-a-chat-room.md)

  - [How to: Read messages sent to a chat room](how-to-read-messages-sent-to-a-chat-room.md)

  - [How to: View chat room participants](how-to-view-chat-room-participants.md)

## See also

  - [What you can do with Persistent Chat](what-you-can-do-with-persistent-chat.md)

  - [Code samples: Lync SDK](code-samples-lync-sdk.md)

