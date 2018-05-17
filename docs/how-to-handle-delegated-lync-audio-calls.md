---
title: 'How to: Handle delegated Lync audio calls'
TOCTitle: 'How to: Handle delegated Lync audio calls'
ms:assetid: ab25f4fb-23fe-4ca2-9c27-9fbcf3203912
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933162(v=office.15)
ms:contentKeyID: 50877301
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Handle delegated Lync audio calls

Learn how to programmatically handle a delegated Microsoft Lync 2013 audio call by using Microsoft Lync 2013 SDK.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Delegator event registration<br />
Handle delegator events<br />
Get a delegator user name when a delegated call is added<br />
Code examples: Delegated Lync audio calls<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Prerequisites

The prerequisites for handling delegated calls are as follows:

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
<td><p><a href="call-delegation-in-lync.md">Call delegation in Lync</a></p></td>
<td><p>Describes call delegation as implemented by Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="conversation-manager.md">Conversation manager</a></p></td>
<td><p>Describes the role of the conversation manager in starting and accepting calls.</p></td>
</tr>
</tbody>
</table>


## Delegator event registration

A [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md) representing a call delegator is added to the [LyncClient.DelegatorClients](lyncclient-delegatorclients-property-microsoft-lync-model_2.md) collection whenever a user delegates the local user to take incoming audio calls. To catch that event, you register for [LyncClient.DelegatorClientAdded](lyncclient-delegatorclientadded-event-microsoft-lync-model_2.md). When the call delegator removes the local user from the call delegate list, the [LyncClient.DelegatorClientRemoved](lyncclient-delegatorclientremoved-event-microsoft-lync-model_2.md) event is raised.

### To register for delegator events in a form load event handler

1.  Get the [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md) and ensure the [State](conversation-state-property-microsoft-lync-model-conversation_2.md) is [ConversationState](conversationstate-enumeration-microsoft-lync-model-conversation_2.md).**SignedIn**.
    
    For information about signing in to Microsoft Lync 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Register for [LyncClient.DelegatorClientAdded](lyncclient-delegatorclientadded-event-microsoft-lync-model_2.md) and [LyncClient.DelegatorClientRemoved](lyncclient-delegatorclientremoved-event-microsoft-lync-model_2.md) on [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md).

3.  Iterate on the collection of [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md) instances in the [DelegatorClients](lyncclient-delegatorclients-property-microsoft-lync-model_2.md) property:
    
    1.  Register for the [ConversationManager.ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event on the [ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md) property of the [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md).
    
    2.  Register for the [ConversationManager.ConversationRemoved](conversationmanager-conversationremoved-event-microsoft-lync-model-conversation_2.md) event on the [ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md) property of the [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md).

## Handle delegator events

You register for delegate conversation events for each [DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md) instance in the [DelegatorClients](lyncclient-delegatorclients-property-microsoft-lync-model_2.md) collection after you have obtained a [LyncClient](lyncclient-class-microsoft-lync-model_2.md) instance in your form **Load** event. In addition, you register and unregister for conversation events in the delegator event handlers.

### To handle the delegator added and the delegator removed

1.  Create a method to handle the [LyncClient.DelegatorClientAdded](lyncclient-delegatorclientadded-event-microsoft-lync-model_2.md) event.
    
    The method signature is System.EventHandler\<[DelegatorClientCollectionEventArgs](delegatorclientcollectioneventargs-class-microsoft-lync-model_2.md)\>.

2.  Create a method to handle the [LyncClient.DelegatorClientRemoved](lyncclient-delegatorclientremoved-event-microsoft-lync-model_2.md) event.
    
    The method signature is System.EventHandler\<[DelegatorClientCollectionEventArgs](delegatorclientcollectioneventargs-class-microsoft-lync-model_2.md)\>.

3.  In the [DelegatorClientAdded](lyncclient-delegatorclientadded-event-microsoft-lync-model_2.md) event, register for the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) and [ConversationRemoved](conversationmanager-conversationremoved-event-microsoft-lync-model-conversation_2.md) events on the [Client.ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md) property of the [DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md).

4.  In the [DelegatorClientRemoved](lyncclient-delegatorclientremoved-event-microsoft-lync-model_2.md) event, unregister for the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) and [ConversationRemoved](conversationmanager-conversationremoved-event-microsoft-lync-model-conversation_2.md) events on the [Client.ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md) property of the [DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md).

## Get a delegator user name when a delegated call is added

