---
title: 'How to: Transfer a Lync audio conversation'
TOCTitle: 'How to: Transfer a Lync audio conversation'
ms:assetid: 0b4a623b-277d-4470-915b-e8edb5026f57
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937258(v=office.15)
ms:contentKeyID: 50877076
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Transfer a Lync audio conversation

Learn how to programmatically transfer a Microsoft Lync 2013 audio call by using Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Call transfer overview<br />
Prerequisites<br />
Transfer an audio conversation<br />
Handle events<br />
Code examples: Audio conversations<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Call transfer overview

To transfer an active audio conversation, you must obtain the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance on the conversation you'll transfer and a [Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) instance representing the person receiving the transferred call. Your application must be able to handle all of the outcomes of the transfer operation. A transfer operation can result in the acceptance of the transfer by a target user or rejection by the same user. When a transfer is rejected, your application is responsible for reacting to the rejection by retrieving the audio/video modality from a hold state or terminating the call. You handle a series of events on the conversation audio/video modality to monitor the progress of the transfer.

The state and the availability of specific actions such as hold, retrieve, transfer, connect, and disconnect must be monitored after a transfer operation is initiated. While a transfer is pending, you cannot retrieve, connect, or disconnect a call. If the transfer is accepted, you're disconnected from the call with no further action on the part of your application. If the transfer is rejected, the retrieve and disconnect actions are available. The conversation state is set to active.

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
<td><p>When forwarding or transferring a conversation using the audio/video modality, the instant messaging modality is connected to the target participant automatically. When a call is transferred to a public switch telephone network (PSTN) telephone, video and IM are disconnected and cannot be reconnected.</p></td>
</tr>
</tbody>
</table>

The following table lists modality actions and their availability while a conversation transfer is pending.

<table style="width:67%;">
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Modality action</strong></p></th>
<th><p><strong>Availability</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Hold</p></td>
<td><p>True</p></td>
</tr>
<tr class="even">
<td><p>Retrieve</p></td>
<td><p>False</p></td>
</tr>
<tr class="odd">
<td><p>Transfer</p></td>
<td><p>False</p></td>
</tr>
</tbody>
</table>

The following table lists modality actions and their availability while a conversation transfer has been rejected.

<table style="width:67%;">
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Modality action</strong></p></th>
<th><p><strong>Availability</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Hold</p></td>
<td><p>False</p></td>
</tr>
<tr class="even">
<td><p>Retrieve</p></td>
<td><p>True</p></td>
</tr>
<tr class="odd">
<td><p>Transfer</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for transferring a call are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

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
<td><p><a href="conversation-modalities.md">Conversation modalities</a></p></td>
<td><p>Describes how the <a href="https://msdn.microsoft.com/library/jj274796(v=office.15)">Microsoft.Lync.Model.Conversation.Modality</a> class represents a mode of communication in a conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="conversation-participants.md">Conversation participants</a></p></td>
<td><p>Describes how users are represented in conversations as participants.</p></td>
</tr>
</tbody>
</table>

## Transfer an audio conversation

### To transfer an audio conversation

1.  Get the [LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance and verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Get a connected instance of [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\))
    
    The conversation direction can be incoming or outgoing. For information about starting an audio conversation, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md).

