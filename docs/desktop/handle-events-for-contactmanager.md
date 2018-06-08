---
title: Handle events for ContactManager
TOCTitle: Handle events for ContactManager
ms:assetid: a53758cd-b11f-4b9e-bfd8-c0dadde38a7a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945571(v=office.15)
ms:contentKeyID: 51541386
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Handle events for ContactManager

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about handling the events raised by the [Microsoft.Lync.Model.ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)) object in Microsoft Lync 2013 SDK.

**Last modified:** February 12, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Event handling overview<br />
Register for contacts and groups manager events<br />
Handle contacts and groups manager events<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Event handling overview

Event handlers triggered by events raised in the contacts and groups manager are a good place to stage the update of a contact list displayed in your user interface. In these event handlers, you can also register for or remove registration for the group’s contact events. For example, when a group is added, it triggers a [GroupAdded](https://msdn.microsoft.com/en-us/library/jj278290\(v=office.15\)) event. The event handler for this event should register for the [ContactAdded](https://msdn.microsoft.com/en-us/library/jj266994\(v=office.15\)) event and [ContactRemoved](https://msdn.microsoft.com/en-us/library/jj277068\(v=office.15\)) event for this new group.

There are three events available for [ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)):

  - [GroupAdded](https://msdn.microsoft.com/en-us/library/jj278290\(v=office.15\))

  - [GroupRemoved](https://msdn.microsoft.com/en-us/library/jj276769\(v=office.15\))

  - [SearchProviderStateChanged](https://msdn.microsoft.com/en-us/library/jj274591\(v=office.15\))

## Register for contacts and groups manager events

To register for events raised by the contacts and groups manager, include one line of code for each event. The following example registers the application for the **GroupAdded** event of the contacts and groups manager, designating the **manager\_GroupAdded** method as the method to be triggered by the event.

```csharp
_LyncClient.ContactManager.GroupAdded += new EventHandler<Object, GroupCollectionChangedEventArgs>(manager_GroupAdded);
```

## Handle contacts and groups manager events

The following examples handle the events raised when a group is added or removed from the contacts and groups manager.

### GroupAdded event

The following example handles the **GroupAdded** event by registering for events on the group.

```csharp
   /// Handler for event raised when a group is added.
        /// <param name="source">Object. The ContactManager instance that raised the event.</param>
        /// <param name="data">GroupCollectionChangedEventArgs. The event state object.</param>
        void manager_GroupAdded(Object source, GroupCollectionChangedEventArgs data)
        {
            if (data.Group.Name.Length > 0)
            {
                data.Group.ContactAdded += new EventHandler<Object, GroupMemberChangedEventArgs>(group_ContactAdded);
                data.Group.ContactRemoved += new EventHandler<Object, GroupMemberChangedEventArgs>(group_ContactRemoved);
                data.Group.NameChanged += new EventHandler<Group, GroupNameChangedEventArgs>(group_NameChanged);

                // Update UI to add group and contacts in the added group.
            }
        }
```

### GroupRemoved event

The following example handles the **GroupRemoved** event by removing the registration for group events on the group and removing the group from the local group Dictionary\<string, Group\>.

```csharp
   /// Handler for event raised when a group is deleted.
        /// <param name="source">ContactsAndGroupsManager event source</param>
        /// <param name="data">GroupCollectionEventData event data</param>
        void manager_GroupRemoved(ContactsAndGroupsManager source, GroupCollectionEventArgs data)
        {
            if (data.Group != null)
            {
                // Remove registration for group events on removed group.
                data.Group.ContactAdded -= group_ContactAdded;
                data.Group.ContactRemoved -= group_ContactRemoved;
                data.Group.NameChanged -= group_NameChanged;

                // Update UI to remove group and contacts in group.
            }
        }
```

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
<td><p>A contact can be a member of multiple groups. If one of a contact's parent groups is removed, the contact might still appear in your contact list because of its membership in another group.</p></td>
</tr>
</tbody>
</table>

### SearchProviderStateChanged event

The following example handles the search provider state changed event by checking the new status. If the search provider is synchronized, it notifies the user. In practice, your application should update a UI element to let a user choose the updated search provider before starting a new contact search.

```csharp
        /// <summary>
        /// Handles the event raised on the ContactManager when a search provider status has changed.
        /// </summary>
        /// <param name="sender">object. the ContactManager that raised the event.</param>
        /// <param name="e">SearchProviderStateChangedEventArgs. The event state.</param>
        void _ContactManager_SearchProviderStateChanged(object sender, SearchProviderStateChangedEventArgs e)
        {
            if (e.NewStatus == SearchProviderStatusType.SyncSucceeded)
            {
                System.Windows.Forms.MessageBox.Show(e.Provider.ToString()
                    + " is now " + e.NewStatus.ToString()
                    + System.Environment.NewLine
                    + "You can conduct contact searches using this provider");
            }
            else if (e.NewStatus == SearchProviderStatusType.SyncSucceededForInternalOnly)
            {
                System.Windows.Forms.MessageBox.Show(e.Provider.ToString()
                    + " is now " + e.NewStatus.ToString()
                    + System.Environment.NewLine
                    + "You can conduct organization contact searches using this provider");
            }
            else if (e.NewStatus == SearchProviderStatusType.SyncSucceededForExternalOnly)
            {
                System.Windows.Forms.MessageBox.Show(e.Provider.ToString()
                    + " is now " + e.NewStatus.ToString()
                    + System.Environment.NewLine
                    + "You can conduct public contact searches using this provider");
            }

        }
```

## See also

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

  - [How to: Display a contact list](how-to-display-a-contact-list.md)

  - [How to: Add, rename, or remove a custom group](how-to-add-rename-or-remove-a-custom-group.md)

