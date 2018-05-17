---
title: 'How to: Add or remove a person from a contact list'
TOCTitle: 'How to: Add or remove a person from a contact list'
ms:assetid: 8089489e-b27a-46e7-a84c-6071b408e1cb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933106(v=office.15)
ms:contentKeyID: 50877240
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Add or remove a person from a contact list

Learn how to remove a contact from a Microsoft Lync 2013 user’s contact list by calling methods from the Microsoft Lync 2013 API.


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
Display contacts<br />
Add a contact to the contact list<br />
Delete a contact from the contact list<br />
Code examples: Contact lists<br />
Next steps<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Prerequisites

The prerequisites for adding or removing a custom group are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Display contacts

To delete a contact from a user’s contact list, a [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) object most be obtained. There are several ways to obtain a [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) object. If you have the SIP URI of the Lync user to be removed from the contact list, simply call the [ContactManager.GetContactByUri](contactmanager-getcontactbyuri-method-microsoft-lync-model_2.md) method. You can also get the **Contact** instance by iterating on the group collection value returned by getting the [ContactManager.Groups](contactmanager-groups-property-microsoft-lync-model_2.md) property and then iterating on each group to access the individual contacts.

Contacts and groups are available when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding a contact list to your UI.

The sample application at the end of this topic displays a list of contacts for the group selected by the user from a list of groups. To fill the group and contact lists in the sample, use the following procedure.

### To display a list of groups

1.  Iterate on the group collection returned in the [ContactManager.Groups](contactmanager-groups-property-microsoft-lync-model_2.md) property value in a foreach loop.

2.  For each group instance, read the string [Group.Name](group-name-property-microsoft-lync-model-group_2.md) property value and add it to the group list in the UI.
    

    > [!TIP]
    > <P>When you get a <STRONG>Group</STRONG> object to display, encapsulate the <STRONG>Group</STRONG> in a custom class that overrides the <STRONG>ToString</STRONG> method. Return the <A href="group-name-property-microsoft-lync-model-group_2.md">Group.Name</A> string as return value in the overridden <STRONG>ToString</STRONG> method. Add the encapsulating class object to the list instead of a simple string. When a user selects a group from the list, the actual group is selected. Doing this allows you to avoid running a routine that gets a group associated with a name string every time a selection is made in the list.</P>

    
    ``` csharp
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
                    GroupList_ListBox.Items.Add(gWrap);
    
                }
            }
    ```

### To display the contacts in a group

1.  Iterate on the [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md) object that the user selected in the group list.
    
    The **Group** object is a collection of [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) objects.

2.  For each **Contact** in the collection, add the display name of the contact to the contact list on the UI.
    

    > [!TIP]
    > <P>When you have gotten a <STRONG>Contact</STRONG> object to display, you should encapsulate the contact in a custom class that overrides the <STRONG>ToString</STRONG> method. Return the contact <A href="contactinformationtype-enumeration-microsoft-lync-model_2.md">ContactInformationType</A><STRONG>.DisplayName</STRONG> string as return value in the overridden <STRONG>ToString</STRONG> method. Add the encapsulating class object to the list instead of a simple string. When a user selects a contact from the list, the actual contact object is selected. Doing this allows you to avoid running a routine that looks up a Contact object based on a display name every time a user selects a contact in the list.</P>

    
    ``` 
            /// <summary>
            /// Loads all of the contacts for a selected group into a contact
            /// list on the UI
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void GroupList_ListBox_SelectionChanged(object sender, System.Windows.Controls.SelectionChangedEventArgs e)
            {
                //Get the selected group
                GroupWrapper groupToList = (GroupWrapper)GroupList_ListBox.SelectedItem; 
    
                //clear the contact list
                ContactList_ListBox.Items.Clear();
    
                foreach (Contact contact in groupToList.LyncGroup)
                {
                    ContactWrapper contactWrapper = new ContactWrapper(contact);
                    ContactList_ListBox.Items.Add(contactWrapper);
                }
            }
    ```

## Add a contact to the contact list

