---
title: 'How to: Accept or decline a request to control a shared resource'
TOCTitle: 'How to: Accept or decline a request to control a shared resource'
ms:assetid: f59772bf-0fd6-481a-9cd8-f212f8381f29
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933256(v=office.15)
ms:contentKeyID: 50877402
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Accept or decline a request to control a shared resource

Learn how to use Microsoft Lync 2013 SDK to accept or decline a request to control a locally shared resource in a Microsoft Lync 2013 conversation.

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
Sample Windows Form<br />
Register for control request events<br />
Accept or decline a resource control request<br />
Application state on completion of how-to tasks<br />
Code examples: Accept or decline a request to control a shared resource<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

Before your application runs the logic in this topic, a resource sharing conversation must be active with one or more participants in addition to the local user. The local user participation state must be [ParticipationState](https://msdn.microsoft.com/en-us/library/jj267952\(v=office.15\))**.Sharing** and a local sharable resource must be shared in the conversation.

  - [How to: Get a shareable resource and share it in a conversation](how-to-get-a-shareable-resource-and-share-it-in-a-conversation.md)

## Sample Windows Form

A Lync user who is sharing a resource such as a desktop or program must be able to accept or decline requests from other conversation participants to control the shared resource. This topic shows how to listen to and respond to control requests. The following figure highlights the part of the sample Windows Form discussed in this topic. The tasks in the following list are discussed in this topic and shown in the code samples. For an overview of resource sharing in Microsoft Lync 2013, see [Application sharing modality](application-sharing-modality.md).

  
![Accept and Decline resource controlling request](images/JJ933256.UC_OCS15ConLyncClient_HowToAcceptorDeclineSharingControlfigure1(Office.15).jpg "Accept and Decline resource controlling request")

## Register for control request events

Before your application can accept or decline a resource control request, you must register an event callback method on the [ApplicationSharingModality.ControlRequestReceived](https://msdn.microsoft.com/en-us/library/jj277299\(v=office.15\)) and [ApplicationSharingModality.ControllerChanged](https://msdn.microsoft.com/en-us/library/jj293289\(v=office.15\)) events of the conversation [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)). When the first event is raised, a conversation participant is requesting control of the locally shared resource. When the second event is raised, control of the resource has been given to the requesting participant.

### To register for control request events

1.  Get the [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/en-us/library/jj276988\(v=office.15\)) object that encapsulates the current sharing conversation.

2.  Read the current state of the conversation [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) object by examining the [Modality.State](https://msdn.microsoft.com/en-us/library/jj276637\(v=office.15\)) property.

3.  If the current state is [ModalityState](https://msdn.microsoft.com/en-us/library/jj293265\(v=office.15\))**.Connected**, register for the [ApplicationSharingModality.ControlRequestReceived](https://msdn.microsoft.com/en-us/library/jj277299\(v=office.15\)) event.
    
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
    <td><p>You can register for the <strong>ControlRequestReceived</strong> event while the application sharing modality is in any valid state. However, control of a locally shared resource cannot be requested until the application sharing resource is connected.</p></td>
    </tr>
    </tbody>
    </table>

## Accept or decline a resource control request

After the code in the previous example has enabled buttons in the UI that lets the user accept or decline a control request, the user can choose the button and accept the request. Accept the control request by calling the **ApplicationSharingModalityBeginAcceptControlRequest(AsyncCallback, object)** method on the requesting participant’s application sharing modality.

### To accept or decline a resource control request

1.  Handle the [ApplicationSharingModality.ControlRequestReceived](https://msdn.microsoft.com/en-us/library/jj277299\(v=office.15\)) event.

2.  Get the name of the requester by calling the [Contact.GetContactInformation](https://msdn.microsoft.com/en-us/library/jj294012\(v=office.15\)) method on the [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object obtained by reading the value of the [ControlRequestReceivedEventArgs.Requester](https://msdn.microsoft.com/en-us/library/jj267980\(v=office.15\)) property.

3.  Notify the user that control of the locally shared resource is requested, naming the requesting user by showing the name string obtained in the previous step.

4.  If the local user accepts the sharing control request, call the **ApplicationSharingModalityBeginAcceptControlRequest(AsyncCallback, object)** method.

5.  If the local user declines the request, call the **ApplicationSharingModalityBeginDeclineControlRequest(AsyncCallback, object)** method.

## Application state on completion of how-to tasks

When your application has responded to a request for control of a shared resource, if accepted, the resource is now controlled by the requester and the [ModalityAction](https://msdn.microsoft.com/en-us/library/jj266957\(v=office.15\))**.RevokeSharingControl** action is available. If declined, the resource is not controlled and the [Microsoft.Lync.Model.Conversation.ModalityAction](https://msdn.microsoft.com/en-us/library/jj266957\(v=office.15\))**.GrantSharingControl** action is available.

## Code examples: Accept or decline a request to control a shared resource

The following examples show the code described in the previous sections.

### Code example

The following example registers an event callback method on the [ApplicationSharingModality.ControlRequestReceived](https://msdn.microsoft.com/en-us/library/jj277299\(v=office.15\)) event and the [ApplicationSharingModality.ControllerChanged](https://msdn.microsoft.com/en-us/library/jj293289\(v=office.15\)) event when the state of the conversation application sharing modality changes to [ModalityState](https://msdn.microsoft.com/en-us/library/jj293265\(v=office.15\))**.Connected**.

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
<td><p>This example is a partial listing of the <strong>StateChanged</strong> event. For a complete example of a <strong>StateChanged</strong> event handler, see <a href="how-to-start-a-resource-sharing-conversation.md">How to: Start a resource sharing conversation</a>.</p></td>
</tr>
</tbody>
</table>

```csharp
        /// <summary>
        /// Handles the event raised the conversation application sharing state changes.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ApplicationSharingModality_StateChanged(object sender, ModalityStateChangedEventArgs e)
        {
            if (sender.GetType().Name != "ApplicationSharingModality")
            {
                return;
            }
            if (e.NewState == ModalityState.Connected)
            { 
                //Register for the application sharing modality event on the conversation itself
                _sharingModality = (ApplicationSharingModality)_conversation.Modalities[ModalityTypes.ApplicationSharing];

                //Register to catch requests from other participants for control of the locally owned sharing resource.
                _sharingModality.ControlRequestReceived += _sharingModality_ControlRequestReceived;
                _sharingModality.ControllerChanged += _sharingModality_ControllerChanged;

            }
        }
```

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
<td><p>You should also register an event callback method on the <a href="https://msdn.microsoft.com/en-us/library/jj293249(v=office.15)">Modality.ActionAvailabilityChanged</a> event. When this event is raised on the conversation or participant application sharing modality for the availability of the <a href="https://msdn.microsoft.com/en-us/library/jj266957(v=office.15)">ModalityAction</a><strong>.AcceptSharingControlRequest</strong> and <a href="https://msdn.microsoft.com/en-us/library/jj266957(v=office.15)">Microsoft.Lync.Model.Conversation.ModalityAction</a><strong>.DeclineSharingControlRequest</strong> actions, you should enable two button controls in the UI that let the user accept or decline a control request. For information about handling the <a href="https://msdn.microsoft.com/en-us/library/jj293249(v=office.15)">Modality.ActionAvailabilityChanged</a> event, see <a href="how-to-get-a-shareable-resource-and-share-it-in-a-conversation.md">How to: Get a shareable resource and share it in a conversation</a>.</p></td>
</tr>
</tbody>
</table>

The following example handles the **ControlRequestReceived** event by updating the Form UI with the name of the participant who is requesting control. A [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object representing the requesting participant is cached in the class field **\_resourceControllingContact**. This **Contact** is used in the **Accept** button click event handler to get the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) object owned by the requesting participant.

```csharp
        /// <summary>
        /// Handles the event raised when a conversation participant requests control of a locally owned resource.
        /// These requests always go to the resource owner, and not the current controller of the resource.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ControlRequestReceived(object sender, ControlRequestReceivedEventArgs e)
        {
            //Get the name of the participant that is requesting control of the locally owned resource.
            string displayRequesterName = e.Requester.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();

            //Update the text of the Accept button to include the name of the requester.
            this.Invoke(new ChangeButtonTextDelegate(ChangeButtonText), new object[] { Accept_Button, "Accept " + displayRequesterName + "  Request" });

            //Store the Contact object for the requesting participant.
            _ResourceControllingContact = e.Requester.Contact;
        }
```

### Code example

The following example calls the **ApplicationSharingModalityBeginAcceptControlRequest(AsyncCallback, object)** method to accept a resource control request after the user chooses to accept the request.

```csharp
       /// <summary>
       ///Accept another participants request to control locally owned and shared resource.
       ///The Accept button is enabled when the _sharingModality_ActionAvailabilityChanged event handler is called
       ///with the event argument that specifies the ModalityAction.AcceptSharingControlRequest action is available.
       /// </summary>
       /// <param name="sender"></param>
       /// <param name="e"></param>
        private void Accept_Button_Click(object sender, EventArgs e)
        {

            //_selectedContact is set to the Contact object of the participant who requested control of the resource. 
            //see the _sharingModality_ControlRequestReceived method in the application sharing modality event handlers region.
            ApplicationSharingModality sharingModality = (ApplicationSharingModality)_participantSharingModalities[_ResourceControllingContact.Uri];
 
            //If the requesting participant application sharing modality is available and the AcceptSharingControlRequest action can be invoked
            if (sharingModality != null && sharingModality.CanInvoke(ModalityAction.AcceptSharingControlRequest))
            {
                //Accept sharing control request.
                sharingModality.BeginAcceptControlRequest(SharingControlCallback, "accept");
            }
        }
```

The following example declines a resource control request after the user chooses to decline the request. Decline the control request by calling the **ApplicationSharingModalityBeginDeclineControlRequest(AsyncCallback, object)** method on the requesting participant’s application sharing modality.

```csharp
        /// <summary>
        ///Decline another participants request to control locally owned and shared resource.
        ///The Decline button is enabled when the _sharingModality_ActionAvailabilityChanged event handler is
        ///called with the event argument that specifies the ModalityAction.DeclineSharingControlRequest action is available.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Decline_Button_Click(object sender, EventArgs e)
        {
            //_selectedContact is set to the Contact object of the participant who requested control of the resource. 
            //see the _sharingModality_ControlRequestReceived method in the application sharing modality event handlers region.
            ApplicationSharingModality sharingModality = (ApplicationSharingModality)_participantSharingModalities[_ResourceControllingContact.Uri];
            if (sharingModality != null && sharingModality.CanInvoke(ModalityAction.DeclineSharingControlRequest))
            {
                sharingModality.BeginDeclineControlRequest(SharingControlCallback, "decline");
            }

        }
```

The following example is invoked by the platform thread when the previous asynchronous control request actions are completed.

```csharp
        /// <summary>
        /// Callback method for all asynchronous modality control methods.
        /// </summary>
        /// <param name="ar"></param>
        private void SharingControlCallback(System.IAsyncResult ar)
        {
            //Get the application sharing modality for the conversation participant to invoke controlling action on.
            ApplicationSharingModality sharingModality = (ApplicationSharingModality)_participantSharingModalities[_ResourceControllingContact.Uri];

            if (ar.IsCompleted == false)
            {
                MessageBox.Show(ar.AsyncState.ToString() +  " did not complete");
            }
            //Complete the asynchronous controlling action according to the asynchronous state string that indicates
            //which controlling action to complete.
            switch (ar.AsyncState.ToString().ToUpper())
            {
                case "ACCEPT":
                    sharingModality.EndAcceptControlRequest(ar);
                    break;
                case "DECLINE":
                    sharingModality.EndDeclineControlRequest(ar);
                    break;
            }
        }
```

### Display the name of the current resource controller

After the user has accepted or declined another conversation participant’s request to control the locally shared resource, your application should confirm the user’s response to the request by updating the application UI with the name of the new resource controller. This is performed by handling the [ApplicationSharingModality.ControllerChanged](https://msdn.microsoft.com/en-us/library/jj293289\(v=office.15\)) event. The event data parameter of the event callback method gives the name of the controller. Use this name property to update the value of a text control in your UI.

#### Code example

The following example updates the Form UI with the name of the participant who is controlling the locally shared resource.

```csharp
        /// <summary>
        /// Handles the event raised when the participant that is controlling the shared conversation application resource
        /// changes. This event is raised locally even when the shared resource is not locally owned.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ControllerChanged(object sender, ControllerChangedEventArgs e)
        {
            this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { ResourceControllerName_Label, e.ControllerName });

            //Store the Contact object for the conversation participant that now controls the shared conversation resource.
            _ResourceControllingContact = ((ApplicationSharingModality)sender).Controller.Contact;

        }
```

## See also

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

  - [How to: Grant and revoke control of a shared resource](how-to-grant-and-revoke-control-of-a-shared-resource.md)

  - [How to: Request and release control of a shared resource](how-to-request-and-release-control-of-a-shared-resource.md)

  - [How to: Start a resource sharing conversation](how-to-start-a-resource-sharing-conversation.md)

