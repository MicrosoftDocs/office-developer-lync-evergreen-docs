---
title: 'How to: Send and receive context information in a Lync conversation'
TOCTitle: 'How to: Send and receive context information in a conversation'
ms:assetid: ea5c0019-4d54-43cd-9025-d5a9a6a7f305
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933248(v=office.15)
ms:contentKeyID: 50877394
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Send and receive context information in a Lync conversation

Learn how to use Microsoft Lync 2013 SDK to send contextual data in a Microsoft Lync 2013 conversation when the UI Lync clients at all endpoints has been suppressed.



**Applies to**: Lync 2013 | Lync Server 2013


<div class="caption">
Watch the video: Lync Contextual Data Part 1: Send Data With An IM Message
</div>
<br />

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/f1447b18-a319-4252-9ee1-39694128bdd4]

<div class="caption">
Watch the video: Lync Contextual Data Part 2: Methods and Events
</div>
<br />

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/820fb295-e1f8-4c44-a31d-cf2a28d272ee]

<div class="caption">
Watch the video: Lync Contextual Data Part 3: Passing an Image File
</div>
<br />

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/b6aaf29e-4c59-491f-a947-a88e1f791204]


## Prerequisites

The prerequisites for sending and receiving contextual information are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

  - A context package must be registered on all computers that run your application.

### Core concepts to know

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
<td><p><a href="how-to-start-a-lync-im-conversation.md">How to: Start a Lync IM conversation</a></p></td>
<td><p>Describes how to use Microsoft Lync 2013 SDK to programmatically start a Microsoft Lync 2013 conversation, invite a user, and send the first IM text.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-conversation-window-extension.md">Lync Conversation Window Extension</a></p></td>
<td><p>Introduces the Conversation Window Extension (CWE) feature of the Microsoft Lync 2013 client conversation window by explaining how a CWE is opened, closed, and sized.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contextual-lync-conversations.md">Contextual Lync conversations</a></p></td>
<td><p>Introduces the concept of contextual conversations in Microsoft Lync 2013 by describing application scenarios, application development models, and contextual extension application package registration.</p></td>
</tr>
</tbody>
</table>

## Register a context package

Before your application is run on a computer that has Microsoft Lync 2013 installed and configured for UI-suppression mode, you must register your application with a GUID as shown in the following example.

    Windows Registry Editor Version 5.00
    
    [HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages]
    
    [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings\ZoneMap\Domains\ServerName]
    "file"=dword:00000002
    
    [HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages\{97AD7B8A-3220-4855-8D1E-E70BB0973C4D}]
    "Name"="UI Suppression Context Passer"

Your application must use the GUID from the previous example as an application ID for all contextual information operations. In your application, declare a string like the following example.

``` 
        /// <summary>
        /// The GUID of a registered Conversation Window Extension application
        /// </summary>
        private string _AppId = "{97AD7B8A-3220-4855-8D1E-E70BB0973C4D}";  
```

## Handle the ConversationAdded event

