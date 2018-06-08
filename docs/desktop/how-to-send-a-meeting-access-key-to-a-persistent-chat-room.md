---
title: 'How to: Send a meeting access key to a Persistent Chat room'
TOCTitle: 'How to: Send a meeting access key to a Persistent Chat room'
ms:assetid: abb71964-129c-4540-96f1-0854c928cdc6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933163(v=office.15)
ms:contentKeyID: 50877303
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Send a meeting access key to a Persistent Chat room

Learn how to use Microsoft Lync 2013 SDK to start a Microsoft Lync 2013 meet-now audio conference. You can then send the meeting access key to a Persistent Chat room so that the room participants can join the conference by clicking a meeting URL in the chat room message or by calling an auto-attendant telephone number.

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
Prerequisites<br />
Start a new meet-now meeting<br />
Post the meeting access key to a chat room<br />
Code examples: Meet-now access manager<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for sending a meeting access key are as follow:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Start a new meet-now meeting

Use Lync 2013 API automation to start an audio conference that people can join from a telephone or a Lync 2013 client on a computer on either side of a corporate firewall.

### To start the meeting

1.  Call the static [LyncClient.GetAutomation](https://msdn.microsoft.com/en-us/library/jj266970\(v=office.15\)) method to obtain the [Microsoft.Lync.Model.Extensibility.Automation](https://msdn.microsoft.com/en-us/library/jj293816\(v=office.15\)) object.

2.  Call the [Automation.BeginMeetNow](https://msdn.microsoft.com/en-us/library/jj277161\(v=office.15\)) method to start the meet-now meeting.

3.  In the callback method or lambda expression passed as the second argument in the previous method call, call the [Automation.EndMeetNow](https://msdn.microsoft.com/en-us/library/jj278119\(v=office.15\)) method and cache the [Microsoft.Lync.Model.Extensibility.ConversationWindow](https://msdn.microsoft.com/en-us/library/jj293606\(v=office.15\)) object that encapsulates the new meeting.
    
    ``` csharp
            /// <summary>
            /// Starts a new meeting by using automation
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void StartMeeting_Button_Click_1(object sender, RoutedEventArgs e)
            {
                if (_Automation != null)
                {
                    _Automation.BeginMeetNow((ar) => 
                    {
                      _ConversationWindow = _Automation.EndMeetNow(ar);
                      _Conversation = _ConversationWindow.Conversation;
                      //Watch for changes in conference properties
                      _Conversation.PropertyChanged += _Conversation_PropertyChanged;
    
                      //Watch for participants added to meeting (Lobby)
                      _Conversation.ParticipantAdded += _Conversation_ParticipantAdded;
    
                    },
                    null);
                }
            }
    ```

4.  Get the [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) object and register for the [Conversation.PropertyChanged](https://msdn.microsoft.com/en-us/library/jj276330\(v=office.15\)) event so that you are notified when the access key property is available.

## Post the meeting access key to a chat room

Now that you have the access key to the new audio conference, you can post the key to a Persistent Chat room as a room message. Other chat room users will be able to click the internal and external meeting URL strings or dial one of the auto-attendant telephone numbers and join the audio conference.

### To get the access key

1.  In the [Conversation.PropertyChanged](https://msdn.microsoft.com/en-us/library/jj276330\(v=office.15\)) event callback method, read the [ConversationPropertyChangedEventArgs.Property](https://msdn.microsoft.com/en-us/library/jj277087\(v=office.15\)) to get the conversation property that has changed.
    
    If the changed property is the [ConversationProperty](https://msdn.microsoft.com/en-us/library/jj266982\(v=office.15\))**.ConferenceAccessInformation** property, continue this procedure.

2.  Get the [Microsoft.Lync.Model.Conversation.ConferenceAccessInformation](https://msdn.microsoft.com/en-us/library/jj266047\(v=office.15\)) object that encapsulates the access key.
    
    The following example reads the event data value to get the conference access key.
    
    ``` csharp
                            ConferenceAccessInformation conferenceAccess = (ConferenceAccessInformation)e.Value;
    ```

3.  Read each property in the **ConferenceAccessInformation** object and form a string to be posted to the chat room.
    
    The following example handles the **PropertyChanged** event on the conversation, gets all components of the access key, and stores them in a **StringBuilder** to be used when the user clicks the **Post Access Key** button in the UI.
    
    ``` csharp
            /// <summary>
            /// Handles event raised when interesting conversation properties changed. 
            /// Handler is only interested in conference properties
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void _Conversation_PropertyChanged(object sender, ConversationPropertyChangedEventArgs e)
            {
                Conversation conference = (Conversation)sender;
                LoadTextBoxDelegate textBoxDelegate = new LoadTextBoxDelegate(LoadTextBox);
    
                switch (e.Property)
                { 
                    case ConversationProperty.ConferenceAccessInformation:
    
                        try
                        {
                            _MeetingKey = new StringBuilder();
    
                            //These properties are used to invite people by creating an email (or text message, or IM)
                            //and adding the dial in number, external Url, internal Url, and conference Id
                            ConferenceAccessInformation conferenceAccess = (ConferenceAccessInformation)e.Value;
    
                            _MeetingKey.Append("Meeting Id: " + conferenceAccess.Id);
                            _MeetingKey.Append(System.Environment.NewLine);
    
                            _MeetingKey.Append(conferenceAccess.AdmissionKey);
                            _MeetingKey.Append(System.Environment.NewLine);
    
                            string[] attendantNumbers = (string[])conferenceAccess.AutoAttendantNumbers;
    
                            StringBuilder sb2 = new StringBuilder();
                            sb2.Append(System.Environment.NewLine);
                            foreach (string aNumber in attendantNumbers)
                            {
                                sb2.Append("\t\t" + aNumber);
                                sb2.Append(System.Environment.NewLine);
                            }
    
                            _MeetingKey.Append("Auto attendant numbers:" + sb2.ToString());
                            _MeetingKey.Append(System.Environment.NewLine);
    
                            _MeetingKey.Append("External Url: " + conferenceAccess.ExternalUrl);
                            _MeetingKey.Append(System.Environment.NewLine);
    
                            _MeetingKey.Append("Inner Url: " + conferenceAccess.InternalUrl);
                            _MeetingKey.Append(System.Environment.NewLine);
    
                            this.Dispatcher.Invoke(
                                new EnableDisableButtonDelegate(EnableDisableButton),
                                new object[] { PostMeetingKey_Button, true });
    
                            this.Dispatcher.Invoke(
                                textBoxDelegate,
                                new object[] { ConferenceAccessInformation_block, _MeetingKey.ToString() });
                        }
                        catch (LyncClientException lce)
                        {
                            System.Diagnostics.Debug.WriteLine("Exception on ConferenceAccessInformation changed " + lce.Message);
                        }
                        break;
                }
    
            }
    ```

### To post the access key to a chat room

1.  Get the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) as the entry point to the managed object model.

2.  Verify that the user is following at least one chat room by reading the **Count** property of the [RoomManager.FollowedRooms](https://msdn.microsoft.com/en-us/library/jj276520\(v=office.15\)) collection.

3.  Get one of the followed rooms.
    
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
    <td><p>This example arbitrarily gets the first followed room but you should iterate on the room collection and look for a room whose title matches one that a user selects.</p></td>
    </tr>
    </tbody>
    </table>

4.  Send the access key to the selected chat room by calling the [Room.BeginSendMessage](https://msdn.microsoft.com/en-us/library/jj293980\(v=office.15\)) method.
    
    ``` csharp
            /// <summary>
            /// Posts the meeting access key to the first followed chat room in the local
            /// user's folled chat room collection
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void PostMeetingKey_Button_Click_1(object sender, RoutedEventArgs e)
            {
                try
                {
                    //get the API entry point
                    LyncClient lyncClient = LyncClient.GetClient();
    
                    //If the user has any followed rooms then get the first one
                    if (lyncClient.RoomManager.FollowedRooms.Count > 0)
                    {
                        //get the first followed chat room
                        Room myRoom = lyncClient.RoomManager.FollowedRooms[0];
    
                        //Create a dictionary to hold the MIME type of the chat room message and the
                        //actual message text (the meet now access key)
                        Dictionary<RoomMessageFormat, string> messageDictionary = new Dictionary<RoomMessageFormat, string>();
                        messageDictionary.Add(RoomMessageFormat.PlainText, _MeetingKey.ToString());
    
                        //Send the message to the chat room as a story
                        myRoom.BeginSendStoryMessage(
                            messageDictionary,
                            "Meeting has started",
                            (ar) =>
                            {
                                try
                                {
                                    myRoom.EndSendStoryMessage(ar);
                                    System.Diagnostics.Debug.WriteLine(
                                        "Succeeded on post story message to " +
                                        myRoom.Properties[RoomProperty.Title].ToString() );
                                }
                                catch (LyncClientException lce)
                                {
                                    System.Diagnostics.Debug.WriteLine(
                                        "Lync client exception on post story message to " + 
                                        myRoom.Properties[RoomProperty.Title].ToString() + 
                                        " " + 
                                        lce.Message);
                                }
                            }
                            ,
                            null);
                    }
                }
                catch (ClientNotFoundException)
                {
                    System.Diagnostics.Debug.WriteLine("Client is not running");
                }
                catch (LyncClientException lce)
                {
                    System.Diagnostics.Debug.WriteLine("Lync client exception on GetClient() " + lce.Message);
                }
    
            }
    ```

## Code examples: Meet-now access manager

The meet-now access manager uses automation to start a new meet-now meeting with no participants. It launches a Lync 2013 conversation window, which requires that the Lync UI is not suppressed. After the meeting is started and the access key is shown in the middle text box, a user can click the **Post Meeting Key** button to post the key to the first followed Persistent Chat room.

Figure 1 shows the meet now access manager. This application starts new meet-now meetings and lets a user post the access key to a followed chat room, set the meeting access type, and let users in from the meeting lobby.

![Meeting access manager with access key shown](images/JJ933163.LyncClientSDK_MeetingAccessKey(Office.15).jpg "Meeting access manager with access key shown")

``` xaml
<Window x:Class="MeetingAccess.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Meet-now Access Manager" Height="690" Width="510" Loaded="Window_Loaded_1">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="10"/>
            <RowDefinition Height="350"/>
            <RowDefinition Height="40*"/>
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="146"/>
            <ColumnDefinition Width="359"/>
            <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <Grid Grid.Row="2" Grid.Column="1">
            <Grid.RowDefinitions>
                <RowDefinition Height="116"/>
                <RowDefinition Height="92*"/>
                <RowDefinition/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="355"/>
                <ColumnDefinition/>
            </Grid.ColumnDefinitions>
            <StackPanel Grid.Row="0" Grid.Column="0" Orientation="Vertical" HorizontalAlignment="Left" Width="355">
                <Separator Margin="0,4,0,1"/>
                <Label Content="Lobby" Width="50" Height="26" HorizontalAlignment="Left"/>
                <ListBox Name="Lobby_ListBox" Width="340" Height="70" Margin="5,1,10,10" HorizontalAlignment="Left"/>
                <Separator />
            </StackPanel>
            <StackPanel Grid.Row="1">
                <Label Content="Meeting roster" />
                <ListBox Name="MeetingRoster_Listbox" Grid.Row="1" Grid.Column="0" Margin="5,1,10,10" Height="146"/>
            </StackPanel>
        </Grid>
        <StackPanel Grid.Row="1" Grid.Column="0">
            <Button Name="StartMeeting_Button" Content="Start Meeting" Width="120" Margin="10,10,10,2" Click="StartMeeting_Button_Click_1"/>
            <Button Name="EndMeeting_Button" Content="End Meeting" Width="120" Margin="10,2,10,2" Click="EndMeeting_Button_Click_1"/>
            <Label Content="Admission Types:" Margin="10,2,10,2"/>
            <RadioButton Name="Anon_Radio" Content="Anonymous"  Margin="10,2,2,2"/>
            <RadioButton Name="Closed_Radio" Content="Closed"  Margin="10,2,2,2"/>
            <RadioButton Name="Locked_Radio" Content="Locked"  Margin="10,2,2,2"/>
            <RadioButton Name="Open_Radio" Content="Open"  Margin="10,2,2,2"/>
            <Button Name="SetAccessType_Button" Content="Set access type" Margin="10,10,10,2" Click="SetAccessType_Button_Click_1" />
            <Button Name="LockMeeting_Button" Content="Lock meeting" Margin="10,2,10,2" Click="LockMeeting_Button_Click_1"/>
            <Label Content="Chat rooms:"/>
            <ListBox Name="RoomList_ListBox" Height="60" Margin="10,2,10,2"/>
            <Button Name="PostMeetingKey_Button" Content="Post Meeting Key" Width="120" Margin="10,10,10,2" IsEnabled="False" Click="PostMeetingKey_Button_Click_1"/>
        </StackPanel>
        <Grid Name="ConferenceInfoGrid" Grid.Column="1" Grid.Row="1" Margin="0,7,10,16" Grid.RowSpan="1">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="353"/>
                <ColumnDefinition/>
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition Height="38"/>
                <RowDefinition Height="200*"/>
            </Grid.RowDefinitions>
            <Label Content="Acccepting participant" Grid.Row="0" Grid.Column="0" Height="28" Width="180" HorizontalAlignment="Left" VerticalAlignment="Top"/>
            <StackPanel Grid.Row="1" Orientation="Vertical">
                <TextBlock Name="ConferenceAcceptingParticipant_block" Margin="5,6,2,1" Grid.Row="0" Grid.Column="0"/>
                <Label Content="Meeting access key" Grid.Row="1" Grid.Column="0"/>
                <TextBox Name="ConferenceAccessInformation_block" Margin="5,5,10,5" Grid.Row="1" Grid.Column="0" Height="197"/>

            </StackPanel>

        </Grid>
        <StackPanel Grid.Row="2" Grid.Column="0" Margin="0,2,0,0">
            <Separator />
            <Button Name="AdmitAll_Button" Content="Admit All" Margin="16,2,10,2" Click="AdmitAll_Button_Click_1"/>
            <Button Name="AdmitOne_Button" Content="Admit Selected" Margin="16,2,10,2" Click="AdmitOne_Button_Click_1"/>
            <Button Name="DenyOne_Button" Content="Deny Selected" Margin="16,2,10,2" Click="DenyOne_Button_Click_1"/>
            <Button Name="DenyAll_Button" Content="Deny All" Margin="16,2,10,12" Click="DenyAll_Button_Click_1"/>
            <Separator />
            <Button Name="PinVideo_Button" Content="Pin video" Click="PinVideo_Button_Click_1"  Margin="16,12,10,2"/>
            <Button Name="LockVideo_Button" Content="Lock video" Click="LockVideo_Button_Click_1"  Margin="16,2,10,2"/>
            <Button Name="MakePresenter_Button" Content="Make presenter" Click="MakePresenter_Button_Click_1"  Margin="16,2,10,2"/>
            <Button Name="MakeParticipant_Button" Content="Make participant" Click="MakeParticipant_Button_Click_1"  Margin="16,2,10,2"/>

        </StackPanel>
    </Grid>
</Window>
```

The following example is the interaction logic for the WPF window declared in the previous example.

``` csharp
using System.Windows;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Extensibility;
using Microsoft.Lync.Model.Room;
using System.Text;
using System.Security.Principal;
using System.Collections.Generic;

namespace MeetingAccess
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        Automation _Automation;
        Conversation _Conversation;
        ConversationWindow _ConversationWindow;
        StringBuilder _MeetingKey;

        public MainWindow()
        {
            InitializeComponent();
        }

        /// <summary>
        /// Starts a new meeting by using automation
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void StartMeeting_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Automation != null)
            {
                _Automation.BeginMeetNow((ar) => 
                {
                  _ConversationWindow = _Automation.EndMeetNow(ar);
                  _Conversation = _ConversationWindow.Conversation;
                  //Watch for changes in conference properties
                  _Conversation.PropertyChanged += _Conversation_PropertyChanged;
                  _Conversation.StateChanged += _Conversation_StateChanged;

                  //MeetingRoster_Listbox
                  //Add the user's name to the lobby listbox
                  this.Dispatcher.Invoke(
                      new LoadListBoxDelegate(LoadListBox),
                      new object[] {MeetingRoster_Listbox, 
                        _Conversation.SelfParticipant.Contact.GetContactInformation(
                        ContactInformationType.DisplayName).ToString()});

                  //Watch for participants added to meeting (Lobby)
                  _Conversation.ParticipantAdded += _Conversation_ParticipantAdded;

                },
                null);
            }
        }

        void _Conversation_StateChanged(object sender, ConversationStateChangedEventArgs e)
        {
            if (e.NewState == ConversationState.Terminated)
            {
                _Conversation.PropertyChanged -= _Conversation_PropertyChanged;
                _Conversation.PropertyChanged -= _Conversation_PropertyChanged;
            }
        }

        /// <summary>
        /// Handles event raised when a participant is added to meeting. If waiting in lobby, adds
        /// user name to lobby list
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _Conversation_ParticipantAdded(object sender, ParticipantCollectionChangedEventArgs e)
        {
            //Watch for changes in participant property (IsInLobby)
            e.Participant.PropertyChanged += Participant_PropertyChanged;
            bool isInLobby = false;
            try
            {
                isInLobby = (bool)e.Participant.Properties[ParticipantProperty.IsInLobby];
            }
            catch (System.NullReferenceException) { }
            //Check to see if participant is in lobby now
            if (isInLobby == true)
            {
                //Add the user's name to the lobby listbox
                this.Dispatcher.Invoke(
                    new LoadListBoxDelegate(LoadListBox),
                    new object[] {Lobby_ListBox, 
                        e.Participant.Contact.GetContactInformation(
                        ContactInformationType.DisplayName).ToString()});
            }
            else
            { 
                //MeetingRoster_Listbox
                //Add the user's name to the lobby listbox
                this.Dispatcher.Invoke(
                    new LoadListBoxDelegate(LoadListBox),
                    new object[] {MeetingRoster_Listbox, 
                        e.Participant.Contact.GetContactInformation(
                        ContactInformationType.DisplayName).ToString()});
            }
        }

        /// <summary>
        /// Handles event raised when participant property (IsInLobby) changes
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Participant_PropertyChanged(object sender, ParticipantPropertyChangedEventArgs e)
        {
            Participant participant = (Participant)sender;

            //If the IsInLobby property changes and user is no longer in the lobby
            //then remove the user's name from the lobby list
            if (e.Property == ParticipantProperty.IsInLobby && (bool)e.Value == false)
            {
                string displayName = participant.Contact.GetContactInformation(
                    ContactInformationType.DisplayName).ToString();

                this.Dispatcher.Invoke(new RemoveListItemDelegate(RemoveListItem), 
                    new object[] { Lobby_ListBox, displayName });


                //MeetingRoster_Listbox
                //Add the user's name to the lobby listbox
                this.Dispatcher.Invoke(
                    new LoadListBoxDelegate(LoadListBox),
                    new object[] {MeetingRoster_Listbox, 
                        displayName});

            }
        }

        /// <summary>
        /// Handles event raised when interesting conversation properties changed. 
        /// Handler is only interested in conference properties
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _Conversation_PropertyChanged(object sender, ConversationPropertyChangedEventArgs e)
        {
            Conversation conference = (Conversation)sender;
            LoadTextBlockDelegate textBlockDelegate = new LoadTextBlockDelegate(LoadTextBlock);
            LoadTextBoxDelegate textBoxDelegate = new LoadTextBoxDelegate(LoadTextBox);

            switch (e.Property)
            {
                case ConversationProperty.ConferenceAcceptingParticipant:
                    Contact acceptingContact = (Contact)e.Value;
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceAcceptingParticipant_block, 
                            "AcceptingParticipant:" + 
                            acceptingContact.GetContactInformation(ContactInformationType.DisplayName).ToString() });
                    break;
                case ConversationProperty.ConferencingUri:
                    if (_MeetingKey == null)
                    {
                        _MeetingKey = new StringBuilder();
                    }
                    _MeetingKey.Append("Meeting Uri: " + "conf:" + e.Value.ToString() + "?conversation-id=null");
                    _MeetingKey.Append(System.Environment.NewLine);
                    break;
                case ConversationProperty.ConferenceAccessInformation:

                    try
                    {
                        if (_MeetingKey == null)
                        {
                            _MeetingKey = new StringBuilder();
                        }

                        _MeetingKey.Append(CreateConferenceKey());


                        this.Dispatcher.Invoke(
                            new EnableDisableButtonDelegate(EnableDisableButton),
                            new object[] { PostMeetingKey_Button, true });

                    }
                    catch (System.NullReferenceException nr)
                    {
                        System.Diagnostics.Debug.WriteLine(
                            "Null ref Eception on ConferenceAccessInformation changed " + nr.Message);
                    }
                    catch (LyncClientException lce)
                    {
                        System.Diagnostics.Debug.WriteLine(
                            "Exception on ConferenceAccessInformation changed " + lce.Message);
                    }
                    break;
            }
            if (_MeetingKey != null)
            {
                this.Dispatcher.Invoke(
                    textBoxDelegate,
                    new object[] { ConferenceAccessInformation_block, _MeetingKey.ToString() });
                _MeetingKey.Clear();
            }
        }

        /// <summary>
        /// Returns the meet-now meeting access key as a string
        /// </summary>
        /// <returns></returns>
        private string CreateConferenceKey()
        {
            string returnValue = string.Empty;
            try
            {
                StringBuilder MeetingKey = new StringBuilder();

                //These properties are used to invite people by creating an email (or text message, or IM)
                //and adding the dial in number, external Url, internal Url, and conference Id
                ConferenceAccessInformation conferenceAccess = 
                    (ConferenceAccessInformation)_Conversation.Properties[ConversationProperty.ConferenceAccessInformation];

                if (conferenceAccess.Id.Length > 0)
                {
                    MeetingKey.Append("Meeting Id: " + conferenceAccess.Id);
                    MeetingKey.Append(System.Environment.NewLine);
                }

                if (conferenceAccess.AdmissionKey.Length > 0)
                {
                    MeetingKey.Append(conferenceAccess.AdmissionKey);
                    MeetingKey.Append(System.Environment.NewLine);
                }

                string[] attendantNumbers = (string[])conferenceAccess.AutoAttendantNumbers;

                StringBuilder sb2 = new StringBuilder();
                sb2.Append(System.Environment.NewLine);
                foreach (string aNumber in attendantNumbers)
                {
                    sb2.Append("\t\t" + aNumber);
                    sb2.Append(System.Environment.NewLine);
                }
                if (sb2.ToString().Trim().Length > 0)
                {
                    MeetingKey.Append("Auto attendant numbers:" + sb2.ToString());
                    MeetingKey.Append(System.Environment.NewLine);
                }

                if (conferenceAccess.ExternalUrl.Length > 0)
                {
                    MeetingKey.Append("External Url: " + conferenceAccess.ExternalUrl);
                    MeetingKey.Append(System.Environment.NewLine);
                }

                if (conferenceAccess.InternalUrl.Length > 0)
                {
                    MeetingKey.Append("Inner Url: " + conferenceAccess.InternalUrl);
                    MeetingKey.Append(System.Environment.NewLine);
                }

                MeetingKey.Append("Meeting access type: " + (
                    (ConferenceAccessType)_Conversation.Properties[ConversationProperty.ConferencingAccessType])
                    .ToString());

                MeetingKey.Append(System.Environment.NewLine);
                returnValue = MeetingKey.ToString();

            }
            catch (System.NullReferenceException nr)
            {
                System.Diagnostics.Debug.WriteLine(
                    "Null ref Eception on ConferenceAccessInformation changed " + nr.Message);
            }
            catch (LyncClientException lce)
            {
                System.Diagnostics.Debug.WriteLine(
                    "Exception on ConferenceAccessInformation changed " + lce.Message);
            }
            return returnValue;
        }

        private delegate void LoadTextBoxDelegate(System.Windows.Controls.TextBox blockToLoad, string newItem);
        private void LoadTextBox(System.Windows.Controls.TextBox boxToLoad, string newItem)
        {
            boxToLoad.Text += newItem;
        }

        private delegate void LoadTextBlockDelegate(System.Windows.Controls.TextBlock blockToLoad, string newItem);
        private void LoadTextBlock(System.Windows.Controls.TextBlock blockToLoad, string newItem)
        {
            blockToLoad.Text = newItem;
        }
        private delegate void LoadListBoxDelegate(System.Windows.Controls.ListBox listToLoad, string newItem);
        private void LoadListBox(System.Windows.Controls.ListBox listToLoad, string newItem)
        {
            if (listToLoad.Items.Contains(newItem))
            {
                return;
            }
            listToLoad.Items.Add(newItem);
        }
        private delegate void ClearListBoxDelegate(System.Windows.Controls.ListBox listToClear);
        private void ClearListBox(System.Windows.Controls.ListBox listToClear)
        {
            listToClear.Items.Clear();
        }

        private delegate void RemoveListItemDelegate(System.Windows.Controls.ListBox listToClear, string listItem);
        private void RemoveListItem(System.Windows.Controls.ListBox listToClear, string listItem)
        {
            listToClear.Items.Remove(listItem);
        }

        private delegate void EnableDisableButtonDelegate(System.Windows.Controls.Button buttonToSet, bool enableState);
        private void EnableDisableButton(System.Windows.Controls.Button buttonToSet, bool enableState)
        {
            buttonToSet.IsEnabled = enableState;
        }

        /// <summary>
        /// Handles the window loaded event and gets the Lync client 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Window_Loaded_1(object sender, RoutedEventArgs e)
        {
            try
            {
                _Automation = LyncClient.GetAutomation();

                //Load a list of the user's followed chat rooms
                LoadRoomList();
                
            }
            catch (ClientNotFoundException)
            {
                System.Diagnostics.Debug.WriteLine("Client is not running");
            }
            catch (LyncClientException lce) 
            {
                System.Diagnostics.Debug.WriteLine(
                    "LyncClientException on getClient(): " + lce.Message);
            }
        }

        //Ends the current meeting
        private void EndMeeting_Button_Click_1(object sender, RoutedEventArgs e)
        {
            try
            {
                if (_ConversationWindow != null)
                {
                    _ConversationWindow.Close();
                }
                ConferenceAccessInformation_block.Text = "";
                MeetingRoster_Listbox.Items.Clear();

            }
            catch (NotInitializedException){}

        }

        /// <summary>
        /// Sets the conference access type property
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SetAccessType_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (!_Conversation.CanSetProperty(ConversationProperty.ConferencingAccessType))
            {
                return;
            }
            if (Anon_Radio.IsChecked == true)
            {
                _Conversation.BeginSetProperty(
                    ConversationProperty.ConferencingAccessType, 
                    ConferenceAccessType.Anonymous, (ar) => 
                    {
                        _Conversation.EndSetProperty(ar);
                    },
                    null);
            }
            if (Open_Radio.IsChecked == true)
            {
                _Conversation.BeginSetProperty(
                    ConversationProperty.ConferencingAccessType,
                    ConferenceAccessType.Open, (ar) =>
                    {
                        _Conversation.EndSetProperty(ar);
                    },
                    null);
            }

            //All invited users must wait in lobby for admission to a closed meeting
            if (Closed_Radio.IsChecked == true)
            {
                _Conversation.BeginSetProperty(
                    ConversationProperty.ConferencingAccessType,
                    ConferenceAccessType.Closed, (ar) =>
                    {
                        _Conversation.EndSetProperty(ar);
                    },
                    null);
            }
            if (Locked_Radio.IsChecked == true)
            {
                _Conversation.BeginSetProperty(
                    ConversationProperty.ConferencingAccessType,
                    ConferenceAccessType.Locked, (ar) =>
                    {
                        _Conversation.EndSetProperty(ar);
                    },
                    null);
            }
        }

        /// <summary>
        /// Locks the meeting so that only the presenter can get in.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void LockMeeting_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (!_Conversation.CanSetProperty(ConversationProperty.ConferencingLocked))
            {
                return;
            }

            _Conversation.BeginSetProperty(
                ConversationProperty.ConferencingLocked,
                true, (ar) =>
                {
                    _Conversation.EndSetProperty(ar);
                },
                null);

        }

        /// <summary>
        /// Admits all people waiting in the meeting lobby
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AdmitAll_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }

            System.Collections.Generic.List<Participant> participants = new System.Collections.Generic.List<Participant>();
            foreach (Participant participant in _Conversation.Participants)
            {
                if ((bool)participant.Properties[ParticipantProperty.IsInLobby] == true)
                {
                    participants.Add(participant);
                }
            }
            if (participants.Count > 0)
            {
                _Conversation.BeginAdmitParticipants(
                    participants,
                    (ar) =>
                    {
                        _Conversation.EndAdmitParticipants(ar);
                    },
                    null);
            }
        }

        /// <summary>
        /// Admits the selected person from the meeting lobby
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AdmitOne_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }
            if (Lobby_ListBox.SelectedItem == null)
            {
                return;
            }
            foreach (Participant participant in _Conversation.Participants)
            {
                if (participant.Contact.GetContactInformation(
                    ContactInformationType.DisplayName).ToString() == Lobby_ListBox.SelectedItem.ToString())
                {
                    if (participant.CanAdmit())
                    {
                        participant.BeginAdmit(
                            (ar) => 
                            {
                                participant.EndAdmit(ar);
                            },
                            null);
                    }
                    break;
                }
            }
        }

        /// <summary>
        /// Denies meeting admission to the person selected in the lobby
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void DenyOne_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }
            if (Lobby_ListBox.SelectedItem == null)
            {
                return;
            }

            foreach (Participant participant in _Conversation.Participants)
            {
                if (participant.Contact.GetContactInformation(
                    ContactInformationType.DisplayName).ToString() == Lobby_ListBox.SelectedItem.ToString())
                {
                    if (participant.CanDeny())
                    {
                        participant.BeginDeny(
                            (ar) =>
                            {
                                participant.EndDeny(ar);
                            },
                            null);
                    }
                    break;
                }
            }

        }

        /// <summary>
        /// Denies meeting admission to all people waiting in the meeting lobby
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void DenyAll_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }

            System.Collections.Generic.List<Participant> participants = new System.Collections.Generic.List<Participant>();
            foreach (Participant participant in _Conversation.Participants)
            {
                if ((bool)participant.Properties[ParticipantProperty.IsInLobby] == true)
                {
                    participants.Add(participant);
                }
            }
            if (participants.Count > 0)
            {
                _Conversation.BeginDenyParticipants(
                    participants,
                    (ar) =>
                    {
                        _Conversation.EndDenyParticipants(ar);
                    },
                    null);
            }

        }

        /// <summary>
        /// Pins or unpins the video stream of the selected participant.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void PinVideo_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }
            foreach (Participant participant in _Conversation.Participants)
            {

                if (MeetingRoster_Listbox.SelectedItem == null)
                {
                    return;
                }
                Contact contact = participant.Contact;
                string displayName;

                displayName = contact.GetContactInformation(
                    ContactInformationType.DisplayName).ToString();

                if (displayName == MeetingRoster_Listbox.SelectedItem.ToString())
                {

                    //The local participant cannot pin themselves in their
                    //video gallery view.
                    if (participant.IsSelf == true)
                    {
                        return;
                    }

                    if ((bool)participant.Properties[ParticipantProperty.IsPinned])
                    {
                        try
                        {
                            participant.BeginUnPinVideo((ar) =>
                            {
                                try
                                {
                                    participant.EndUnPinVideo(ar);
                                }
                                catch (LyncClientException) { };
                            }, null);
                        }
                        catch (System.ArgumentException) { };
                    }
                    
                    else
                    {
                        try
                        {
                            participant.BeginPinVideo((ar) =>
                            {
                                try
                                {
                                    participant.EndPinVideo(ar);
                                }
                                catch (LyncClientException) { };
                            }, null);
                        }
                        catch (System.ArgumentException) { };
                    }
                    break;
                }
            }
        }


        /// <summary>
        /// Locks or unlocks the selected participant video in the video gallery so 
        /// that other conversation participants cannot remove the participant's 
        /// video stream from their view of the video gallery.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void LockVideo_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }
            if (MeetingRoster_Listbox.SelectedItem == null)
            {
                return;
            }

            //Only presenters can lock participant video
            if (!(bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter])
            {
                return;
            }

            foreach (Participant participant in _Conversation.Participants)
            {
                Contact contact = participant.Contact;
                string displayName = contact.GetContactInformation(
                    ContactInformationType.DisplayName).ToString();

                if (displayName == MeetingRoster_Listbox.SelectedItem.ToString())
                {
                    if ((bool)participant.Properties[ParticipantProperty.IsLocked])
                    {
                        participant.BeginUnLockVideo((ar) => 
                        { participant.EndUnLockVideo(ar); }, null);
                    }
                    else
                    {
                        participant.BeginLockVideo((ar) => 
                        { participant.EndLockVideo(ar); }, null);
                    }
                    break;
                }
            }
        }

        private void MakePresenter_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }
            if (MeetingRoster_Listbox.SelectedItem == null)
            {
                return;
            }

            if ((bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter] == false)
            {
                return;
            }
            foreach (Participant participant in _Conversation.Participants)
            {
                string displayName = participant.Contact.GetContactInformation(
                    ContactInformationType.DisplayName).ToString();

                if (displayName == MeetingRoster_Listbox.SelectedItem.ToString())
                {
                    if (!(bool)participant.Properties[ParticipantProperty.IsPresenter])
                    {
                        participant.BeginSetProperty(
                            ParticipantProperty.IsPresenter,
                            true,
                            (ar) => 
                            {
                                participant.EndSetProperty(ar); 
                            },
                            null);
                    }
                    break;
                }
            }

        }

        private void MakeParticipant_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_Conversation == null)
            {
                return;
            }
            if (MeetingRoster_Listbox.SelectedItem == null)
            {
                return;
            }

            if ((bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter] == false)
            {
                return;
            }
            foreach (Participant participant in _Conversation.Participants)
            {
                string displayName = participant.Contact.GetContactInformation(
                    ContactInformationType.DisplayName).ToString();

                if (displayName == MeetingRoster_Listbox.SelectedItem.ToString())
                {
                    if ((bool)participant.Properties[ParticipantProperty.IsPresenter])
                    {
                        if (participant.CanSetProperty(ParticipantProperty.IsPresenter))
                        {
                            participant.BeginSetProperty(
                                ParticipantProperty.IsPresenter,
                                false,
                                (ar) =>
                                {
                                    participant.EndSetProperty(ar);
                                },
                                null);
                        }
                    }
                    break;
                }
            }

        }

        private void PostMeetingKey_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (RoomList_ListBox.SelectedItem == null)
            {
                MessageBox.Show("You must select a chat room");
                return;
            }
            try
            {
                Room myRoom = ((RoomWrapper)RoomList_ListBox.SelectedItem).ChatRoom;
                    
                Dictionary<RoomMessageFormat, string> messageDictionary = new Dictionary<RoomMessageFormat, string>();
                messageDictionary.Add(RoomMessageFormat.PlainText, CreateConferenceKey());
                myRoom.BeginSendStoryMessage(
                    messageDictionary,
                    RoomMessageType.Alert
                    ,
                    "Meeting has started",
                    (ar) =>
                    {
                        try
                        {
                            myRoom.EndSendStoryMessage(ar);
                            MessageBox.Show(
                                "Meeting access key successfully posted to " +
                                myRoom.Properties[RoomProperty.Title].ToString(),"Chat room post");
                        }
                        catch (LyncClientException lce)
                        {
                            System.Diagnostics.Debug.WriteLine(
                                "Lync client exception on post story message to " + 
                                myRoom.Properties[RoomProperty.Title].ToString() + 
                                " " + 
                                lce.Message);
                        }
                    }
                    ,
                    null);
            }
            catch (LyncClientException lce)
            {
                System.Diagnostics.Debug.WriteLine(
                    "Lync client exception on most message to room() " + lce.Message);
            }

        }

        /// <summary>
        /// Loads the user's followed chat rooms into a UI listbox.
        /// </summary>
        private void LoadRoomList()
        {
            foreach (Room room in LyncClient.GetClient().RoomManager.FollowedRooms)
            {
                RoomList_ListBox.Items.Add(new RoomWrapper(room));
            }
        }
    }

    internal class RoomWrapper
    {
        Room _Room;
        public override string ToString()
        {
            return _Room.Properties[RoomProperty.Title].ToString();
        }
        public Room ChatRoom
        {
            get
            {
                return _Room;
            }
            set
            {
                _Room = value;
            }
        }
        public RoomWrapper(Room roomToWrap)
        {
            _Room = roomToWrap;
        }
    }
}
```

## See also

  - [What you can do with Lync meetings](what-you-can-do-with-lync-meetings.md)

  - [Meeting dial-in access keys](meeting-dial-in-access-keys.md)

