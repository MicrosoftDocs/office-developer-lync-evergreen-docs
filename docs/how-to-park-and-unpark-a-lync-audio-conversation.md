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


_**Applies to:** Lync 2013 | Lync Server 2013_

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


> [!TIP]
> <P>You can park an audio/video call, however only the audio portion of the call is parked. The video channel is disconnected. You must reconnect the video channel when the call is picked up from a call park orbit.</P>



In the following procedure, a local client application places a conversation on a network call-park service. The procedure concludes by showing how a different user retrieves the parked call represented by the broadcasted orbit. The procedure creates a new conversation and adds the parked call as a participant. To park a call, use the [BeginPark](conversation-beginpark-method-microsoft-lync-model-conversation_2.md) method of the conversation. When a call is parked, retrieve the call using the [CallParkOrbit](callparkorbit-class-microsoft-lync-model-conversation-audiovideo_2.md) property of the conversation.


> [!WARNING]
> <P>The call park feature is not available when Microsoft Lync Server 2013 is in branch-datacenter resiliency mode.</P>



## Prerequisites

The prerequisites for parking a Lync audio conversation are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Park an audio conversation

The following figure illustrates the classes, methods, and events used in the process of parking an audio conversation.

![OCOM\_ParkCall](images/JJ937317.OCOM_ParkCall(Office.15).png "OCOM_ParkCall")

### To park an audio conversation

1.  Declare an instance of [CallParkOrbit](callparkorbit-class-microsoft-lync-model-conversation-audiovideo_2.md) as a private class field.

2.  Add an audio conversation.
    
    For more information, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md).
    

    > [!TIP]
    > <P>You can park any active audio or audio/video conversation regardless of the origin. When parking an audio/video conversation, the video channel of the conversation is disconnected. If you want to display video, you must reconnect the video channel when picking up a park conversation.</P>



3.  Call the [CanInvoke](conversation-caninvoke-method-microsoft-lync-model-conversation_2.md) method. If true is returned, go to the next step. Otherwise, you should verify the conversation is connected and not on hold.

4.  Call the [BeginPark](conversation-beginpark-method-microsoft-lync-model-conversation_2.md) method on the conversation with an asynchronous callback method conforming to the signature of **System.AsyncCallback** as the first argument.

5.  In the callback method, call the [Conversation.EndPark](conversation-endpark-method-microsoft-lync-model-conversation_2.md) method.

6.  Handle the [Conversation.StateChanged](conversation-statechanged-event-microsoft-lync-model-conversation_2.md) event and run the following logic if the new state is [Microsoft.Lync.Model.Conversation.ConversationState](conversationstate-enumeration-microsoft-lync-model-conversation_2.md)**.Parked**.
    
    Get the [CallParkOrbit](callparkorbit-class-microsoft-lync-model-conversation-audiovideo_2.md) that holds the parked call and read the [Properties](conversation-properties-property-microsoft-lync-model-conversation_2.md) property collection with the [ConversationProperty](conversationproperty-enumeration-microsoft-lync-model-conversation_2.md).**CallParkOrbit** enumerator. Get the orbit of the parked call by reading the [FriendlyOrbit](callparkorbit-friendlyorbit-property-microsoft-lync-model-conversation-audiovideo_2.md) property. If you want to give other users a reference to the parked call, you must provide the string value of [FriendlyOrbit](callparkorbit-friendlyorbit-property-microsoft-lync-model-conversation-audiovideo_2.md) to all potential users. An example of a mechanism you can use is the IM conversation you can create with a participant list that includes users who can retrieve the parked call. You can send the **FriendlyOrbit** string to each participant as message text.

## What is the SafeRetrieveUri property used for?

Use the [SafeRetrieveUri](callparkorbit-saferetrieveuri-property-microsoft-lync-model-conversation-audiovideo_2.md) property if you intend for the local user to retrieve her own parked call. In the following scenario, the [SafeRetrieveUri](callparkorbit-saferetrieveuri-property-microsoft-lync-model-conversation-audiovideo_2.md) property should be used. Suppose Mary calls Bob. Bob parks Mary on orbit 123. Mary decides not to wait until her call is picked up from a park orbit and hangs up. Orbit 123 becomes available for another parked call. Michael and Steven are having a conversation at the same time. Michael parks Steven on the now free orbit 123. Bob tries to retrieve Mary using the **FriendlyOrbit** property and obtains the call at orbit 123. Bob is surprised to discover he is talking to Steven instead of Mary.

