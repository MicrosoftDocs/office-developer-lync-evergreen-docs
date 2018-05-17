---
title: 'How to: Start a Lync audio conversation'
TOCTitle: 'How to: Start a Lync audio conversation'
ms:assetid: f3aae105-f30f-47a6-a5be-6bff50a25046
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933255(v=office.15)
ms:contentKeyID: 50877401
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Start a Lync audio conversation

Learn how to start a Microsoft Lync 2013 audio conversation by using methods in Microsoft Lync 2013 SDK.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Audio conversation overview<br />
Prerequisites<br />
Start an audio conversation<br />
Handle events<br />
Code examples: Audio conversations<br />
Next steps<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Audio conversation overview

Starting a Lync audio conversation involves creating a conversation with a local and remote participant and connecting to the remote participant using the participant’s audio/video modality. To complete this procedure, you must handle state change events on both the client’s [ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) instance and the conversation itself.

## Prerequisites

The prerequisites for starting an audio conversation are as follows:

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
<td><p><a href="conversation-manager.md">Conversation manager</a></p></td>
<td><p>Describes the role of the <a href="conversationmanager-class-microsoft-lync-model-conversation_2.md">Microsoft.Lync.Model.Conversation.ConversationManager</a> class in starting conversations and responding to incoming conversation invitations.</p></td>
</tr>
<tr class="even">
<td><p><a href="conversation-participants.md">Conversation participants</a></p></td>
<td><p>Describes how users are represented in conversations as participants.</p></td>
</tr>
</tbody>
</table>


## Start an audio conversation

Conversations can only be started when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding an audio call feature to your UI.

The following figure illustrates the classes, methods, and events used in the process of starting an audio conversation.

![OCOM\_StartAudioConversation](images/JJ933255.OCOM_StartAudioConversation(Office.15).png "OCOM_StartAudioConversation")

### To start an audio conversation

1.  Create a callback method that handles the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event.

2.  Create a callback method that handles the [ParticipantAdded](conversation-participantadded-event-microsoft-lync-model-conversation_2.md) event.

3.  Get the [LyncClient](lyncclient-class-microsoft-lync-model_2.md) instance and verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

4.  Get the [ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) instance by reading the [ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md) property of the [LyncClient](lyncclient-class-microsoft-lync-model_2.md) class instance.

5.  Register for the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event on the [ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) instance.

6.  Call the [AddConversation](conversationmanager-addconversation-method-microsoft-lync-model-conversation_2.md) method on the [ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) instance.

## Handle events

### To handle the ConversationAdded event

1.  Check the modality state of the audio/video modality on the added conversation.
    
    If the modality is [ModalityState](modalitystate-enumeration-microsoft-lync-model-conversation_2.md).**Notified**, the conversation was not started by the local user. For this procedure, handle the event for only the conversation added by the local user.
    

    > [!TIP]
    > <P>The <A href="conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md">ConversationAdded</A> event is raised when either a local user starts a conversation or a remote user invites the local user to a new conversation.</P>



2.  Register for state change events on the conversation.

3.  Call the [CanInvoke](conversation-caninvoke-method-microsoft-lync-model-conversation_2.md) method and pass [ConversationAction](conversationaction-enumeration-microsoft-lync-model-conversation_2.md).**AddParticipant**.

4.  If you can add a participant, get a [Contact](contact-class-microsoft-lync-model_2.md) instance to add to the conversation by calling into [GetContactByUri](contactmanager-getcontactbyuri-method-microsoft-lync-model_2.md).
    
    A contact that resolves to the passed URI is returned.

5.  Call the [AddParticipant](conversation-addparticipant-method-microsoft-lync-model-conversation_2.md) method on the conversation and pass the [Contact](contact-class-microsoft-lync-model_2.md) instance from step 4 as the contact argument.
    

    > [!IMPORTANT]
    > <P>If you add two or more participants to an audio conversation, the conversation is automatically converted to an audio conference and hosted on Microsoft Lync Server 2013. When it is converted to a conference, the conversation object is provisioned with conference properties that you can use to assign meeting access, lobby management, and presenter promotion. For information about audio meetings, see <A href="what-you-can-do-with-lync-meetings.md">What you can do with Lync meetings</A>.</P>