3.  Register for the [StateChanged](https://msdn.microsoft.com/library/jj278070\(v=office.15\)) event on the [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) instance.

4.  Get the **AVModality** instance from the collection of modalities on the [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) instance.
    
    Read the [Modalities](https://msdn.microsoft.com/library/jj275560\(v=office.15\)) property. Use the [ModalityTypes](https://msdn.microsoft.com/library/jj274831\(v=office.15\)).**AudioVideo** enumerator as an index to specify which modality to get.

5.  Register for the [ModalityStateChanged](https://msdn.microsoft.com/library/jj278080\(v=office.15\)) and [ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) events on the conversation [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance.

6.  Get a [Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) instance that resolves to the user you target for the transfer.
    
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
    <td><p>If the target user is not a contact in one of the groups exposed by <a href="https://msdn.microsoft.com/library/jj277988(v=office.15)">Groups</a>, you can obtain the contact by searching for the contact using the Microsoft Lync 2013 API search feature or you can call into <strong>GetContactByuri(string)</strong> if you have the URI of the target user.</p>
    <p>For information about searching for a contact, see <a href="https://msdn.microsoft.com/library/jj933159(v=office.15)">How to: Search for a contact or distribution group</a>.</p></td>
    </tr>
    </tbody>
    </table>

7.  To start the transfer operation, call into the [BeginTransfer](https://msdn.microsoft.com/library/jj293455\(v=office.15\)) or [BeginTransfer](https://msdn.microsoft.com/library/jj293455\(v=office.15\)) method of the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance. Pass the target contact as the first argument of the method call. If you're transferring a call to a public switched telephone network (PSTN) phone, voicemail or other type of contact endpoint, call the overload of **BeginTransfer** and pass the [ContactEndpoint](https://msdn.microsoft.com/library/jj276722\(v=office.15\)) representing the transfer target.

8.  Catch the series of [ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) events raised by the audio/video modality.
    
    As the availability of hold, retrieve, and transfer change as the transfer operation progresses, your event callback for these events is invoked. If the transfer is rejected, the retrieve, disconnect, and transfer options are made available. If the transfer is accepted, your event callback for these events is not invoked.
    
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
    <td><p>You should use these events to trigger the update of call action button controls you place on your UI. For example, when the hold action is not available, disable a hold button on your form.</p></td>
    </tr>
    </tbody>
    </table>

9.  Catch the series of [StateChanged](https://msdn.microsoft.com/library/jj278070\(v=office.15\)) events raised by the conversation.
    
    After completing the transfer operation, your event callback for these events is invoked. If the transfer is accepted, your event callback is invoked and the state of the conversation is [ConversationState](https://msdn.microsoft.com/library/jj277587\(v=office.15\)).**Terminated**. If the transfer is rejected, your event callback is invoked and the state of the conversation is [ConversationState](https://msdn.microsoft.com/library/jj277587\(v=office.15\)).**Active**.
    
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
    <td><p>The conversation state changes several times while the transfer operation is in progress. You receive the event indicating the conversation is active before the transfer is accepted or rejected, and again if the transfer is rejected. Each time you handle the event with this conversation state, you must evaluate the availability of the retrieve action on the audio/video modality (step 8). If the conversation becomes active and the retrieve action is available, the transfer is rejected.</p></td>
    </tr>
    </tbody>
    </table>

## Handle events

**Audio/Video modality [ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) event**

### To handle call transfer events

  - Check the [Action](https://msdn.microsoft.com/library/jj276590\(v=office.15\)) and [IsAvailable](https://msdn.microsoft.com/library/jj293614\(v=office.15\)) properties. If the action is [ModalityAction](https://msdn.microsoft.com/library/jj266957\(v=office.15\)).**Retrieve**, .**Disconnect**, .**RemoteTransfer**, .**ConsultativeTransfer**, **LocalTransfer**, or **Forward**, then you get the [IsAvailable](https://msdn.microsoft.com/library/jj293614\(v=office.15\)) property. If true, the transfer was rejected. In this case, you also receive a conversation state changed event indicating the conversation is now active.

**Conversation [StateChanged](https://msdn.microsoft.com/library/jj278070\(v=office.15\)) event**

  - Read the [NewState](https://msdn.microsoft.com/library/jj294024\(v=office.15\)) property. The resulting enumerator indicates the state of the transfer operation.
    
    If the state is [ConversationState](https://msdn.microsoft.com/library/jj277587\(v=office.15\)).**Terminated**, then the transfer is accepted and you should unregister for conversation and modality events and dispose of the conversation. If the state is .**Active** and the audio/video modality can be retrieved, disconnected, transferred, or forwarded, then the transfer operation was rejected.

## Code examples: Audio conversations

### Class field declarations

The following declarations are added to your custom class. You initiate \_AVModality with the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) obtained from the [Modalities](https://msdn.microsoft.com/library/jj275560\(v=office.15\)) property of the active conversation.

```csharp
        private AVModality _AVModality;
        private LyncClient _LyncClient;

        /// <summary>
        /// Updates a form control based on action.
        /// </summary>
        /// <param name="action">UIDelegateAction. The action to perform on a control.</param>
        /// <param name="formControl">object. The form control to act on.</param>
        /// <param name="updateValue">updateValue. The value to set on the control property.</param>
        delegate void UpdateFormControlDelegate(UIDelegateAction action, object formControl, object updateValue);

    enum UIDelegateAction
    { 
        SetButtonEnableState = 0,
        SetAllButtonsEnableState = 1,
        SetButtonText = 2,
        SetLabelText = 3,
        CloseForm = 4,
        ShutdownForm = 5
    }
```

### Transfer a call

The following example uses an active [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) instance where the audio/video modality is connected to a remote user.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The example only illustrates the tasks needed to transfer a call. For an example of starting an audio conversation, see <a href="how-to-start-a-lync-audio-conversation.md">How to: Start a Lync audio conversation</a>.</p></td>
</tr>
</tbody>
</table>

```csharp
        /// <summary>
        /// Performs a "blind transfer" on the active conversation
        /// </summary>
        /// <param name="targetURI">string. Uri string resolving to a contact or a telephone such as a mobile phone.</param>
        private void TransferConversation(string targetURI)
        {
            try
            {
                Contact TargetContact = _LyncClient.ContactManager.GetContactByUri(targetURI);
                if (TargetContact != null)
                {
                    List<string> _context = new List<string>();
                    Object[] asyncState = { ModalityState.Transferring, _context, _AVModality };
                    _AVModality.BeginTransfer(TargetContact, TransferOptions.None, TransferModalityCallback, asyncState);
                }
            }
            catch (ArgumentException) { 
                MessageBox.Show("Entered Uri is not valid " + targetURI); 
            }
            catch (ItemNotFoundException) { 
                MessageBox.Show("Entered Uri could not be resolved to a Contact " + targetURI); 
            }

        }
```

### Transfer operation callback

The following example is called asynchronously on the Lync thread when the transfer operation completes.

```csharp
        /// <summary>
        /// Called on the LyncClient worker thread when a call transfer operation completes.
        /// </summary>
        /// <param name="ar">IAsyncResult. The state of the asynchronous operation.</param>
        private void TransferModalityCallback(IAsyncResult ar)
        {
            if (ar.IsCompleted == true)
            {
                _ConsultTransferTargetConversation = null;
                Object[] _asyncState = (Object[])ar.AsyncState;
                ModalityState _targetState = (ModalityState)_asyncState[0];
                IList<string> _contextProperties = (List<string>)_asyncState[1];
                ((AVModality)_asyncState[2]).EndTransfer(out _targetState, out _contextProperties, ar);

                if (_targetState == ModalityState.Disconnected)
                {
                    this.Invoke(
                        new UpdateFormControlDelegate(UpdateFormControl),
                        new object[] {UIDelegateAction.SetAllButtonsEnableState, 
                        null, 
                        false });
                }
            }
        }
```

### Modality.ActionAvailabilityChanged event

Handle the event to discover ability to hold, retrieve, and transfer. Event is raised when your ability to do any of these actions changes. When transferring, actions change. When transfer is rejected, actions change.

```csharp
        /// <summary>
        /// The availability of an action on the audio/video modality has changed. This event triggers the enable state of
        /// MainForm action buttons.
        /// </summary>
        /// <param name="sender">object. the AVModality instance whose action availability has changed.</param>
        /// <param name="e">ModalityActionAvailabilityChangedEventArgs. Event state data providing the action and availability that changed.</param>
        void _AVModality_ActionAvailabilityChanged(object sender, ModalityActionAvailabilityChangedEventArgs e)
        {
            string HoldButtonText = string.Empty;
            switch (e.Action)
            {
                case ModalityAction.Hold:
                    if (e.IsAvailable == true)
                    {
                        HoldButtonText = "Hold Conversation";
                    }
                    if (e.IsAvailable == false)
                    {
                        HoldButtonText = "Pick up Conversation";
                    }
                    break;
                case ModalityAction.LocalTransfer:
                    this.Invoke(
                        new UpdateFormControlDelegate(UpdateFormControl),
                        new object[] {UIDelegateAction.SetButtonEnableState, 
                            Transfer_Button, 
                            e.IsAvailable });
                    break;
            }

            if (HoldButtonText.Length > 0)
            {
                this.Invoke(
                    new UpdateFormControlDelegate(UpdateFormControl),
                    new object[] {UIDelegateAction.SetButtonText, 
                        Hold_Button, 
                        HoldButtonText });
            }
        }
```

### ConversationStateChanged event

Use **ConversationState.Inactive** when a call is placed on hold after a call transfer. Use **ConversationState.Active** when transfer is rejected. After the transfer is rejected, the call must be retrieved.

```csharp
        /// <summary>
        /// Handles event raised when the state of an active conversation has changed. 
        /// </summary>
        /// <param name="source">Conversation. The active conversation that raised the state change event.</param>
        /// <param name="data">ConversationStateChangedEventArgs. Event data containing state change data</param>
        void Conversation_ConversationChangedEvent(object source, ConversationStateChangedEventArgs data)
        {
            UpdateFormControlDelegate del = new UpdateFormControlDelegate(UpdateFormControl);
            if (data.NewState == ConversationState.Inactive)
            {
                MessageBox.Show("Transfer is in progress.", "Conversation State Changed");
            }
            if (data.NewState == ConversationState.Active)
            {
                if (((Conversation)source).Modalities[ModalityTypes.AudioVideo].CanInvoke(ModalityAction.Retrieve) || ((Conversation)source).Modalities[ModalityTypes.AudioVideo].CanInvoke(ModalityAction.Transfer))
                {
                    MessageBox.Show("Transfer has been rejected.", "Conversation State Changed");
                }
            }
            if (data.NewState == ConversationState.Terminated)
            {
                MessageBox.Show("Conversation state is terminated", "Conversation State Changed");
                // Update form status label text with current state of conversation.
            }
        }
```

### Windows form control update helper

The following example is called using the delegate declared as a class field. This example is invoked on the Lync thread and the event data is marshaled to the UI thread by the **Invoke** call.

```csharp
        /// <summary>
        /// Updates a form control based on action.
        /// </summary>
        /// <param name="action">UIDelegateAction. The action to perform on a control.</param>
        /// <param name="formControl">object. The form control to act on.</param>
        /// <param name="updateValue">updateValue. The value to set on the control property.</param>
        private void UpdateFormControl(UIDelegateAction action, object formControl, object updateValue)
        {
            switch (action)
            { 
                case UIDelegateAction.CloseForm:
                    System.Windows.Forms.Form formToClose = (System.Windows.Forms.Form)formControl;
                    formToClose.Close();
                    break;
                case UIDelegateAction.SetButtonEnableState:
                    System.Windows.Forms.Button buttonToToggle = (System.Windows.Forms.Button)formControl;
                    buttonToToggle.Enabled = (Boolean)updateValue;
                    break;
                case UIDelegateAction.SetAllButtonsEnableState:
                    Park_Button.Enabled = (Boolean)updateValue;
                    Hold_Button.Enabled = (Boolean)updateValue;
                    ConsultTransfer_Button.Enabled = (Boolean)updateValue;
                    Transfer_Button.Enabled = (Boolean)updateValue;
                    CompleteConsult_Button.Enabled = (Boolean)updateValue;
                    break;
                case UIDelegateAction.SetButtonText:
                    System.Windows.Forms.Button buttonToUpdate = (System.Windows.Forms.Button)formControl;
                    buttonToUpdate.Text = (string)updateValue;
                    break;
                case UIDelegateAction.SetLabelText:
                    System.Windows.Forms.Label labelToUpdate = (System.Windows.Forms.Label)formControl;
                    labelToUpdate.Text = (string)updateValue;
                    break;
                case UIDelegateAction.ShutdownForm:
                    this._ClientModel.Dispose();
                    this.Close();
                    break;
            }
        }
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

