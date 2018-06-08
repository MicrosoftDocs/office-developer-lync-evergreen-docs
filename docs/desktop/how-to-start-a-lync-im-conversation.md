---
title: 'How to: Start a Lync IM conversation'
TOCTitle: 'How to: Start a Lync IM conversation'
ms:assetid: 356b4dba-139f-48bf-a8d5-df445524d998
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937298(v=office.15)
ms:contentKeyID: 50877126
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Start a Lync IM conversation

Learn how to use Microsoft Lync 2013 SDK to programmatically start a Microsoft Lync 2013 conversation, invite a user, and send the first instant messaging (IM) text.

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
IM conversation programming overview<br />
Start an IM conversation<br />
Handle events<br />
Send and receive messages<br />
Code examples: Lync IM conversations<br />
Additional resources</p></td>
<td><div class="caption">
Watch the video: Start an IM conversation
</div>
<br />
&gt; [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/b50363b0-139b-4333-aa4f-898286190d9e]</td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for starting an IM conversation are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

The following topics describe the three components of a Lync 2013 conversation.

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
<td><p>Describes the role of the conversation manager in creating conversations.</p></td>
</tr>
<tr class="even">
<td><p><a href="conversation-modalities.md">Conversation modalities</a></p></td>
<td><p>Describes how conversation modes are encapsulated by modalities.</p></td>
</tr>
<tr class="odd">
<td><p><a href="conversation-participants.md">Conversation participants</a></p></td>
<td><p>Describes how conversation participants are encapsulated.</p></td>
</tr>
</tbody>
</table>

## IM conversation programming overview

Conversations can only be started when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding an IM feature to your UI.

A Lync 2013 IM conversation is represented by three API objects:

  - **Conversation** object

  - **Participant** object collection

  - **Modality** object collection

Each of these objects exposes properties, methods, and events that play a role in programmatic interaction with the conversation. The following diagram shows you how the objects interact.

  
![LyncIM\_Article\_StartCall](images/JJ937298.LyncIM_Article_StartCall(Office.15).png "LyncIM_Article_StartCall")

## Start an IM conversation

The following procedure obtains a conversations manager and adds the conversation.

### To start an IM conversation

1.  Create a callback method that handles the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event.

