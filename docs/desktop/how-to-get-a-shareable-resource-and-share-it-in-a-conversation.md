---
title: 'How to: Get a shareable resource and share it in a conversation'
TOCTitle: 'How to: Get a shareable resource and share it in a conversation'
ms:assetid: 9626409f-cf49-4f1e-9212-045d990f1923
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933119(v=office.15)
ms:contentKeyID: 50877253
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Get a shareable resource and share it in a conversation

Learn how to use classes in Microsoft Lync 2013 SDK to select a locally shareable resource such as a desktop, monitor, or running program and share it in a Microsoft Lync 2013 conversation.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Shareable resource overview<br />
Prerequisites<br />
Share a resource<br />
Handle the Modality.ActionAvailabilityChanged event<br />
Handle the Modality.ModalityStateChanged event<br />
Code example: Get a shareable resource and share in a conversation<br />
Code example: Handle the Modality.ActionAvailabilityChanged event<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Shareable resource overview

For an overview of resource sharing in Microsoft Lync 2013, see [Sharing resources in a conversation](sharing-resources-in-a-conversation.md).

Before you start the procedures in this topic, a resource sharing conversation must be active with one or more participants in addition to the local user. The application UI must also show a list of shareable resources in a list. For information about reaching this application state, see [How to: Start a resource sharing conversation](how-to-start-a-resource-sharing-conversation.md).

## Prerequisites

The prerequisites for sharing a resource in a conversation are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

Understanding the following concepts is essential to using resource sharing conversions in an application.

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
<td><p><a href="how-to-start-a-lync-im-conversation.md">How to: Start a Lync IM conversation</a></p></td>
<td><p>Describes how to start a Lync 2013 conversation.</p></td>
</tr>
<tr class="even">
<td><p><a href="sharing-resources-in-a-conversation.md">Sharing resources in a conversation</a></p></td>
<td><p>Learn about programmatically sharing a computer monitor, desktop, or running program with another Microsoft Lync 2013 user in a conversation window by using classes in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="odd">
<td><p><a href="application-sharing-modality.md">Application sharing modality</a></p></td>
<td><p>Learn about the <strong>ApplicationSharingModality</strong> class and how it enables you to share resources in an application.</p></td>
</tr>
</tbody>
</table>

## Share a resource

The shareable resource list is a list of the locally shareable resource names. These names are added to the list in the order that they are read from the [ApplicationSharingModality.ShareableResources](https://msdn.microsoft.com/library/jj278380\(v=office.15\)) collection. For this reason, the selected index of the list is used in the Share Resources application to get the corresponding [Microsoft.Lync.Model.Conversation.Sharing.SharingResource](https://msdn.microsoft.com/library/jj293621\(v=office.15\)) instance from the collection.

### To share a resource

1.  Get the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) object from the active conversation.
    
    This is shown in the following example.

