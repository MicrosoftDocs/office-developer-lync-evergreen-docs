---
title: 'How to: Park and unpark a Lync audio conversation'
TOCTitle: 'How to: Park and unpark a Lync audio conversation'
ms:assetid: 4fcc4bf9-ee96-44c1-b5e6-5ff19944b093
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937317(v=office.15)
ms:contentKeyID: 50877148
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Park and unpark a Lync audio conversation

Learn how the Microsoft Lync 2013 call park feature can be used programmatically with Microsoft Lync 2013 SDK and provides a call hold and call park feature.

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
Call park overview<br />
Prerequisites<br />
Park an audio conversation<br />
What is the SafeRetrieveUri property used for?<br />
Retrieve a parked conversation<br />
Code examples: Lync audio conversations<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Call park overview

Parking a call is simply sending a conversation to the Microsoft Lync Server 2013 call park server and then disconnecting locally. Unparking a call is starting a new conversation and inviting the call parked on the server to the new conversation, thereby unparking the call and connecting the user who is picking up the parked call.

With the call park feature, a user simultaneously places a call on hold and sends the call to a network call-park service where another user can retrieve the call. You do not need to know which user will pick the call up from the network call-park service. While the call is parked on the network, you can broadcast the call park URI of the parked call to multiple potential users. One of these users can retrieve the call from the network call-park service using the orbit of the parked call. Broadcasting the orbit gives unintended users access to the parked call. If this is a concern, you should identify a target user and directly transfer the call instead of parking it.

Local client resources and network bandwidth resources are not dedicated to maintaining the state of the conversation. The only state object that a local client application should maintain is the string object representing the parked call orbit. A network call-park service typically maintains a limited number of orbits on which you can park a call. If an orbit is not available, a park request fails. To avoid using an orbit unnecessarily, you should transfer a call if you have determined a specific transfer target. While a call participant is on hold in the network call-park service, an audio stream configured by an administrator is streamed to the participant. This feature is configured using Lync Server Control Panel.

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
<td><p>You can park an audio/video call, however only the audio portion of the call is parked. The video channel is disconnected. You must reconnect the video channel when the call is picked up from a call park orbit.</p></td>
</tr>
</tbody>
</table>

