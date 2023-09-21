---
title: 'How to: Start a resource sharing conversation'
TOCTitle: 'How to: Start a resource sharing conversation'
ms:assetid: 547bfc80-f975-4109-acf9-b8455d07825b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937320(v=office.15)
ms:contentKeyID: 50877150
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Start a resource sharing conversation

Learn how to use Microsoft Lync 2013 SDK to start a Microsoft Lync 2013 sharing conversation and get a list of shareable resources that are shared in the conversation.



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
Resource sharing overview<br />
Share Resources application Windows Form<br />
Initial application state<br />
Handle the form loaded event<br />
Get contacts from a user’s contact list<br />
Add a new conversation<br />
Configure the newly added conversation<br />
Get a list of shareable resources<br />
Code examples: Share resources<br />
Next steps<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Resource sharing overview

This topic describes how to build the UI elements highlighted in figure 1 by completing the following tasks. For more information about the Share Resources sample application, see [Code samples: Lync SDK](code-samples-lync-sdk.md). For an overview of resource sharing in Microsoft Lync 2013, see [Sharing resources in a conversation](sharing-resources-in-a-conversation.md).

## Prerequisites

The prerequisites for starting a resource sharing conversation are as follows:

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
<td><p><a href="sharing-resources-in-a-conversation.md">Sharing resources in a conversation</a></p></td>
<td><p>Learn about programmatically sharing a computer monitor, desktop, or running program with another Microsoft Lync 2013 user in a conversation window by using classes in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="application-sharing-modality.md">Application sharing modality</a></p></td>
<td><p>Learn about the <strong>ApplicationSharingModality</strong> class and how it enables you to share resources in an application.</p></td>
</tr>
</tbody>
</table>

## Share Resources application Windows Form

The following figure shows a sample application Windows Form.

Figure 1. Application Windows Form

  
![Conversation starting-related controls highlighted](images/JJ937320.UC_OCS15ConLyncClient_HowToStartResourceSharingConversationfigure1(Office.15).jpg "Conversation starting-related controls highlighted")

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
<td><p>You can only get shareable resources in the context of an active conversation. For this reason, the following examples do not fill the shared resources list until after the conversation is started. For information about how to create a contact list, see <a href="how-to-display-a-contact-list.md">How to: Display a contact list</a>.</p></td>
</tr>
</tbody>
</table>

## Initial application state

Before you complete the procedures in this topic, your application must declare and initialize an instance of [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)). The Lync client must be signed in. For more information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

In addition to the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance, your application must declare a button and two lists. The first list displays contact SIP addresses for Lync users, the button starts the conversation, and the second list displays the resources that can be shared in the new conversation. The SIP address list should let a user select multiple addresses so that multiple users can be invited to join the new conversation.

