---
title: 'How to: Set meeting access'
TOCTitle: 'How to: Set meeting access'
ms:assetid: a06b10ba-e0f1-48b7-8ee9-0c7678d9b657
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933127(v=office.15)
ms:contentKeyID: 50877269
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Set meeting access

Learn how to programmatically set the access type of a Microsoft Lync 2013 meet-now meeting by using Microsoft Lync 2013 SDK.

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
Set a meet-now meeting access type<br />
Code examples: Meeting access manager<br />
Next steps<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for setting a meet-now meeting access type are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Set a meet-now meeting access type

Meeting access types determine the ability of a person to join a meet-now meeting. Meeting access can be set to allow any person to join a meeting directly as long as that person has a valid admission key. Successive constraints can be added to meeting admission that conform to your meeting requirements. For information about the kinds of meeting access types that are available, see [Meeting lobby management](meeting-lobby-management.md).

### To set a meet-now meeting access type

1.  Get the [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) object that encapsulates the meeting.
    
    For information about getting the **Conversation**, see [How to: Start a meet-now meeting](how-to-start-a-meet-now-meeting.md).

2.  Verify that the conferencing access type property can be set on the conversation by calling the [Conversation.CanSetProperty](https://msdn.microsoft.com/en-us/library/jj265992\(v=office.15\)) method.

3.  Call the [Conversation.BeginSetProperty](https://msdn.microsoft.com/en-us/library/jj294127\(v=office.15\)) method.
    
    The following example gets the access type choice made by a user, verifies that the access type property can be set, and then sets the property.
    
    ```csharp
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
    ```

## Code examples: Meeting access manager

The following example declares a WPF window that provides a Lync 2013 user with an application that manages meeting access for a new meet-now meeting.

```xaml
<Window x:Class="MeetingAccess.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="Meeting Access Manager" Height="560" Width="1125" Loaded="Window_Loaded_1">
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
    </Grid>
</Window>
```

The following example is the window interaction logic for the previously declared WPF window.

```csharp
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

            //Check to see if participant is in lobby now
            if ((bool)e.Participant.Properties[ParticipantProperty.IsInLobby] == true)
            { 
                //Add the user's name to the lobby listbox
                this.Dispatcher.Invoke(
                    new LoadListBoxDelegate(LoadListBox),
                    new object[] {Lobby_ListBox, 
                        e.Participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString()});
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
                string displayName = participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                this.Dispatcher.Invoke(new RemoveListItemDelegate(RemoveListItem), new object[] { Lobby_ListBox, displayName });
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
            LoadListBoxDelegate listDelegate = new LoadListBoxDelegate(LoadListBox);
            LoadTextBlockDelegate textBlockDelegate = new LoadTextBlockDelegate(LoadTextBlock);
            LoadTextBoxDelegate textBoxDelegate = new LoadTextBoxDelegate(LoadTextBox);

            switch (e.Property)
            { 
                case ConversationProperty.ConferenceAcceptingParticipant:
                    Contact acceptingContact = (Contact)conference.Properties[e.Property];
                    this.Dispatcher.Invoke(
                        textBlockDelegate, 
                        new object[] { ConferenceAcceptingParticipant_block, "AcceptingParticipant:" + acceptingContact.GetContactInformation(ContactInformationType.DisplayName).ToString() });
                    break;
                case ConversationProperty.ConferenceAccessInformation:

                    //These properties are used to invite people by creating an email (or text message, or IM)
                    //and adding the dial in number, external Url, internal Url, and conference Id
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
                        new object[] { ConferenceDisclaimer_block, "Disclaimer:"  + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferenceDisclaimerAccepted:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceDisclaimerAccepted_block, "Disclaimer Accepted:" + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferenceEscalationProgress:
                    ConferenceEscalationProgress progress = (ConferenceEscalationProgress)_Conversation.Properties[e.Property];
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceEscalationProgress_block, "Escalation Progress:" + progress.ToString() });
                    break;
                case ConversationProperty.ConferenceEscalationResult:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceEscalationResult_block, "Escalation Result:" + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferenceInviterRepresentationInfo:
                    object representationDetails = _Conversation.Properties[e.Property];
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceInviterRepresentationInfo_block, "InviterRepresentationInfo type:" + representationDetails.GetType().Name });
                    break;
                case ConversationProperty.ConferenceJoinDialogCompleted:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceJoinDialogCompleted_block, "JoinDialogCompleted:" + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferenceTerminateOnLeave:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferenceTerminateOnLeave_block, "TerminateOnLeave:" + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferencingAccessType:
                    ConferenceAccessType accessType = (ConferenceAccessType)_Conversation.Properties[e.Property];
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingAccessType_block, "AccessType:" + accessType.ToString() });
                    break;
                case ConversationProperty.ConferencingFirstInstantMessage:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingFirstInstantMessage_block, "FirstInstantMessage:" + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferencingInvitedModes:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingInvitedModes_block, "InvitedModes:" + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferencingLocked:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingLocked_block, "Locked:" + _Conversation.Properties[e.Property].ToString() });
                    break;
                case ConversationProperty.ConferencingUri:
                    this.Dispatcher.Invoke(
                        textBlockDelegate,
                        new object[] { ConferencingUri_block, "Uri:" + _Conversation.Properties[e.Property].ToString() });
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
        /// Handles the window loaded event and gets the Lync client 
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

        //Ends the current meeting
        private void EndMeeting_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (_ConversationWindow != null)
            {
                _ConversationWindow.Close();
            }

        }

        /// <summary>
        /// Sets the conference access type property
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SetAccessType_Button_Click_1(object sender, RoutedEventArgs e)
        {
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
        /// Admits the selected person from the meeting lobby
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AdmitOne_Button_Click_1(object sender, RoutedEventArgs e)
        {
            foreach (Participant participant in _Conversation.Participants)
            {
                if (participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString() == Lobby_ListBox.SelectedItem.ToString())
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
            foreach (Participant participant in _Conversation.Participants)
            {
                if (participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString() == Lobby_ListBox.SelectedItem.ToString())
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
    }
}
```

## Next steps

  - [How to: Admit or deny people in the meeting lobby](how-to-admit-or-deny-people-in-the-meeting-lobby.md)

## See also

  - [What you can do with Lync meetings](what-you-can-do-with-lync-meetings.md)