In the following procedure, a local client application places a conversation on a network call-park service. The procedure concludes by showing how a different user retrieves the parked call represented by the broadcasted orbit. The procedure creates a new conversation and adds the parked call as a participant. To park a call, use the [BeginPark](https://msdn.microsoft.com/en-us/library/jj266985\(v=office.15\)) method of the conversation. When a call is parked, retrieve the call using the [CallParkOrbit](https://msdn.microsoft.com/en-us/library/jj294115\(v=office.15\)) property of the conversation.

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
<td><p>The call park feature is not available when Microsoft Lync Server 2013 is in branch-datacenter resiliency mode.</p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for parking a Lync audio conversation are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Park an audio conversation

The following figure illustrates the classes, methods, and events used in the process of parking an audio conversation.

![OCOM\_ParkCall](images/JJ937317.OCOM_ParkCall(Office.15).png "OCOM_ParkCall")

### To park an audio conversation

1.  Declare an instance of [CallParkOrbit](https://msdn.microsoft.com/en-us/library/jj294115\(v=office.15\)) as a private class field.

2.  Add an audio conversation.
    
    For more information, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md).
    
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
    <td><p>You can park any active audio or audio/video conversation regardless of the origin. When parking an audio/video conversation, the video channel of the conversation is disconnected. If you want to display video, you must reconnect the video channel when picking up a park conversation.</p></td>
    </tr>
    </tbody>
    </table>

3.  Call the [CanInvoke](https://msdn.microsoft.com/en-us/library/jj277273\(v=office.15\)) method. If true is returned, go to the next step. Otherwise, you should verify the conversation is connected and not on hold.

4.  Call the [BeginPark](https://msdn.microsoft.com/en-us/library/jj266985\(v=office.15\)) method on the conversation with an asynchronous callback method conforming to the signature of **System.AsyncCallback** as the first argument.

5.  In the callback method, call the [Conversation.EndPark](https://msdn.microsoft.com/en-us/library/jj276992\(v=office.15\)) method.

6.  Handle the [Conversation.StateChanged](https://msdn.microsoft.com/en-us/library/jj278070\(v=office.15\)) event and run the following logic if the new state is [Microsoft.Lync.Model.Conversation.ConversationState](https://msdn.microsoft.com/en-us/library/jj277587\(v=office.15\))**.Parked**.
    
    Get the [CallParkOrbit](https://msdn.microsoft.com/en-us/library/jj294115\(v=office.15\)) that holds the parked call and read the [Properties](https://msdn.microsoft.com/en-us/library/jj266972\(v=office.15\)) property collection with the [ConversationProperty](https://msdn.microsoft.com/en-us/library/jj266982\(v=office.15\)).**CallParkOrbit** enumerator. Get the orbit of the parked call by reading the [FriendlyOrbit](https://msdn.microsoft.com/en-us/library/jj274862\(v=office.15\)) property. If you want to give other users a reference to the parked call, you must provide the string value of [FriendlyOrbit](https://msdn.microsoft.com/en-us/library/jj274862\(v=office.15\)) to all potential users. An example of a mechanism you can use is the IM conversation you can create with a participant list that includes users who can retrieve the parked call. You can send the **FriendlyOrbit** string to each participant as message text.

## What is the SafeRetrieveUri property used for?

Use the [SafeRetrieveUri](https://msdn.microsoft.com/en-us/library/jj267963\(v=office.15\)) property if you intend for the local user to retrieve her own parked call. In the following scenario, the [SafeRetrieveUri](https://msdn.microsoft.com/en-us/library/jj267963\(v=office.15\)) property should be used. Suppose Mary calls Bob. Bob parks Mary on orbit 123. Mary decides not to wait until her call is picked up from a park orbit and hangs up. Orbit 123 becomes available for another parked call. Michael and Steven are having a conversation at the same time. Michael parks Steven on the now free orbit 123. Bob tries to retrieve Mary using the **FriendlyOrbit** property and obtains the call at orbit 123. Bob is surprised to discover he is talking to Steven instead of Mary.

If Bob had used the **SafeRetrieveUri** property, the network call-park service would have gracefully failed to retrieve the call at orbit 123. **SafeRetrieveUri** is used when you want to be sure that you do not pick up a call that you did not park.

## Retrieve a parked conversation

These procedures assume that a user has obtained the parked call orbit broadcast by the user who parked the call originally. The procedures create a new audio conversation and add the parked call as the remote user. For information about starting an audio conversation, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md).

### To retrieve a parked conversation

1.  Register for [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)).

2.  Call into [AddConversation](https://msdn.microsoft.com/en-us/library/jj276176\(v=office.15\)) to create a new conversation specifying the audio/video modality.

3.  Register for [ParticipantAdded](https://msdn.microsoft.com/en-us/library/jj275759\(v=office.15\)) on the new conversation returned in the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event handler.

4.  Verify that a participant can be added to the new conversation by calling into [CanInvoke](https://msdn.microsoft.com/en-us/library/jj277273\(v=office.15\)), passing [ConversationAction](https://msdn.microsoft.com/en-us/library/jj276195\(v=office.15\)).**AddParticipant**. If true is returned, proceed to the next step of the walkthrough.

5.  Create a new [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) by passing either a safe retrieve URI or friendly orbit URI into **GetContactByUri(string)** and add the returned [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) to a new [Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) by calling into [AddParticipant](https://msdn.microsoft.com/en-us/library/jj266479\(v=office.15\)).

6.  Call the [BeginConnect(AsyncCallback, Object)](https://msdn.microsoft.com/en-us/library/jj268193\(v=office.15\)) method on the audio/video modality returned by [Modalities](https://msdn.microsoft.com/en-us/library/jj275560\(v=office.15\))\[[ModalityTypes](https://msdn.microsoft.com/en-us/library/jj274831\(v=office.15\)).**AudioVideo**\] to allow both the local and remote endpoints to accept the conversation. You must call **EndConnect** after calling **BeginConnect**. You can call **EndConnect** on your UI thread or you can call it within a **System.AsyncCallback** method you pass into **BeginConnect**.

## Code examples: Lync audio conversations

The following example parks a conversation named myConversation and designates the ConversationCallback method as the callback for the [BeginPark](https://msdn.microsoft.com/en-us/library/jj266985\(v=office.15\)) method.

``` csharp
        /// <summary>
        /// Parks a conversation.
        /// </summary>
        private void ParkConversation()
        {
            _ParkOrbit = null;
            try
            {
                if (_Conversation.CanInvoke(ConversationAction.Park))
                {
                    _Conversation.BeginPark(CallParkCallback, _Conversation);
                }
            }
            catch (NotReadyException e)
            {
                MessageBox.Show("Conversation park: Lync Exception: " + e.Message);
            }

        }
```

The following example handles the [ActionAvailabilityChanged](https://msdn.microsoft.com/en-us/library/jj293249\(v=office.15\)) event raised by the [Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) instance when the call is parked or unparked.

``` csharp
        void Conversation_ActionAvailabilityChanged(Conversation source, ConversationActionAvailabilityEventArgs data)
        {
            // Is this event the result of a Park operation?
            if (data.Action == ConversationAction.ParkAction)
            {
                if (source.State == ConversationState.Parked)
                {
                    MessageBox.Show("Conversation Parked");
                }
                else if (source.State == ConversationState.Active)
                {
                    MessageBox.Show("Conversation Activated");
                }
            }
        }
```

The next example is the callback method for the call to the [BeginPark](https://msdn.microsoft.com/en-us/library/jj266985\(v=office.15\)) method. This method retrieves and stores locally the value of the [CallParkOrbit](https://msdn.microsoft.com/en-us/library/jj294115\(v=office.15\)) property in the [ConversationProperty](https://msdn.microsoft.com/en-us/library/jj266982\(v=office.15\)) enumeration of the conversation that was parked. The example reads the **AsyncState** property that allows it to associate its invocation with the call park operation that initiated the callback.

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
<td><p>It is not necessary to provide a callback method to the call into park if you handle the <a href="https://msdn.microsoft.com/en-us/library/jj293249(v=office.15)">ActionAvailabilityChanged</a> event. You can obtain the <a href="https://msdn.microsoft.com/en-us/library/jj294115(v=office.15)">CallParkOrbit</a> instance from the <strong>Conversation</strong> instance in the <a href="https://msdn.microsoft.com/en-us/library/jj293249(v=office.15)">ActionAvailabilityChanged</a> event handler if you do not provide an asynchronous callback method to be invoked by the conversation when it is parked.</p>
<p>If a network call-park service is not available, the operation completes its run but does not succeed.</p></td>
</tr>
</tbody>
</table>

``` csharp
        /// <summary>
        /// Called on the LyncClient worker thread when asynchronous call park operation completes.
        /// </summary>
        /// <param name="ar">IAsyncResult. The state of the asynchronous operation.</param>
        private void CallParkCallback(IAsyncResult ar)
        {
            if (ar.IsCompleted == true)
            {
                object orbitProperty = ((Conversation)ar.AsyncState).Properties[ConversationProperty.CallParkOrbit];
                ((Conversation)ar.AsyncState).EndPark(ar);
                _ParkOrbit = orbitProperty as CallParkOrbit;
                ((Conversation)ar.AsyncState).End();
                _Conversation = null;
            }
        }
```

For an example of starting an audio conversation in order to pick up a parked call, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md). Use the friendly orbit URI or safe retrieve orbit URI string to get a [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) to be added to the new audio conversation.

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