To give the local user the delegator name on an incoming delegated call, add code from the following procedure to your [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event handler. For more information about handing incoming calls, see [How to: Join a Lync conversation](how-to-join-a-lync-conversation.md).

### To get call a delegator’s name

  - For each [DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md) instance in the [LyncClient.DelegatorClients](lyncclient-delegatorclients-property-microsoft-lync-model_2.md) property, get a [ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) by reading the [ConversationManager](client-conversationmanager-property-microsoft-lync-model_2.md) property on [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md).
    
    1.  Compare the delegator client’s [ConversationManager](conversationmanager-class-microsoft-lync-model-conversation_2.md) to the source of the [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event:(ConversationManager)source.
    
    2.  If the two **ConversationManager** instances are identical, the added conversation is a delegated conversation.
        
        1.  Get the [Contact](contact-class-microsoft-lync-model_2.md) of the call delegator by calling into **GetContactByUri** and then passing the [Uri](client-uri-property-microsoft-lync-model_2.md) of the [Microsoft.Lync.Model.DelegatorClient](delegatorclient-class-microsoft-lync-model_2.md).
        
        2.  Call [GetContactInformation](contact-getcontactinformation-method-microsoft-lync-model_2.md), passing [ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md).**DisplayName** to get the name of the call delegator.
        
        3.  Break out of the **foreach** loop.

## Code examples: Delegated Lync audio calls

### Register for delegator events in a forms load event handler

The following example handles the **Load** event in Microsoft Windows Forms. For information about signing in to Lync 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

``` csharp
        ...
        private LyncClient _lyncClient;
        ...
        /// <summary>
        /// Main form loader
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void MainForm_Load(object sender, EventArgs e)
        {
            try
            {
                _lyncClient = LyncClient.GetClient();

                //Client sign-in code is omitted for clarity
                ...
                _LyncClient.DelegatorClientAdded += _LyncClient_DelegatorClientAdded;
                _LyncClient.DelegatorClientRemoved += _LyncClient_DelegatorClientRemoved;

                foreach (DelegatorClient _DelegatorClient in _ClientModel._LyncClient.DelegatorClients)
                {
                    _DelegatorClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
                    _DelegatorClient.ConversationManager.ConversationRemoved += ConversationManager_ConversationRemoved;
                }
            }
            catch (Exception ex)
            {
                MessageBox.Show("Critial Exception on initiate client " + ex.Message);
            }
        }
```

### Handle the delegator added and the delegator removed

The following example registers or unregisters for conversation events on a delegator client.

``` csharp
        /// <summary>
        /// Handles event that is raised when a user removes local user from a call delegate list
        /// </summary>
        /// <param name="sender">LyncClient. The local client</param>
        /// <param name="e"></param>
        void _LyncClient_DelegatorClientRemoved(object sender, DelegatorClientCollectionEventArgs e)
        {
            e.DelegatorClient.ConversationManager.ConversationAdded -= ConversationManager_ConversationAdded;
        }

        /// <summary>
        /// Handles event that is raised when a user adds local user to a call delegate list
        /// </summary>
        /// <param name="sender">LyncClient. The local client</param>
        /// <param name="e"></param>
        void _LyncClient_DelegatorClientAdded(object sender, DelegatorClientCollectionEventArgs e)
        {
            e.DelegatorClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
        }
```

### Get call delegator’s name

The following example code should be added to your [ConversationAdded](conversationmanager-conversationadded-event-microsoft-lync-model-conversation_2.md) event handler.

``` csharp
    //The call is a delegated call.
    if ((ConversationManager)sender != _LyncClient.ConversationManager)
    {
        //Look for the delegator ConversationManager that raised the event.
        foreach (DelegatorClient _DelegateClient in _LyncClient.DelegatorClients)
        {
            //Did this delegator conversation manager raise the ConversationAdded event?
            if (_DelegateClient.ConversationManager == (ConversationManager)sender)
            {
                //Get the Contact representing the call delegator.
                Contact delegatorContact = _LyncClient.ContactManager.GetContactByUri(_DelegateClient.Uri);
                //Add the name of the delegator to a StringBuilder instance.
                sb.Append("Incoming call delegated by " + delegatorContact.GetContactInformation(ContactInformationType.DisplayName).ToString());

                //Add the name of the caller to the string builder instance
                string delegateCallName = e.Conversation.Participants[1].Contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
                sb.Append("Caller: " + delegateCallName);

                //Break out of foreach loop, correct delegator conversation manager found.
                break;
            }
        }
    }
```

## Additional resources

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