> [!IMPORTANT]
> <P>You must register for and handle events on both locally originated conversations and conversations you obtain by accepting an invitation from a remote user.</P>



### To handle the ParticipantAdded event

1.  Read the [IsSelf](participant-isself-property-microsoft-lync-model-conversation_2.md) property of the added participant exposed by [Participant](participantcollectionchangedeventargs-participant-property-microsoft-lync-model-conversation_2.md) property.
    
    The following steps should not be executed for the self-participant.

2.  Get the [AVModality](avmodality-class-microsoft-lync-model-conversation-audiovideo_2.md) from the [Modalities](conversation-modalities-property-microsoft-lync-model-conversation_2.md) property of the conversation in the source parameter of the callback method: source.Modalities\[ModalityTypes.AudioVideo\].

3.  Cast the obtained [Modality](modality-class-microsoft-lync-model-conversation_2.md) class instance to [AVModality](avmodality-class-microsoft-lync-model-conversation-audiovideo_2.md).

4.  Register for [ModalityStateChanged](modality-modalitystatechanged-event-microsoft-lync-model-conversation_2.md) on the audio/video modality to catch the [ModalityState](modalitystate-enumeration-microsoft-lync-model-conversation_2.md).**Connected** event that is raised after you connect to the modality.

5.  Register for participant events on the remote participant.

6.  Call the [BeginConnect](modality-beginconnect-method-microsoft-lync-model-conversation_2.md) method on this [AVModality](avmodality-class-microsoft-lync-model-conversation-audiovideo_2.md) instance to allow both the local and remote endpoints to accept the conversation. You must call [EndConnect](modality-endconnect-method-microsoft-lync-model-conversation_2.md) after calling **BeginConnect**. You can call **EndConnect** on your UI thread or you can call it within a **System.AsyncCallback** method you pass into **BeginConnect**.

## Code examples: Audio conversations

