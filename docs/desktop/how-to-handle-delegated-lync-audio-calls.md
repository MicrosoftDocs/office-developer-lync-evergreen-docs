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

A [Microsoft.Lync.Model.DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)) representing a call delegator is added to the [LyncClient.DelegatorClients](https://msdn.microsoft.com/en-us/library/jj277686\(v=office.15\)) collection whenever a user delegates the local user to take incoming audio calls. To catch that event, you register for [LyncClient.DelegatorClientAdded](https://msdn.microsoft.com/en-us/library/jj267354\(v=office.15\)). When the call delegator removes the local user from the call delegate list, the [LyncClient.DelegatorClientRemoved](https://msdn.microsoft.com/en-us/library/jj278340\(v=office.15\)) event is raised.

### To register for delegator events in a form load event handler

1.  Get the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) and ensure the [State](https://msdn.microsoft.com/en-us/library/jj267978\(v=office.15\)) is [ConversationState](https://msdn.microsoft.com/en-us/library/jj277587\(v=office.15\)).**SignedIn**.
    
    For information about signing in to Microsoft Lync 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Register for [LyncClient.DelegatorClientAdded](https://msdn.microsoft.com/en-us/library/jj267354\(v=office.15\)) and [LyncClient.DelegatorClientRemoved](https://msdn.microsoft.com/en-us/library/jj278340\(v=office.15\)) on [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)).

3.  Iterate on the collection of [Microsoft.Lync.Model.DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)) instances in the [DelegatorClients](https://msdn.microsoft.com/en-us/library/jj277686\(v=office.15\)) property:
    
    1.  Register for the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event on the [ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)) property of the [Microsoft.Lync.Model.DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)).
    
    2.  Register for the [ConversationManager.ConversationRemoved](https://msdn.microsoft.com/en-us/library/jj293976\(v=office.15\)) event on the [ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)) property of the [Microsoft.Lync.Model.DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)).

## Handle delegator events

You register for delegate conversation events for each [DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)) instance in the [DelegatorClients](https://msdn.microsoft.com/en-us/library/jj277686\(v=office.15\)) collection after you have obtained a [LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance in your form **Load** event. In addition, you register and unregister for conversation events in the delegator event handlers.

### To handle the delegator added and the delegator removed

1.  Create a method to handle the [LyncClient.DelegatorClientAdded](https://msdn.microsoft.com/en-us/library/jj267354\(v=office.15\)) event.
    
    The method signature is System.EventHandler\<[DelegatorClientCollectionEventArgs](https://msdn.microsoft.com/en-us/library/jj275274\(v=office.15\))\>.

2.  Create a method to handle the [LyncClient.DelegatorClientRemoved](https://msdn.microsoft.com/en-us/library/jj278340\(v=office.15\)) event.
    
    The method signature is System.EventHandler\<[DelegatorClientCollectionEventArgs](https://msdn.microsoft.com/en-us/library/jj275274\(v=office.15\))\>.

3.  In the [DelegatorClientAdded](https://msdn.microsoft.com/en-us/library/jj267354\(v=office.15\)) event, register for the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) and [ConversationRemoved](https://msdn.microsoft.com/en-us/library/jj293976\(v=office.15\)) events on the [Client.ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)) property of the [DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)).

4.  In the [DelegatorClientRemoved](https://msdn.microsoft.com/en-us/library/jj278340\(v=office.15\)) event, unregister for the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) and [ConversationRemoved](https://msdn.microsoft.com/en-us/library/jj293976\(v=office.15\)) events on the [Client.ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)) property of the [DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)).

## Get a delegator user name when a delegated call is added

To give the local user the delegator name on an incoming delegated call, add code from the following procedure to your [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event handler. For more information about handing incoming calls, see [How to: Join a Lync conversation](how-to-join-a-lync-conversation.md).

### To get call a delegator’s name

  - For each [DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)) instance in the [LyncClient.DelegatorClients](https://msdn.microsoft.com/en-us/library/jj277686\(v=office.15\)) property, get a [ConversationManager](https://msdn.microsoft.com/en-us/library/jj266018\(v=office.15\)) by reading the [ConversationManager](https://msdn.microsoft.com/en-us/library/jj276841\(v=office.15\)) property on [Microsoft.Lync.Model.DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)).
    
    1.  Compare the delegator client’s [ConversationManager](https://msdn.microsoft.com/en-us/library/jj266018\(v=office.15\)) to the source of the [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event:(ConversationManager)source.
    
    2.  If the two **ConversationManager** instances are identical, the added conversation is a delegated conversation.
        
        1.  Get the [Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) of the call delegator by calling into **GetContactByUri** and then passing the [Uri](https://msdn.microsoft.com/en-us/library/jj293482\(v=office.15\)) of the [Microsoft.Lync.Model.DelegatorClient](https://msdn.microsoft.com/en-us/library/jj266028\(v=office.15\)).
        
        2.  Call [GetContactInformation](https://msdn.microsoft.com/en-us/library/jj294012\(v=office.15\)), passing [ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\)).**DisplayName** to get the name of the call delegator.
        
        3.  Break out of the **foreach** loop.

## Code examples: Delegated Lync audio calls

### Register for delegator events in a forms load event handler

The following example handles the **Load** event in Microsoft Windows Forms. For information about signing in to Lync 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

```csharp
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

```csharp
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

The following example code should be added to your [ConversationAdded](https://msdn.microsoft.com/en-us/library/jj266470\(v=office.15\)) event handler.

```csharp
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

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

