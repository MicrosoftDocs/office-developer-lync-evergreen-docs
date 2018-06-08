---
title: 'How to: Add, rename, or remove a custom group'
TOCTitle: 'How to: Add, rename, or remove a custom group'
ms:assetid: 2ecbf5aa-3dfb-4726-a9c0-38363bf8ca43
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937292(v=office.15)
ms:contentKeyID: 50877116
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
- csharp
---

# How to: Add, rename, or remove a custom group

Learn how to add or remove a custom group from a user’s contact list in Microsoft Lync 2013 by using Microsoft Lync 2013 SDK.

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
Custom group overview<br />
Add a custom group<br />
Add a distribution group<br />
Remove a custom group<br />
Rename a custom group<br />
Code examples: Add, remove, and rename custom groups<br />
Next steps<br />
Additional resources</p></td>
<td><div class="caption">
Watch the video: Add, rename, and delete custom groups in Lync
</div>
<br />
&gt; [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/a5835343-787b-4041-9afc-bea073a748da]</td>
</tr>
</tbody>
</table>

## Custom group overview

When a local user performs any of the group operations described in this topic using Lync 2013, the result of the operation must be visible to the local user immediately on any signed-in endpoint. To make this possible, the API sends the group operation request to Microsoft Lync Server 2013 and result is sent to all of the user’s signed-in endpoints. For this reason, group operations are asynchronous even though only the local user sees the result of the operation. For information about asynchronous coding patterns with the Microsoft Lync 2013 API, see [Asynchronous programming in Lync SDK](asynchronous-programming-in-lync-sdk.md).

## Prerequisites

The prerequisites for adding or removing a custom group are as follows:

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
<td><p><a href="lync-contact-groups.md">Lync contact groups</a></p></td>
<td><p>Describes the features and limitations of custom groups in Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p><a href="distribution-groups.md">Distribution groups</a></p></td>
<td><p>Learn about the distribution a Microsoft Lync 2013 group and the classes and events in Microsoft Lync 2013 SDK that let you programmatically iterate on the contacts and any nested distribution groups.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-contacts.md">Lync contacts</a></p></td>
<td><p>Learn about the Microsoft Lync 2013 classes and enumerations that encapsulate all of the attributes of a Lync 2013 contact.</p></td>
</tr>
</tbody>
</table>

Contacts and groups are available when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding a contact list to your UI.

## Add a custom group