2.  Get a [Microsoft.Lync.Model.Conversation.Sharing.SharingResource](https://msdn.microsoft.com/library/jj293621\(v=office.15\)) object from the application sharing modality’s **ShareableResources** collection by the selected index.

3.  Read the [SharingResource.Type](https://msdn.microsoft.com/library/jj275958\(v=office.15\)) property of the selected resource to determine the correct sharing method to call.

4.  Call the [ApplicationSharingModality.CanShare](https://msdn.microsoft.com/library/jj276997\(v=office.15\)) method to determine whether the selected resource can be shared.

5.  If the sharing resource type is [Microsoft.Lync.Model.Conversation.Sharing.SharingResourceType](https://msdn.microsoft.com/library/jj278136\(v=office.15\))**.Desktop**, call the [ApplicationSharingModality.BeginShareDesktop](https://msdn.microsoft.com/library/jj275900\(v=office.15\)) method.

6.  If the sharing resource type is [SharingResourceType](https://msdn.microsoft.com/library/jj278136\(v=office.15\))**.Monitor** or [SharingResourceType](https://msdn.microsoft.com/library/jj278136\(v=office.15\))**.Process**, do the following:
    
    1.  Obtain the process to share by getting the [Microsoft.Lync.Model.Conversation.Sharing.SharingResource](https://msdn.microsoft.com/library/jj293621\(v=office.15\)) from the [ApplicationSharingModality.ShareableResources](https://msdn.microsoft.com/library/jj278380\(v=office.15\)) collection on the conversation application sharing modality.
    
    2.  Call the [ApplicationSharingModality.BeginShareResources](https://msdn.microsoft.com/library/jj275502\(v=office.15\)) method, passing the sharing resource that was obtained in the previous step.

## Handle the Modality.ActionAvailabilityChanged event

Use the [Modality.ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) event to prompt a user when a resource control action is available. The sample prompts the user by enabling or disabling one of a set of UI buttons for each action.

The [Modality.ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) event is raised on the conversation and participant **ApplicationSharingModality** objects when a control action is made available or not available. The event callback method for this event enables or disables buttons in the **Take a control action** group as action availability changes.

Any presenter in an active conversation can share a resource at any time after the **ApplicationSharingModality** is connected. This event can be raised regardless of who is sharing a resource. For information about when to register for this event in a new sharing conversation, see [How to: Start a resource sharing conversation](how-to-start-a-resource-sharing-conversation.md).

To set the **Enabled** property of a button, the event callback method reads the [Action](https://msdn.microsoft.com/library/jj276590\(v=office.15\)) property and the [IsAvailable](https://msdn.microsoft.com/library/jj293614\(v=office.15\)) property. The value of the **Action** property determines which button is set and the **IsAvailable** property value is used to set the **Button.Enabled** property value.

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
<td><p>The same event callback method for this event should be registered on all instances of the <a href="https://msdn.microsoft.com/library/jj275536(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality</a> object.</p></td>
</tr>
</tbody>
</table>

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
<td><p>Another conversation presenter can preempt your locally shared resource by sharing a resource of his or her own. The only way to prevent this is to demote all conversation participants to the attendee role except for the locally signed-in user. When your shared resource is preempted by another presenter’s resource, several <strong>ActionAvailabilityChanged</strong> events are raised. The result of this series of events is that you can no longer grant or revoke control of the shared resource. Instead, you can request control of the resource and if your request is accepted, you can release the control.</p></td>
</tr>
</tbody>
</table>

## Handle the Modality.ModalityStateChanged event

Use the [Modality.ModalityStateChanged](https://msdn.microsoft.com/library/jj278080\(v=office.15\)) event to update a UI list of users who have accepted an invitation to join the conversation.

The [Modality.ModalityStateChanged](https://msdn.microsoft.com/library/jj278080\(v=office.15\)) event is raised when the state of [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) objects for the conversation and each participant changes. When a participant’s modality state becomes [ModalityState](https://msdn.microsoft.com/library/jj293265\(v=office.15\))**.Connected**, the participant has accepted the invitation. The participant can now view shared resources and if the participant is a presenter, can share a local resource.

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
<td><p>While it is a good practice to update your UI participant list with the name of each participant as each modality is connected, be prepared to remove a participant’s name if the participant declines the invitation or leaves the conversation. You are notified of this change in the <a href="https://msdn.microsoft.com/library/jj268280(v=office.15)">Conversation.ParticipantRemoved</a> event. If the participant is removed from the conversation before the his or her modality is connected, the participant declined the invitation.</p></td>
</tr>
</tbody>
</table>

### Code example

The following example updates a participant list in the UI with each [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) that is connected to the conversation.

```csharp
        /// <summary>
        /// Handles the even raised when the state of an application sharing modality changes.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ModalityStateChanged(object sender, ModalityStateChangedEventArgs e)
        {
 
            //Modality will be connected for each particpant whethere they have accepted the shariing invite or not.
            
            ApplicationSharingModality thisModality = (ApplicationSharingModality)sender;
            if (e.NewState == ModalityState.Connected)
            {
                this.Invoke(new AddAContactDelegate(AddAContact), new object[] { thisModality.Participant.Contact.Uri });
            }
        }
```

## Code example: Get a shareable resource and share in a conversation

The following example handles the click event when a user presses the **Share Resource** button after the user selects a shareable resource from the list.

```csharp
        /// <summary>
        /// Handles click event on the Share Resource button. User must select a resource
        /// from the sharable resources list before clicking the button.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void StartSharingResource_Button_Click(object sender, EventArgs e)
        {
 
            //If there is no active conversation to share this resource in, return from handler
            if (_conversation == null)
            {
                return;
            }
 
            //If there is no sharing modality stored locally on the active conversation, get it from the active conversation and store it.
            if (_sharingModality == null)
            {
                _sharingModality = _conversation.Modalities[ModalityTypes.ApplicationSharing] as ApplicationSharingModality;
            }
 
            //Process the users selected resource choice by calling this helper method
            ShareSelectedResource(SharedResources_ListBox.SelectedIndex);
        }
```

The following example shares a resource by completing steps 2 through 7c in the previous procedure.

```csharp
        /// <summary>
        /// Shares the resource selected by the user.
        /// </summary>
        private void ShareSelectedResource(Int32 selectedResource)
        {

            //Get the type of resource selected by the user
            SharingResourceType selectedResourceType = ((SharingResource)_sharingModality.ShareableResources[selectedResource]).Type;

            CanShareDetail sharingDetail;
            if (!_sharingModality.CanShare(selectedResourceType, out sharingDetail))
            {
                switch (sharingDetail)
                {
                    case CanShareDetail.DisabledByOrganizerPolicy:
                        MessageBox.Show("The conversation organizer has disallowed sharing" );
                        break;
                    case CanShareDetail.DisabledByPolicy:
                        MessageBox.Show("Sharing resources is not allowed ");
                        break;
                    case CanShareDetail.DisabledByRole:
                        MessageBox.Show("Conference attendees cannot share resources" );
                        break;
                }
                return;
            }
            if (selectedResourceType == SharingResourceType.Desktop)
            {
                _sharingModality.BeginShareDesktop((ar) =>
                {
                    _sharingModality.EndShareDesktop(ar);
                }
                    , null);
            }
            else
            {
                _sharingModality.BeginShareResources((SharingResource)_sharingModality.ShareableResources[selectedResource], (ar) =>
                {
                    try
                    {
                        _sharingModality.EndShareResources(ar);
                    }
                    catch (OperationException oe) { throw oe; }
                    catch (LyncClientException lce) { throw lce; }
                }
                , null);
            }
        }
```

## Code example: Handle the Modality.ActionAvailabilityChanged event

The following example handles the [Modality.ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) event by invoking a UI thread delegate that takes a button and a Boolean argument. The button is the UI button to update, and the Boolean is the new value of the **Button.Enabled** property. The sample uses this logic to enable or disable a control action button when the availability of the action changes.

```csharp
        /// <summary>
        /// Event handler for sharing modality action availability change
        /// This method enables or disables the modality control action buttons on the UI according to
        /// the availability of a given action.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ActionAvailabilityChanged(object sender, ModalityActionAvailabilityChangedEventArgs e)
        {

            ApplicationSharingModality thisModality = (ApplicationSharingModality)sender;
            Button buttonToUpdate = null;
 
            //Enable or disable a UI action button that corresponds to the action whose availability has changed.
            switch (e.Action)
            {
                case ModalityAction.AcceptSharingControlRequest:
                    buttonToUpdate = Accept_Button;
                    break;
                case ModalityAction.DeclineSharingControlRequest:
                    buttonToUpdate = Decline_Button;
                    break;
                case ModalityAction.GrantSharingControl:
                    buttonToUpdate = Grant_Button;
                    break;
                case ModalityAction.ReleaseSharingControl:
                    buttonToUpdate = Release_Button;
                    break;
                case ModalityAction.RequestSharingControl:
                    buttonToUpdate = Request_Button;
                    break;
                case ModalityAction.RevokeSharingControl:
                    buttonToUpdate = Revoke_Button;
                    break;
                case ModalityAction.Disconnect:
                    buttonToUpdate = Disconnect_Button;
                    break;
            }
 
            //Not all possible cases of ActionAvailability are represented in the previous switch statement. 
            //For this reason, buttonToUpdate may be null.
            if (buttonToUpdate != null)
            {
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { buttonToUpdate, e.IsAvailable });
            }
        }
        private delegate void EnableDisableButtonDelegate(Button buttonToUpdate, Boolean actionAvailability);
        private void EnableDisableButton(Button buttonToUpdate, Boolean actionAvailability)
        {
            buttonToUpdate.Enabled = actionAvailability;
        }
```

## Next steps

  - [How to: Accept or decline a request to control a shared resource](how-to-accept-or-decline-a-request-to-control-a-shared-resource.md)

  - [How to: Grant and revoke control of a shared resource](how-to-grant-and-revoke-control-of-a-shared-resource.md)

## See also

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