2.  Create a callback method that handles the [ParticipantAdded](https://msdn.microsoft.com/en-us/library/jj275759\(v=office.15\)) event.

3.  Get the [LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance and verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

4.  Get the [ConversationManager](https://msdn.microsoft.com/en-us/library/jj266018\(v=office.15\)) class instance by reading the [ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)) property.

5.  Register for the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event.

6.  Call [AddConversation](https://msdn.microsoft.com/en-us/library/jj276176\(v=office.15\)).
    
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
    <td><p>If you have a conference URL and intend to join the associated conference, call <a href="https://msdn.microsoft.com/en-us/library/jj276639(v=office.15)">JoinConference</a> instead of <strong>AddConversation</strong>. An instance of <a href="https://msdn.microsoft.com/en-us/library/jj276988(v=office.15)">Conversation</a> is returned.</p></td>
    </tr>
    </tbody>
    </table>

## Handle events

The next two procedures are examples of the steps to create event handlers for conversation-related events. Examples of the event handler methods are included later in this topic.

### Handle the ConversationAdded event

Complete the following steps within a callback method that handles [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)).

### To handle the ConversationAdded event

1.  Check the modality state of the IM modality on the added conversation.
    
    If the modality is [ModalityState](https://msdn.microsoft.com/en-us/library/jj293265\(v=office.15\)).**Notified**, the conversation was not started by the local user. For this procedure, handle the event for only the conversation added by the local user.
    
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
    <td><p>The <a href="https://msdn.microsoft.com/en-us/library/jj266470(v=office.15)">ConversationAdded</a> event is raised when either a local user starts a conversation or a remote user invites the local user to a new conversation.</p></td>
    </tr>
    </tbody>
    </table>

2.  Register for conversation state change events on the [Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) instance.

3.  Call the [CanInvoke](https://msdn.microsoft.com/en-us/library/jj277273\(v=office.15\)) method and pass [ConversationAction](https://msdn.microsoft.com/en-us/library/jj276195\(v=office.15\)).**AddParticipant**. Continue the steps if a true value is returned.

4.  If you can add a participant, get a [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) instance to add to the conversation by calling into [GetContactByUri](https://msdn.microsoft.com/en-us/library/jj274481\(v=office.15\)).
    
    A contact that resolves to the passed URI is returned.

5.  Get the IM [Modality](https://msdn.microsoft.com/en-us/library/jj274796\(v=office.15\)) instance from the [Modalities](https://msdn.microsoft.com/en-us/library/jj275560\(v=office.15\)) property of the [Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) instance in the data parameter of the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event handler: data.Conversation.Modalities\[ModalityTypes.InstantMessagingModality\].

### Handle the ParticipantAdded event

Complete the following steps within a callback method that handles [ParticipantAdded](https://msdn.microsoft.com/en-us/library/jj275759\(v=office.15\)).

### To handle the ParticipantAdded event

1.  Read the [IsSelf](https://msdn.microsoft.com/en-us/library/jj267304\(v=office.15\)) property of the added participant exposed by [Participant](https://msdn.microsoft.com/en-us/library/jj293211\(v=office.15\)) property.
    
    The following steps should not be executed for the self-participant.

2.  Get the remote participant [InstantMessageModality](https://msdn.microsoft.com/en-us/library/jj266036\(v=office.15\)) from [Participant](https://msdn.microsoft.com/en-us/library/jj293211\(v=office.15\)) by reading the [Modalities](https://msdn.microsoft.com/en-us/library/jj267336\(v=office.15\)) property collection and returning the [InstantMessageModality](https://msdn.microsoft.com/en-us/library/jj266036\(v=office.15\)).
    
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
    <td><p>The IM modality is auto-accepted at both the local and remote endpoints. You do not need to call <strong>Connect</strong> on this modality. The IM modality is ready to use when you obtain it from the conversation's modalities collection.</p></td>
    </tr>
    </tbody>
    </table>

3.  Cast the **Modality** class instance to the [InstantMessageModality](https://msdn.microsoft.com/en-us/library/jj266036\(v=office.15\)) class to obtain instant messaging receive features.

4.  Register for [InstantMessageReceived](https://msdn.microsoft.com/en-us/library/jj293201\(v=office.15\)) message received events to catch incoming instant messages from other participants.

5.  Register for participant events on the remote participant.

## Send and receive messages

As the previous figure illustrates, the procedure to send an IM message involve many more steps than those you execute to receive and render an instant message from a remote participant. In both cases, you use the [InstantMessageContentType](https://msdn.microsoft.com/en-us/library/jj293461\(v=office.15\)) enumeration to either set the message format of a message you send or determine the message format of a message you receive. A sent or received message is encapsulated in a generic **IDictionary** that uses an enumerator of [InstantMessageContentType](https://msdn.microsoft.com/en-us/library/jj293461\(v=office.15\)) as the key and a formatted message string as the value of the dictionary entry.

### Send a message

Sending an instant message involves setting the local user’s composing state to typing, capturing and sending text, and setting the user’s composing state to idle. These actions are performed in this sequence and each depends on the completion of the previous step. You should use the **System.AsyncCallback** method you define for each operation to initiate the next operation in the sequence.

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
<td><p>If you send IM text in a format not supported by the target IM client, a <a href="https://msdn.microsoft.com/en-us/library/jj294075(v=office.15)">LyncClientException</a> is raised on your client. The exception message text is &quot;Generic COM Exception. Code is 0x80EF019F.&quot; To avoid this exception, send text formatted as plain text. If you use any other formatting, you should enclose <a href="https://msdn.microsoft.com/en-us/library/jj293829(v=office.15)">EndSendMessage</a> in an try/catch block that catches <a href="https://msdn.microsoft.com/en-us/library/jj294075(v=office.15)">LyncClientException</a>.</p></td>
</tr>
</tbody>
</table>

### To send a message

1.  Verify that the conversation is active and the conversation IM modality is connected.

2.  When the local user begins to type in the form entry control designated to accept message text, call into [CanInvoke](https://msdn.microsoft.com/en-us/library/jj267958\(v=office.15\)), passing [ModalityAction](https://msdn.microsoft.com/en-us/library/jj266957\(v=office.15\)). **SetIsTyping**. If you cannot set this property, skip the next step.

3.  Call [BeginSetComposing](https://msdn.microsoft.com/en-us/library/jj274836\(v=office.15\)) on the conversation IM modality and pass true as the first argument.

4.  In the callback invoked by the previous step or upon completion of typing in the form control, instantiate an instance of IDictionary\<InstantMessageContentType, string\> and add an entry containing a key as enumerator for the message text formatting and value as message text.

5.  Call [BeginSendMessage](https://msdn.microsoft.com/en-us/library/jj274588\(v=office.15\)) and pass your message dictionary as the first argument and then pass a **System.AsyncCallback** method in the second argument.

6.  In the callback invoked after the previous step:
    
    1.  Call [EndSendMessage](https://msdn.microsoft.com/en-us/library/jj293829\(v=office.15\)). You must surround this call with a try/catch block, catching the [LyncClientException](https://msdn.microsoft.com/en-us/library/jj294075\(v=office.15\)). A remote contact can change his or her availability to DND or offline at any time. Such an availability change causes this exception to be raised when your message cannot be delivered to the remote contact.
    
    2.  Call [BeginSetComposing](https://msdn.microsoft.com/en-us/library/jj274836\(v=office.15\)) on the conversation IM modality. Pass false as the first argument.

### Receive a message

The following procedure handles the [InstantMessageReceived](https://msdn.microsoft.com/en-us/library/jj293201\(v=office.15\)) event by getting the message text formatting enumerator for the incoming message and parsing the message text according to the specified formatting.

### To receive a message

1.  Get the message contents as IDictionary\<InstantMessageContentType,string\> by reading [Contents](https://msdn.microsoft.com/en-us/library/jj267964\(v=office.15\)).

2.  A single message contains text in one of several formats enumerated by [InstantMessageContentType](https://msdn.microsoft.com/en-us/library/jj293461\(v=office.15\)). For each format sent, an entry exists in the dictionary you get from the previous step. Iterate on the dictionary items and assemble a display string based on the format and contents of the dictionary.
    
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
    <td><p>Lync 2013 formats IM text as <a href="https://msdn.microsoft.com/en-us/library/jj293461(v=office.15)">InstantMessageContentType</a><strong>.Html</strong> or .<strong>Ink</strong>. Previous versions of the client format messages as .<strong>RichText</strong>. For the best interoperability experience, you should send messages in .<strong>PlainText</strong>.</p></td>
    </tr>
    </tbody>
    </table>

3.  Display the resulting string.

## Code examples: Lync IM conversations

The procedure assumes that you have created a Windows.Forms object and populated it with a **TextBox** control for user entry.

### Start a conversation

The following example creates a new conversation by calling into [AddConversation](https://msdn.microsoft.com/en-us/library/jj276176\(v=office.15\)) on [ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)).

``` csharp
        private string myRemoteParticipantUri;
        private Conversation _Conversation;

        //assume example has obtained and signed in to this LyncClient instance.
        private LyncClient _LyncClient;
        public void StartIMConversation(string participantUri)
        {
            _LyncClient.ConversationManager.ConversationAdded += ConversationsManager_ConversationAdded;
            myRemoteParticipantUri = participantUri;
            _Conversation = _LyncClient.ConversationManager.AddConversation();
        }
```

### Register for conversation events

The following example registers for [Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) events. The [Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) obtained from [Conversation](https://msdn.microsoft.com/en-us/library/jj276980\(v=office.15\)) is a reference to the new conversation. You can register for events on the **Conversation** using the [Conversation](https://msdn.microsoft.com/en-us/library/jj276980\(v=office.15\)) instance.

``` csharp
        /// Handles ConversationAdded state change event raised on ConversationsManager
        /// <param name="source">ConversationsManager: The source of the event</param>
        /// <param name="data">ConversationsManagerEventArgs The event data. The incoming Conversation is obtained here</param>
        void ConversationsManager_ConversationAdded(Object source, ConversationManagerEventArgs data)
        {
            // Register for Conversation state changed events.
            data.Conversation.ParticipantAdded += Conversation_ParticipantAdded;
            data.Conversation.StateChanged += Conversation_ConversationChangedEvent;

            // Add a remote participant.
            data.Conversation. AddParticipant(_LyncClient.ContactManager.GetContactByUri(this.myRemoteParticipantUri));

        }
```

### ParticipantAdded event

The following example handles the [ParticipantAdded](https://msdn.microsoft.com/en-us/library/jj275759\(v=office.15\)) event. The example event handler gets the IM modality from the modality collection on the new participant and registers for messages received from the participant. [InstantMessageReceived](https://msdn.microsoft.com/en-us/library/jj293201\(v=office.15\)) is raised on any participant when that participant sends a message.

``` csharp
        /// <summary>
        /// ParticipantAdded callback handles ParticpantAdded event raised by Conversation
        /// </summary>
        /// <param name="source">Conversation Source conversation.</param>
        /// <param name="data">ParticpantCollectionEventArgs Event data</param>
        void Conversation_ParticipantAdded(Object source, ParticipantCollectionChangedEventArgs data)
        {
            
            if (data.Participant.IsSelf == false)
            {
                if (((Conversation)source).Modalities.ContainsKey(ModalityTypes.InstantMessage))
                {
                    ((InstantMessageModality)data.Participant.Modalities[ModalityTypes.InstantMessage]).InstantMessageReceived += myInstantMessageModality_MessageReceived;
                    ((InstantMessageModality)data.Participant.Modalities[ModalityTypes.InstantMessage]).IsTypingChanged += myInstantMessageModality_ComposingChanged;
               }
            }
        }
```

### User starts typing

A user’s cursor has entered a text entry control and the example sets the [IsTyping](https://msdn.microsoft.com/en-us/library/jj276342\(v=office.15\)) property to true.

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
<td><p>The conversation IM modality must be used to set the typing property for the local user rather than the IM modality of the local participant.</p></td>
</tr>
</tbody>
</table>

``` csharp
        private void txtMessage_Enter(object sender, EventArgs e)
        {
            if ((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).CanInvoke(ModalityAction.SetIsTyping))
            {
                ((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).BeginSetComposing(true, ComposingCallback, null);
            }
        }
```

### User completes typing

A user’s cursor has left a text entry control and the example sets the [IsTyping](https://msdn.microsoft.com/en-us/library/jj276342\(v=office.15\)) property to false.

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
<td><p>The conversation IM modality must be used to set the typing property for the local user rather than the IM modality of the local participant.</p></td>
</tr>
</tbody>
</table>

``` csharp
        private void txtMessage_Leave(object sender, EventArgs e)
        {
            if ((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).CanInvoke(ModalityAction.SetIsTyping))
            {
                ((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).BeginSetComposing(false, ComposingCallback, null);
            }
        }
```

### Send a message in plain text

The following example sends the text content of a UI text box to a remote conversation participant.

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
<td><p>The conversation IM modality must be used to send an instant message to other users instead of the local participant’s IM modality.</p></td>
</tr>
</tbody>
</table>

``` csharp
        private void SendMessage(string messageToSend)
        {
            try
            {
                IDictionary<InstantMessageContentType, string> textMessage = new Dictionary<InstantMessageContentType, string>();
                textMessage.Add(InstantMessageContentType.PlainText, messageToSend);
                if (((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).CanInvoke(ModalityAction.SendInstantMessage))
                {
                    ((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).BeginSendMessage(
                        textMessage
                        , SendMessageCallback
                        , textMessage);
                }
            }
            catch (LyncPlatformException e)
            {
                MessageBox.Show("Client Platform Exception: " + e.Message, "Send Message");
            }
        }
```

### SendMessage callback

The following example callback method is invoked by [InstantMessageModality](https://msdn.microsoft.com/en-us/library/jj266036\(v=office.15\)) after [BeginSendMessage](https://msdn.microsoft.com/en-us/library/jj274588\(v=office.15\)) is complete. Verify the asynchronous operation results if you want to see whether the message was sent successfully.

``` csharp
        /// <summary>
        /// Async callback method invoked by InstantMessageModality instance when SendMessage completes
        /// </summary>
        /// <param name="_asyncOperation">IAsyncResult The operation result</param>
        /// 
        private void SendMessageCallback( IAsyncResult ar)
        {
            ((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).BeginSetComposing(false, ComposingCallback, null);
            if (ar.IsCompleted == true)
            {

                try
                {
                     ((InstantMessageModality)_Conversation.Modalities[ModalityTypes.InstantMessage]).EndSendMessage(ar);
                }
                catch (LyncClientException lce)
                {
                    MessageBox.Show("Lync Client Exception on EndSendMessage " + lce.Message);
                }

            }
        }
```

### ComposingChanged event

The following example handles the event raised when a participant starts or stops typing.

``` csharp
        void myInstantMessageModality_ComposingChanged(object source, IsTypingChangedEventArgs data)
        {
            if (data.IsTyping == true
            {
                MessageBox.Show(((InstantMessageModality)source).Participant.Contact.GetContactInformation(ContactInformationType.DisplayName) + " is typing");
            }
        }
```

### InstantMessageModality MessageReceived event

The following example handles the [InstantMessageReceived](https://msdn.microsoft.com/en-us/library/jj293201\(v=office.15\)) and uses the **PlainText** enumerator. If this enumerator is used, message content is rendered as plain text regardless of how it was formatted by the sender. If the incoming message contains data that cannot be rendered as plain text, the data is not rendered.

``` csharp
        /// <summary>
        /// Callback is invoked when IM Modality state changes upon receipt of message
        /// </summary>
        /// <param name="source">InstantMessageModality Modality </param>
        /// <param name="data">SendMessageEventArgs The new message.</param>
        void myInstantMessageModality_MessageReceived(Object source, MessageSentEventArgs data)
        {
            IDictionary<InstantMessageContentType,string> messageFormatProperty = data.Contents;
            if (messageFormatProperty.ContainsKey(InstantMessageContentType.PlainText))
            {
                string outVal = string.Empty;
                string Sender = (string)((InstantMessageModality)source).Participant.Contact.GetContactInformation(ContactInformationType.DisplayName);
                if (messageFormatProperty.TryGetValue(InstantMessageContentType.PlainText, out outVal))
                {
                    //outVal will be an empty string if the received message contains only an image.
                    MessageBox.Show("New message: " + outVal);
                    //invoke delegate that sets text property of a form browser control with outVal
                }
            }
        }
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