These procedures assume that you have created a **Windows.Forms** object and populated it with a textbox for entry of a contact’s URI and a button that you use to start a conversation. If you create a WPF application and use this example code, you must marshal event data using [System.Windows.Threading.Dispatcher.BeginInvoke(Delegate, Object\[\])](http://msdn.microsoft.com/en-us/library/cc190824.aspx).

The following example creates a new conversation by calling into the [AddConversation](conversationmanager-addconversation-method-microsoft-lync-model-conversation_2.md) method on an instance of the [ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md).

### Declarations

The following declarations provide this example with the ability to marshal event data to the UI thread from the Lync 2013 thread. UIUpdater is invoked using the UpdateFormControlDelegate so that updates to controls on the UI can be made.

``` csharp
using System;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Conversation.AudioVideo;

namespace CustomAudioConversation
{

    public partial class MainForm : Form
    {
        private string targetUri;
        private Conversation _Conversation;
        private LyncClient _LyncClient;
...
```

### Start a conversation

The following example registers for conversation manager events and starts the conversation. Assume the [LyncClient](lyncclient-class-microsoft-lync-model_2.md) was obtained using the steps in [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

``` csharp
public void StartConversation()
{
   _LyncClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
   _Conversation = _LyncClient.ConversationsManager.AddConversation();
}
```

### ConversationManager events

The following example registers for conversation instance events and adds a participant to the new conversation after verifying that the added conversation is the one started in the previous example.

``` csharp
        /// <summary>
        /// Called on the LyncClient worker thread by the ConversationManager instance when a conversation has been
        /// added to the Conversations collection on ConversationManager.
        /// A conversation is added when ConversationManager.AddConversation() is called on the UI thread or when a remote user
        /// is calling the local user.
        /// </summary>
        /// <param name="sender">object. A ConversationManager instance.</param>
        /// <param name="e">ConversationManagerEventArgs. The event state data object.</param>
        void ConversationManager_ConversationAdded(object sender, ConversationManagerEventArgs e)
        {
            //Conversation originated with remote SIP user
            if (e.Conversation.Modalities[ModalityTypes.AudioVideo].State != ModalityState.Notified)
            {
                if (e.Conversation.CanInvoke(ConversationAction.AddParticipant)
                {
                    e.Conversation.ParticipantAdded += Conversation_ParticipantAdded;
                    e.Conversation.AddParticipant(_LyncClient.ContactManager.GetContactByUri("bob@contoso.com"));
                }
            }
        }
```

### Conversation events

The previous example added a participant. This example handles the event raised when the participant is added. It obtains the [AVModality](avmodality-class-microsoft-lync-model-conversation-audiovideo_2.md) of the new conversation and begins to connect to the remote participant using this modality. When the modality is connected, a state change event for the modality is raised.


> [!TIP]
> <P>A collection of modalities is also surfaced by the new participant but you do not connect to the remote participant using these. The participant modality collection is only used for instant messaging.</P>



``` csharp
        /// <summary>
        /// ParticipantAdded callback handles ParticpantAdded event raised by Conversation
        /// </summary>
        /// <param name="source">Conversation Source conversation.</param>
        /// <param name="data">ParticpantCollectionEventArgs Event data</param>
        void Conversation_ParticipantAdded(object source, ParticipantCollectionChangedEventArgs data)
        {
            if (data.Participant.IsSelf != true)
            {
                if (((Conversation)source).Modalities[ModalityTypes.AudioVideo].CanInvoke(ModalityAction.Connect))
                {
                    object[] asyncState = { ((Conversation)source).Modalities[ModalityTypes.AudioVideo], "CONNECT" };
                    try
                    {
                         ((Conversation)source).Modalities[ModalityTypes.AudioVideo].ModalityStateChanged += _AVModality_ModalityStateChanged;
                         ((Conversation)source).Modalities[ModalityTypes.AudioVideo].BeginConnect(ModalityConnectOptions.None, ModalityCallback, asyncState);
                    }
                    catch (LyncPlatformException ce)
                    {
                        throw new Exception("Lync Platform Exception on BeginConnect: " + ce.Message);
                    }
                }
            }
        }
```

### Conversation modality operation callback

The following example calls [EndConnect](modality-endconnect-method-microsoft-lync-model-conversation_2.md) to complete the connect operation. Because several different modality operations can be executed, it is important that your callback method determines which started operation triggers the asynchronous callback. The example uses the asynchronous state property of **IAsyncResult** to indicate the operation that was started on the UI thread.

Calling the [EndConnect](modality-endconnect-method-microsoft-lync-model-conversation_2.md) method in the callback instead of in the UI thread prevents the example application from blocking while the call is connected.

``` csharp
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
            catch (LyncPlatformException)
            { }
        }
```

### Modality events

This example handles the modality state change event that is raised when the conversation audio/video modality has connected to the remote participant.


> [!WARNING]
> <P>You might experience an eventing delay after a participant endpoint has disconnected from a modality. For example, if an attempt to connect a participant to the audio modality ends in failure because the telephone number that was called is busy, you might not receive a modality state change event for the disconnect immediately.</P>



``` csharp
        /// <summary>
        /// Handles the Modality state changed event for a Conversation
        /// </summary>
        /// <param name="source">Modality. Modality whose state has changed.</param>
        /// <param name="data">ModalityStateChangedEventArgs. Old and new modality states.</param>
        void _AVModality_ModalityStateChanged(object sender, ModalityStateChangedEventArgs e)
        {
            switch (e.NewState)
            {
                case ModalityState.Connected:
                    MessageBox.Show(″Conversation audio is connected. You should say hello now.″);
                    break;
            }
        }
```

## Next steps

  - [How to: Park and unpark a Lync audio conversation](how-to-park-and-unpark-a-lync-audio-conversation.md)

  - [How to: Transfer a Lync audio conversation](how-to-transfer-a-lync-audio-conversation.md)

  - [How to: Hold and retrieve a Lync audio conversation](how-to-hold-and-retrieve-a-lync-audio-conversation.md)

  - [How to: Forward a Lync audio conversation](how-to-forward-a-lync-audio-conversation.md)

## Additional resources

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

