---
title: Maintaining contacts and groups
TOCTitle: Maintaining contacts and groups
ms:assetid: 9233ed77-bebb-4ad4-aa9e-c19eb752d186
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454634(v=office.15)
ms:contentKeyID: 57092876
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Maintaining contacts and groups


**Applies to:** Lync 2013 | Lync Server 2013

 

When a subscription to the self-published contact list is in a Subscribed state, an application can add another contact or group to the existing contact list, remove a contact or group from the contact list, and update a contact or group in the list. These operations can be identified as publications of contacts or groups category instances. In UCMA, they are exposed by the related methods of the ContactGroupServices object.

## Adding a contact to a contact list

Adding a contact to an existing contact list is an asynchronous operation and involves calls to BeginAddContact/EndAddContact on the ContactGroupServices object. The following code example shows how this is implemented in a UCMA application.

```csharp
        public void AddContact(string contactUri, string contactData, string contactExtension, string contactName, int containerId)
        {
            if (_cgServices.CurrentState == CollaborationSubscriptionState.Subscribed) 
            {
                ContactAddOptions options = new ContactAddOptions();
                options.ContactData = contactData;
                options.ContactExtension = contactExtension;
                options.ContactName = contactName;
                options.ContainerId = containerId;
                _cgServices.BeginAddContact(contactUri, options, CallbackOnBeginAddContact, _cgServices);
            }

        }
        void CallbackOnBeginAddContact(IAsyncResult result)
        {
            if (_cgServices != result as ContactGroupServices)
                return;
            try
            {
                _cgServices.EndAddContact(result);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Failed to AddContact: " + ex.Message);
            }
        }

```

## Removing a contact from a contact list

Removing a contact from an existing contact list is an asynchronous operation and involves calls to BeginDeleteContact/EndDeleteContact on the ContactGroupServices object. The following code example shows how this is implemented in a UCMA application.

```csharp
        public void DeleteContact(string contactUri)
        {
            if (_cgServices.CurrentState == CollaborationSubscriptionState.Subscribed)
            {
                _cgServices.BeginDeleteContact(
                    contactUri, CallbackOnBeginDeleteContact, contactUri);
            }

                
        }

        void CallbackOnBeginDeleteContact(IAsyncResult result)
        {
            try
            {
                if (result.IsCompleted)
                {
                    // Stop subscription to the presence of the last removed contact.
                    string sipUri = result.AsyncState as string;
                    this.UnsubscribeToContactsPresence(new string[] {sipUri} );

                    // Complete the operation to delete the contact.
                    _cgServices.EndDeleteContact(result);
                }
            }
            catch (Exception ex)
            {
                MessageBox.Show("Failed to DeleteContact: " + ex.Message);
            }
        }

```

## Updating a contact in a contact list

Updating a contact in an existing contact list is an asynchronous operation and involves calls to BeginUpdateContact/EndUpdateContact on the ContactGroupServices object. The following code example shows how this is implemented in a UCMA application.

```csharp
        public void UpdateContact(Contact contact)
        {
            if (_cgServices.CurrentState == CollaborationSubscriptionState.Subscribed)
            {
                _cgServices.BeginUpdateContact(
                    contact, CallbackOnBeginUpdateContact, _cgServices);
            }
           
        }
        void CallbackOnBeginUpdateContact(IAsyncResult result)
        {
            if (_cgServices != result as ContactGroupServices)
                return;
            try
            {
                _cgServices.EndUpdateContact(result);
            }
            catch (Exception ex)
            {
                MessageBox.Show("Failed to UpdateContact: " + ex.Message);
            }
        }

```

## Adding, deleting, and updating a group

Adding, deleting, and updating a group in an existing contact list are asynchronous operations and involve calls to BeginAddGroup/EndAddgroup, BeginDeleteGroup/EndDeleteGroup and BeginUpdateGroup/EndUpdateGroup on the ContactGroupServices object. The following code example shows how these are implemented in a UCMA application.

```csharp
        public void AddGroup(string groupName, string groupData)
        {
            if (_cgServices.CurrentState == CollaborationSubscriptionState.Subscribed)
            {
                _cgServices.EndAddGroup(
                    _cgServices.BeginAddGroup(groupName, groupData, null, null));
            }
        }

        public void DeleteGroup(int groupId, string groupData)
        {
            if (_cgServices.CurrentState == CollaborationSubscriptionState.Subscribed)
            {
                _cgServices.EndDeleteGroup(
                    _cgServices.BeginDeleteGroup(groupId, null, null));
            }
        }

        public void UpdateGroup(Group group)
        {
            if (_cgServices.CurrentState == CollaborationSubscriptionState.Subscribed)
            {
                _cgServices.EndUpdateGroup(
                    _cgServices.BeginUpdateGroup(group, null, null));
            }
        }

```


> [!NOTE]
> <P>To highlight the features that are related to managing contact groups, the previous code example simplifies the asynchronous patterns into synchronous calls. You can follow the previous contact-managing examples to revert these calls to their asynchronous counterparts.</P>



## See also

#### Concepts

[Managing self-published contact lists](managing-self-published-contact-lists.md)