Use the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event to register for the [Conversation.InitialContextReceived](https://msdn.microsoft.com/en-us/library/jj267349\(v=office.15\)) event and [Conversation.ContextDataReceived](https://msdn.microsoft.com/en-us/library/jj275926\(v=office.15\)) event.

### To handle the ConversationAdded event

1.  Read the state of the conversation IM modality. If it is not [Microsoft.Lync.Model.Conversation.ModalityState](https://msdn.microsoft.com/en-us/library/jj293265\(v=office.15\))**.Notified**, then the conversation started locally and you must add a remote user as a participant.

2.  Register for the [Conversation.ParticipantAdded](https://msdn.microsoft.com/en-us/library/jj275759\(v=office.15\)) event.

3.  Add a participant by calling the [Conversation.AddParticipant](https://msdn.microsoft.com/en-us/library/jj266479\(v=office.15\)) method.

4.  Register for the [Conversation.InitialContextReceived](https://msdn.microsoft.com/en-us/library/jj267349\(v=office.15\)) event and [Conversation.ContextDataReceived](https://msdn.microsoft.com/en-us/library/jj275926\(v=office.15\)) event.

5.  Register for the [InstantMessageModality.InstantMessageReceived](https://msdn.microsoft.com/en-us/library/jj293201\(v=office.15\)) event.
    
    The following example handles the conversation added event.
    
    ```csharp
            /// <summary>
            /// New conversation is added because the user added it or was invited to a conversation by another user
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void ConversationManager_ConversationAdded(object sender, Microsoft.Lync.Model.Conversation.ConversationManagerEventArgs e)
            {
                if (_conversation == null)
                {
                    _conversation = e.Conversation;
                }
    
                _conversation.ParticipantAdded += _conversation_ParticipantAdded;
                if (_conversation.Modalities[ModalityTypes.InstantMessage].State != ModalityState.Notified)
                {
                    _RemoteContact = _LyncClient.ContactManager.GetContactByUri("danilop1@contoso.com");
                    _conversation.AddParticipant(_RemoteContact);
                }
    
                e.Conversation.InitialContextReceived += Conversation_InitialContextReceived;
                e.Conversation.ContextDataReceived += Conversation_ContextDataReceived;
                e.Conversation.StateChanged += Conversation_StateChanged;
                ((InstantMessageModality)e.Conversation.Modalities[ModalityTypes.InstantMessage]).InstantMessageReceived += MainWindow_InstantMessageReceived;
            }
    ```

## Get the conversation subject from the InitialContextReceived event

The subject of the conversation as provided by the conversation initiator is available as application data in the [Conversation.InitialContextReceived](https://msdn.microsoft.com/en-us/library/jj267349\(v=office.15\)) event.

### To handle the InitialContextReceived event

1.  Verify that the application ID from the [InitialContextEventArgs.ApplicationId](https://msdn.microsoft.com/en-us/library/jj293433\(v=office.15\)) property matches the GUID you assign to your application.

2.  Get the initial context string from the [InitialContextEventArgs.ApplicationData](https://msdn.microsoft.com/en-us/library/jj277565\(v=office.15\)) property.
    
    The following example handles the [Conversation.InitialContextReceived](https://msdn.microsoft.com/en-us/library/jj267349\(v=office.15\)) event.
    
    ```csharp
            /// <summary>
            /// Displays the initial context received string in the UI list box.  
            /// This event is not raised in this code when Lync is not in UI suppressed mode.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void Conversation_InitialContextReceived(object sender, Microsoft.Lync.Model.Conversation.InitialContextEventArgs e)
            {
                if (e.ApplicationId != _AppId)
                {
                    return;
                }
                this.Dispatcher.Invoke(
                    new ControlContentUpdateDelegate(ControlContentUpdate), 
                    new object[] { Inbound_Listbox,  e.ApplicationData.ToString() });
    
            }
    ```

## Get additional conversation context information from the ContextDataReceived event

### To handle the ContextDataReceived event

1.  Verify that the application ID from the [InitialContextEventArgs.ApplicationId](https://msdn.microsoft.com/en-us/library/jj293433\(v=office.15\)) property matches the GUID you assign to your application.

2.  Get the MIME type of the context data in this event by reading the [ContextEventArgs.ContextDataType](https://msdn.microsoft.com/en-us/library/jj275527\(v=office.15\)) property.

3.  Parse the [ContextEventArgs.ContextData](https://msdn.microsoft.com/en-us/library/jj277173\(v=office.15\)) property text value according to the MIME type specified in step 2.
    
    The following example gets the context data, which is formatted as plain text, and then adds the text as an item in the UI list box.
    
    ```csharp
            /// <summary>
            /// Displays the received context data string in the UI list box
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void Conversation_ContextDataReceived(object sender, Microsoft.Lync.Model.Conversation.ContextEventArgs e)
            {
                if (e.ApplicationId != _AppId)
                {
                    return;
                }
                if (e.ContextDataType.ToLower() == "text/plain")
                {
                    this.Dispatcher.Invoke(
                        new ControlContentUpdateDelegate(ControlContentUpdate), 
                        new object[] { Inbound_Listbox,  e.ContextData.ToString() });
                }
            }
    ```

## Send initial context data in a new conversation

1.  Verify that the new conversation is active by reading the new state of the conversation from the value of the [Conversation.State](https://msdn.microsoft.com/en-us/library/jj267978\(v=office.15\)) property.

2.  If the conversation state is [Microsoft.Lync.Model.Conversation.ConversationState](https://msdn.microsoft.com/en-us/library/jj277587\(v=office.15\))**.Active**, send the initial conversation context by calling the [Conversation.BeginSendInitialContext](https://msdn.microsoft.com/en-us/library/jj275891\(v=office.15\)) method, passing the GUID registered as the context package in an enumerable collection of [Microsoft.Lync.Model.Conversation.ContextType](https://msdn.microsoft.com/en-us/library/jj275691\(v=office.15\)) enumerator and object key/value pairs.
    
    The initial context and all additional context sending operations must include the application GUID and context data.
    
    ```csharp
            /// <summary>
            /// Sends initial conversation context when a) local user selected Start Conversation radio button 
            /// and b) the resulting new conversation is active.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void Conversation_StateChanged(object sender, ConversationStateChangedEventArgs e)
            {
                this.Dispatcher.Invoke(new ControlContentUpdateDelegate(ControlContentUpdate), new object[] { ConversationStatus_Label,  e.NewState.ToString() });
                if (_StartConversation == false)
                {
                    return;
                }
                if (e.NewState == ConversationState.Active)
                {
                    try
                    {
                        System.Collections.Generic.Dictionary<ContextType, object> initialContext = new System.Collections.Generic.Dictionary<ContextType, object>();
                        initialContext.Add(ContextType.ApplicationId, _AppId);
                        initialContext.Add(ContextType.ApplicationData, "Initial Context");
                        _conversation.BeginSendInitialContext(
                            initialContext,
                            (ar) =>
                            {
                                _conversation.EndSendContextData(ar);
                            },
                            null);
    
                    }
    
                    // this exception is raised if the _AppId GUID string is not found in the system registry as a ContextPackage subkey
                    catch (ItemNotFoundException inf)
                    {
                        MessageBox.Show("ItemNotFound exception on send initial context: " + inf.Message);
                    }
                }
    
            }
    ```

## Send additional context data in a conversation

### To send additional context data in a conversation

1.  Verify that the conversation state is still active.

2.  Send the additional context data by calling the [Conversation.BeginSendContextData](https://msdn.microsoft.com/en-us/library/jj278336\(v=office.15\)) method.
    
    The following example sends additional context data specifying the GUID of the registered context package, a MIME type describing the format of the context data, and the context data itself.
    
    ``` 
            /// <summary>
            /// Sends additional conversation context information
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void SendText_Button_Click(object sender, RoutedEventArgs e)
            {
                if (_conversation == null)
                {
                    return;
                }
                if (_conversation.State != ConversationState.Active)
                {
                    return;
                }
                _conversation.BeginSendContextData(
                    _AppId,
                    "text/plain",
                    OutboundContext_Textbox.Text,
                    (ar) => 
                    {
                        _conversation.EndSendContextData(ar);
                    },
                    null);
            }
    ```

## Code examples: Context sending window

The following example declares a WPF window that sends and receives contextual information in a conversation.

```xaml
<Window x:Class="ContextSenderWindow.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525" Closing="Window_Closing">
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="252"/>
            <ColumnDefinition Width="251*"/>
        </Grid.ColumnDefinitions>
        <StackPanel Grid.Column="0">
            <StackPanel Grid.Column="0" Orientation="Horizontal">
                <Label Content="Text to send " Margin="10,10,10,10"/>
                <TextBox Name="OutboundContext_Textbox" Width="120" Height="30" Margin="10,10,10,10" HorizontalAlignment="Left"/>
            </StackPanel>
            <Button Name="SendText_Button" Content="Send" Margin="10,10,10,10" Width="80" Height="30" Click="SendText_Button_Click"/>
            <StackPanel Grid.Column="0" Orientation="Horizontal">
                <RadioButton Content="Start conversation" Name="StartConversation_Radio" Checked="StartConversation_Radio_Checked" Margin="5,5,5,5"/>
                <RadioButton Content="Wait for invitation" Name="WaitForInvite_Radio" Checked="WaitForInvite_Radio_Checked" Margin="5,5,5,5"/>
            </StackPanel>
            <StackPanel Orientation="Vertical" Grid.Column="0">
                <Label Name="ConversationStatus_Label" Width="190" Height="30" HorizontalAlignment="Left" Margin="10,10,10,10"/>
                <Label Name="Participant_Label" Width="190" Height="30" HorizontalAlignment="Left" Margin="10,10,10,10"/>
            </StackPanel>
            <StackPanel Orientation="Horizontal">
                <Label Name="ClientState_Label" Margin="10,10,10,10" Content="State: "/>
                <ListBox Name="ClientState_Listbox" Margin="10,10,10,10" Width="140" Height="60"/>
            </StackPanel>
        </StackPanel>
        <StackPanel Grid.Column="1">
            <ListBox Name="Inbound_Listbox" Width="200" Height="144" Margin="10,10,10,10" />
            <TextBlock Name="InboundIM_Textblock" Width="200" Height="124" Margin="10,10,10,10"/>
        </StackPanel>
    </Grid>
</Window>
```

The following example is the interaction logic for the previous WPF declaration. The example starts a conversation or waits for a conversation invitation. When a conversation is established, the example sends contextual information and displays received contextual information.

```csharp
using System;
using System.Windows;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Conversation;

namespace ContextSenderWindow
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {

        private LyncClient _LyncClient;

        /// <summary>
        /// The GUID of a registered Conversation Window Extension application
        /// </summary>
        private string _AppId = "{97AD7B8A-3220-4855-8D1E-E70BB0973C4D}";  

        private Conversation _conversation;
        private Boolean _thisInitializedLync = false;
        private Boolean _StartConversation = false;

        Contact _RemoteContact;

        public MainWindow()
        {
            InitializeComponent();
            try
            {
                _LyncClient = LyncClient.GetClient();
                _LyncClient.StateChanged += _LyncClient_StateChanged;

                if (_LyncClient.State != ClientState.SignedIn)
                {
                    //When UI suppression is enabled, the Lync client is uninitialized when not running.
                    if (_LyncClient.State == ClientState.Uninitialized)
                    {
                        //Start the Lync process
                        _LyncClient.BeginInitialize(
                            (ar) =>
                            {
                                _LyncClient.EndInitialize(ar);

                                //Set flag that indicates THIS ContextSenderWindow process started Lync.
                                _thisInitializedLync = true;
                            },
                            null);
                    }
                }
            }
            catch (ClientNotFoundException) { Console.WriteLine("Lync client was not found on startup"); }
            catch (LyncClientException lce) { MessageBox.Show("Lyncclientexception: " + lce.Message); }

        }

        /// <summary>
        /// Handles state change by updating UI with current client state and then starts a new
        /// conversation if a) user clicked Start Conversation radio button and b) the client is now
        /// signed in
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _LyncClient_StateChanged(object sender, ClientStateChangedEventArgs e)
        {
            this.Dispatcher.Invoke(
                new ControlContentUpdateDelegate(ControlContentUpdate), 
                new object[] { ClientState_Listbox, e.NewState.ToString() });

            if (_StartConversation == true && e.NewState == ClientState.SignedIn)
            {
                _conversation = _LyncClient.ConversationManager.AddConversation();
            }

        }

        /// <summary>
        /// New conversation is added because the user added it or was invited to a conversation by another user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ConversationManager_ConversationAdded(object sender, Microsoft.Lync.Model.Conversation.ConversationManagerEventArgs e)
        {
            if (_conversation == null)
            {
                _conversation = e.Conversation;
            }

            _conversation.ParticipantAdded += _conversation_ParticipantAdded;
            if (_conversation.Modalities[ModalityTypes.InstantMessage].State != ModalityState.Notified)
            {
                _RemoteContact = _LyncClient.ContactManager.GetContactByUri("danilop1@contoso.com");
                _conversation.AddParticipant(_RemoteContact);
            }

            e.Conversation.InitialContextReceived += Conversation_InitialContextReceived;
            e.Conversation.ContextDataReceived += Conversation_ContextDataReceived;
            e.Conversation.StateChanged += Conversation_StateChanged;
            ((InstantMessageModality)e.Conversation.Modalities[ModalityTypes.InstantMessage]).InstantMessageReceived += MainWindow_InstantMessageReceived;
        }

        /// <summary>
        /// Updates UI with new IM message text
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void MainWindow_InstantMessageReceived(object sender, MessageSentEventArgs e)
        {
            this.Dispatcher.Invoke(
                new ControlContentUpdateDelegate(ControlContentUpdate), 
                new object[] { InboundIM_Textblock,  e.Text });
        }

        /// <summary>
        /// Sends initial conversation context when a) local user selected Start Conversation radio button 
        /// and b) the resulting new conversation is active.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Conversation_StateChanged(object sender, ConversationStateChangedEventArgs e)
        {
            this.Dispatcher.Invoke(new ControlContentUpdateDelegate(ControlContentUpdate), new object[] { ConversationStatus_Label,  e.NewState.ToString() });
            if (_StartConversation == false)
            {
                return;
            }
            if (e.NewState == ConversationState.Active)
            {
                try
                {
                    System.Collections.Generic.Dictionary<ContextType, object> initialContext = new System.Collections.Generic.Dictionary<ContextType, object>();
                    initialContext.Add(ContextType.ApplicationId, _AppId);
                    initialContext.Add(ContextType.ApplicationData, "Initial Context");
                    _conversation.BeginSendInitialContext(
                        initialContext,
                        (ar) =>
                        {
                            _conversation.EndSendContextData(ar);
                        },
                        null);

                }

                // this exception is raised if the _AppId GUID string is not found in the system registry as a ContextPackage subkey
                catch (ItemNotFoundException inf)
                {
                    MessageBox.Show("ItemNotFound exception on send initial context: " + inf.Message);
                }
            }

        }

        /// <summary>
        /// Sends first IM message to activate the new conversation and updates UI with
        /// the display name of the added conversation participant
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_ParticipantAdded(object sender, ParticipantCollectionChangedEventArgs e)
        {
            if (!e.Participant.IsSelf)
            {
                ((InstantMessageModality)_conversation.Modalities[ModalityTypes.InstantMessage]).BeginSendMessage(
                    "Hi", 
                    (ar) => 
                    {
                        ((InstantMessageModality)_conversation.Modalities[ModalityTypes.InstantMessage]).EndSendMessage(ar);
                    }
                    , null);

                this.Dispatcher.Invoke(
                    new ControlContentUpdateDelegate(ControlContentUpdate), 
                    new object[] 
                    {
                        Participant_Label,
                       
                        "Participant: " + e.Participant.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString()
                    });

            }
        }

        /// <summary>
        /// Displays the received context data string in the UI list box
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Conversation_ContextDataReceived(object sender, Microsoft.Lync.Model.Conversation.ContextEventArgs e)
        {
            if (e.ApplicationId != _AppId)
            {
                return;
            }
            if (e.ContextDataType.ToLower() == "text/plain")
            {
                this.Dispatcher.Invoke(
                    new ControlContentUpdateDelegate(ControlContentUpdate), 
                    new object[] { Inbound_Listbox,  e.ContextData.ToString() });
            }
        }

        /// <summary>
        /// Displays the initial context received string in the UI list box.
        /// This event is not raised in this code when Lync is not in UI suppressed mode.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Conversation_InitialContextReceived(object sender, Microsoft.Lync.Model.Conversation.InitialContextEventArgs e)
        {
            if (e.ApplicationId != _AppId)
            {
                return;
            }
            this.Dispatcher.Invoke(
                new ControlContentUpdateDelegate(ControlContentUpdate), 
                new object[] { Inbound_Listbox,  e.ApplicationData.ToString() });

        }

        /// <summary>
        /// Updates the properties of controls owned by the UI thread
        /// </summary>
        /// <param name="labelToUpdate">object. The control to be updated</param>
        /// <param name="newValue">string. The new content, text, or list item value</param>
        private delegate void ControlContentUpdateDelegate(object labelToUpdate, string newValue);

        private void ControlContentUpdate(object labelToUpdate,  string newValue)
        {
            string ControlType = labelToUpdate.GetType().Name;
            if (ControlType == "Label")
            {
                System.Windows.Controls.Label alabel = (System.Windows.Controls.Label)labelToUpdate;
                alabel.Content = newValue;
            }
            else if (ControlType == "TextBlock")
            {
                System.Windows.Controls.TextBlock aBlock = (System.Windows.Controls.TextBlock)labelToUpdate;
                aBlock.Text = newValue;
            }
            else if (ControlType == "TextBox")
            {
                System.Windows.Controls.TextBox aBlock = (System.Windows.Controls.TextBox)labelToUpdate;
                aBlock.Text = newValue;
            }
            else if (ControlType == "ListBox")
            {
                System.Windows.Controls.ListBox aList = (System.Windows.Controls.ListBox)labelToUpdate;
                aList.Items.Add(newValue);
            }
        }

        /// <summary>
        /// Signs the user in if not signed in or adds a conversation if the user is already signed in
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void StartConversation_Radio_Checked(object sender, RoutedEventArgs e)
        {
            _LyncClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;

            //Set flag to be read in the Client.StateChanged event.
            //In StateChanged event logic: If flag is set and the state changes to SignedIn, then add a conversation
            _StartConversation = true;

            if (_LyncClient.State == ClientState.SignedOut)
            {
                //Sign-in operation raises StateChanged event on client when user is signed in.
                _LyncClient.BeginSignIn(
                    "danilop@contoso.com",
                    "danilop@contoso.com",
                    "danilop",
                    (ar2) =>
                    {
                        _LyncClient.EndSignIn(ar2);
                    },
                    null);
            }
            else if (_LyncClient.State == ClientState.SignedIn)
            {
                _conversation = _LyncClient.ConversationManager.AddConversation();
            }

        }

        /// <summary>
        /// Signs the user in to Lync and registers for the Conversation added event.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void WaitForInvite_Radio_Checked(object sender, RoutedEventArgs e)
        {
            if (_LyncClient.State == ClientState.SignedOut)
            {
                _LyncClient.BeginSignIn(
                    "danilop@contoso.com", 
                    "danilop@contoso.com", 
                    "danilop", 
                    (ar2) => 
                    {
                        _LyncClient.EndSignIn(ar2);
                    }, 
                    null);
            }
            //This event is raised when user is invited to a conversation.
            _LyncClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;

        }

        /// <summary>
        /// Sends additional conversation context information
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SendText_Button_Click(object sender, RoutedEventArgs e)
        {
            if (_conversation == null)
            {
                return;
            }
            if (_conversation.State != ConversationState.Active)
            {
                return;
            }
            _conversation.BeginSendContextData(
                _AppId,
                "text/plain",
                OutboundContext_Textbox.Text,
                (ar) => 
                {
                    _conversation.EndSendContextData(ar);
                },
                null);
        }

        /// <summary>
        /// On window closing, shuts down Lync if THIS application instance initialized Lync.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Window_Closing(object sender, System.ComponentModel.CancelEventArgs e)
        {
            if (_thisInitializedLync != true)
            {
                return;
            }
            if (_LyncClient.State == ClientState.SignedIn)
            {
                _LyncClient.BeginSignOut(
                    (ar) =>
                    {
                        _LyncClient.EndSignOut(ar);
                    },
                    null);
            }
            if (_LyncClient.State == ClientState.SignedOut)
            {
                _LyncClient.BeginShutdown(
                    (ar) =>
                    {
                        _LyncClient.EndShutdown(ar);
                    },
                    null);
            }
        }

    }
}
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

