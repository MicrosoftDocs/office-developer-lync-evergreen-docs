---
title: 'How to: Move or copy a contact between custom groups in Lync SDK'
TOCTitle: 'How to: Move or copy a contact between custom groups'
ms:assetid: f3a39bc2-0648-4eb0-8444-99ad8363a65a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933228(v=office.15)
ms:contentKeyID: 50877372
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Move or copy a contact between custom groups in Lync SDK

Learn how to programmatically move or copy a Microsoft Lync 2013 contact from one Lync 2013 group to another in a user’s contact list.

**Last modified:** July 01, 2013

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
<td><p>You cannot move contacts out of a distribution group or copy contacts into a distribution group by using the Microsoft Lync 2013 API.</p></td>
</tr>
</tbody>
</table>

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Move a contact from one group to another group<br />
Copy a contact from one group to another group<br />
Code examples: My contact mover<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-add-or-remove-f70ab894">Add or remove contacts from the &quot;Other Contacts&quot; group</a></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for moving a contact to another group are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

Contacts and groups are available when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding a contact list to your UI.

## Move a contact from one group to another group

### To move a contact

1.  Get the name of the custom group to which the contact is to be moved.

2.  Get the [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/en-us/library/jj266012\(v=office.15\)) object from the groups collection returned by the [ContactManager.Groups](https://msdn.microsoft.com/en-us/library/jj277988\(v=office.15\)) property based on the group name.

3.  Move the contact by specifying the target group and source group by calling the [Contact.BeginMoveToGroup](https://msdn.microsoft.com/en-us/library/jj294107\(v=office.15\)) method.
    
    The following example gets a group based on a group name and then moves a contact from a source group to the target group.
    
    ```csharp
            /// <summary>
            /// Moves a contact from the selected group to a custom group whose
            /// name matches 
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void MoveContact_Click(object sender, RoutedEventArgs e)
            {
                //Get the selected group
                ContactMover.GroupWrapper groupToList = (ContactMover.GroupWrapper)GroupList_ListBox.SelectedItem;
                _SelectedGroup = groupToList.LyncGroup;
    
                Microsoft.Lync.Model.Group.Group targetGroup;
                if (_LyncClient.ContactManager.Groups.TryGetGroup(NewGroup.Text, out targetGroup))
                {
                    //Get the selected group
                    ContactMover.ContactWrapper contactToMove = (ContactMover.ContactWrapper)ContactList_ListBox.SelectedItem;
                    contactToMove.LyncContact.BeginMoveToGroup(
                        targetGroup,
                        _SelectedGroup, (ar) => { contactToMove.LyncContact.EndMoveToGroup(ar); },
                        null);
                }
            }
    ```

## Copy a contact from one group to another group

### To copy a contact

1.  Get the name of the custom group to which the contact is to be copied.

2.  Get the [Microsoft.Lync.Model.Group.Group](https://msdn.microsoft.com/en-us/library/jj266012\(v=office.15\)) object from the groups collection returned by the [ContactManager.Groups](https://msdn.microsoft.com/en-us/library/jj277988\(v=office.15\)) property based on the group name.

3.  Copy the contact by calling the [Group.BeginAddContact](https://msdn.microsoft.com/en-us/library/jj275692\(v=office.15\)) method on the target group.
    
    The following example gets a group based on a group name and then moves a contact from a source group to the target group.
    
    ```csharp
            /// <summary>
            /// Copies a selected contact to a group specified by a group name string
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void CopyContact_Click(object sender, RoutedEventArgs e)
            {
                Microsoft.Lync.Model.Group.Group targetGroup;
                if (_LyncClient.ContactManager.Groups.TryGetGroup(NewGroup.Text, out targetGroup))
                {
                    //Get the selected group
                    ContactMover.ContactWrapper contactToMove = (ContactMover.ContactWrapper)ContactList_ListBox.SelectedItem;
                    targetGroup.BeginAddContact(contactToMove.LyncContact, (ar) => { targetGroup.EndAddContact(ar); }, null);
                }
    
            }
    ```

## Code examples: My contact mover

The following example declares a WPF window that presents a list of groups from a user’s contact list, a list of contacts in a selected group, and controls that give you the ability to move a contact from one group to another.

```xaml
<Window x:Class="ContactMover.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
        Title="My Contact Mover" Height="422" Width="541" Loaded="Window_Loaded_1" >
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="80*"/>
            <RowDefinition Height="40*"/>
        </Grid.RowDefinitions>
        <StackPanel Orientation="Horizontal" Margin="0,0,0,12">
            <ListBox Name="GroupList_ListBox" Width="200" Height="195" Margin="10,10,10,10" SelectionChanged="GroupList_ListBox_SelectionChanged"/>
            <ListBox Name="ContactList_ListBox" Height="195"  Width="272" Margin="10,10,10,10" />
        </StackPanel>
        <StackPanel Grid.Row="1" Orientation="Horizontal" Margin="0,0,10,0">
            <Label Content="Group Name:" Height="23"/>
            <TextBox Name="NewGroup" Margin="10,10,10,10" Width="150" Height="23"/>
            <Button Name="MoveContact" Content="Move to new group"  Click="MoveContact_Click" Height="23" Width="120" Margin="0,0,10,0"/>
            <Button Name="CopyContact" Content="Copy to new group" Click="CopyContact_Click" Height="23" Width="120"/>
        </StackPanel>
    </Grid>
</Window>
```

The following example is the interaction logic for the previously declared WPF window.

```csharp
 using System.Windows;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;
using System.Diagnostics;

namespace ContactMover
{

    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        LyncClient _LyncClient;
        Group _SelectedGroup;

        public MainWindow()
        {
            InitializeComponent();
        }

        private void Window_Loaded_1(object sender, RoutedEventArgs e)
        {
            //GroupList_ListBox
            try 
            {
                _LyncClient = LyncClient.GetClient();
                LoadList();
                GroupList_ListBox.SelectedIndex = 0;
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
                ContactMover.GroupWrapper gWrap = new ContactMover.GroupWrapper(group);

                GroupList_ListBox.Items.Add(gWrap);
            }
        }

        /// <summary>
        /// Loads all of the contacts for a selected group into a contact
        /// list on the UI
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void GroupList_ListBox_SelectionChanged(object sender, System.Windows.Controls.SelectionChangedEventArgs e)
        {
            //Get the selected group
            ContactMover.GroupWrapper groupToList = (ContactMover.GroupWrapper)GroupList_ListBox.SelectedItem;
            _SelectedGroup = groupToList.LyncGroup;

            //clear the contact list
            ContactList_ListBox.Items.Clear();

            foreach (Microsoft.Lync.Model.Contact contact in groupToList.LyncGroup)
            {
                ContactMover.ContactWrapper contactWrapper = new ContactMover.ContactWrapper(contact);
                ContactList_ListBox.Items.Add(contactWrapper);
            }
        }

        /// <summary>
        /// Moves a contact from the selected group to a custom group whose
        /// name matches 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void MoveContact_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                //Get the selected group
                ContactMover.GroupWrapper groupToList = (ContactMover.GroupWrapper)GroupList_ListBox.SelectedItem;
                _SelectedGroup = groupToList.LyncGroup;

                Microsoft.Lync.Model.Group.Group targetGroup;
                if (_LyncClient.ContactManager.Groups.TryGetGroup(NewGroup.Text, out targetGroup))
                {
                    //Get the selected group
                    ContactMover.ContactWrapper contactToMove = (ContactMover.ContactWrapper)ContactList_ListBox.SelectedItem;
                    contactToMove.LyncContact.BeginMoveToGroup(
                        targetGroup,
                        _SelectedGroup, (ar) => { contactToMove.LyncContact.EndMoveToGroup(ar); },
                        null);
                }
            }
            //NotSupportedException is raised when trying to move to a DistributionGroup
            catch (System.NotSupportedException nse) { System.Diagnostics.Debug.WriteLine("NotSupportedException on copy to group: " + nse.Message); }

            //NotImplementedExcption is raised when trying to move to a FrequentContacts group
            catch (System.NotImplementedException nie) { System.Diagnostics.Debug.WriteLine("NotImplementedException on copy to group: " + nie.Message); }
        }

        /// <summary>
        /// Copies a selected contact to a group specified by a group name string
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void CopyContact_Click(object sender, RoutedEventArgs e)
        {
            try
            {
                Microsoft.Lync.Model.Group.Group targetGroup;
                if (_LyncClient.ContactManager.Groups.TryGetGroup(NewGroup.Text, out targetGroup))
                {
                    //Get the selected group
                    ContactMover.ContactWrapper contactToMove = (ContactMover.ContactWrapper)ContactList_ListBox.SelectedItem;
                    targetGroup.BeginAddContact(contactToMove.LyncContact, (ar) => { targetGroup.EndAddContact(ar); }, null);
                }
            }
            //NotSupportedException is raised when trying to copy to a DistributionGroup
            catch (System.NotSupportedException nse) { System.Diagnostics.Debug.WriteLine("NotSupportedException on copy to group: " + nse.Message); }

            //NotImplementedExcption is raised when trying to copy to a FrequentContacts group
            catch (System.NotImplementedException nie) { System.Diagnostics.Debug.WriteLine("NotImplementedException on copy to group: " + nie.Message); }

        }
    }

    internal class ContactWrapper
    {
        Contact _contact;
        private string displayName;
        internal Contact LyncContact
        {
            get
            {
                return _contact;
            }
        }
        public override string ToString()
        {
            return displayName; // 
        }
        internal ContactWrapper(Contact contact)
        {
            _contact = contact;
            displayName = _contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
        }
    }

    internal class GroupWrapper
    {
        Group _group;
        
        public override string ToString()
        {
            return _group.Name;
        }

        internal Group LyncGroup
        {
            get
            {
                return _group;
            }
        }
        internal GroupWrapper(Group group)
        {
            _group = group;
        }

    }
}
```

## See also

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