To add a contact to the user’s contact list, get a contact object and add it to any of the custom groups in the contact list. Although you can add a [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md) object to the contact list regardless of the origin of the contact, it is best to add contacts that publish presence availability. A contact that is obtained by using the search feature of the Lync 2013 API is guaranteed to publish presence availability. To learn how to search for a contact, see [How to: Search for a contact or distribution group in Lync SDK](https://msdn.microsoft.com/en-us/library/jj933159\(v=office.15\)).

### To add a contact to the contact list

1.  Select a [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md) object from the user’s custom group collection by getting a **Group** from the [ContactManager.Groups](contactmanager-groups-property-microsoft-lync-model_2.md) property.

2.  Select a [Contact](contact-class-microsoft-lync-model_2.md) object from the collection of search results returned by a contact search.

3.  Add the selected contact to the selected group by calling the [Group.BeginAddContact](group-beginaddcontact-method-microsoft-lync-model-group_2.md) method.
    
    The following example gets a selected contact from the [Microsoft.Lync.Controls.ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) control on a WPF form and then adds the contact to a previously selected [Microsoft.Lync.Model.Group.Group](group-class-microsoft-lync-model-group_2.md).
    
    ``` 
            /// <summary>
            /// Adds the contact that is selected in the contact search results list to the group that is selected.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void AddContactToGroup_Click(object sender, RoutedEventArgs e)
            {
                Microsoft.Lync.Controls.SearchResult selectedContact = (Microsoft.Lync.Controls.SearchResult)ResultList.SelectedItem;
                if (selectedContact.Result.GetType().Name == "Contact")
                {
                    Contact contact = selectedContact.Result as Contact;
                    selectedGroup.BeginAddContact(contact, (ar) => { selectedGroup.EndAddContact(ar); }, null);
    
                }
            }
    ```
    
    After the contact is added to the selected group, the contact appears in the Lync 2013 contact list under the selected group.

## Delete a contact from the contact list

Deleting a contact from the user’s contact list requires that the contact is removed from every group in the list. You can remove a contact from one group at a time or remove the contact from all groups in a single operation. The following procedure shows how to remove a contact with a single operation.

### To delete a contact

1.  Get the **Contact** object selected in the contact list in the UI.

2.  Call the **ContactManagerBeginRemoveContactFromAllGroups(Contact, AsyncCallback, Object)** method, passing the selected contact in the first argument.
    
    ``` csharp
            /// <summary>
            /// remove the selected contact from every group in the users contact list
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void RemoveContact_Button_Click(object sender, RoutedEventArgs e)
            {
                if (ContactList_ListBox.SelectedItem == null)
                {
                    return;
                }
                ContactWrapper selectedContact = (ContactWrapper)ContactList_ListBox.SelectedItem;
                _LyncClient.ContactManager.BeginRemoveContactFromAllGroups(
                    selectedContact.LyncContact,
                     (ar) =>
                     {
                         _LyncClient.ContactManager.EndRemoveContactFromAllGroups(ar);
                      },
                     null);
    
            }
    ```

## Code examples: Contact lists

The following example declares a window that shows a list of groups and a list of contacts that are in the selected group.

``` xaml
<Window x:Class="GroupManager.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
        Title="My Contact List" Height="422" Width="717" Loaded="Window_Loaded_1" >
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="30*"/>
            <RowDefinition Height="5*"/>
        </Grid.RowDefinitions>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="80*"/>
            <ColumnDefinition Width="30*"/>
        </Grid.ColumnDefinitions>
        <StackPanel Grid.Row="0" Grid.Column="0" Orientation="Horizontal">
            <ListBox Name="GroupList_ListBox" Width="200" Height="195" Margin="10,10,10,10" SelectionChanged="GroupList_ListBox_SelectionChanged"/>
            <ListBox Name="ContactList_ListBox" Height="195"  Width="272" Margin="10,10,10,10" />
        </StackPanel>
        <StackPanel Grid.Row="0" Grid.Column="1">
            <Button Content="Remove Contact" Height="23" Name="RemoveContact_button" Margin="10,65,10,10" Click="RemoveContact_Button_Click"/>
            <Button Content="Add Contact" Height="23" Name="button1" Width="75" Click="AddContactToGroup_Click"/>
            <controls:ContactSearchInputBox x:Name="searchInput"/>
            <controls:ContactSearchResultList
                ItemsSource="{Binding Results, ElementName=searchInput, Mode=OneWay}"
                ResultsState="{Binding SearchState, ElementName=searchInput, Mode=OneWay}" Name="ResultList"/>

        </StackPanel>
    </Grid>
</Window>
```

The following example handles platform events for the [Microsoft.Lync.Model.ContactManager](contactmanager-class-microsoft-lync-model_2.md) and events raised by the previous window.

``` csharp
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
        Group selectedGroup;

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
                GroupWrapper gWrap = new GroupWrapper(group);

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
            GroupWrapper groupToList = (GroupWrapper)GroupList_ListBox.SelectedItem;
            selectedGroup = groupToList.LyncGroup;

            //clear the contact list
            ContactList_ListBox.Items.Clear();

            foreach (Contact contact in groupToList.LyncGroup)
            {
                ContactWrapper contactWrapper = new ContactWrapper(contact);
                ContactList_ListBox.Items.Add(contactWrapper);
            }
        }

        /// <summary>
        /// remove the selected contact from every group in the users contact list
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void RemoveContact_Button_Click(object sender, RoutedEventArgs e)
        {
            if (ContactList_ListBox.SelectedItem == null)
            {
                return;
            }
            ContactWrapper selectedContact = (ContactWrapper)ContactList_ListBox.SelectedItem;
                _LyncClient.ContactManager.BeginRemoveContactFromAllGroups(
                    selectedContact.LyncContact,
                    (ar) =>
                    {
                        _LyncClient.ContactManager.EndRemoveContactFromAllGroups(ar);
                    },
                    null);

        }

        /// <summary>
        /// Adds the contact that is selected in the contact search results list to the group that is selected.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void AddContactToGroup_Click(object sender, RoutedEventArgs e)
        {
            Microsoft.Lync.Controls.SearchResult selectedContact = (Microsoft.Lync.Controls.SearchResult)ResultList.SelectedItem;
            if (selectedContact.Result.GetType().Name == "Contact")
            {
                Contact contact = selectedContact.Result as Contact;
                selectedGroup.BeginAddContact(contact, (ar) => { selectedGroup.EndAddContact(ar); }, null);

            }
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

## Next steps

After learning how to remove a contact from a contact list, you should learn how to move a contact from one group to a different group or simply remove a contact from one of the groups that the contact is in. To create a contact list that displays a current list of groups and the contacts in the groups, the second of these next steps gets you started building a contact list.

  - [How to: Move or copy a contact between custom groups in Lync SDK](how-to-move-or-copy-a-contact-between-custom-groups-in-lync-sdk.md)

  - [How to: Display a contact list](how-to-display-a-contact-list.md)

## Additional resources

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

