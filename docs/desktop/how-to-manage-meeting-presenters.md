---
title: 'How to: Manage meeting presenters'
TOCTitle: 'How to: Manage meeting presenters'
ms:assetid: 12482075-3fe5-456d-8dd6-ce36e212aa2a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937265(v=office.15)
ms:contentKeyID: 50877084
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Manage meeting presenters

Learn how to programmatically promote participants to the presenter role in a Microsoft Lync 2013 meeting by using Microsoft Lync 2013 SDK.

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
Promote and demote participants in a meeting<br />
Code example: Meeting manager<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for promoting meeting participants to presenters are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Promote and demote participants in a meeting

To promote or demote a participant in a meeting, the local user must be a meeting presenter.

### To promote a participant to a presenter

1.  Verify that the local user is a presenter in the meeting by reading the [ParticipantProperty](https://msdn.microsoft.com/en-us/library/jj277580\(v=office.15\))**.IsPresenter** property on the [Conversation.SelfParticipant](https://msdn.microsoft.com/en-us/library/jj266427\(v=office.15\)) property. If the value is **true**, promote the selected participant.

2.  Get the [Microsoft.Lync.Model.Conversation.Participant](https://msdn.microsoft.com/en-us/library/jj267311\(v=office.15\)) object to be promoted and read the [ParticipantProperty](https://msdn.microsoft.com/en-us/library/jj277580\(v=office.15\))**.IsPresenter** property.
    
    If the participant is an attendee, the participant can be promoted.

3.  Promote the presenter by setting the [ParticipantProperty](https://msdn.microsoft.com/en-us/library/jj277580\(v=office.15\))**.IsPresenter** to true by calling the [Participant.BeginSetProperty](https://msdn.microsoft.com/en-us/library/jj267268\(v=office.15\)) method.
    
    The following example verifies that the local participant is a presenter, gets a participant to be promoted, and then promotes the selected participant to a presenter.
    
    ``` csharp
            /// <summary>
            /// Promotes a meeting attendee to the presenter role
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void MakePresenter_Button_Click_1(object sender, RoutedEventArgs e)
            {
                if ((bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter] == false)
                {
                    return;
                }
                foreach (Participant participant in _Conversation.Participants)
                {
                    string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                    if (displayName != MeetingRoster_Listbox.SelectedItem.ToString())
                    {
                        continue;
                    }
                    //If the participant is not already a presenter, promote the participant to presenter.
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
    ```

### To demote a presenter to attendee

1.  Verify that the local user is a presenter in the meeting by reading the [Microsoft.Lync.Model.Conversation.ParticipantProperty](https://msdn.microsoft.com/en-us/library/jj277580\(v=office.15\))**.IsPresenter** property on the [Conversation.SelfParticipant](https://msdn.microsoft.com/en-us/library/jj266427\(v=office.15\)) property. If the value is **true**, promote the selected participant.

2.  Get the [Microsoft.Lync.Model.Conversation.Participant](https://msdn.microsoft.com/en-us/library/jj267311\(v=office.15\)) object to be promoted and read the [Microsoft.Lync.Model.Conversation.ParticipantProperty](https://msdn.microsoft.com/en-us/library/jj277580\(v=office.15\))**.IsPresenter** property.
    
    If the participant is a presenter, the participant can be demoted to an attendee.

3.  Demote the presenter by setting the [ParticipantProperty](https://msdn.microsoft.com/en-us/library/jj277580\(v=office.15\))**.IsPresenter** property to **false** by calling the [Participant.BeginSetProperty](https://msdn.microsoft.com/en-us/library/jj267268\(v=office.15\)) method.
    
    The following example verifies that the local participant is a presenter, gets a participant to be promoted, and then promotes the selected participant to presenter.
    
    ``` csharp
            /// <summary>
            /// Demotes a meeting presenter to a meeting attendee
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void MakeAttendee_Button_Click_1(object sender, RoutedEventArgs e)
            {
                if ((bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter] == false)
                {
                    return;
                }
                foreach (Participant participant in _Conversation.Participants)
                {
                    string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                    if (displayName != MeetingRoster_Listbox.SelectedItem.ToString())
                    {
                        continue;
                    }
                    if ((bool)participant.Properties[ParticipantProperty.IsPresenter])
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
                    break;
                }
            }
    ```

## Code example: Meeting manager

The following example declares a WPF window that lets a user manage a meeting lobby, pin and lock participant video, and promote participants to the presenter role.

``` xaml
<Window x:Class="MeetingAccess.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Meeting Manager" Height="560" Width="1125" Loaded="Window_Loaded_1">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="36"/>
            <RowDefinition Height="260"/>
            <RowDefinition Height="80*"/>
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="140"/>
            <ColumnDefinition Width="650"/>
            <ColumnDefinition Width="10*"/>
        </Grid.ColumnDefinitions>
        <Grid Grid.Row="1" Grid.Column="2">
            <Grid.RowDefinitions>
                <RowDefinition Height="90"/>
                <RowDefinition Height="30*"/>
            </Grid.RowDefinitions>
            <StackPanel Grid.Row="0" Grid.Column="0" Orientation="Horizontal">
                <Label Content="Lobby" Width="50" Height="26" />
                <ListBox Name="Lobby_ListBox" Width="190" Height="70" Margin="10,5,10,10"/>
            </StackPanel>
            <StackPanel Grid.Row="1" Grid.Column="0">
                <Button Name="AdmitAll_Button" Content="Admit All" Margin="10,10,10,10" Click="AdmitAll_Button_Click_1" />
                <Button Name="AdmitOne_Button" Content="Admit Selected" Margin="10,10,10,10" Click="AdmitOne_Button_Click_1" />
                <Button Name="DenyOne_Button" Content="Deny Selected" Margin="10,10,10,10" Click="DenyOne_Button_Click_1"/>
                <Button Name="DenyAll_Button" Content="Deny All" Margin="10,10,10,10" Click="DenyAll_Button_Click_1" />
            </StackPanel>
        </Grid>
        <StackPanel Grid.Row="1" Grid.Column="0">
            <Button Name="StartMeeting_Button" Content="Start Meeting" Width="120" Margin="10,10,10,10" Click="StartMeeting_Button_Click_1"/>
            <Button Name="EndMeeting_Button" Content="End Meeting" Width="120" Margin="10,10,10,10" Click="EndMeeting_Button_Click_1"/>
        </StackPanel>
        <Grid Name="ConferenceInfoGrid" Grid.Column="1" Grid.Row="1" Margin="0,0,10,0">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="320"/>
                <ColumnDefinition Width="60*"/>
            </Grid.ColumnDefinitions>
            <StackPanel Grid.Column="0">
                <TextBlock Name="ConferenceAcceptingParticipant_block" Margin="5,2,2,2" Height="26"/>
                <TextBox Name="ConferenceAccessInformation_block" Margin="5,2,2,2" Height="66" />
                <TextBlock Name="ConferenceDisclaimer_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferenceDisclaimerAccepted_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferenceEscalationProgress_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferenceEscalationResult_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferenceInviterRepresentationInfo_block" Margin="5,2,2,2" Height="26"/>
            </StackPanel>
            <StackPanel Grid.Column="1">
                <TextBlock Name="ConferenceJoinDialogCompleted_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferenceTerminateOnLeave_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferencingAccessType_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferencingFirstInstantMessage_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferencingInvitedModes_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferencingLocked_block" Margin="5,2,2,2" Height="26"/>
                <TextBlock Name="ConferencingUri_block" Margin="5,2,2,2" Height="26"/>

            </StackPanel>

        </Grid>
        <Grid Grid.Row="2" Grid.Column="1">
            <StackPanel Orientation="Horizontal">
                <ListBox Name="Error_Log" Margin="10,10,10,10" Width="610" Height="170"/>
            </StackPanel>
        </Grid>
        <StackPanel Grid.Row="2" Grid.Column="0">
            <RadioButton Name="Anon_Radio" Content="Anonymous"  Margin="2,2,2,2"/>
            <RadioButton Name="Closed_Radio" Content="Closed"  Margin="2,2,2,2"/>
            <RadioButton Name="Locked_Radio" Content="Locked"  Margin="2,2,2,2"/>
            <RadioButton Name="Open_Radio" Content="Open"  Margin="2,2,2,2"/>
            <Button Name="SetAccessType_Button" Content="Set access type" Margin="10,10,10,10" Click="SetAccessType_Button_Click_1" />
            <Button Name="LockMeeting_Button" Content="Lock meeting" Margin="10,10,10,10" Click="LockMeeting_Button_Click_1"/>
        </StackPanel>
        <Grid Grid.Row="2" Grid.Column="2">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="100"/>
                <ColumnDefinition Width="90*"/>
            </Grid.ColumnDefinitions>
            <StackPanel Grid.Row="0" Grid.Column="0" Orientation="Vertical">
                <Button Name="PinVideo_Button" Content="Pin video" Click="PinVideo_Button_Click_1" Height="26" Width="94" Margin="2,30,2,2"/>
                <Button Name="LockVideo_Button" Content="Lock video" Click="LockVideo_Button_Click_1" Height="26" Width="94" Margin="2,2,2,2"/>
                <Button Name="MakePresenter_Button" Content="Make presenter" Click="MakePresenter_Button_Click_1" Height="26" Width="94" Margin="2,2,2,2"/>
                <Button Name="MakeAttendee_Button" Content="Make attendee" Click="MakeAttendee_Button_Click_1" Height="26" Width="94" Margin="2,2,2,2"/>
            </StackPanel>
            <ListBox Name="MeetingRoster_Listbox" Margin="10,10,10,10" Width="190" Height="180" Grid.Column="1"/>

        </Grid>
    </Grid>
</Window>
```

The following example is the interaction logic for the window declared in the previous example.

``` csharp
using System.Windows;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Extensibility;
using System.Text;

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

        public MainWindow()
        {
            InitializeComponent();
        }

        /// <summary>
        /// Starts a new meeting by using automation.
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

        /// <summary>
        /// Handles the event raised when a participant is added to meeting. If waiting in lobby, adds the
        /// user name to lobby list.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _Conversation_ParticipantAdded(object sender, ParticipantCollectionChangedEventArgs e)
        {
            //Watch for changes in the participant property (IsInLobby)
            e.Participant.PropertyChanged += Participant_PropertyChanged;

            //Check to see if the participant is in lobby now.
            if ((bool)e.Participant.Properties[ParticipantProperty.IsInLobby] == true)
            {
                //Add the user's name to the lobby listbox.
                this.Dispatcher.Invoke(
                    new LoadListBoxDelegate(LoadListBox),
                    new object[] {Lobby_ListBox, 
                        e.Participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString()});
            }
            else
            { 
                //MeetingRoster_Listbox
                //Add the user's name to the lobby listbox.
                this.Dispatcher.Invoke(
                    new LoadListBoxDelegate(LoadListBox),
                    new object[] {MeetingRoster_Listbox, 
                        e.Participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString()});
            }
        }

        /// <summary>
        /// Handles the event raised when the participant property (IsInLobby) changes.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Participant_PropertyChanged(object sender, ParticipantPropertyChangedEventArgs e)
        {
            Participant participant = (Participant)sender;

            //If the IsInLobby property changes and the user is no longer in the lobby,
            // remove the user's name from the lobby list.
            if (e.Property == ParticipantProperty.IsInLobby && (bool)e.Value == false)
            {
                string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                this.Dispatcher.Invoke(new RemoveListItemDelegate(RemoveListItem), new object[] { Lobby_ListBox, displayName });

                //MeetingRoster_Listbox
                //Add the user's name to the lobby listbox.
                this.Dispatcher.Invoke(
                    new LoadListBoxDelegate(LoadListBox),
                    new object[] {MeetingRoster_Listbox, 
                        displayName});

            }
        }

        /// <summary>
        /// Handles the event raised when interesting conversation properties changed.
        /// The handler is only interested in conference properties.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _Conversation_PropertyChanged(object sender, ConversationPropertyChangedEventArgs e)
        {
            Conversation conference = (Conversation)sender;
            LoadListBoxDelegate listDelegate = new LoadListBoxDelegate(LoadListBox);
            LoadTextBlockDelegate textBlockDelegate = new LoadTextBlockDelegate(LoadTextBlock);
            LoadTextBoxDelegate textBoxDelegate = new LoadTextBoxDelegate(LoadTextBox);

            switch (e.Property)
            { 
                case ConversationProperty.ConferenceAcceptingParticipant:
                    Contact acceptingContact = (Contact)e.Value;
                    this.Dispatcher.Invoke(
                        textBlockDelegate, 
                        new object[] { ConferenceAcceptingParticipant_block, "AcceptingParticipant:" + acceptingContact.GetContactInformation(ContactInformationType.DisplayName).ToString() });
                    break;
                case ConversationProperty.ConferenceAccessInformation:

                    
                    //These properties are used to invite people by creating an email (or text message or IM)
                    //and adding the dial-in number, external URL, internal URL, and conference ID.
                    ConferenceAccessInformation conferenceAccess = (ConferenceAccessInformation)e.Value;

                    StringBuilder sb = new StringBuilder();
                    sb.Append("Addmission key: " + conferenceAccess.AdmissionKey);
                    sb.Append(System.Environment.NewLine);

                    string[] attendantNumbers = (string[])conferenceAccess.AutoAttendantNumbers;

                    StringBuilder sb2 = new StringBuilder();
                    foreach (string aNumber in attendantNumbers)
                    {
                        sb2.Append(aNumber + ", ");
                    }

                    sb.Append("Auto attendant numbers:" + sb2.ToString());
                    sb.Append(System.Environment.NewLine);

                    sb.Append("External Url: " + conferenceAccess.ExternalUrl);
                    sb.Append(System.Environment.NewLine);

                    sb.Append("Id: " + conferenceAccess.Id);
                    sb.Append(System.Environment.NewLine);

                    sb.Append("Inner Url: " + conferenceAccess.InternalUrl);
                    sb.Append(System.Environment.NewLine);

                    this.Dispatcher.Invoke(
                        textBoxDelegate,
                        new object[] { ConferenceAccessInformation_block, sb.ToString() });
                    break;
                case ConversationProperty.ConferenceDisclaimer:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceDisclaimer_block, "Disclaimer:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferenceDisclaimerAccepted:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceDisclaimerAccepted_block, "Disclaimer Accepted:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferenceEscalationProgress:
                    ConferenceEscalationProgress progress = (ConferenceEscalationProgress)e.Value;
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceEscalationProgress_block, "Escalation Progress:" + progress.ToString() });
                    break;
                case ConversationProperty.ConferenceEscalationResult:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceEscalationResult_block, "Escalation Result:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferenceInviterRepresentationInfo:
                    object representationDetails = e.Value;
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceInviterRepresentationInfo_block, "InviterRepresentationInfo type:" + representationDetails.GetType().Name });
                    break;
                case ConversationProperty.ConferenceJoinDialogCompleted:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceJoinDialogCompleted_block, "JoinDialogCompleted:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferenceTerminateOnLeave:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceTerminateOnLeave_block, "TerminateOnLeave:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferencingAccessType:
                    ConferenceAccessType accessType = (ConferenceAccessType)e.Value;
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingAccessType_block, "AccessType:" + accessType.ToString() });
                    break;
                case ConversationProperty.ConferencingFirstInstantMessage:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingFirstInstantMessage_block, "FirstInstantMessage:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferencingInvitedModes:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingInvitedModes_block, "InvitedModes:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferencingLocked:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingLocked_block, "Locked:" + e.Value.ToString() });
                    break;
                case ConversationProperty.ConferencingUri:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingUri_block, "Uri:" + e.Value.ToString() });
                    break;
            }

        }
        private delegate void LoadTextBoxDelegate(System.Windows.Controls.TextBox blockToLoad, string newItem);
        private void LoadTextBox(System.Windows.Controls.TextBox boxToLoad, string newItem)
        {
            boxToLoad.Text = newItem;
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
        /// <summary>
        /// Handles the window loaded event and gets the Lync client.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Window_Loaded_1(object sender, RoutedEventArgs e)
        {
            try
            {
                _Automation = LyncClient.GetAutomation();
            }
            catch (ClientNotFoundException)
            {
                Error_Log.Items.Add("Client is not running");
            }
            catch (LyncClientException lce) 
            {
                Error_Log.Items.Add("LyncClientException on getClient(): " + lce.Message);
            }
        }

        //Ends the current meeting.
        private void EndMeeting_Button_Click_1(object sender, RoutedEventArgs e)
        {
            try
            {
                if (_ConversationWindow != null)
                {
                    _ConversationWindow.Close();
                }
            }
            catch (NotInitializedException){}

        }

        /// <summary>
        /// Sets the conference access type property.
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

            //All invited users must wait in the lobby for admission to a closed meeting.
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
        /// Admits all people waiting in the meeting lobby.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AdmitAll_Button_Click_1(object sender, RoutedEventArgs e)
        {
            System.Collections.Generic.List<Participant> participants = new System.Collections.Generic.List<Participant>();
            foreach (Participant participant in _Conversation.Participants)
            {
                if ((bool)participant.Properties[ParticipantProperty.IsInLobby] == true)
                {
                    participants.Add(participant);
                }
            }
            _Conversation.BeginAdmitParticipants(
                participants, 
                (ar) => 
                {
                    _Conversation.EndAdmitParticipants(ar);
                },
                null);
        }

        /// <summary>
        /// Admits the selected person from the meeting lobby.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AdmitOne_Button_Click_1(object sender, RoutedEventArgs e)
        {
            foreach (Participant participant in _Conversation.Participants)
            {
                if (participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString() != Lobby_ListBox.SelectedItem.ToString())
                {
                    continue;
                }
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

        /// <summary>
        /// Denies meeting admission to the person selected in the lobby.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void DenyOne_Button_Click_1(object sender, RoutedEventArgs e)
        {
            foreach (Participant participant in _Conversation.Participants)
            {
                if (participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString() != Lobby_ListBox.SelectedItem.ToString())
                {
                    continue;
                }
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

        /// <summary>
        /// Denies meeting admission to all people waiting in the meeting lobby.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void DenyAll_Button_Click_1(object sender, RoutedEventArgs e)
        {
            System.Collections.Generic.List<Participant> participants = new System.Collections.Generic.List<Participant>();
            foreach (Participant participant in _Conversation.Participants)
            {
                if ((bool)participant.Properties[ParticipantProperty.IsInLobby] == true)
                {
                    participants.Add(participant);
                }
            }
            _Conversation.BeginDenyParticipants(
                participants,
                (ar) =>
                {
                    _Conversation.EndDenyParticipants(ar);
                },
                null);

        }

        private void PinVideo_Button_Click_1(object sender, RoutedEventArgs e)
        {
            foreach (Participant participant in _Conversation.Participants)
            { 
                string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                if (displayName != MeetingRoster_Listbox.SelectedItem.ToString())
                {
                    continue;
                }
                if ((bool)participant.Properties[ParticipantProperty.IsPinned])
                {
                    participant.BeginUnPinVideo((ar) => { participant.EndUnPinVideo(ar); }, null);
                }
                else
                {
                    participant.BeginPinVideo((ar) => { participant.EndPinVideo(ar); }, null);
                }
                break;
            }
        }

        /// <summary>
        /// Locks the selected participant video in the video gallery so that other conversation participants cannot remove the participant's 
        /// video stream from their view of the video gallery.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void LockVideo_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if ((bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter] == false)
            {
                return;
            }
            foreach (Participant participant in _Conversation.Participants)
            {
                string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                if (displayName != MeetingRoster_Listbox.SelectedItem.ToString())
                {
                    continue;
                }
                if ((bool)participant.Properties[ParticipantProperty.IsLocked])
                {
                    participant.BeginUnLockVideo((ar) => { participant.EndUnLockVideo(ar); }, null);
                }
                else
                {
                    participant.BeginLockVideo((ar) => { participant.EndLockVideo(ar); }, null);
                }
                break;
            }
        }

        /// <summary>
        /// Promotes a meeting attendee to the presenter role.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void MakePresenter_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if ((bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter] == false)
            {
                return;
            }
            foreach (Participant participant in _Conversation.Participants)
            {
                string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                if (displayName != MeetingRoster_Listbox.SelectedItem.ToString())
                {
                    continue;
                }
                //If participant is not already a presenter then he or she is promoted to presenter.
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

        /// <summary>
        /// Demotes a meeting presenter to a meeting attendee.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void MakeAttendee_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if ((bool)_Conversation.SelfParticipant.Properties[ParticipantProperty.IsPresenter] == false)
            {
                return;
            }
            foreach (Participant participant in _Conversation.Participants)
            {
                string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                if (displayName != MeetingRoster_Listbox.SelectedItem.ToString())
                {
                    continue;
                }
                if ((bool)participant.Properties[ParticipantProperty.IsPresenter])
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
                break;
            }
        }
    }
}
```

## See also

  - [What you can do with Lync meetings](what-you-can-do-with-lync-meetings.md)

