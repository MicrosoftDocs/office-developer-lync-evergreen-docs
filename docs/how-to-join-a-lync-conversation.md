---
title: 'How to: Join a Lync conversation'
TOCTitle: 'How to: Join a Lync conversation'
ms:assetid: 04d46079-25e3-4cf6-be61-48533cc7665b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937250(v=office.15)
ms:contentKeyID: 50877062
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Join a Lync conversation

Learn how to use Microsoft Lync 2013 SDK to let a user join a Microsoft Lync 2013 conversation after receiving an invitation from another Lync 2013 user or a federated user.


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
Prepare for conversation invitations<br />
Handle a conversation invitation<br />
Code examples: Lync conversations<br />
Additional resources</p></td>
<td><p><img src="images/JJ937288.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><br />
<a href="http://code.msdn.microsoft.com/lync-2013-accept-requests-2ae187c4">Accept request using the AcceptConversation method</a><br />
</p></td>
</tr>
</tbody>
</table>


## Prerequisites

The prerequisites for joining a Microsoft Lync 2013 conversation are as follow:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Prepare for conversation invitations

Conversation invitations are only sent when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding an IM feature to your UI.

### To prepare for conversation invitations

1.  Create a method called using the System.EventHandler\<[ConversationManagerEventArgs](conversationmanagereventargs-class-microsoft-lync-model-conversation_2.md)\> delegate to handle the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event that is raised on an incoming invitation.
    
    You accept or reject a conversation invitation in this method. The details of this delegate method are described in the following steps.

2.  Get the [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md) and make sure the [State](conversation-state-property-microsoft-lync-model-conversation_2.md) is [ConversationState](conversationstate-enumeration-microsoft-lync-model-conversation_2.md).**SignedIn**.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

3.  Get the [Microsoft.Lync.Model.Conversation.ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) class instance by reading the [ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md) property of [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md).

