---
title: Making an outgoing IM call and sending messages
TOCTitle: Making an outgoing IM call and sending messages
ms:assetid: a782284c-7f62-4df1-98a7-7f92223b5227
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn756469(v=office.15)
ms:contentKeyID: 62525830
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Making an outgoing IM call and sending messages

Learn how to make outgoing IM calls to a contact and then send outgoing IM messages to the remote participant in your UCWA 1.0 Windows Store app in C\#/XMAL and XML.


**In this article**  
Before you start  
Overview of the process for making outgoing calls  
Get ready to make a call  
Make an outgoing IM call  
Handle events to monitor the progress of a call invitation  
Process communication-sourced events for outgoing calls  
Handle conversation-sourced events for outgoing calls  
Send outgoing IMs  
Additional resources  

To ensure the success of a call and the exchange of messages during a conversation, your instant messaging (IM) application will need to handle appropriate event notifications. In this article, I’ll explain what basic events to catch and how to process them in order to run a basic IM call and conversation.

In UCWA, to make an IM call, you submit a POST request on the [startMessaging](http://ucwa.skype.com/documentation/resources-startmessaging) resource and include at least the SIP URI of the user you’re calling. This sends an invitation to the specified user via the UCWA event channel. When the recipient answers the call, the caller is notified that the call state changed from connecting to connected.

After the call is connected, participants can send messages to other participants. To send a message, a UCWA application makes a POST request against the [sendMessage](http://ucwa.skype.com/documentation/resources-sendmessage) resource with the message as the payload. The messages can be formatted as a plain text or HTML.

## Before you start

Complete the following tasks before you start the process described in this article:

  - Create your [application](http://ucwa.skype.com/documentation/resources-application).

  - Start the [event channel](http://ucwa.skype.com/documentation/programmingconcepts-events).

  - Sign in to UCWA.

  - Enable the application to receive incoming notifications and incoming IM messages.

  - Retrieve the updated [application](http://ucwa.skype.com/documentation/resources-application) resource.

For more information, see [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md) and [Set up the UCWA event channel to receive incoming notifications](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md).

## Overview of the process for making outgoing calls

To make an outgoing IM call by using UCWA:

1.  Submit a POST request on the [startMessaging](http://ucwa.skype.com/documentation/resources-startmessaging) resource. You can navigate to this operational resource from the [communication](http://ucwa.skype.com/documentation/resources-communication) resource embedded in the [application](http://ucwa.skype.com/documentation/resources-application) resource.
    
    As a result, the [messagingInvitation](http://ucwa.skype.com/documentation/resources-messaginginvitation) events are sent from the event channel.

2.  Handle the outgoing **messagingInvitation** event sent from the **communication** resource. The event state changes from Connecting to Connected as the event type changes from started to completed.

3.  Handle the [conversation](http://ucwa.skype.com/documentation/resources-conversation) event, also sent from the **communication** resource. The event state changes from Connecting to Connected as the event type changes from added to updated.
    
    After a conversation is connected, a series of modality- or functionality-related events will also appear in the event channel. You can use these events to determine which of the following modalities is currently available in your application:
    
      - [Messaging](http://ucwa.skype.com/documentation/resources-messaging)
    
      - [AudioVideo](http://ucwa.skype.com/documentation/resources-audiovideo)
    
      - [ApplicationSharing](http://ucwa.skype.com/documentation/resources-applicationsharing)
    
      - [DataCollaboration](http://ucwa.skype.com/documentation/resources-datacollaboration)
    
    Because you started the call by using the **startMessaging** resource, only the messaging modality will be connected while all others remain in the disconnected state. If the messaging modality is in the disconnected state, you can enable or reenable it by calling the [addMessaging](http://ucwa.skype.com/documentation/resources-addmessaging) resource.

4.  Handle the [messaging](http://ucwa.skype.com/documentation/resources-messaging) events to retrieve the URI to the [sendMessage](http://ucwa.skype.com/documentation/resources-sendmessage) resource. You will use this operational resource to send messages to remote participants.

5.  After receiving notification of the updated conversation, submit a GET request on the [conversation](http://ucwa.skype.com/documentation/resources-conversation). The response should contain the connected**conversation** resource. You can use this resource to add audio/video modalities or invite new participants to the conversation.

6.  Submit a POST request on the [sendMessage](http://ucwa.skype.com/documentation/resources-sendmessage) resource to send a message to the remote participants. The request payload contains the message. When this operation is successful, you should receive **message**completed event fired by the **conversation** resource.

7.  To end the call, submit a POST request on the [stopMessaging](http://ucwa.skype.com/documentation/resources-stopmessaging) resource.

Let’s dive into the details.

## Get ready to make a call

Before you make the call, make sure that the user is signed in and can receive notifications. To do this, submit a POST request on the [makeMeAvailable](http://ucwa.skype.com/documentation/resources-makemeavailable) resource. For more information, see [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md).

You also need to [Set up the UCWA event channel to receive incoming notifications](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md), including incoming call invitations and other event notifications.

Create a class named UcwaAppCommunication to encapsulate communications for the application. The constructor takes a logged on [application](http://ucwa.skype.com/documentation/resources-application) resource with incoming notifications and IM messages enabled to initialize the UcwaAppCommunication object.

```csharp
    public class UcwaAppCommunication
    {
        UcwaApp ucwaApp;
        public UcwaAppCommunication(UcwaApp app)
        {
            this.ucwaApp = app;
            this.Resource = new UcwaResourceCommunication(
                this.ucwaApp.ApplicationResource.GetEmbeddedResource("communication"));
            this.ucwaApp.OnEventsReceived += new UcwaAppEventsReceivedEventHandler(ProcessEvents);            
        }

        void ProcessEvents(string sender, IEnumerable<UcwaEvent> events)
        {
        }
```

The encapsulated [communication](http://ucwa.skype.com/documentation/resources-communication) resource is embedded in the **application** resource. It contains the URI to the [startMessaging](http://ucwa.skype.com/documentation/resources-startmesssaging) resource you need to start the call.

Because the communication uses the event notifications, this is also a good place to register with the UCWA event channel in order to receive event notifications. You will fill in the ProcessEvent method later in the process.

## Make an outgoing IM call

To make an outgoing IM call, submit a POST request on the **startMessaging** resource, and specify the recipient SIP URI as well as one or more optional parameters. When you specify optional parameters, the data must be packaged as the payload to the POST request. If you don’t specify optional parameters, you can specify the required recipient’s SIP URI as a query parameter appended to the resource URI. The following code example shows the operations.

```csharp
        string operationId = Guid.NewGuid().ToString();
        string threadId = Guid.NewGuid().ToString();

        public async Task<UcwaAppOperationResult> StartIM(string toUri, string subject, string importance = "normal")
        {
            var startMessagingUri = this.Resource.GetLinkUri("startMessaging");
            
            ShowProcessProgress("startMessaging Uri = " + startMessagingUri);
            string firstMessage = "Hi!";
            string requestInput = string.Format(startMessagingInputFormat, operationId, toUri, importance, subject, threadId, firstMessage);
            var result = await this.ucwaApp.Transport.PostResourceAsync(startMessagingUri, requestInput);
            if (result.StatusCode != HttpStatusCode.Created)
                ShowProcessProgress("startMessaging request failed. \r\n" + result.Resource.OuterXml);
            return result;
        }
```

You can format the message body, requestInput, as shown.

```csharp
        string startMessagingInputFormat = "<?xml version=\"1.0\" encoding=\"utf-8\"?>" +
            "<input xmlns=\"http://schemas.microsoft.com/rtc/2012/03/ucwa\">" +
            "  <property name=\"operationId\">{0}</property>" +
            "  <property name=\"to\">{1}</property>" +
            "  <property name=\"importance\">{2}</property>" +
            "  <property name=\"subject\">{3}</property>" +
            "  <property name=\"threadId\">{4}</property>" +
            "  <link rel=\"message\" href=\"data:text/plain,{5}\" />" +
            "</input>";
```

The to parameter, which specifies the SIP URI of the recipient, is required. All other parameters are optional. A UCWA application can assign an operationId value to the call and use it to filter out events related to this call only. You can use the threadId property to associate different operations with the call. For example, when a user sends a message to two different users, each conversation has a different threadId value. You can use this property to keep track of the different conversations.

When the request is successful, a series of events are raised at various stages of the invitation and notifications are sent from the event channel. The application that sends the invitation must be aware of these events to be ready to participate in the conversation.

## Handle events to monitor the progress of a call invitation

To monitor the progress of an outgoing call invitation, your application handles notifications from two event sources: the [communication](http://ucwa.skype.com/documentation/resources-communication) and the [conversation](http://ucwa.skype.com/documentation/resources-conversation) resources. Update the ProccessEvents method with the following code.

```csharp
        void ProcessEvents(string sender, IEnumerable<UcwaEvent> events)
        {
            switch (sender)
            {
                case "communication":
                    ProcessCommunicationEvents(events);
                    break;
                case "conversation":
                    ProcessConversationEvents(events);
                    break;
                default:
                    break;
            }
        }
```

The UCWA event channel parses events into lists per event source, as described in [Setting up the event channel to receive incoming notifications](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md). Your application only processes communication and conversation events and ignores events from other sources.

## Process communication-sourced events for outgoing calls

To complete placing outgoing calls, your application needs to be aware of the **messagingInvittaion**-started and completed events.

When a **startMessaging** request is submitted successfully, a messagingInvitation starts and remains in a connecting state until the recipient accepts (or declines) the call. When the party accepts the call, the messagingInvitation is completed and its state changes from connecting to connected. The application can then send and receive messages.

When the invitation is started, a conversation is also created in a connecting state. When the invitation is accepted, the conversation state changes to connected. At each stage, the application receives an event notification that contains the corresponding [conversation](http://ucwa.skype.com/documentation/resources-conversation) resource. When a conversation ends, either when the user disconnects or when the application times out, your application receives a [conversation](http://ucwa.skype.com/documentation/resources-conversation)-deleted event.

In the following code example, the messageInvitation and communication resources are cached at each stage of the state transition so that the most up-to-date resources are available for the application. Alternatively, these resources can be made available only when the messagingInvitation or communication state changes to connected.

```csharp
        async void ProcessCommunicationEvents(IEnumerable<UcwaEvent> events)
        {
            foreach (var e in events)
            {
                // Handle IM invite.
                switch (e.Name)
                {
                    case "messagingInvitation":
                        this.messagingInvite = new UcwaResourceMessageInvitation(e);
                        NotifyResourceStateChange(messagingInvite.State.ToLower(), messagingInvite.Name);
                        break;
                    case "conversation":
                        if (e.Type.ToLower() == "deleted")
                            NotifyResourceStateChange("deleted", e.Name);
                        else
                            if (e.Resource != null)
                            {
                                this.conversation = new UcwaResourceConversation(e.Resource);
                                NotifyResourceStateChange(conversation.State.ToLower(), conversation.Name);
                            }
                        break;
                    default:
                        break;
                }
            }
        }
```

You implement the NotifyResourceStateChange method to forward the state changes to the UI control, which blocks the user from sending any message until it receives notification of the connectedmessagingInvitation state.

## Handle conversation-sourced events for outgoing calls

After a conversation is created as part of the call invitation, the recipient is added as a participant and the messaging modality is added to the conversation. These activities are accompanied by the following event notifications from the [conversation](http://ucwa.skype.com/documentation/resources-conversation) resource:

  - [participant](http://ucwa.skype.com/documentation/resources-participant)added or updated

  - [messaging](http://ucwa.skype.com/documentation/resources-messaging)added or updated

The newly added [messaging](http://ucwa.skype.com/documentation/resources-messaging) resource contains the link to the [sendMessage](http://ucwa.skype.com/documentation/resources-sendmessage) resource, which is used to send outgoing messages. It also contains the other messaging-related operational resources:

  - [stopMessaging](http://ucwa.skype.com/documentation/resources-stopmessaging) — Used to end the call.

  - [setIsTyping](http://ucwa.skype.com/documentation/resources-setistyping) — Used to notify others that a user is typing.

  - [typingParticipant](http://ucwa.skype.com/documentation/resources-typingparticipant) — Used to identify the person typing.

Some of these resources might not be available when a messaging resource is in the connecting state.

The participant-added events contain information about the remote participant, including where to get full contact information or to subscribe to their presence information.

The following code example shows one way to fetch and cache the name of the remote participant when they’re added to the conversation and to delete the participant name from the cache when they’re removed. In addition, the most up-to-date [messaging](http://ucwa.skype.com/documentation/resources-messaging) resource is cached so that the resources it contains are available to the application. Alternatively, you can do this only for the **messaging**added event in the connected state and ignore the other **messaging** events.

```csharp
        async void ProcessConversationEvents(IEnumerable<UcwaEvent> events)
        {
            foreach (var e in events)
            {
                switch (e.Name)
                {
                    case "participant":
                        if (e.Type.ToLower() == "deleted")
                        {
                            if (participantNames.ContainsKey(e.Uri))
                                participantNames.Remove(e.Uri);
                        }
                        else 
                        {
                            if (!participantNames.ContainsKey(e.Uri))
                            {
                                var pName = await GetParticipantName(e.Uri);
                                if (!string.IsNullOrEmpty(pName) && !participantNames.ContainsKey(e.Uri))
                                    participantNames.Add(e.Uri, pName);
                            }
                        }
                        break;
                    case "messaging":
                        messaging = new UcwaResourceMessaging(e);
                        NotifyResourceStateChange(messaging.State.ToLower(), messaging.Name);
                        if (messaging.State.ToLower() == "connected")
                        {
                            var result = await this.ucwaApp.Transport.GetResourceAsync(messaging.conversationUri);
                            if (result.StatusCode == HttpStatusCode.OK)
                            {
                                this.conversation = new UcwaResourceConversation(result.Resource);
                                NotifyResourceStateChange(conversation.State.ToLower(), conversation.Name);
                            }
                            else
                            {
                                this.ShowProcessProgress("Failed to GET conversation after a successful messaging invitation: " + result.Exception.Message);
                            }
                        }
                        break;
                    default:
                        break;
                }
            }
        }
```

When the [messagingInvitation](http://ucwa.skype.com/documentation/resources-messaginginvitation) is successfully completed, the application is ready to send and receive IMs through the connected [conversation](http://ucwa.skype.com/documentation/resources-conversation).

## Send outgoing IMs

To send an IM in a conversation, submit a POST request on the [sendMessage](http://ucwa.skype.com/documentation/resources-sendmessage) resource. The URI to this resource is available from the [messaging](http://ucwa.skype.com/documentation/resources-messaging) resource from the event channel. In the following code example, the URI is cached as an instance of the UcwaAppResourceMessaging class. See the accompanying [sample application solution](http://code.msdn.microsoft.com/lync-2013-ucwa-windows-2f0ce645) for details.

You can send the message in plain text format, as shown in the following code example, where the message is input from a **TextBox** control. Make sure that the supported messaging modalities include plain text and the Content-Type is set to "text/plain". You can also send the HTML-formatted message, for example, \<span\>Hello\!\</span\>, if the supported messaging modalities include HTML. In this case, you need to specify the content type as "text/html" instead.

```csharp
        public async Task<UcwaAppOperationResult> SendMessage(string msg ="Hello, this is a test.")
        {
            if (operationId == null) operationId = Guid.NewGuid().ToString();
            UcwaAppOperationResult result = null;
            if (messaging!= null && messaging.sendMessageUri != null)
            {
                var uri = messaging.sendMessageUri + "?OperationId="+  operationId;
                result = await this.ucwaApp.Transport.PostResourceAsync(uri, msg, "text/plain");
            }
            if (messaging != null && messaging.sendMessageUri == null)
            {
                result = new UcwaAppOperationResult(HttpStatusCode.BadRequest, new Exception("null sendMessageUri received/cached."));
            }
            else if (messaging == null)
            {
                result = new UcwaAppOperationResult(HttpStatusCode.BadRequest, new Exception("null messaging received/cached."));
            }
            
            return result;
        }
```

Typically, the POST request is initiated when the user enters a text and clicks a **Send** button on a UI page, as shown in the following example.

```csharp
        private async void SendButton_Click(object sender, RoutedEventArgs e)
        {
            var result = await this.ucwaApp.Communication.SendMessage(textBoxImInput.Text);
            if (result == null)
                textBlockStatus.Text = "ERROR: SendMessage returned null result.";
            else if (result.Resource != null)
                textBlockStatus.Text += Environment.NewLine + result.Resource.OuterXml;
            else
                textBlockStatus.Text += Environment.NewLine + "SendMessage: " + result.StatusCode.ToString();
            Communication_OnMessageReceived("OK", DateTime.Now.ToString(), textBoxImInput.Text, this.ucwaApp.Me.DisplayName);
        }
```

That’s it for the basic steps to place an outgoing IM call and to send the first message. In the next article, I'll cover the other end of the process, including the basic steps to accept an IM call and to receive incoming messages.

## See also

  - [Getting Started](http://ucwa.skype.com/documentation/getting-started) with UCWA 1.0.

  - UCWA 1.0 [Event Channel Details](http://ucwa.skype.com/documentation/gettingstarted-events)

  - UCWA 1.0 [events](http://ucwa.skype.com/documentation/resources-events) resource reference page

  - [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md)

  - [Setting up the UCWA event channel to receive incoming notifications](set-up-the-ucwa-event-channel-to-receive-incoming-notifications.md)

  - [Answer an incoming IM call and receive messages](answer-an-incoming-im-call-and-receive-messages.md)

  - [Lync 2013: UCWA Windows Store app to start and accept IM calls](http://code.msdn.microsoft.com/lync-2013-ucwa-windows-2f0ce645)