To make the following example code easier to read, several conversation-related API state objects are stored in class fields. These objects include the following:

  - A [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) object that represents the Lync client and is the entry point to the Microsoft Lync 2013 API.

  - A [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) object that represents the new conversation.

  - A **Dictionary\<string,**[Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\))**\>** object that contains the users selected to join the conversation.

  - A [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) that represents the application sharing modality of the conversation.

  - A **Dictionary\<string,**[Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\))**\>** object that is a collection of the application sharing modalities of invited users. The dictionary key is the [Contact.Uri](https://msdn.microsoft.com/library/jj293279\(v=office.15\)) property for a conversation participant.

### Code examples

The following example references the namespaces that are used in the following Windows Forms examples.

```csharp
using System;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Conversation.Sharing;
using System.Collections.Generic;
```

The following example declares the class fields that are referenced in the following sections of this topic.

```csharp
        /// <summary>
        /// Lync client platform. The entry point to the API
        /// </summary>
        Microsoft.Lync.Model.LyncClient _LyncClient;
 
        /// <summary>
        /// Represents a Lync conversation
        /// </summary>
        Conversation _conversation;

        /// <summary>
        /// A Contact instance representing the participant selected to be granted control of a resource
        /// </summary>
        Contact _ResourceControllingContact;
 
        /// <summary>
        /// Dictionary of all contacts selected from the multi-select enabled contact list on UI
        /// </summary>
        Dictionary<string, Contact> _selectedContacts = new Dictionary<string, Contact>();
 
        /// <summary>
        /// Collection of all participants application sharing modalities, keyed by Contact.Uri.
        /// </summary>
        Dictionary<string, ApplicationSharingModality> _participantSharingModalities = new Dictionary<string, ApplicationSharingModality>();
 
        /// <summary>
        /// The Application sharing modality of the conversation itself
        /// </summary>
        ApplicationSharingModality _sharingModality;
 
        /// <summary>
        /// The Application sharing modality of the local participant.
        /// </summary>
        ApplicationSharingModality _LocalParticipantSharingModality;
```

## Handle the form loaded event

The sample is ready to start a new conversation or host a conversation to which the signed-in user is invited as soon as the logic in the form load event finishes.

The [Microsoft.Lync.Model.Conversation.ConversationManager](https://msdn.microsoft.com/library/jj266018\(v=office.15\)) class lets you start a new conversation. Get a **ConversationManager** instance and register for events on it before starting any of the other tasks in this topic.

### To handle the form loaded event

1.  Get the API entry point by calling the static [LyncClient.GetClient](https://msdn.microsoft.com/library/jj278213\(v=office.15\)) method and put the returned [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) object into the \_lyncClient class field declared previously.

2.  Read the [LyncClient.InSuppressedMode](https://msdn.microsoft.com/library/jj275500\(v=office.15\)) property of the client. If **false** is returned, continue with the next step. Otherwise, stop this procedure.
    
    Resource sharing is not supported when UI suppression is enabled.

3.  Read the [Client.State](https://msdn.microsoft.com/library/jj274837\(v=office.15\)) property and continue to the next step if the current state is [ClientState](https://msdn.microsoft.com/library/jj275269\(v=office.15\))**.Signedin**. Otherwise, sign in to Lync with the user’s credentials.

4.  Read the [Client.ConversationManager](https://msdn.microsoft.com/library/jj276841\(v=office.15\)) property of the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)).

5.  Register a callback method for the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) and [ConversationManager.ConversationRemoved](https://msdn.microsoft.com/library/jj293976\(v=office.15\)) events on the conversation manager.

6.  Get the SIP addresses of all contacts in the user’s contact list.

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
<td><p>The example code in this topic is driven by the chain of events started when the <a href="https://msdn.microsoft.com/library/jj276176(v=office.15)">ConversationManager.AddConversation</a> method is called. The event callback method that is invoked for <a href="https://msdn.microsoft.com/library/jj266470(v=office.15)">ConversationManager.ConversationAdded</a> adds the invited users to the new <a href="https://msdn.microsoft.com/library/jj276988(v=office.15)">Microsoft.Lync.Model.Conversation.Conversation</a> object. For each user who is added to the conversation, a <a href="https://msdn.microsoft.com/library/jj275759(v=office.15)">Conversation.ParticipantAdded</a> event is raised. The event callback method that is invoked for this event gets the new participant’s <a href="https://msdn.microsoft.com/library/jj275536(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality</a>, and then registers event handlers for events on the participant’s sharing modality. The sharing modality events drive the UI state changes that enable or prevent a user from performing actions on the shared resource.</p></td>
</tr>
</tbody>
</table>

### Code example

The following example gets the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) and registers for events on the **LyncClient** and the **ConversationManager** instance.

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
<td><p>The code in this example assumes that a user has signed in to Lync 2013. For information about how to programmatically sign a user in to the client, see <a href="how-to-sign-a-user-in-to-lync.md">How to: Sign a user in to Lync</a>.</p></td>
</tr>
</tbody>
</table>

```csharp
        /// <summary>
        /// invoked when sample form is loaded. Initializes fields, gets API entry point, 
        /// registers for events on Lync Client and ConversationManager.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ShareResources_Form_Load(object sender, EventArgs e)
        {
            try
            {
                //Get the API entry point
                _LyncClient = LyncClient.GetClient();

                //Resource sharing is not supported in UI suppression mode. Sample closes
                //if Lync UI is suppressed
                if (_LyncClient.InSuppressedMode == true)
                {
                    MessageBox.Show("Lync Client is in UI Suppressed mode. Sharing is not supported.", "Application Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                    this.Close();
                }
 
                //If the Lync client is signed out, sign into the Lync client
                if (_LyncClient.State == ClientState.SignedOut)
                {
                    _LyncClient.EndSignIn(_LyncClient.BeginSignIn(
                        "AndreasH@contoso.com",
                        "AndreasH@contoso.com",
                        "My_Passw0rd",
                        null,
                        null));
                }
 
                //Register for the three Lync client events needed so that application is notified when:
                // * Lync client signs in or out
                // * A new conversation is added (remotely via invite or locally by user)
                // * A conversation is removed (conversation ends)
                _LyncClient.StateChanged += _LyncClient_StateChanged;
                _LyncClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
                _LyncClient.ConversationManager.ConversationRemoved += ConversationManager_ConversationRemoved;
 
                //Get the Sip addresses of all contacts in the user’s contact list.                
                //ShareResources.LoadAllContacts loads the contact list on the UI with
                //all contacts that are in the user's Lync client contact list.
                LoadAllContacts(); 
            }
            catch (ClientNotFoundException)
            {
                MessageBox.Show("Client is not running.  Closing form", "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
            catch (Exception exc)
            {
                MessageBox.Show("General exception: " + exc.Message, "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }

        }
```

The form is now loaded and the user’s contact list is displayed in the contact list in the UI.

## Get contacts from a user’s contact list

To get the contacts that a user has added to the local contact list, you must read the [Client.ContactManager](https://msdn.microsoft.com/library/jj275688\(v=office.15\)) property and then get the collection of [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/library/jj266012\(v=office.15\)) objects by reading the [ContactManager.Groups](https://msdn.microsoft.com/library/jj277988\(v=office.15\)) property. For more information about retrieving contacts, see [How to: Display a contact list](how-to-display-a-contact-list.md).

### To get the user’s contacts

1.  Read the [Client.ContactManager](https://msdn.microsoft.com/library/jj275688\(v=office.15\)) property on the **\_LyncClient** class field.

2.  Read the [ContactManager.Groups](https://msdn.microsoft.com/library/jj277988\(v=office.15\)) property on the contact manager.
    
    A collection of [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/library/jj266012\(v=office.15\)) objects is returned.

3.  Iterate on the **Group** objects.
    
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
    <td><p>A group is a collection of contacts that can be treated as a <a href="https://msdn.microsoft.com/library/jj266463(v=office.15)">Microsoft.Lync.Model.Contact</a> object collection.</p></td>
    </tr>
    </tbody>
    </table>

4.  For each group, iterate over the **Contact** objects.

5.  For each contact, add the user’s SIP address to the contact list in the UI. Get the SIP address by reading the [Contact.Uri](https://msdn.microsoft.com/library/jj293279\(v=office.15\)) property.

### Code example

The following example updates the application UI by using the current state of the client, gets the user’s URI, checks the state of the room manager, and adds the title of every room in the followed room collection to a list in the Persistent Chat room UI.

```csharp
        /// <summary>
        /// Iterates on all groups and adds an Uri string for each contact in a group to a list on the UI
        /// </summary>
        private void LoadAllContacts()
        {
            //Set the selection mode of the UI list to multi-select
            Contact_ListBox.SelectionMode = SelectionMode.MultiSimple;
            Contact_ListBox.Items.Clear();
            foreach (Group group in _LyncClient.ContactManager.Groups)
            {
                foreach (Contact contact in group)
                {
                    if (!Contact_ListBox.Items.Contains(contact.Uri))
                       Contact_ListBox.Items.Add(contact.Uri);
                }
            }
        }
```

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
<td><p>A contact can be in multiple groups. To avoid adding the same contact to the list twice, the previous example checks whether the contact has already been added to the list when it is processing successive groups.</p></td>
</tr>
</tbody>
</table>

## Add a new conversation

A user can select as many contacts as wanted to invite to a conversation. The list declared in the sample form is enabled for multiple selections. Each selection is only a SIP address and corresponding [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) objects are needed when you are adding selected contacts to the new conversation.

For each SIP address selected on the contact list, the sample gets the corresponding **Contact** by calling the [ContactManager.GetContactByUri](https://msdn.microsoft.com/library/jj274481\(v=office.15\)) method. The contact objects are stored in the **\_selectedContacts** dictionary that was declared previously and then used in the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event.

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
<td><p>When you add a new conversation, you have only started a SIP dialog with Microsoft Lync Server 2013 but you have not set a list of users to be invited or registered for conversation-related events. You must wait for a confirmation from Lync Server 2013 that a conversation SIP dialog is established. You are notified in the <strong>ConversationAdded</strong> event.</p></td>
</tr>
</tbody>
</table>

### Code example

The following example starts a new conversation.

```csharp
        /// <summary>
        /// Starts a new conversation
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Start_Button_Click(object sender, EventArgs e)
        {
            Contact aContact;
            foreach (Object selectedObject in Contact_ListBox.SelectedItems)
            {
                aContact = _LyncClient.ContactManager.GetContactByUri(selectedObject.ToString());
                if (!_selectedContacts.ContainsKey(selectedObject.ToString()))
                {
                    _selectedContacts.Add(selectedObject.ToString(), aContact);
                }
            }
            _conversation = _LyncClient.ConversationManager.AddConversation();
        }
```

## Configure the newly added conversation

The [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event is raised when the conversation is established and you can add users to the conversation and register event callback methods for the conversation-related events.

Register for events on the conversation and the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) of the new conversation. This includes the participant that represents the local user. The best place to register for the conversation **ApplicationSharingModality** events is in the **ConversationAdded** event callback method. You must register for all participant’s **ApplicationSharingModality** events in your [Conversation.ParticipantAdded](https://msdn.microsoft.com/library/jj275759\(v=office.15\)) event.

### Handle the ConversationAdded event

Although the [ConversationManager.AddConversation](https://msdn.microsoft.com/library/jj276176\(v=office.15\)) method returns a new [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) object synchronously, a set of SIP messages is sent to Lync Server 2013 and used by the server to create a client/server SIP dialog that encapsulates the conversation. When the SIP dialog is established, the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event is raised. Use this event to register for conversation-related events and send conversation invitations to all of the contacts that the user selected. The following procedure describes the tasks completed by the event callback method that handles **ConversationAdded**.

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
<td><p>This sample class listens for any new conversation started by the local user or by another user who invites the local user. When this type of conversation is added, it only hosts that conversation and is not designed to handle additional new conversations. To make this possible, the sample unregisters the <strong>ConversationAdded</strong> event callback. The callback is reregistered when the conversation is ended.</p></td>
</tr>
</tbody>
</table>

### To handle the ConversationAdded event

1.  Unregister the event callback method on [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) so that the sample ignores any other new conversations until this conversation is finished.

2.  Register for the [Conversation.StateChanged](https://msdn.microsoft.com/library/jj278070\(v=office.15\)) and [Conversation.ParticipantAdded](https://msdn.microsoft.com/library/jj275759\(v=office.15\)) events on the new conversation.

3.  Store the [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) object from the **Conversation**.

4.  Register event callback methods for all of the events that are exposed by the conversation **ApplicationSharingModality**.

5.  Add participants to the new conversation.

After the **ConversationAdded** event callback method is finished, the application is listening for events on the conversation **ApplicationSharingModality**, and invitations have been sent to the contacts that are added to the conversation.

#### Code example

The following example handles the **ConversationAdded** event.

```csharp
        /// <summary>
        /// Handles the event raised when a new conversation is added. This sample only hosts one conversation
        /// at a time. Once this event is handled, the sample un-registers for this event. The event is registered again when
        /// this conversation is removed from the ContactManager.Conversations collection upon termination of this conversation.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ConversationManager_ConversationAdded(object sender, Microsoft.Lync.Model.Conversation.ConversationManagerEventArgs e)
        {
            //Flag that indicates that the new conversation was started locally instead of by a remote user. 
            Boolean addedByThisProcess = true;

            //Suspend hosting new conversations until this conversation is ended
            _LyncClient.ConversationManager.ConversationAdded -= ConversationManager_ConversationAdded;

            //If this class field is null then the new conversation was not started by this running process. It was
            //Started by the Lync client or by a remote user.
            if (_conversation == null)
            {
                addedByThisProcess = false;
                _conversation = e.Conversation;
            }

            //Register for conversation state changes such as Active->Terminated.
            _conversation.StateChanged += _conversation_StateChanged;
 
            //Register for participant added events on the new conversation
            //The next important action in the chain of conversation intiating action happens in the ParticipantAdded event handler.
            _conversation.ParticipantAdded += _conversation_ParticipantAdded;
            _conversation.ParticipantRemoved += _conversation_ParticipantRemoved;
 
            //Register for the application sharing modality event on the conversation itself
            _sharingModality = (ApplicationSharingModality)_conversation.Modalities[ModalityTypes.ApplicationSharing];
 
            //Register for state changes like connecting->connected
            _sharingModality.ModalityStateChanged += _sharingModality_ModalityStateChanged;
 
            //Register to catch requests from other participants for control of the locally owned sharing resource.
            _sharingModality.ControlRequestReceived += _sharingModality_ControlRequestReceived;
            _sharingModality.ControllerChanged += _sharingModality_ControllerChanged;
 
            //Register to catch changes in the list of local sharable resources such as a process that starts up or terminates.
            _sharingModality.LocalSharedResourcesChanged += _sharingModality_LocalSharedResourcesChanged;
 
            //Register for changes in the availbility of resource controlling actions such as grant and revoke.
            _sharingModality.ActionAvailabilityChanged += _sharingModality_ActionAvailabilityChanged;
 
            //Register for changes in the local participant's mode of sharing participation
            // such as Viewing->Sharing, Requesting Control->Controlling.
            _sharingModality.ParticipationStateChanged += _sharingModality_ParticipationStateChanged;
 
            // If the new conversation was started by the local user, the conversation does not have
            // any participants yet. Participants are added from the contacts selected by the local user
            if (addedByThisProcess == true)
            {
                Contact aContact;
 
                //Clear out the contact list on the UI to be replaced with only the contacts selected for the current conversation.
                this.Invoke(new ClearAllContactsDelegate(ClearAllContacts));
 
                //Iterate on the contact dictionary that is filled from the contact Sip addresses selected from the 
                //contact list UI control. Add each selected contact to the conversation, causing an invitation to be
                //sent to each contact.
                foreach (Contact selectedContact in _selectedContacts.Values)
                {
                    Participant newParticipant =  _conversation.AddParticipant(selectedContact);
                    this.Invoke(new AddAContactDelegate(AddAContact), new object[] { selectedContact.Uri });
                }
            }
 
            //Update the list of local sharable resources on the UI
            this.Invoke(new UpdateSharedResourcesListboxDelegate(UpdateSharedResourcesListbox));
 
            //Set the enabled state of the resource sharing button, end conversation button, and start conversation button.
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, true });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, true });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, false });
         }
```

### Handle the ParticipantAdded event

The [Conversation.ParticipantAdded](https://msdn.microsoft.com/library/jj275759\(v=office.15\)) event is raised when a participant is added to the **Conversation** object. A **ParticipantAdded** event callback must handle the following tasks:

  - Register for the [Modality.ActionAvailabilityChanged](https://msdn.microsoft.com/library/jj293249\(v=office.15\)) event on the added participant’s [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) instance.

  - For the self-participant, read the [Participant.Properties](https://msdn.microsoft.com/library/jj278318\(v=office.15\)) property, specifying the [ParticipantProperty](https://msdn.microsoft.com/library/jj277580\(v=office.15\))**.IsPresenter** enumerator as the property collection key.

  - Enable the UI to allow sharing a local resource if the **IsPresenter** property is a Boolean true value.

  - For the self-participant, register for the [Participant.PropertyChanged](https://msdn.microsoft.com/library/jj293995\(v=office.15\)) event to be notified if the self-participant is promoted to presenter or demoted to attendee.

The following example registers for the [Conversation.ParticipantAdded](https://msdn.microsoft.com/library/jj275759\(v=office.15\)) event and stores the participant [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality](https://msdn.microsoft.com/library/jj275536\(v=office.15\)) object in a dictionary that uses the [Contact.Uri](https://msdn.microsoft.com/library/jj293279\(v=office.15\)) string as a key. To grant control of a locally shared resource in the conversation, the appropriate participant **ApplicationSharingModality** is retrieved from the dictionary by the user’s URI and then the [ApplicationSharingModality.BeginGrantControl](https://msdn.microsoft.com/library/jj274501\(v=office.15\)) method is called on modality.

#### Code example

The following example handles the [Conversation.ParticipantAdded](https://msdn.microsoft.com/library/jj275759\(v=office.15\)) event.

```csharp
        /// <summary>
        /// Handles the participant added event. Registers for events on the application sharing modality for the 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_ParticipantAdded(object sender, ParticipantCollectionChangedEventArgs e)
        {
            //Is this added participant the local user?
            if (e.Participant.IsSelf)
            {
                //Store the application sharing modality of the local user so that
                //the user can request or release control of a remotely owned and shared resource.
                _LocalParticipantSharingModality = (ApplicationSharingModality)e.Participant.Modalities[ModalityTypes.ApplicationSharing];
 
                //Enable or disable the Start Resource Sharing button according to the role of the local participant.
                //Roles can be Presenter or Attendee.
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, (Boolean)e.Participant.Properties[ParticipantProperty.IsPresenter] });
 
                //Register for the particpant property changed event to be notified when the role of the local user changes.
                e.Participant.PropertyChanged += Participant_PropertyChanged;
            }
 
             //Get the application sharing modality of the added participant and store it in a class dictionary field for easy access later.
            ApplicationSharingModality participantSharingModality = (ApplicationSharingModality)e.Participant.Modalities[ModalityTypes.ApplicationSharing];
            _participantSharingModalities.Add(e.Participant.Contact.Uri, participantSharingModality);
 
            //register for important events on the application sharing modality of the new participant.
            participantSharingModality.ActionAvailabilityChanged += _sharingModality_ActionAvailabilityChanged;
            participantSharingModality.ModalityStateChanged += _sharingModality_ModalityStateChanged;
 
        }
```

### Handle the ParticipantRemoved event

The [Conversation.ParticipantRemoved](https://msdn.microsoft.com/library/jj268280\(v=office.15\)) event is raised when a participant has declined an invitation to join a conversation. Use this event to remove the **ApplicationSharingModality** object from the Dictionary that you added it to in the previous example. You should also unregister any event callback methods that you registered on this participant’s modalities when the participant was added.

#### Code example

The following example unregisters for participant events, removes the participant’s **ApplicationSharingModality** from the Dictionary, and then removes the URI of the participant from the UI list.

```csharp
        /// <summary>
        /// Handles the event raised when a particpant is removed from the conversation.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_ParticipantRemoved(object sender, ParticipantCollectionChangedEventArgs e)
        {
 
            //get the application sharing modality of the removed participant out of the class modalty dicitonary
            ApplicationSharingModality removedModality = _participantSharingModalities[e.Participant.Contact.Uri];
 
            //Un-register for modality events on this participant's application sharing modality.
            removedModality.ActionAvailabilityChanged -= _sharingModality_ActionAvailabilityChanged;
 
            //Remove the modality from the dictionary.
            _participantSharingModalities.Remove(e.Participant.Contact.Uri);

            //Remove the modality from the UI list.
            this.Invoke(new RemoveAContactDelegate(RemoveAContact), new object[] { e.Participant.Contact.Uri});
        }
```

#### Handle the ParticipantPropertyChanged event

If the self-participant **IsPresenter** property value changes from true to false, the local user has been demoted to attendee and can no longer share a local resource. If the property value changes from false to true, the local user has been promoted to presenter and can share local resources in the conversation. Use this event to update your UI controls that start sharing a resource.

#### Code example

The following example enables or disables a UI button that starts resource sharing.

```csharp
        /// <summary>
        /// Called when a participant property is changed.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Participant_PropertyChanged(object sender, ParticipantPropertyChangedEventArgs e)
        {
            if (e.Property == ParticipantProperty.IsPresenter)
            {
                //Enable or disable the Start Sharing Resource button according to the participant role
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, (Boolean)e.Value });
            }
        }
```

## Get a list of shareable resources

You can fill or refresh a UI list of locally shareable resources at any time after the conversation is created. The best place to call a method that does this is in the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event.

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
<td><p>You must get the locally shareable resources from the <strong>Conversation</strong><a href="https://msdn.microsoft.com/library/jj275536(v=office.15)">Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality</a> instead of any participant <strong>ApplicationSharingModality</strong>.</p></td>
</tr>
</tbody>
</table>

### Code example

The following example fills a list that has the resources that can be shared in a conversation.

```csharp
        /// <summary>
        /// Fills a UI list with the names of all local resources that can be shared.
        /// </summary>
        private void UpdateSharedResourcesListbox()
        {
            SharedResources_ListBox.Items.Clear();
            if (_sharingModality == null || _sharingModality.ShareableResources == null)
            {
                return;
            }
            if (_sharingModality.ShareableResources.Count > 0)
            {
                SharingResource sharingResource;
                for (int j = 0; j < _sharingModality.ShareableResources.Count; j++)
                {
                    sharingResource = _sharingModality.ShareableResources[j];
                    SharedResources_ListBox.Items.Add(sharingResource.Name);
                }
            }
        }
```

## Code examples: Share resources

The following example declares a Windows Form that lets a user start a new conversation, select a shareable resource, share the resource, and then manage the control of the shared resource.

```csharp
namespace ShareResources
{
    partial class ShareResources_Form
    {
        /// <summary>
        /// Required designer variable.
        /// </summary>
        private System.ComponentModel.IContainer components = null;

        /// <summary>
        /// Clean up any resources being used.
        /// </summary>
        /// <param name="disposing">true if managed resources should be disposed; otherwise, false.</param>
        protected override void Dispose(bool disposing)
        {
            if (disposing && (components != null))
            {
                components.Dispose();
            }
            base.Dispose(disposing);
        }

        #region Windows Form Designer generated code

        /// <summary>
        /// Required method for Designer support - do not modify
        /// the contents of this method with the code editor.
        /// </summary>
        private void InitializeComponent()
        {
            this.ClientState_Label = new System.Windows.Forms.Label();
            this.ClientStateString_Label = new System.Windows.Forms.Label();
            this.Contact_ListBox = new System.Windows.Forms.ListBox();
            this.StartSharingResource_Button = new System.Windows.Forms.Button();
            this.Accept_Button = new System.Windows.Forms.Button();
            this.Decline_Button = new System.Windows.Forms.Button();
            this.Grant_Button = new System.Windows.Forms.Button();
            this.SharingAction_GroupBox = new System.Windows.Forms.GroupBox();
            this.Disconnect_Button = new System.Windows.Forms.Button();
            this.Revoke_Button = new System.Windows.Forms.Button();
            this.Request_Button = new System.Windows.Forms.Button();
            this.Release_Button = new System.Windows.Forms.Button();
            this.SharingParticipationState_Label = new System.Windows.Forms.Label();
            this.SharingParticipationStateString_Label = new System.Windows.Forms.Label();
            this.SharedResources_ListBox = new System.Windows.Forms.ListBox();
            this.ConversationActions_Group = new System.Windows.Forms.GroupBox();
            this.EndConversation_Button = new System.Windows.Forms.Button();
            this.Start_Button = new System.Windows.Forms.Button();
            this.ResourceController_Label = new System.Windows.Forms.Label();
            this.ResourceControllerName_Label = new System.Windows.Forms.Label();
            this.ShareableResources_Label = new System.Windows.Forms.Label();
            this.ContactList_Label = new System.Windows.Forms.Label();
            this.SharedResource_Label = new System.Windows.Forms.Label();
            this.groupBox1 = new System.Windows.Forms.GroupBox();
            this.Acceptx_Button = new System.Windows.Forms.Button();
            this.RejectX_Button = new System.Windows.Forms.Button();
            this.RefreshResource_Button = new System.Windows.Forms.Button();
            this.SharingAction_GroupBox.SuspendLayout();
            this.ConversationActions_Group.SuspendLayout();
            this.groupBox1.SuspendLayout();
            this.SuspendLayout();
            // 
            // ClientState_Label
            // 
            this.ClientState_Label.AutoSize = true;
            this.ClientState_Label.Location = new System.Drawing.Point(13, 13);
            this.ClientState_Label.Name = "ClientState_Label";
            this.ClientState_Label.Size = new System.Drawing.Size(64, 13);
            this.ClientState_Label.TabIndex = 0;
            this.ClientState_Label.Text = "Client State:";
            // 
            // ClientStateString_Label
            // 
            this.ClientStateString_Label.AutoSize = true;
            this.ClientStateString_Label.Location = new System.Drawing.Point(112, 15);
            this.ClientStateString_Label.Name = "ClientStateString_Label";
            this.ClientStateString_Label.Size = new System.Drawing.Size(58, 13);
            this.ClientStateString_Label.TabIndex = 1;
            this.ClientStateString_Label.Text = "Signed out";
            // 
            // Contact_ListBox
            // 
            this.Contact_ListBox.FormattingEnabled = true;
            this.Contact_ListBox.Location = new System.Drawing.Point(13, 63);
            this.Contact_ListBox.Name = "Contact_ListBox";
            this.Contact_ListBox.SelectionMode = System.Windows.Forms.SelectionMode.MultiSimple;
            this.Contact_ListBox.Size = new System.Drawing.Size(180, 82);
            this.Contact_ListBox.TabIndex = 2;
            // 
            // StartSharingResource_Button
            // 
            this.StartSharingResource_Button.Location = new System.Drawing.Point(12, 397);
            this.StartSharingResource_Button.Name = "StartSharingResource_Button";
            this.StartSharingResource_Button.Size = new System.Drawing.Size(153, 23);
            this.StartSharingResource_Button.TabIndex = 3;
            this.StartSharingResource_Button.Text = "4) Share Resource";
            this.StartSharingResource_Button.UseVisualStyleBackColor = true;
            this.StartSharingResource_Button.Click += new System.EventHandler(this.StartSharingResource_Button_Click);
            // 
            // Accept_Button
            // 
            this.Accept_Button.Enabled = false;
            this.Accept_Button.Location = new System.Drawing.Point(11, 28);
            this.Accept_Button.Name = "Accept_Button";
            this.Accept_Button.Size = new System.Drawing.Size(130, 23);
            this.Accept_Button.TabIndex = 4;
            this.Accept_Button.Text = "Accept";
            this.Accept_Button.UseVisualStyleBackColor = true;
            this.Accept_Button.Click += new System.EventHandler(this.Accept_Button_Click);
            // 
            // Decline_Button
            // 
            this.Decline_Button.Enabled = false;
            this.Decline_Button.Location = new System.Drawing.Point(11, 57);
            this.Decline_Button.Name = "Decline_Button";
            this.Decline_Button.Size = new System.Drawing.Size(130, 23);
            this.Decline_Button.TabIndex = 5;
            this.Decline_Button.Text = "Decline";
            this.Decline_Button.UseVisualStyleBackColor = true;
            this.Decline_Button.Click += new System.EventHandler(this.Decline_Button_Click);
            // 
            // Grant_Button
            // 
            this.Grant_Button.Enabled = false;
            this.Grant_Button.Location = new System.Drawing.Point(11, 86);
            this.Grant_Button.Name = "Grant_Button";
            this.Grant_Button.Size = new System.Drawing.Size(130, 23);
            this.Grant_Button.TabIndex = 6;
            this.Grant_Button.Text = "Grant";
            this.Grant_Button.UseVisualStyleBackColor = true;
            this.Grant_Button.Click += new System.EventHandler(this.Grant_Button_Click);
            // 
            // SharingAction_GroupBox
            // 
            this.SharingAction_GroupBox.Controls.Add(this.Disconnect_Button);
            this.SharingAction_GroupBox.Controls.Add(this.Revoke_Button);
            this.SharingAction_GroupBox.Controls.Add(this.Request_Button);
            this.SharingAction_GroupBox.Controls.Add(this.Release_Button);
            this.SharingAction_GroupBox.Controls.Add(this.Accept_Button);
            this.SharingAction_GroupBox.Controls.Add(this.Grant_Button);
            this.SharingAction_GroupBox.Controls.Add(this.Decline_Button);
            this.SharingAction_GroupBox.Location = new System.Drawing.Point(235, 15);
            this.SharingAction_GroupBox.Name = "SharingAction_GroupBox";
            this.SharingAction_GroupBox.Size = new System.Drawing.Size(162, 232);
            this.SharingAction_GroupBox.TabIndex = 7;
            this.SharingAction_GroupBox.TabStop = false;
            this.SharingAction_GroupBox.Text = "6) Take a control action";
            // 
            // Disconnect_Button
            // 
            this.Disconnect_Button.Enabled = false;
            this.Disconnect_Button.Location = new System.Drawing.Point(11, 202);
            this.Disconnect_Button.Name = "Disconnect_Button";
            this.Disconnect_Button.Size = new System.Drawing.Size(130, 23);
            this.Disconnect_Button.TabIndex = 10;
            this.Disconnect_Button.Text = "Stop Sharing";
            this.Disconnect_Button.UseVisualStyleBackColor = true;
            this.Disconnect_Button.Click += new System.EventHandler(this.Disconnect_Button_Click);
            // 
            // Revoke_Button
            // 
            this.Revoke_Button.Enabled = false;
            this.Revoke_Button.Location = new System.Drawing.Point(11, 115);
            this.Revoke_Button.Name = "Revoke_Button";
            this.Revoke_Button.Size = new System.Drawing.Size(130, 23);
            this.Revoke_Button.TabIndex = 9;
            this.Revoke_Button.Text = "Revoke";
            this.Revoke_Button.UseVisualStyleBackColor = true;
            this.Revoke_Button.Click += new System.EventHandler(this.Revoke_Button_Click);
            // 
            // Request_Button
            // 
            this.Request_Button.Enabled = false;
            this.Request_Button.Location = new System.Drawing.Point(11, 144);
            this.Request_Button.Name = "Request_Button";
            this.Request_Button.Size = new System.Drawing.Size(130, 23);
            this.Request_Button.TabIndex = 8;
            this.Request_Button.Text = "Request";
            this.Request_Button.UseVisualStyleBackColor = true;
            this.Request_Button.Click += new System.EventHandler(this.Request_Button_Click);
            // 
            // Release_Button
            // 
            this.Release_Button.Enabled = false;
            this.Release_Button.Location = new System.Drawing.Point(11, 173);
            this.Release_Button.Name = "Release_Button";
            this.Release_Button.Size = new System.Drawing.Size(130, 23);
            this.Release_Button.TabIndex = 7;
            this.Release_Button.Text = "Release";
            this.Release_Button.UseVisualStyleBackColor = true;
            this.Release_Button.Click += new System.EventHandler(this.Release_Button_Click);
            // 
            // SharingParticipationState_Label
            // 
            this.SharingParticipationState_Label.AutoSize = true;
            this.SharingParticipationState_Label.Location = new System.Drawing.Point(240, 253);
            this.SharingParticipationState_Label.Name = "SharingParticipationState_Label";
            this.SharingParticipationState_Label.Size = new System.Drawing.Size(27, 13);
            this.SharingParticipationState_Label.TabIndex = 8;
            this.SharingParticipationState_Label.Text = "I am";
            // 
            // SharingParticipationStateString_Label
            // 
            this.SharingParticipationStateString_Label.AutoSize = true;
            this.SharingParticipationStateString_Label.Location = new System.Drawing.Point(264, 253);
            this.SharingParticipationStateString_Label.Name = "SharingParticipationStateString_Label";
            this.SharingParticipationStateString_Label.Size = new System.Drawing.Size(62, 13);
            this.SharingParticipationStateString_Label.TabIndex = 9;
            this.SharingParticipationStateString_Label.Text = " not sharing";
            // 
            // SharedResources_ListBox
            // 
            this.SharedResources_ListBox.FormattingEnabled = true;
            this.SharedResources_ListBox.HorizontalScrollbar = true;
            this.SharedResources_ListBox.Location = new System.Drawing.Point(12, 283);
            this.SharedResources_ListBox.Name = "SharedResources_ListBox";
            this.SharedResources_ListBox.Size = new System.Drawing.Size(181, 108);
            this.SharedResources_ListBox.TabIndex = 11;
            // 
            // ConversationActions_Group
            // 
            this.ConversationActions_Group.Controls.Add(this.EndConversation_Button);
            this.ConversationActions_Group.Controls.Add(this.Start_Button);
            this.ConversationActions_Group.Location = new System.Drawing.Point(12, 158);
            this.ConversationActions_Group.Name = "ConversationActions_Group";
            this.ConversationActions_Group.Size = new System.Drawing.Size(161, 89);
            this.ConversationActions_Group.TabIndex = 13;
            this.ConversationActions_Group.TabStop = false;
            this.ConversationActions_Group.Text = "2) Start a conversation";
            // 
            // EndConversation_Button
            // 
            this.EndConversation_Button.Enabled = false;
            this.EndConversation_Button.Location = new System.Drawing.Point(16, 50);
            this.EndConversation_Button.Name = "EndConversation_Button";
            this.EndConversation_Button.Size = new System.Drawing.Size(130, 23);
            this.EndConversation_Button.TabIndex = 0;
            this.EndConversation_Button.Text = "End";
            this.EndConversation_Button.UseVisualStyleBackColor = true;
            this.EndConversation_Button.Click += new System.EventHandler(this.EndConversation_Button_Click);
            // 
            // Start_Button
            // 
            this.Start_Button.Enabled = false;
            this.Start_Button.Location = new System.Drawing.Point(16, 21);
            this.Start_Button.Name = "Start_Button";
            this.Start_Button.Size = new System.Drawing.Size(130, 23);
            this.Start_Button.TabIndex = 16;
            this.Start_Button.Text = "Start";
            this.Start_Button.UseVisualStyleBackColor = true;
            this.Start_Button.Click += new System.EventHandler(this.Start_Button_Click);
            // 
            // ResourceController_Label
            // 
            this.ResourceController_Label.AutoSize = true;
            this.ResourceController_Label.Location = new System.Drawing.Point(240, 300);
            this.ResourceController_Label.Name = "ResourceController_Label";
            this.ResourceController_Label.Size = new System.Drawing.Size(103, 13);
            this.ResourceController_Label.TabIndex = 14;
            this.ResourceController_Label.Text = "Resource Controller:";
            // 
            // ResourceControllerName_Label
            // 
            this.ResourceControllerName_Label.AutoSize = true;
            this.ResourceControllerName_Label.Location = new System.Drawing.Point(240, 322);
            this.ResourceControllerName_Label.Name = "ResourceControllerName_Label";
            this.ResourceControllerName_Label.Size = new System.Drawing.Size(0, 13);
            this.ResourceControllerName_Label.TabIndex = 15;
            // 
            // ShareableResources_Label
            // 
            this.ShareableResources_Label.AutoSize = true;
            this.ShareableResources_Label.Location = new System.Drawing.Point(13, 267);
            this.ShareableResources_Label.Name = "ShareableResources_Label";
            this.ShareableResources_Label.Size = new System.Drawing.Size(93, 13);
            this.ShareableResources_Label.TabIndex = 17;
            this.ShareableResources_Label.Text = "3) Pick a resource";
            // 
            // ContactList_Label
            // 
            this.ContactList_Label.AutoSize = true;
            this.ContactList_Label.Location = new System.Drawing.Point(12, 44);
            this.ContactList_Label.Name = "ContactList_Label";
            this.ContactList_Label.Size = new System.Drawing.Size(99, 13);
            this.ContactList_Label.TabIndex = 20;
            this.ContactList_Label.Text = "1) Choose contacts";
            // 
            // SharedResource_Label
            // 
            this.SharedResource_Label.AutoSize = true;
            this.SharedResource_Label.Location = new System.Drawing.Point(243, 350);
            this.SharedResource_Label.Name = "SharedResource_Label";
            this.SharedResource_Label.Size = new System.Drawing.Size(33, 13);
            this.SharedResource_Label.TabIndex = 21;
            this.SharedResource_Label.Text = "None";
            // 
            // groupBox1
            // 
            this.groupBox1.Controls.Add(this.RejectX_Button);
            this.groupBox1.Controls.Add(this.Acceptx_Button);
            this.groupBox1.Location = new System.Drawing.Point(235, 381);
            this.groupBox1.Name = "groupBox1";
            this.groupBox1.Size = new System.Drawing.Size(164, 96);
            this.groupBox1.TabIndex = 22;
            this.groupBox1.TabStop = false;
            this.groupBox1.Text = "Sharing Invitiation Action";
            // 
            // Acceptx_Button
            // 
            this.Acceptx_Button.Enabled = false;
            this.Acceptx_Button.Location = new System.Drawing.Point(11, 19);
            this.Acceptx_Button.Name = "Acceptx_Button";
            this.Acceptx_Button.Size = new System.Drawing.Size(130, 23);
            this.Acceptx_Button.TabIndex = 0;
            this.Acceptx_Button.Text = "Accept";
            this.Acceptx_Button.UseVisualStyleBackColor = true;
            this.Acceptx_Button.Click += new System.EventHandler(this.Acceptx_Button_Click);
            // 
            // RejectX_Button
            // 
            this.RejectX_Button.Enabled = false;
            this.RejectX_Button.Location = new System.Drawing.Point(11, 48);
            this.RejectX_Button.Name = "RejectX_Button";
            this.RejectX_Button.Size = new System.Drawing.Size(130, 23);
            this.RejectX_Button.TabIndex = 1;
            this.RejectX_Button.Text = "Reject";
            this.RejectX_Button.UseVisualStyleBackColor = true;
            this.RejectX_Button.Click += new System.EventHandler(this.RejectX_Button_Click);
            // 
            // RefreshResource_Button
            // 
            this.RefreshResource_Button.Location = new System.Drawing.Point(12, 445);
            this.RefreshResource_Button.Name = "RefreshResource_Button";
            this.RefreshResource_Button.Size = new System.Drawing.Size(153, 23);
            this.RefreshResource_Button.TabIndex = 23;
            this.RefreshResource_Button.Text = "Refresh resources";
            this.RefreshResource_Button.UseVisualStyleBackColor = true;
            this.RefreshResource_Button.Click += new System.EventHandler(this.RefreshResource_Button_Click);
            // 
            // ShareResources_Form
            // 
            this.AutoScaleDimensions = new System.Drawing.SizeF(6F, 13F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(409, 489);
            this.Controls.Add(this.RefreshResource_Button);
            this.Controls.Add(this.groupBox1);
            this.Controls.Add(this.SharedResource_Label);
            this.Controls.Add(this.ContactList_Label);
            this.Controls.Add(this.ShareableResources_Label);
            this.Controls.Add(this.ResourceControllerName_Label);
            this.Controls.Add(this.ResourceController_Label);
            this.Controls.Add(this.ConversationActions_Group);
            this.Controls.Add(this.SharedResources_ListBox);
            this.Controls.Add(this.SharingParticipationStateString_Label);
            this.Controls.Add(this.SharingParticipationState_Label);
            this.Controls.Add(this.SharingAction_GroupBox);
            this.Controls.Add(this.StartSharingResource_Button);
            this.Controls.Add(this.Contact_ListBox);
            this.Controls.Add(this.ClientStateString_Label);
            this.Controls.Add(this.ClientState_Label);
            this.Name = "ShareResources_Form";
            this.StartPosition = System.Windows.Forms.FormStartPosition.CenterScreen;
            this.Text = "Share Resources";
            this.Load += new System.EventHandler(this.ShareResources_Form_Load);
            this.SharingAction_GroupBox.ResumeLayout(false);
            this.ConversationActions_Group.ResumeLayout(false);
            this.groupBox1.ResumeLayout(false);
            this.ResumeLayout(false);
            this.PerformLayout();

        }

        #endregion

        private System.Windows.Forms.Label ClientState_Label;
        private System.Windows.Forms.Label ClientStateString_Label;
        private System.Windows.Forms.ListBox Contact_ListBox;
        private System.Windows.Forms.Button StartSharingResource_Button;
        private System.Windows.Forms.Button Accept_Button;
        private System.Windows.Forms.Button Decline_Button;
        private System.Windows.Forms.Button Grant_Button;
        private System.Windows.Forms.GroupBox SharingAction_GroupBox;
        private System.Windows.Forms.Button Release_Button;
        private System.Windows.Forms.Button Revoke_Button;
        private System.Windows.Forms.Button Request_Button;
        private System.Windows.Forms.Label SharingParticipationState_Label;
        private System.Windows.Forms.Label SharingParticipationStateString_Label;
        private System.Windows.Forms.ListBox SharedResources_ListBox;
        private System.Windows.Forms.GroupBox ConversationActions_Group;
        private System.Windows.Forms.Button EndConversation_Button;
        private System.Windows.Forms.Button Disconnect_Button;
        private System.Windows.Forms.Label ResourceController_Label;
        private System.Windows.Forms.Label ResourceControllerName_Label;
        private System.Windows.Forms.Button Start_Button;
        private System.Windows.Forms.Label ShareableResources_Label;
        private System.Windows.Forms.Label ContactList_Label;
        private System.Windows.Forms.Label SharedResource_Label;
        private System.Windows.Forms.GroupBox groupBox1;
        private System.Windows.Forms.Button RejectX_Button;
        private System.Windows.Forms.Button Acceptx_Button;
        private System.Windows.Forms.Button RefreshResource_Button;
    }
}
```

The following example interacts with the Windows Form declared in the previous example.

```csharp
using System;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;
using Microsoft.Lync.Model.Conversation;
using Microsoft.Lync.Model.Conversation.Sharing;
using System.Collections.Generic;

namespace ShareResources
{
    public partial class ShareResources_Form : Form
    {

        #region class field declarations
        /// <summary>
        /// Lync client platform. The entry point to the API
        /// </summary>
        Microsoft.Lync.Model.LyncClient _LyncClient;

        /// <summary>
        /// Represents a Lync conversation
        /// </summary>
        Conversation _conversation;

        /// <summary>
        /// A Contact instance representing the participant selected to be granted control of a resource
        /// </summary>
        Contact _ResourceControllingContact;

        /// <summary>
        /// Dictionary of all contacts selected from the multi-select enabled contact list on UI
        /// </summary>
        Dictionary<string, Contact> _selectedContacts = new Dictionary<string, Contact>();

        /// <summary>
        /// Collection of all participants application sharing modalities, keyed by Contact.Uri.
        /// See _controllingContact class field...
        /// </summary>
        Dictionary<string, ApplicationSharingModality> _participantSharingModalities = new Dictionary<string, ApplicationSharingModality>();

        /// <summary>
        /// The Application sharing modality of the conversation itself
        /// </summary>
        ApplicationSharingModality _sharingModality;

        /// <summary>
        /// The Application sharing modality of the local participant.
        /// </summary>
        ApplicationSharingModality _LocalParticipantSharingModality;
        #endregion

        #region UI event handlers

        /// <summary>
        /// invoked when sample form is loaded. Initializes fields, gets API entry point, 
        /// registers for events on Lync Client and ConversationManager.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ShareResources_Form_Load(object sender, EventArgs e)
        {
            try
            {
                //Get the API entry point
                _LyncClient = LyncClient.GetClient();

                //Resource sharing is not supported in UI suppression mode. Sample closes
                //if Lync UI is suppressed
                if (_LyncClient.InSuppressedMode == true)
                {
                    MessageBox.Show("Lync Client is in UI Suppressed mode. Sharing is not supported.", "Application Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                    this.Close();
                }

                //Display the current state of the Lync client.
                ClientStateString_Label.Text = _LyncClient.State.ToString();

                //If the Lync client is signed out, sign into the Lync client
                if (_LyncClient.State == ClientState.SignedOut)
                {
                    _LyncClient.EndSignIn(_LyncClient.BeginSignIn(
                        "terrya@contoso.com",
                        "terrya@contoso.com",
                        "MyPassword",
                        null,
                        null));
                }

                //Display the current state of the Lync client.
                ClientStateString_Label.Text = _LyncClient.State.ToString();

                //Register for the three Lync client events needed so that application is notified when:
                // * Lync client signs in or out
                // * A new conversation is added (remotely via invite or locally by user)
                // * A conversation is removed (conversation ends)
                _LyncClient.StateChanged += _LyncClient_StateChanged;
                _LyncClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
                _LyncClient.ConversationManager.ConversationRemoved += ConversationManager_ConversationRemoved;

                //Enable the start conversation button on the UI
                Start_Button.Enabled = true;

                //ShareDesktop.LoadAllContacts loads the contact list on the UI with  all contacts that are in the user's Lync client contact list.
                LoadAllContacts();

            }
            catch (NotInitializedException)
            {
                MessageBox.Show("Client is not initialized.  Closing form", "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
            catch (ClientNotFoundException)
            {
                MessageBox.Show("Client is not running.  Closing form", "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
            catch (Exception exc)
            {
                MessageBox.Show("General exception: " + exc.Message, "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }

        }

        /// <summary>
        /// Handles click event on sharing resource button. User must select a resource
        /// from the sharable resources list before clicking the button.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void StartSharingResource_Button_Click(object sender, EventArgs e)
        {

            //If there is no active conversation to share this resource in, return from handler
            if (_conversation == null)
            {
                return;
            }

            //If there is no sharing modality stored locally on the active conversation, get it from the active conversation and store it.
            if (_sharingModality == null)
            {
                _sharingModality = _conversation.Modalities[ModalityTypes.ApplicationSharing] as ApplicationSharingModality;
            }

            //Process the users selected resource choice by calling this helper method
            ShareSelectedResource(SharedResources_ListBox.SelectedIndex);
        }

       /// <summary>
       ///Accept another participants request to control locally owned and shared resource.
       ///The Accept button is enabled when the _sharingModality_ActionAvailabilityChanged event handler is called
       ///with the event argument that specifies the ModalityAction.AcceptSharingControlRequest action is available.
       /// </summary>
       /// <param name="sender"></param>
       /// <param name="e"></param>
        private void Accept_Button_Click(object sender, EventArgs e)
        {
            Accept_Button.Text = "Accept";

            //_selectedContact is set to the Contact object of the participant who requested control of the resource. 
            //see the _sharingModality_ControlRequestReceived method in the application sharing modality event handlers region.
            ApplicationSharingModality sharingModality = (ApplicationSharingModality)_participantSharingModalities[_ResourceControllingContact.Uri];

            //If the requesting participant application sharing modality is available and the AcceptSharingControlRequest action can be invoked
            if (sharingModality != null && sharingModality.CanInvoke(ModalityAction.AcceptSharingControlRequest))
            {
                //Accept sharing control request.
                sharingModality.BeginAcceptControlRequest((ar) => {sharingModality.EndAcceptControlRequest(ar);}, null);
            }
        }

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
                sharingModality.BeginDeclineControlRequest((ar) => { sharingModality.EndDeclineControlRequest(ar); }, null);
            }

        }

        /// <summary>
        ///Grant another participant control of a locally owned and shared resource.
        ///The Grant button is enabled when the _sharingModality_ActionAvailabilityChanged event handler is
        ///called with the event argument that specifies the ModalityAction.GrantSharingControl action is available.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Grant_Button_Click(object sender, EventArgs e)
        {
            if (Contact_ListBox.SelectedItems.Count == 0)
            {
                MessageBox.Show("Please select a conversation participant");
                return;
            }
            //Get the sharing modality of the participant which the local user has selected to control the locally owned resource.
            try
            {
                ApplicationSharingModality sharingModality = (ApplicationSharingModality)_participantSharingModalities[Contact_ListBox.SelectedItem.ToString()];

                //If the application sharing modality is available and the resource can still be granted then grant
                //control of the resource.
                if (sharingModality != null && sharingModality.CanInvoke(ModalityAction.GrantSharingControl))
                {
                    sharingModality.BeginGrantControl((ar) => { sharingModality.EndGrantControl(ar); }
                        , null);
                }
            }
            catch (NullReferenceException) { MessageBox.Show("Chosen participant does not have an application sharing modality.", "Grant control error"); }

        }

        /// <summary>
        ///Release control of a remotely owned resource and shared resource.
        ///The Release button is enabled when the _sharingModality_ActionAvailabilityChanged event handler is
        ///called with the event argument that specifies the ModalityAction.ReleaseSharingControl action is available.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Release_Button_Click(object sender, EventArgs e)
        {
            if (_LocalParticipantSharingModality != null && _LocalParticipantSharingModality.CanInvoke(ModalityAction.ReleaseSharingControl))
            {
                _LocalParticipantSharingModality.BeginReleaseControl((ar) => { _LocalParticipantSharingModality.EndReleaseControl(ar); }, null);
            }
        }

        /// <summary>
        ///Request control of a remotely owned resource and shared resource.
        ///The Request button is enabled when the _sharingModality_ActionAvailabilityChanged event handler is called
        ///with the event argument that specifies the ModalityAction.RequestSharingControl action is available.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Request_Button_Click(object sender, EventArgs e)
        {
            if (_LocalParticipantSharingModality != null && _LocalParticipantSharingModality.CanInvoke(ModalityAction.RequestSharingControl))
            {
                _LocalParticipantSharingModality.BeginRequestControl((ar) => { _LocalParticipantSharingModality.EndRequestControl(ar); }, null);
            }
        }

        /// <summary>
        ///Revoke control of a remotely controlled resource and locally owned shared resource.
        ///The Revoke button is enabled when the _sharingModality_ActionAvailabilityChanged event handler is called
        ///with the event argument that specifies the ModalityAction.RevokeSharingControl action is available.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Revoke_Button_Click(object sender, EventArgs e)
        {
            if (_ResourceControllingContact == null)
            {
                return;
            }
            ApplicationSharingModality sharingModality = (ApplicationSharingModality)_participantSharingModalities[_ResourceControllingContact.Uri];
            if (sharingModality != null && sharingModality.CanInvoke(ModalityAction.RevokeSharingControl))
            {
                sharingModality.BeginRevokeControl((ar) => 
                {
                    try
                    {

                        sharingModality.EndRevokeControl(ar);
                    }
                    catch (OperationException oe) { MessageBox.Show("Operation exception " + oe.Message); }
                }
                , null);
            }

        }

        private void EndConversation_Button_Click(object sender, EventArgs e)
        {
            if (_conversation == null)
            {
                return;
            }
            if (_conversation.State != ConversationState.Terminated)
            {
                _conversation.End();
            }
        }

        /// <summary>
        /// Starts a new conversation
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Start_Button_Click(object sender, EventArgs e)
        {
            if (_conversation == null)
            {
                Contact aContact;
                foreach (Object selectedObject in Contact_ListBox.SelectedItems)
                {
                    aContact = _LyncClient.ContactManager.GetContactByUri(selectedObject.ToString());
                    if (!_selectedContacts.ContainsKey(selectedObject.ToString()))
                    {
                        _selectedContacts.Add(selectedObject.ToString(), aContact);
                    }
                }
                _conversation = _LyncClient.ConversationManager.AddConversation();
            }

        }

        /// <summary>
        /// Disconnects the conversation application sharing modality so that the user
        /// is no longer sharing or viewing a resource.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Disconnect_Button_Click(object sender, EventArgs e)
        {
            if (_sharingModality != null && _sharingModality.CanInvoke(ModalityAction.Disconnect))
            {
                _sharingModality.BeginDisconnect(ModalityDisconnectReason.None, (ar) => { _sharingModality.EndDisconnect(ar); }, null);

            }
        }

        /// <summary>
        /// Accepts an invitation to connect to a resource sharing modality
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Acceptx_Button_Click(object sender, EventArgs e)
        {
            _sharingModality.Accept();
        }

        /// <summary>
        /// Rejects an invitiation to connect to a resource sharing modality
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void RejectX_Button_Click(object sender, EventArgs e)
        {
            _sharingModality.Reject(ModalityDisconnectReason.Decline);
        }

        /// <summary>
        /// Updates the locally shareable resource list with the newest
        /// list of locally shareable resources
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void RefreshResource_Button_Click(object sender, EventArgs e)
        {
            UpdateSharedResourcesListbox();
        }

        #endregion

        #region Client event handlers

        /// <summary>
        /// Handles the event raised when a user signs in to or out of the Lync client.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _LyncClient_StateChanged(object sender, ClientStateChangedEventArgs e)
        {

            //If the client has signed in then get the client's contact list and enable the conversation start button.
            if (e.NewState == ClientState.SignedIn)
            {
                this.Invoke(new LoadAllContactsDelegate(LoadAllContacts));
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, true });
                this.Invoke(new UpdateSharedResourcesListboxDelegate(UpdateSharedResourcesListbox));

            }
            else
            {
                this.Invoke(new ClearAllContactsDelegate(ClearAllContacts));
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, false });

                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { ClientStateString_Label, e.NewState.ToString() });
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, false });
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, false });

            }
        }
        #endregion

        #region conversation manager event handlers
        /// <summary>
        /// Handles the event raised when the active conversation is terminated and removed from the collection of conversations
        /// on ConversationManager.Conversations
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ConversationManager_ConversationRemoved(object sender, ConversationManagerEventArgs e)
        {
            this.Invoke(new SetContactSelectionModeDelegate(SetContactSelectionMode), new object[] { SelectionMode.MultiSimple });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, false });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Disconnect_Button, false });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Request_Button, false });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, false });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, true });
            this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { ContactList_Label, "1) Choose contacts" });
            this.Invoke(new UpdateSharedResourcesListboxDelegate(UpdateSharedResourcesListbox));

            this.Invoke(new LoadAllContactsDelegate(LoadAllContacts));

            //Un-register for participant events on the conversation that is terminated.
            _conversation.ParticipantAdded -= _conversation_ParticipantAdded;
            _conversation.ParticipantRemoved -= _conversation_ParticipantRemoved;
            _conversation.StateChanged -= _conversation_StateChanged;

            //Unregister for events on the terminated conversation's sharing modality events.
            _sharingModality.ModalityStateChanged -= _sharingModality_ModalityStateChanged;
            _sharingModality.ControlRequestReceived -= _sharingModality_ControlRequestReceived;
            _sharingModality.LocalSharedResourcesChanged -= _sharingModality_LocalSharedResourcesChanged;
            _sharingModality.ControllerChanged -= _sharingModality_ControllerChanged;
            _sharingModality.ActionAvailabilityChanged -= _sharingModality_ActionAvailabilityChanged;

            //Unregister for the application sharing events on each and every participant in the terminated 
            //conversation
            foreach (string contactUri in _selectedContacts.Keys)
            {
                ApplicationSharingModality participantSharingModality = (ApplicationSharingModality)_participantSharingModalities[contactUri];
                participantSharingModality.ActionAvailabilityChanged -= _sharingModality_ActionAvailabilityChanged;
            }

            //If the removed conversation is the conversation hosted by this window then resume listening for new conversations.
            if (_conversation == e.Conversation)
            {
                //Resume listening for new conversations
                _LyncClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
            }

            //de-reference the class state
            _conversation = null;
            _ResourceControllingContact = null;
            _sharingModality = null;
            _participantSharingModalities.Clear();

        }

        /// <summary>
        /// Handles the event raised when a new conversation is added. This sample only hosts one conversation
        /// at a time. Once this event is handled, the sample un-registers for this event. The event is registered again when
        /// this conversation is removed from the ContactManager.Conversations collection upon termination of this conversation.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ConversationManager_ConversationAdded(object sender, Microsoft.Lync.Model.Conversation.ConversationManagerEventArgs e)
        {
            Boolean addedByThisProcess = true;

            try
            {
                //Suspend hosting new conversations until this conversation is ended
                _LyncClient.ConversationManager.ConversationAdded -= ConversationManager_ConversationAdded;
            }

            catch (Exception ex) { MessageBox.Show("Exception on de-register for ConversationAdded: " + ex.Message); }

            //If this class field is null then the new conversation was not started by this running process. It was
            //Started by the Lync client or by a remote user.
            if (_conversation == null)
            {
                addedByThisProcess = false;
                _conversation = e.Conversation;
            }

            //Register for conversation state changes such as Active->Terminated.
            _conversation.StateChanged += _conversation_StateChanged;

            //Register for the application sharing modality event on the conversation itself
            _sharingModality = (ApplicationSharingModality)_conversation.Modalities[ModalityTypes.ApplicationSharing];

            //Register for state changes like connecting->connected
            _sharingModality.ModalityStateChanged += _sharingModality_ModalityStateChanged;

            //Register to catch requests from other participants for control of the locally owned sharing resource.
            _sharingModality.ControlRequestReceived += _sharingModality_ControlRequestReceived;
            _sharingModality.ControllerChanged += _sharingModality_ControllerChanged;

            //Register to catch changes in the list of local sharable resources such as a process that starts up or terminates.
            _sharingModality.LocalSharedResourcesChanged += _sharingModality_LocalSharedResourcesChanged;

            //Register for changes in the availbility of resource controlling actions such as grant and revoke.
            _sharingModality.ActionAvailabilityChanged += _sharingModality_ActionAvailabilityChanged;

            //Register for changes in the local participant's mode of sharing participation
            // such as Viewing->Sharing, Requesting Control->Controlling.
            _sharingModality.ParticipationStateChanged += _sharingModality_ParticipationStateChanged;

            //Register for participant added events on the new conversation
            //The next important action in the chain of conversation intiating action happens in the ParticipantAdded event handler.
            _conversation.ParticipantAdded += _conversation_ParticipantAdded;
            _conversation.ParticipantRemoved += _conversation_ParticipantRemoved;

            if (addedByThisProcess == true)
            {
                Contact aContact;

                //Clear out the contact list on the UI to be replaced with only the contacts selected for the current conversation.
                this.Invoke(new ClearAllContactsDelegate(ClearAllContacts));

                //Iterate on the contact dictionary that is filled from the contact Sip addresses selected from the 
                //contact list UI control. Add each selected contact to the conversation, causing an invitation to be
                //sent to each contact.
                foreach (Contact selectedContact in _selectedContacts.Values)
                {
                    Participant newParticipant =  _conversation.AddParticipant(selectedContact);

                    //Register for events on the conversation participant's application sharing modality
                    ((ApplicationSharingModality)newParticipant.Modalities[ModalityTypes.ApplicationSharing]).ActionAvailabilityChanged += _sharingModality_ActionAvailabilityChanged;

               //     this.Invoke(new AddAContactDelegate(AddAContact), new object[] { selectedContact.Uri });
                }
            }

            //Update the list of local sharable resources on the UI
            this.Invoke(new UpdateSharedResourcesListboxDelegate(UpdateSharedResourcesListbox));

            //Set the enabled state of the resource sharing button, end conversation button, and start conversation button.
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, true });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { EndConversation_Button, true });
            this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { Start_Button, false });

            ((InstantMessageModality)_conversation.Modalities[ModalityTypes.InstantMessage]).BeginSendMessage("hi", (ar) => {

                ((InstantMessageModality)_conversation.Modalities[ModalityTypes.InstantMessage]).EndSendMessage(ar);
            }, null);

        }
        #endregion

        #region Conversation event handlers

        /// <summary>
        /// Handles the event raised when a conversation becomes active or is terminated.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_StateChanged(object sender, ConversationStateChangedEventArgs e)
        {
        }

        /// <summary>
        /// Handles the participant added event. Registers for events on the application sharing modality for the 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_ParticipantAdded(object sender, ParticipantCollectionChangedEventArgs e)
        {
            //Is this added participant the local user?
            if (e.Participant.IsSelf)
            {
                //Store the application sharing modality of the local user so that
                //the user can request or release control of a remotely owned and shared resource.
                _LocalParticipantSharingModality = (ApplicationSharingModality)e.Participant.Modalities[ModalityTypes.ApplicationSharing];

                //Enable or disable the Start Resource Sharing button according to the role of the local participant.
                //Roles can be Presenter or Attendee.

                if (e.Participant.Properties[ParticipantProperty.IsPresenter] != null)
                { 
                     this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, (Boolean)e.Participant.Properties[ParticipantProperty.IsPresenter] });
                }
                //Register for the particpant property changed event to be notified when the role of the local user changes.
                e.Participant.PropertyChanged += Participant_PropertyChanged;

                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { SharingParticipationStateString_Label, "not sharing" });

            }

            //Get the application sharing modality of the added participant and store it in a class dictionary field for easy access later.
            ApplicationSharingModality participantSharingModality = (ApplicationSharingModality)e.Participant.Modalities[ModalityTypes.ApplicationSharing];
            _participantSharingModalities.Add(e.Participant.Contact.Uri, participantSharingModality);

            //register for important events on the application sharing modality of the new participant.
            participantSharingModality.ActionAvailabilityChanged += _sharingModality_ActionAvailabilityChanged;
            participantSharingModality.ModalityStateChanged += _sharingModality_ModalityStateChanged;

        }

        /// <summary>
        /// Handles the event raised when a particpant is removed from the conversation.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _conversation_ParticipantRemoved(object sender, ParticipantCollectionChangedEventArgs e)
        {

            //get the application sharing modality of the removed participant out of the class modalty dicitonary
            ApplicationSharingModality removedModality = _participantSharingModalities[e.Participant.Contact.Uri];

            //Un-register for modality events on this participant's application sharing modality.
            removedModality.ActionAvailabilityChanged -= _sharingModality_ActionAvailabilityChanged;

            //Remove the modality from the dictionary.
            _participantSharingModalities.Remove(e.Participant.Contact.Uri);
            this.Invoke(new RemoveAContactDelegate(RemoveAContact), new object[] { e.Participant.Contact.Uri});
        }
        #endregion

        #region Participant event handlers
        /// <summary>
        /// Called when a participant property is changed.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void Participant_PropertyChanged(object sender, ParticipantPropertyChangedEventArgs e)
        {
            if (e.Property == ParticipantProperty.IsPresenter)
            {
                //Enable or disable the Start Sharing Resource button according to the participant role
                this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { StartSharingResource_Button, (Boolean)e.Value });
            }
        }

        #endregion

        #region application sharing modality event handlers

        /// <summary>
        /// Handles the event raised when the local user has started or ended a shareable process.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_LocalSharedResourcesChanged(object sender, LocalSharedResourcesChangedEventArgs e)
        {
            //Update the shareable resources list box with the currently available shareable resources.
            if (e.ResourceList.Count > 0)
            {
                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { SharedResource_Label, e.ResourceList[0].Name });
            }
            else
            {
                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { SharedResource_Label, "None" });
            }
        }

        /// <summary>
        /// Handles the even raised when the state of an application sharing modality changes.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ModalityStateChanged(object sender, ModalityStateChangedEventArgs e)
        {

            //Modality will be connected for each particpant whethere they have accepted the shariing invite or not.
            
            ApplicationSharingModality thisModality = (ApplicationSharingModality)sender;
            if (e.NewState == ModalityState.Connected)
            {
                this.Invoke(new AddAContactDelegate(AddAContact), new object[] { thisModality.Participant.Contact.Uri });
                this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { ContactList_Label, "5) Pick a participant" });
            }
        }

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
            if (((ApplicationSharingModality)sender).Controller != null)
            {
                _ResourceControllingContact = ((ApplicationSharingModality)sender).Controller.Contact;
            }

        }

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

        /// <summary>
        /// Handles the event raised when a participant participation state changes.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ParticipationStateChanged(object sender, ParticipationStateChangedEventArgs e)
        {
            if (((ApplicationSharingModality)sender) == _sharingModality)
            {
                if (e.NewState.ToString() == "None")
                {
                    this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { SharingParticipationStateString_Label, "not sharing" });
                }
                else
                {
                    this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { SharingParticipationStateString_Label, e.NewState.ToString() });

                }
                ApplicationSharingModality participantModality = (ApplicationSharingModality)sender;
                if (participantModality.Controller != null)
                {
                    string userName = participantModality.Controller.Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                    this.Invoke(new ChangeLabelTextDelegate(ChangeLabelText), new object[] { SharedResource_Label, userName });
                }
            }
        }

        /// <summary>
        /// Event handler for sharing modality action availability change
        /// This method enables or disables the modality control action buttons on the UI according to
        /// the availability of a given action.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _sharingModality_ActionAvailabilityChanged(object sender, ModalityActionAvailabilityChangedEventArgs e)
        {
            try
            {
                ApplicationSharingModality thisModality = (ApplicationSharingModality)sender;
                Button buttonToUpdate = null;

                //Enable or disable a UI action button that corresponds to the action whose availability has changed.
                switch (e.Action)
                {
                    case ModalityAction.Accept:
                        buttonToUpdate = Acceptx_Button;
                        break;
                    case ModalityAction.Reject:
                        buttonToUpdate = RejectX_Button;
                        break;
                    case ModalityAction.AcceptSharingControlRequest:
                        buttonToUpdate = Accept_Button;
                        break;
                    case ModalityAction.DeclineSharingControlRequest:
                        buttonToUpdate = Decline_Button;
                        break;
                    case ModalityAction.GrantSharingControl:
                        buttonToUpdate = Grant_Button;
                        break;
                    case ModalityAction.ReleaseSharingControl:
                        buttonToUpdate = Release_Button;
                        break;
                    case ModalityAction.RequestSharingControl:
                        buttonToUpdate = Request_Button;
                        break;
                    case ModalityAction.RevokeSharingControl:
                        buttonToUpdate = Revoke_Button;
                        break;
                    case ModalityAction.Disconnect:
                        buttonToUpdate = Disconnect_Button;
                        break;
                }

                //Not all possible cases of ActionAvailability are represented in the previous switch statement. 
                //For this reason, buttonToUpdate may be null.
                if (buttonToUpdate != null)
                {
                    this.Invoke(new EnableDisableButtonDelegate(EnableDisableButton), new object[] { buttonToUpdate, e.IsAvailable });
                }
            }
            catch (Exception)  { }
        }
        #endregion

        #region API Operation callback methods

        /// <summary>
        /// Completes the desktop sharing operation.
        /// </summary>
        /// <param name="ar"></param>
        private void ShareDesktopCallback(System.IAsyncResult ar)
        {
            try
            {
                ApplicationSharingModality sharingModality = (ApplicationSharingModality)ar.AsyncState;
                sharingModality.EndShareDesktop(ar);
            }
            catch (LyncClientException )  {}
            catch (InvalidCastException) { };
        }

        /// <summary>
        /// Completes the process sharing operation
        /// </summary>
        /// <param name="ar"></param>
        private void ShareResourcesCallback(System.IAsyncResult ar)
        {
            try
            {
                ((ApplicationSharingModality)ar.AsyncState).EndShareResources(ar);
            }
            catch (OperationException) { }
            catch (LyncClientException ) {}
            catch (InvalidCastException) { };

        }

        /// <summary>
        /// Completes the monitor sharing operation
        /// </summary>
        /// <param name="ar"></param>
        private void ShareMonitorCallback(System.IAsyncResult ar)
        {
            try
            {
                ApplicationSharingModality sharingModality = (ApplicationSharingModality)ar.AsyncState;
                sharingModality.EndShareMonitor(ar);
            }
            catch (InvalidCastException ) {}
            catch (LyncClientException )  {}

        }

        #endregion

        #region UI update helper methods and their delegates

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

            switch (selectedResourceType)
            {
                case SharingResourceType.Desktop:
                    _sharingModality.BeginShareDesktop((ar) => 
                        {
                            _sharingModality.EndShareDesktop(ar);
                        }
                        , null);
                    break;
                case SharingResourceType.Monitor:

                    //Share the primary monitor
                    //Iterate on all system displays and find the primary display
                    for (int i = 0; i < System.Windows.Forms.Screen.AllScreens.Length; i++)
                    {
                        //If this screen is the primary display, 
                        if (((Screen)System.Windows.Forms.Screen.AllScreens[i]).Primary)
                        {
                            //Share the primary display using a 1-based index value
                            _sharingModality.BeginShareMonitor(i + 1, (ar) => 
                                {
                                    try
                                    {
                                        _sharingModality.EndShareMonitor(ar);
                                    }
                                    catch (LyncClientException lce) { throw lce; }
                                }
                                , null);
                        }
                    }
                    break;
                case SharingResourceType.Process:

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
                    break;
            }
        }

        private delegate void EnableDisableButtonDelegate(Button buttonToUpdate, Boolean newButtonEnableState);

        /// <summary>
        /// Enables or disables a UI button based on the actionAvailability
        /// </summary>
        /// <param name="buttonToUpdate"></param>
        /// <param name="newButtonEnableState"></param>
        private void EnableDisableButton(Button buttonToUpdate, Boolean newButtonEnableState)
        {
            buttonToUpdate.Enabled = newButtonEnableState;
        }

        private delegate void LoadAllContactsDelegate();

        /// <summary>
        /// Iterates on all groups and adds an Uri string for each contact in a group to a list on the UI
        /// </summary>
        private void LoadAllContacts()
        {
            //Set the selection mode of the UI list to multi-select
            Contact_ListBox.SelectionMode = SelectionMode.MultiSimple;
            Contact_ListBox.Items.Clear();
            foreach (Group group in _LyncClient.ContactManager.Groups)
            {
                foreach (Contact contact in group)
                {
                    if (!Contact_ListBox.Items.Contains(contact.Uri))
                       Contact_ListBox.Items.Add(contact.Uri);
                }
            }
        }

        private delegate void ClearAllContactsDelegate();
        private void ClearAllContacts()
        {
            Contact_ListBox.Items.Clear();
        }

        private delegate void AddAContactDelegate(string ContactUri);
        private void AddAContact(string ContactUri)
        {
            Contact_ListBox.SelectionMode = SelectionMode.One;
            if (!Contact_ListBox.Items.Contains(ContactUri))
            {
                Contact_ListBox.Items.Add(ContactUri);
            }
        }

        private delegate void RemoveAContactDelegate(string ContactUri);
        private void RemoveAContact(string ContactUri)
        {
            Contact_ListBox.Items.Remove(ContactUri);
        }

        private delegate void UpdateSharedResourcesListboxDelegate();

        /// <summary>
        /// Fills a UI list with the names of all local resources that can be shared.
        /// </summary>
        private void UpdateSharedResourcesListbox()
        {
            SharedResources_ListBox.Items.Clear();
            if (_sharingModality == null || _sharingModality.ShareableResources == null)
            {
                return;
            }
            if (_sharingModality.ShareableResources.Count > 0)
            {
                SharingResource sharingResource;
                for (int j = 0; j < _sharingModality.ShareableResources.Count; j++)
                {
                    sharingResource = _sharingModality.ShareableResources[j];
                    SharedResources_ListBox.Items.Add(sharingResource.Name);
                }
            }
        }

        private delegate void ChangeButtonTextDelegate(Button buttonToChange, string newText);
        private void ChangeButtonText(Button buttonToChange, string newText)
        {
            buttonToChange.Text = newText;
        }

        private delegate void SetContactSelectionModeDelegate(SelectionMode newMode);
        /// <summary>
        /// Changes the contact list on the UI from single-select to multi-select mode
        /// </summary>
        /// <param name="newMode"></param>
        private void SetContactSelectionMode(SelectionMode newMode)
        {
            Contact_ListBox.SelectionMode = newMode;
        }

        private delegate void ChangeLabelTextDelegate(Label labelToUpdate, string newText);
        /// <summary>
        /// Replaces the text of any label control on the UI with new text
        /// </summary>
        /// <param name="labelToUpdate"></param>
        /// <param name="newText"></param>
        private void ChangeLabelText(Label labelToUpdate, string newText)
        {
            labelToUpdate.Text = newText;
        }

        #endregion

        #region constructors
        public ShareResources_Form()
        {
            InitializeComponent();
        }
        #endregion

    }
}
```

## Next steps

  - [How to: Get a shareable resource and share it in a conversation](how-to-get-a-shareable-resource-and-share-it-in-a-conversation.md)

## See also

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

