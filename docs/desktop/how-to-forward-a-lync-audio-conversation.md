---
title: 'How to: Forward a Lync audio conversation'
TOCTitle: 'How to: Forward a Lync audio conversation'
ms:assetid: 7c28e6c9-ad8a-4b33-b1a6-31794f52a746
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933092(v=office.15)
ms:contentKeyID: 50877224
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Forward a Lync audio conversation

Learn how to programmatically forward a Microsoft Lync 2013 audio call by using Microsoft Lync 2013 SDK.

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
Call forwarding overview<br />
Prerequisites<br />
Forward an audio conversation<br />
Handle conversation events<br />
Code examples: Audio conversations<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Call forwarding overview

To forward an incoming audio conversation, you must obtain the [AVModality](https://msdn.microsoft.com/en-us/library/jj274580\(v=office.15\)) on the conversation. You forward an audio conversation to either a **Contact** instance representing the person receiving the transferred call or a [ContactEndpoint](https://msdn.microsoft.com/en-us/library/jj276722\(v=office.15\)) representing a user’s phone. The conversation is forwarded by calling into [BeginForward](https://msdn.microsoft.com/en-us/library/jj274482\(v=office.15\)) on the [AVModality](https://msdn.microsoft.com/en-us/library/jj274580\(v=office.15\)) and pass the [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) or [ContactEndpoint](https://msdn.microsoft.com/en-us/library/jj276722\(v=office.15\)) as the first argument of the method.

The forwarding feature described in this topic does not create a set of call routing rules to be published on behalf of the local user. Instead, it implements client-side logic that responds to a previously routed call by forwarding it to another user.

When forwarding or transferring a conversation using the audio/video modality, the instant messaging modality is connected to the target participant automatically. When a call is transferred or forwarded to a public switch telephone network (PSTN) telephone, video and IM are disconnected and cannot be reconnected.

## Prerequisites

The prerequisites for forwarding an audio call are as follows:

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
<td><p>Describes how the <a href="https://msdn.microsoft.com/en-us/library/jj274796(v=office.15)">Microsoft.Lync.Model.Conversation.Modality</a> class represents a mode of communication in a conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="conversation-participants.md">Conversation participants</a></p></td>
<td><p>Describes how users are represented in conversations as participants.</p></td>
</tr>
</tbody>
</table>

## Forward an audio conversation

The client call forwarding operation should be started as soon as an audio call invitation is received by the platform. The earliest opportunity to forward the call is the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event. To forward an audio conversation, you must obtain the [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) instance to be forwarded from the event data argument.

### To forward an audio conversation

1.  Define an event callback method to handle the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event raised when an audio conversation is received.

2.  Get the [LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance and verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

3.  Register for the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event on the [ConversationManager](https://msdn.microsoft.com/en-us/library/jj266018\(v=office.15\)) instance.

## Handle conversation events

### To handle conversation events

1.  Check the [State](https://msdn.microsoft.com/en-us/library/jj276637\(v=office.15\)) of the audio/video modality on the new conversation triggering the event. If the state is [ModalityState](https://msdn.microsoft.com/en-us/library/jj293265\(v=office.15\)).**Notified**, you can forward the new conversation.

2.  Check the availability of the [ModalityAction](https://msdn.microsoft.com/en-us/library/jj266957\(v=office.15\)).**Forward** on the audio/video modality of the new conversation by calling into [CanInvoke](https://msdn.microsoft.com/en-us/library/jj267958\(v=office.15\)) on the modality. If **true** is returned, you can forward the conversation.
    
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
    <td><p>If you are forwarding to one of the local user’s phones, get the appropriate <a href="https://msdn.microsoft.com/en-us/library/jj275506(v=office.15)">Phone</a> instance by calling into <a href="https://msdn.microsoft.com/en-us/library/jj266043(v=office.15)">GetPhone</a>. You read the <a href="https://msdn.microsoft.com/en-us/library/jj277017(v=office.15)">Endpoint</a> property to get a <a href="https://msdn.microsoft.com/en-us/library/jj276722(v=office.15)">ContactEndpoint</a> that is passed into <strong>BeginForward</strong>.</p>
    <p>If you are forwarding to another user, get the appropriate <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Contact</a> or <a href="https://msdn.microsoft.com/en-us/library/jj276722(v=office.15)">ContactEndpoint</a> instance. Call into <strong>Forward</strong> and pass the <strong>Contact</strong> instance obtained in the previous step.</p></td>
    </tr>
    </tbody>
    </table>

## Code examples: Audio conversations

### Class field declarations

```csharp
        private LyncClient _LyncClient;
```

### ConversationAdded event

The following example handles the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event by forwarding any incoming audio conversation to a specified phone number.

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
<td><p>The example only illustrates the procedural tasks used to forward a call. For an example of a complete event handler, see <a href="how-to-start-a-lync-audio-conversation.md">How to: Start a Lync audio conversation</a>.</p></td>
</tr>
</tbody>
</table>

```csharp
        /// <summary>
        /// Handles ConversationAdded state change event raised on ConversationsManager
        /// </summary>
        /// <param name="source">ConversationsManager The source of the event.</param>
        /// <param name="data">ConversationsManagerEventArgs The event data. The incoming Conversation is obtained here.</param>
        void ConversationsManager_ConversationAdded(ConversationsManager source, ConversationsManagerEventArgs data)
        {
            if (data.Conversation.Modalities[ModalityTypes.AudioVideo].State == ModalityState.Notified)
            {
                Contact _ForwardContact = _LyncClient.ContactManager.GetContactByUri("TEL:+14255551212");
                object[] asyncState = { data.Conversation.Modalities[ModalityTypes.AudioVideo], "FORWARD" };
                data.Conversation.Modalities[ModalityTypes.AudioVideo].BeginForward(_ForwardContact, ModalityCallback, asyncState);
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
            catch (LyncPlatformException)
            { }
        }
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