To add a new custom group, call the [BeginAddGroup](https://msdn.microsoft.com/en-us/library/jj266433\(v=office.15\)) method on the contacts and groups manager, supplying the name of the new group. You must call [EndAddGroup](https://msdn.microsoft.com/en-us/library/jj277049\(v=office.15\)) to complete the operation. You receive the [GroupAdded](https://msdn.microsoft.com/en-us/library/jj278290\(v=office.15\)) event when the new custom group is added. Read the [Group](https://msdn.microsoft.com/en-us/library/jj276719\(v=office.15\)) property to get an instance of the new custom group that is added.

### To add a custom group

1.  In your form class, create an event handler for the [GroupAdded](https://msdn.microsoft.com/en-us/library/jj278290\(v=office.15\)) event.
    
    For more information about the **GroupAdded** event, see [Handle events for ContactManager](handle-events-for-contactmanager.md).

2.  Add a **System.AsyncCallback** method to be invoked when the [BeginAddGroup](https://msdn.microsoft.com/en-us/library/jj266433\(v=office.15\)) operation completes.

3.  Get a [LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance, and then verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

4.  Read the [ContactManager](https://msdn.microsoft.com/en-us/library/jj275688\(v=office.15\)) property on the [LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) instance to get the contact manager.

5.  Register for the [GroupAdded](https://msdn.microsoft.com/en-us/library/jj278290\(v=office.15\)) event on [ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)).

6.  Call [BeginAddGroup](https://msdn.microsoft.com/en-us/library/jj266433\(v=office.15\)) on [ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)), passing a string containing the requested group name. If you want to block execution on your UI thread until the operation completes, call [EndAddGroup](https://msdn.microsoft.com/en-us/library/jj277049\(v=office.15\)) after the first call. To avoid blocking your UI thread, pass a **System.AsyncCallback** method into **BeginAddGroup**, and then call [EndAddGroup](https://msdn.microsoft.com/en-us/library/jj277049\(v=office.15\)) within the callback when it is invoked from the Lync thread.

The following figure illustrates the classes, methods, and events used in the process of adding a custom group and adding a contact to the group.

  
![Shows the logic flow of the add contact group proc](images/JJ937292.Lync_AddGroup(Office.15).jpg "Shows the logic flow of the add contact group proc")

## Add a distribution group

A distribution group is created outside of the scope of this API. It is obtained and added to a user’s contact list using the Microsoft Lync 2013 API. For information about obtaining an existing distribution group, see [How to: Search for a contact or distribution group in Lync SDK](https://msdn.microsoft.com/en-us/library/jj933159\(v=office.15\)).

When you have obtained a distribution group in a set of search results, add the distribution group to the contact list by calling into [BeginAddGroup](https://msdn.microsoft.com/en-us/library/jj266433\(v=office.15\)), passing the distribution group as the first argument.

## Remove a custom group

To remove a custom group, call the [BeginRemoveGroup](https://msdn.microsoft.com/en-us/library/jj278089\(v=office.15\)) method on the contacts and groups manager, supplying the group to be removed. If the group is removed, you receive the [GroupRemoved](https://msdn.microsoft.com/en-us/library/jj276769\(v=office.15\)) event on the [ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)) instance.

### To remove a custom group

1.  In your form class, create an event handler for the [GroupRemoved](https://msdn.microsoft.com/en-us/library/jj276769\(v=office.15\)) event.
    
    For more information about the **GroupRemoved** event, see [Handle events for ContactManager](handle-events-for-contactmanager.md).

2.  Verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

3.  Read the [Client.ContactManager](https://msdn.microsoft.com/en-us/library/jj275688\(v=office.15\)) property to get the [Microsoft.Lync.Model.ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)) instance you use to remove a custom group.

4.  Register for the [GroupRemoved](https://msdn.microsoft.com/en-us/library/jj276769\(v=office.15\)) event on **ContactManager**.

5.  Remove any registrations for events on the group to be removed.

6.  Call [ContactManager.BeginRemoveGroup](https://msdn.microsoft.com/en-us/library/jj278089\(v=office.15\)) on the contact manager, passing the [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/en-us/library/jj266012\(v=office.15\)) to be removed.
    
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
    <td><p>If the group to be removed contains contacts, these contained contacts are not removed from any other containing custom groups.</p>
    <p>To remove a contact from all groups, call <a href="https://msdn.microsoft.com/en-us/library/jj276345(v=office.15)">ContactManager.BeginRemoveContactFromAllGroups</a>.</p></td>
    </tr>
    </tbody>
    </table>

7.  Call [ContactManager.EndRemoveGroup](https://msdn.microsoft.com/en-us/library/jj275547\(v=office.15\)) to complete the operation.

8.  Catch the [ContactManager.GroupRemoved](https://msdn.microsoft.com/en-us/library/jj276769\(v=office.15\)) event when the state of the contact manager group collection ([ContactManager.Groups](https://msdn.microsoft.com/en-us/library/jj277988\(v=office.15\))) has changed.

## Rename a custom group

The group rename operation is restricted to groups of type [Microsoft.Lync.Model.Group.GroupType](https://msdn.microsoft.com/en-us/library/jj276550\(v=office.15\)).**CustomGroup**.

### To rename a custom group

1.  Verify that the client is signed in to the server.
    
    For information about signing in to Microsoft Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Register for the [NameChanged](https://msdn.microsoft.com/en-us/library/jj294077\(v=office.15\)) event on all [Group](https://msdn.microsoft.com/en-us/library/jj266012\(v=office.15\)) instances.
    
    You should perform this step when you obtain the collection of a local user’s contact list groups in the form load event.

3.  Verify that the group to be renamed is of type [GroupType](https://msdn.microsoft.com/en-us/library/jj276550\(v=office.15\)). **CustomGroup**.
    
    Only a custom group can be renamed.

4.  Cast the group to be renamed to [Microsoft.Lync.Model.Group.CustomGroup](https://msdn.microsoft.com/en-us/library/jj277245\(v=office.15\)).

5.  Call [BeginRename](https://msdn.microsoft.com/en-us/library/jj294118\(v=office.15\)) on the custom group, passing the new name of the group as a string.

6.  Call [EndRename](https://msdn.microsoft.com/en-us/library/jj275929\(v=office.15\)) to complete the operation.

7.  Catch the [Group.NameChanged](https://msdn.microsoft.com/en-us/library/jj294077\(v=office.15\)) event raised when the state of the custom group has changed as a result of the operation.

## Code examples: Add, remove, and rename custom groups

The following example declares a WPF window that contains a list box that shows all contact group names and a set of buttons that let a user add, remove, and rename custom groups.

```xaml
<Window x:Class="GroupManager.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="My Group Manager" Height="315" Width="439" Loaded="Window_Loaded_1">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="30*"/>
            <RowDefinition Height="5*"/>
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="80*"/>
            <ColumnDefinition Width="30*"/>
        </Grid.ColumnDefinitions>
        <StackPanel Grid.Row="0" Grid.Column="0" >
            <ListBox Name="GroupList_ListBox" Width="200" Height="195" Margin="10,10,10,10"/>
        </StackPanel>
        <StackPanel Grid.Row="0" Grid.Column="1">
            <TextBox Height="23" Name="GroupName_textbox" TextWrapping="Wrap" Text="" Margin="10,10,10,10"/>
            <Button Content="Add Group" Name="AddGroup_Button" Click="AddGroup_Button_Click_1" Margin="10,10,10,10"/>
            <Button Content="Remove Group" Name="RemoveGroup_Button" Click="RemoveGroup_Button_Click_1" Margin="10,10,10,10"/>
            <Button Content="Rename Group" Name="RenameGroup_Button" Click="RenameGroup_Button_Click_1" Margin="10,10,10,10"/>
        </StackPanel>
    </Grid>
</Window>
```

The following figure shows the example application UI with the three default groups for the signed-in user. No custom groups have been created for this user.

  
![A window that lets user add, remove, rename groups](images/JJ937292.Lync_MyGroupManager(Office.15).jpg "A window that lets user add, remove, rename groups")

The following example handles group collection events on the [ContactManager](https://msdn.microsoft.com/en-us/library/jj266459\(v=office.15\)) object, fills the group list in the UI, and handles click events for buttons in the UI.

```csharp
using System.Windows;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;
using System.Diagnostics;
using System;
using System.Collections.Generic;

namespace GroupManager
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        LyncClient _LyncClient;
        private Dictionary<string, GroupWrapper> _Groups = new Dictionary<string, GroupWrapper>();

        public MainWindow()
        {
            InitializeComponent();
        }

        /// <summary>
        /// Adds a new custom group to the signed in user's contact list
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AddGroup_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (GroupName_textbox.Text.Length > 0)
            {
                _LyncClient.ContactManager.BeginAddGroup(
                    GroupName_textbox.Text, 
                    (ar) => 
                    {
                        try
                        {
                            _LyncClient.ContactManager.EndAddGroup(ar);
                        }
                        catch (LyncClientException lce) 
                        {
                            Debug.WriteLine(
                                "Lync client exception on add group: " + 
                                lce.Message); 
                        }
                    },
                    null);
                GroupName_textbox.Text = string.Empty;
            }

        }

        private void RemoveGroup_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (GroupList_ListBox.SelectedItem == null)
            {
                return;
            }
            try
            {
                GroupWrapper groupToRemove;
                if (_Groups.TryGetValue(GroupList_ListBox.SelectedItem.ToString(), out groupToRemove))
                {
                    _LyncClient.ContactManager.BeginRemoveGroup(
                        groupToRemove.LyncGroup,
                        (ar) =>
                        {
                            try
                            {
                                _LyncClient.ContactManager.EndRemoveGroup(ar);
                            }
                            catch (LyncClientException lce) 
                            {
                                Debug.WriteLine(
                                    "Lync client exception on remove group: " + lce.Message); 
                            }
                        },
                        null);

                }
                else
                {
                    Debug.WriteLine(
                        GroupList_ListBox.SelectedItem.ToString() + 
                        " was not found in the dictionary");
                }

            }
            catch (InvalidOperationException)
            {
                Debug.WriteLine(
                    "Invalid operation in RemoveGroup_Button_Click1"); 
            }

        }

        private void RenameGroup_Button_Click_1(object sender, RoutedEventArgs e)
        {
            if (GroupList_ListBox.SelectedItem == null || GroupName_textbox.Text.Length < 1)
            {
                return;
            }

            GroupWrapper groupToRename;
            if (_Groups.TryGetValue(GroupList_ListBox.SelectedItem.ToString(), out groupToRename))
            {
                //Rename a Group after casting to CustomGroup
                ((CustomGroup)groupToRename.LyncGroup).BeginRename(
                    GroupName_textbox.Text,
                    (ar) =>
                    {
                        try
                        {
                            ((CustomGroup)groupToRename.LyncGroup).EndRename(ar);
                        }
                        catch (LyncClientException lce) 
                        {
                            Debug.WriteLine(
                                "Lync client exception on rename group: " + 
                                lce.Message); 
                        };
                    },
                    null);

                GroupName_textbox.Text = string.Empty;
            }
            else
            {
                Debug.WriteLine(
                    GroupList_ListBox.SelectedItem.ToString() + 
                    " was not found in the dictionary");
            }

        }

        private void Window_Loaded_1(object sender, RoutedEventArgs e)
        {
            //GroupList_ListBox
            try 
            {
                _LyncClient = LyncClient.GetClient();
                _LyncClient.ContactManager.GroupAdded += ContactManager_GroupAdded;
                _LyncClient.ContactManager.GroupRemoved += ContactManager_GroupRemoved;
                LoadList();
            }
            catch (LyncClientException lce) 
            {
                Debug.WriteLine(
                    "Lync client exception on GetClient() in Window Loaded " + 
                    lce.Message);
            }

        }

        /// <summary>
        /// Loads a list box with existing contact list groups
        /// by iterating on the Groups collection of the ContactManager 
        /// property on LyncClient.
        /// </summary>
        private void LoadList()
        {
            GroupList_ListBox.Items.Clear();
            foreach (Group group in _LyncClient.ContactManager.Groups)
            {
                //The Group is wrapped in a custom class to allow
                //override of ToString() method
                GroupWrapper gWrap = new GroupWrapper(group);

                //GroupWrapper class registers for the Group.NameChanged
                //event and bubbles event to UI layer so the 
                //listbox gets reloaded with new name
                gWrap.NameChanged += gWrap_NameChanged;

                GroupList_ListBox.Items.Add(gWrap);
                if (_Groups.ContainsKey(group.Name))
                {
                    continue;
                }

                //Dictionary of GroupWrapper objects with group name as key
                _Groups.Add(group.Name, gWrap);
            }
        }
        void ContactManager_GroupRemoved(object sender, GroupCollectionChangedEventArgs e)
        {
            this.Dispatcher.Invoke(new DelegatedMethod(RemoveGroupFromList), new object[] {e.Group});
        }

        void ContactManager_GroupAdded(object sender, GroupCollectionChangedEventArgs e)
        {
            this.Dispatcher.Invoke(new DelegatedMethod(AddGroupToList), new object[] { e.Group });
        }

        private delegate void DelegateNoParams();

        private delegate void DelegatedMethod(Group group);

        private void RemoveGroupFromList(Group group)
        {
                GroupWrapper groupToRemove;
                if (_Groups.TryGetValue(group.Name, out groupToRemove))
                {
                    if (GroupList_ListBox.Items.Contains(groupToRemove))
                    {
                        GroupList_ListBox.Items.Remove(groupToRemove);
                        _Groups.Remove(group.Name);
                    }
                    else
                    {
                        Debug.WriteLine(group.Name + " was not found in list");
                    }
                }

        }

        private void AddGroupToList(Group group)
        {
            if (!GroupList_ListBox.Items.Contains(group.Name))
            {
                GroupWrapper gWrap = new GroupWrapper(group);
                gWrap.NameChanged += gWrap_NameChanged;
                GroupList_ListBox.Items.Add(gWrap);
                _Groups.Add(gWrap.LyncGroup.Name, gWrap);
            }
        }

        void gWrap_NameChanged(string oldName, string newName)
        {
            this.Dispatcher.Invoke(new DelegateNoParams(LoadList));
        }
    }
    internal class GroupWrapper
    {
        public delegate void NameChangedDelegate(string oldName, string newName);

        public event NameChangedDelegate NameChanged;
        Group _group;
        private string originalName;
        
        public override string ToString()
        {
            return _group.Name;
        }

        public Group LyncGroup
        {
            get
            {
                return _group;
            }
        }
        internal GroupWrapper(Group group)
        {
            _group = group;
            originalName = group.Name;
            _group.NameChanged += _group_NameChanged;
        }

        void _group_NameChanged(object sender, GroupNameChangedEventArgs e)
        {
            if (NameChanged != null)
            {
                NameChanged(originalName, e.NewName);
                originalName = e.NewName;
            }
        }
    }
}
```

## Next steps

  - [How to: Move or copy a contact between custom groups in Lync SDK](how-to-move-or-copy-a-contact-between-custom-groups-in-lync-sdk.md)

  - [How to: Display a contact list](how-to-display-a-contact-list.md)

## See also

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [Lync contact groups](lync-contact-groups.md)