4.  Register for the [ConversationManager.ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event on [ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md).

5.  Get the **Contact** instance representing the local user from the signed-in [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md) instance, and then verify that this contact can participate in conversations using the conversation's modalities.

## Handle a conversation invitation

You execute the following steps within a method that handles [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md).


> [!IMPORTANT]
> <P>A conversation whose only notified modality is the <A href="instantmessagemodality-class-microsoft-lync-model-conversation_2.md">InstantMessageModality</A> should be accepted but the modality is automatically connected. You can send and receive messages as soon as the IM conversation is active.</P>



### To handle a conversation invitation

1.  Check the state of the [Microsoft.Lync.Model.Conversation.InstantMessageModality](instantmessagemodality-class-microsoft-lync-model-conversation_2.md) of the added conversation.
    
    If the state is [ModalityState.Notified](https://msdn.microsoft.com/en-us/library/gg255331\(v=office.15\)), the added conversation is the result of an invitation and must be accepted or rejected. If accepted, the **AVModality** must be connected as shown in step 5.
    

    > [!IMPORTANT]
    > <P><A href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md">ConversationAdded</A> is also raised when your application creates a new conversation and generates an invitation to a remote user. In this case, the conversation modality state is <A href="modalitystate-enumeration-microsoft-lync-model-conversation_2.md">ModalityState</A>.<STRONG>Disconnected</STRONG> when the new conversation is obtained in the <A href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md">ConversationAdded</A> event.</P>



2.  Verify that there is an active audio device configured on the local machine by reading the [ActiveAudioDevice](devicemanager-activeaudiodevice-property-microsoft-lync-model-device_2.md) property.
    
    If the property returns a null value, an audio device is not configured on the local computer.

3.  Reject the incoming call if the previous step shows that there is no active audio device and then call [Reject](modality-reject-method-microsoft-lync-model-conversation_2.md) on the conversation [Microsoft.Lync.Model.Conversation.AudioVideo.AVModality](avmodality-class-microsoft-lync-model-conversation-audiovideo_2.md).

4.  Accept the conversation modality notification by calling [Modality.Accept](modality-accept-method-microsoft-lync-model-conversation_2.md) on the **Modality** instance.

5.  Connect to the audio/video modality to activate the audio portion of the conversation.

## Code examples: Lync conversations

The following example accepts or rejects an incoming conversation invitation based on the modalities specified for the conversation.

``` csharp
        /// <summary>
        /// Handles ConversationAdded state change event raised on ConversationsManager
        /// </summary>
        /// <param name="source">ConversationsManager The source of the event.</param>
        /// <param name="data">ConversationsManagerEventArgs The event data. The incoming Conversation is obtained here.</param>
        void ConversationManager_ConversationAdded(object sender, ConversationManagerEventArgs data)
        {

            Boolean IncomingAV = false;
            System.Text.StringBuilder sb = new System.Text.StringBuilder();
            //Is this an audio/video invitation?
            if (data.Conversation.Modalities[ModalityTypes.AudioVideo].State == ModalityState.Notified)
            {
                if (_LyncClient.DeviceManager.ActiveAudioDevice != null)
                {
                    sb.Append("Incoming call from ");
                    IncomingAV = true;
                }
                else
                {
                    data.Conversation.Modalities[ModalityTypes.AudioVideo].Reject(ModalityDisconnectReason.NotAcceptableHere);
                }
            }
            if (data.Conversation.Modalities[ModalityTypes.InstantMessage].State == ModalityState.Connected)
            {
                sb.Append("Incoming IM from ");
            }
            string callerName = data.Conversation.Participants[1].Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
            sb.Append(callerName);
            sb.Append(System.Environment.NewLine);
            sb.Append("Do you want to accept the invitiation?");
            if (System.Windows.Forms.MessageBox.Show(
                sb.ToString()
                , "Incoming Invitation"
                , System.Windows.Forms.MessageBoxButtons.YesNo
                , System.Windows.Forms.MessageBoxIcon.Question) == System.Windows.Forms.DialogResult.Yes)
            {
                data.Conversation.ParticipantAdded += Conversation_ParticipantAdded;
                data.Conversation.StateChanged += Conversation_ConversationChangedEvent;
                data.Conversation.ActionAvailabilityChanged += Conversation_ActionAvailabilityChanged;
                if (IncomingAV == true)
                {
                    InitiateAVStream(data.Conversation);
                }
            }
        }
```

The following example registers for participant events on the new conversation, accepts the conversation notification, and then connects to the conversation modality.

``` csharp
        /// <summary>
        /// Registers for events on a new conversation and connects to audio/video modality if call is incoming.
        /// </summary>
        /// <param name="pConversation">Conversation. New conversation.</param>
        private void InitiateAVStream(Conversation pConversation)
        {
            if (pConversation.State == ConversationState.Terminated)
            {
                return;
            }

            if (pConversation.Modalities[ModalityTypes.AudioVideo].CanInvoke(ModalityAction.Connect))
            {
                pConversation.Modalities[ModalityTypes.AudioVideo].ModalityStateChanged += _AVModality_ModalityStateChanged;
                pConversation.Modalities[ModalityTypes.AudioVideo].ActionAvailabilityChanged += _AVModality_ActionAvailabilityChanged;

                //Accept the notification. If Lync UI is enabled, incoming call notification is closed.
                pConversation.Modalities[ModalityTypes.AudioVideo].Accept();

                //Connect the AV modality and begin to send and received AV stream.
                object[] asyncState = { pConversation.Modalities[ModalityTypes.AudioVideo], "CONNECT" };
                pConversation.Modalities[ModalityTypes.AudioVideo].BeginConnect(ModalityCallback, asyncState);

            }
        }

        /// <summary>
        /// Called on the LyncClient worker thread when an audio/video modality action completes.
        /// </summary>
        /// <param name="ar">IAsyncResult. The state of the asynchronous operation.</param>
        private void ModalityCallback(IAsyncResult ar)
        {

            Object[] asyncState = (Object[])ar.AsyncState;
            try
            {
                if (ar.IsCompleted == true)
                {
                    if (asyncState[1].ToString() == "RETRIEVE")
                    {
                        ((AVModality)asyncState[0]).EndRetrieve(ar);
                    }
                    if (asyncState[1].ToString() == "HOLD")
                    {
                        ((AVModality)asyncState[0]).EndHold(ar);
                    }
                    if (asyncState[1].ToString() == "CONNECT")
                    {
                        ((AVModality)asyncState[0]).EndConnect(ar);
                    }
                    if (asyncState[1].ToString() == "FORWARD")
                    {
                        ((AVModality)asyncState[0]).EndForward(ar);
                    }
                }
            }
            catch (LyncClientExceptions)
            { }

        }
```

## Additional resources

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

