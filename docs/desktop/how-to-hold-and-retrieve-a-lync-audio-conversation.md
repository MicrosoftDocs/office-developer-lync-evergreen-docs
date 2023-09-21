---
title: 'How to: Hold and retrieve a Lync audio conversation'
TOCTitle: 'How to: Hold and retrieve a Lync audio conversation'
ms:assetid: b9befd44-6382-41eb-8e2d-41036940ddda
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933173(v=office.15)
ms:contentKeyID: 50877313
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Hold and retrieve a Lync audio conversation

Learn how to programmatically hold and retrieve a Microsoft Lync 2013 audio call by using Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Audio conversation overview<br />
Hold or retrieve an audio conversation<br />
Code examples: Lync audio conversations<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Audio conversation overview

To hold or retrieve an audio conversation, you call methods on the audio/video modality from the [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) class. If a conversation includes both the IM modality and audio/video modality, the conversation can still be held, forwarded, or transferred. These actions must be performed on the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance of the conversation.

## Prerequisites

The prerequisites for holding and retrieving a call are as follows:

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

## Hold or retrieve an audio conversation

### To hold and retrieve an audio conversation

1.  Get a connected instance of [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)).
    
    For information about starting an audio conversation, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md).

2.  Register for the [StateChanged](https://msdn.microsoft.com/library/jj278070\(v=office.15\)) event on the [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) instance.

3.  Get the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance from the collection of modalities on the [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) instance.

4.  Read the [Modalities](https://msdn.microsoft.com/library/jj275560\(v=office.15\)) property and use the [ModalityTypes](https://msdn.microsoft.com/library/jj274831\(v=office.15\)).**AudioVideo** enumerator as an index to specify which modality to get.

5.  Register for the [ModalityStateChanged](https://msdn.microsoft.com/library/jj278080\(v=office.15\)) and [ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) events on the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance.

6.  To hold a conversation, call into the [BeginHold](https://msdn.microsoft.com/library/jj293226\(v=office.15\)) method on the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance.

7.  To catch the asynchronous result of the hold operation, pass a callback method in the first argument and a state object in the second argument. Otherwise, pass null values in both arguments.

8.  Retrieve a conversation. If the state of the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance is **ModalityState.Hold**, call **Retrieve** on the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance using the same arguments.

9.  To catch the asynchronous result of the retrieve operation, pass a callback method in the first argument and a state object in the second argument. Otherwise, pass null values in both arguments.

10. Handle the [StateChanged](https://msdn.microsoft.com/library/jj278070\(v=office.15\)) event raised by the [Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) instance when the state of the conversation changes to [ConversationState](https://msdn.microsoft.com/library/jj277587\(v=office.15\)).**Inactive**.

11. Handle the [ModalityStateChanged](https://msdn.microsoft.com/library/jj278080\(v=office.15\)) event raised by the [AVModality](https://msdn.microsoft.com/library/jj274580\(v=office.15\)) instance when the state of the modality changes to [ModalityState](https://msdn.microsoft.com/library/jj293265\(v=office.15\)).**OnHold**.

## Code examples: Lync audio conversations

The examples in this section hold or retrieve a call and handle all related events.

### Hold or retrieve a call

The following example holds or retrieves a call.

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
<td><p>The example only illustrates the tasks needed to hold or retrieve a call. For an example of a complete event handler, see <a href="how-to-start-a-lync-audio-conversation.md">How to: Start a Lync audio conversation</a>.</p></td>
</tr>
</tbody>
</table>

```csharp
        /// <summary>
        /// Hold or retrieve a conversation
        /// </summary>
        private void HoldConversation(Conversation pConversation)
        {
            if (pConversation.Modalities[ModalityTypes.AudioVideo].State == ModalityState.OnHold)
            {
                object[] asyncState = { pConversation.Modalities[ModalityTypes.AudioVideo], "RETRIEVE" };
                pConversation.Modalities[ModalityTypes.AudioVideo].BeginRetrieve(ModalityCallback, asyncState);
            }
            else if (pConversation.Modalities[ModalityTypes.AudioVideo].State == ModalityState.Connected)
            {
                object[] asyncState = { pConversation.Modalities[ModalityTypes.AudioVideo], "HOLD" };
                IAsyncResult ar = pConversation.Modalities[ModalityTypes.AudioVideo].BeginHold(ModalityCallback, asyncState);
            }

        }
```

### ConversationStateChange event

The following example is invoked by a **Conversation** instance when the state of the conversation changes.

```csharp
         /// <summary>
        /// Handles event raised when the state of an active conversation has changed. 
        /// </summary>
        /// <param name="source">Conversation. The active conversation that raised the state change event.</param>
        /// <param name="data">ConversationStateChangedEventArgs. Event data containing state change data.</param>
        void Conversation_ConversationChangedEvent(object source, ConversationStateChangedEventArgs data)
        {
            if (data.NewState == ConversationState.Inactive)
            {
                MessageBox.Show("Conversation is on hold");
                //Enable a hold retrieve button.
            }
            if (data.NewState == ConversationState.Active)
            {
                MessageBox.Show("Conversation is active");
                //Enable a hold button.
            }
        }
```

### Modality operation callback method

The following example is invoked by an instance of **AVModality** when a modality operation is complete.

```csharp
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

### Audio/video modality ActionAvailabilityChanged event

```csharp
        void myAVModality_ActionAvailabilityChanged(object sender, ModalityActionAvailabilityChangedEventArgs e)
        {
            switch (e.Action)
            {
                case ModalityAction.Hold:
                    if (e.IsAvailable == true)
                    {
                        MessageBox.Show("Call can be placed on hold.");
                    }
                    break;
                case ModalityAction.Retrieve:
                    if (e.IsAvailable == true)
                    {
                        MessageBox.Show("Call is on hold and can be retrieved");
                    }
                    break;
            }
        }
```

### ModalityStateChanged event

The following example handles the **ModalityStateChanged** event raised by the audio/video modality when a call is placed on hold or retrieved from hold.

```csharp
        /// <summary>
        /// Handles the Modality state changed event for a Conversation
        /// </summary>
        /// <param name="source">Modality. Modality whose state has changed.</param>
        /// <param name="data">ModalityStateChangedEventArgs. Old and new modality states.</param>
        void _AVModality_ModalityStateChanged(object sender, ModalityStateChangedEventArgs e)
        {
                switch (e.NewState)
                {
                    case ModalityState.OnHold:
                        //Enable a call transfer button.
                        break;
                    case ModalityState.Connecting:

                        //Update connecting status string on UI.
                        break;
                    case ModalityState.Forwarding:
                        //Update connecting status string on UI.
                        break;
                    case ModalityState.Transferring:
                        //Update connecting status string on UI.
                        break;
                    case ModalityState.Connected:
                        //Update connecting status string on UI.
                        //Enable a call hold button.
                        break;
                }
        }
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