If Bob had used the **SafeRetrieveUri** property, the network call-park service would have gracefully failed to retrieve the call at orbit 123. **SafeRetrieveUri** is used when you want to be sure that you do not pick up a call that you did not park.

## Retrieve a parked conversation

These procedures assume that a user has obtained the parked call orbit broadcast by the user who parked the call originally. The procedures create a new audio conversation and add the parked call as the remote user. For information about starting an audio conversation, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md).

### To retrieve a parked conversation

1.  Register for [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md).

2.  Call into [AddConversation](conversationmanager-addconversation-method-microsoft-lync-model-conversation_2.md) to create a new conversation specifying the audio/video modality.

3.  Register for [ParticipantAdded](conversation-participantadded-event-microsoft-lync-model-conversation_2.md) on the new conversation returned in the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event handler.

4.  Verify that a participant can be added to the new conversation by calling into [CanInvoke](conversation-caninvoke-method-microsoft-lync-model-conversation_2.md), passing [ConversationAction](conversationaction-enumeration-microsoft-lync-model-conversation_2.md).**AddParticipant**. If true is returned, proceed to the next step of the walkthrough.

5.  Create a new [Contact](contact-class-microsoft-lync-model_2.md) by passing either a safe retrieve URI or friendly orbit URI into **GetContactByUri(string)** and add the returned [Contact](contact-class-microsoft-lync-model_2.md) to a new [Conversation](conversation-class-microsoft-lync-model-conversation_2.md) by calling into [AddParticipant](conversation-addparticipant-method-microsoft-lync-model-conversation_2.md).

6.  Call the [BeginConnect(AsyncCallback, Object)](modality-beginconnect-method-microsoft-lync-model-conversation_2.md) method on the audio/video modality returned by [Modalities](conversation-modalities-property-microsoft-lync-model-conversation_2.md)\[[ModalityTypes](modalitytypes-enumeration-microsoft-lync-model-conversation_2.md).**AudioVideo**\] to allow both the local and remote endpoints to accept the conversation. You must call **EndConnect** after calling **BeginConnect**. You can call **EndConnect** on your UI thread or you can call it within a **System.AsyncCallback** method you pass into **BeginConnect**.

## Code examples: Lync audio conversations

The following example parks a conversation named myConversation and designates the ConversationCallback method as the callback for the [BeginPark](conversation-beginpark-method-microsoft-lync-model-conversation_2.md) method.

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

The following example handles the [ActionAvailabilityChanged](modality-actionavailabilitychanged-event-microsoft-lync-model-conversation_2.md) event raised by the [Conversation](conversation-class-microsoft-lync-model-conversation_2.md) instance when the call is parked or unparked.

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

The next example is the callback method for the call to the [BeginPark](conversation-beginpark-method-microsoft-lync-model-conversation_2.md) method. This method retrieves and stores locally the value of the [CallParkOrbit](callparkorbit-class-microsoft-lync-model-conversation-audiovideo_2.md) property in the [ConversationProperty](conversationproperty-enumeration-microsoft-lync-model-conversation_2.md) enumeration of the conversation that was parked. The example reads the **AsyncState** property that allows it to associate its invocation with the call park operation that initiated the callback.


> [!TIP]
> <P>It is not necessary to provide a callback method to the call into park if you handle the <A href="modality-actionavailabilitychanged-event-microsoft-lync-model-conversation_2.md">ActionAvailabilityChanged</A> event. You can obtain the <A href="callparkorbit-class-microsoft-lync-model-conversation-audiovideo_2.md">CallParkOrbit</A> instance from the <STRONG>Conversation</STRONG> instance in the <A href="modality-actionavailabilitychanged-event-microsoft-lync-model-conversation_2.md">ActionAvailabilityChanged</A> event handler if you do not provide an asynchronous callback method to be invoked by the conversation when it is parked.</P>
> <P>If a network call-park service is not available, the operation completes its run but does not succeed.</P>



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

For an example of starting an audio conversation in order to pick up a parked call, see [How to: Start a Lync audio conversation](how-to-start-a-lync-audio-conversation.md). Use the friendly orbit URI or safe retrieve orbit URI string to get a [Contact](contact-class-microsoft-lync-model_2.md) to be added to the new audio conversation.

## Additional resources

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

