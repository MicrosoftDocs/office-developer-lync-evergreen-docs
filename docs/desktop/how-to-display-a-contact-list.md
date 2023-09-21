---
title: 'How to: Display a contact list'
TOCTitle: 'How to: Display a contact list'
ms:assetid: e69504aa-b198-4ade-8853-60c42380415e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933244(v=office.15)
ms:contentKeyID: 50877390
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
- csharp
---

# How to: Display a contact list

Learn how to use members of the [Microsoft.Lync.Model](https://msdn.microsoft.com/library/jj274810\(v=office.15\)) namespace to provide contact presence and presence updates to build a custom Lync contact list UI.



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
Fill a contact list from a custom group<br />
Fill a contact list from a distribution group<br />
Code examples: Custom contact lists<br />
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
<td><p>Describes how distribution groups work in Microsoft Lync 2013 SDK.</p></td>
</tr>
</tbody>
</table>

## Fill a contact list from a custom group

The classes, methods, and events appearing in the following illustration are used in the process of filling a contact list from a custom group.

![OCOM\_WalkthroughContactList](images/JJ933244.OCOM_WalkthroughContactList(Office.15).png "OCOM_WalkthroughContactList")

Contacts and groups are available when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding a contact list to your UI.

To fill a contact list from a custom group, start by getting a collection of [Group](https://msdn.microsoft.com/library/jj266012\(v=office.15\)) class instances from the [ContactManager](https://msdn.microsoft.com/library/jj266459\(v=office.15\)) class. This collection is available using the [Groups](https://msdn.microsoft.com/library/jj277988\(v=office.15\)) property of the contacts and groups manager. The collection contains both custom groups defined by a local user and other groups provided by Microsoft Lync Server 2013.

### To fill a contact list from a custom group

1.  Get the [LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance and verify that the client is signed in to Lync 2013.
    
    For information about signing in to Lync 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Create a [ContactSubscription](https://msdn.microsoft.com/library/jj268195\(v=office.15\)) instance by calling into [CreateSubscription](https://msdn.microsoft.com/library/jj267359\(v=office.15\)).
    
    The [ContactSubscription](https://msdn.microsoft.com/library/jj268195\(v=office.15\)) instance exposes an empty **Contacts** collection that you fill in a following step.

3.  Iterate through the [Groups](https://msdn.microsoft.com/library/jj277988\(v=office.15\)) collection of the [ContactManager](https://msdn.microsoft.com/library/jj266459\(v=office.15\)) instance to find the groups that you want to list.

4.  Register for group events on each group to be listed.

5.  Iterate through the contact collection of the desired group by using a foreach loop.

6.  Register for contact events on each contact.

7.  Add the [Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) instance to the subscription if that contact is not already in the [ContactSubscription](https://msdn.microsoft.com/library/jj268195\(v=office.15\)) instance you created in step 2.
    
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
    <td><p>An individual contact can be in multiple groups but can only be added to a subscription once.</p></td>
    </tr>
    </tbody>
    </table>

8.  Get presence item values of interest from each contact.
    
    For information about getting presence items, see [How to: Get the enhanced presence of a Lync user](how-to-get-the-enhanced-presence-of-a-lync-user.md).
    
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
    <td><p>A contact’s properties and presence information might not be cached locally at the time you obtain the <strong>Contact</strong> instance and query for presence or read properties. For this reason, it's important that you handle the contact events you register for in the previous step. A <a href="https://msdn.microsoft.com/library/jj275543(v=office.15)">Contact.ContactInformationChanged</a> event is raised as each additional element of presence information pushed to the client from Microsoft Lync Server 2013.</p></td>
    </tr>
    </tbody>
    </table>

9.  Insert code to take the action you want for each contact.
    
    The next example adds the contact to an instance of the [ContactSubscription](https://msdn.microsoft.com/library/jj268195\(v=office.15\)) class and to a list used by the UI.

10. Call [Subscribe](https://msdn.microsoft.com/library/jj277847\(v=office.15\)) on your [ContactSubscription](https://msdn.microsoft.com/library/jj268195\(v=office.15\)) instance after you have completed the foreach loop on the contact collection.
    
    The [Subscribe](https://msdn.microsoft.com/library/jj277847\(v=office.15\)) method creates a request on Lync Server 2013 that asks for continuous updates of the presence information from each contact added to the subscription.

## Fill a contact list from a distribution group

A distribution group is also a collection of contacts.

### To fill a contact list from a distribution group

1.  Get the [LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) instance and verify that the client is signed in to the server.
    
    For information about signing in to Lync Server 2013, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

2.  Select a distribution group.
    
    For more information about searching for distribution groups, see [How to: Search for a contact or distribution group in Lync SDK](https://msdn.microsoft.com/library/jj933159\(v=office.15\)).

3.  Call the [BeginGetAllMembers](https://msdn.microsoft.com/library/jj268237\(v=office.15\)) method on the distribution group instance, passing the callback delegate as a parameter.
    
    This starts an operation that returns a [ContactCollection](https://msdn.microsoft.com/library/jj267665\(v=office.15\)) instance when you call [EndGetAllMembers](https://msdn.microsoft.com/library/jj274834\(v=office.15\)).

4.  Create the callback method to manipulate the instance of the [ContactCollection](https://msdn.microsoft.com/library/jj267665\(v=office.15\)) class returned in the callback.

## Code examples: Custom contact lists

The following examples execute the basic logic necessary to obtain [Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) instances that can be used to build a list of contacts in a UI. The first example iterates on all groups returned by the [Groups](https://msdn.microsoft.com/library/jj277988\(v=office.15\)) property and gets the contacts from all groups of the [GroupType](https://msdn.microsoft.com/library/jj276550\(v=office.15\)).**CustomGroup** type.

Figure 1 shows a sample WPF application that lists a user’s contact groups in a list on the left side of the window and a list of the selected group contacts on the right side of the window.

Figure 1. My Contact List sample application

  
![A list of groups and contacts in a WPF window](images/JJ933244.LyncClientSDK_HowToDisplayContactList(Office.15).png "A list of groups and contacts in a WPF window")

```xaml
<Window x:Class="MyContactList.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="My Contact List" Height="350" Width="525" Loaded="Window_Loaded_1" Background="Aquamarine">
    <Grid Background="AliceBlue">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="260"/>
            <ColumnDefinition Width="260*"/>
        </Grid.ColumnDefinitions>
        <Label Content="Groups" Grid.Column="0" Margin="22,5,10,10"/>
        <ListBox Name="MyGroups_ListBox" Grid.Column="0" Width="200" Height="260" SelectionChanged="MyGroups_ListBox_Selected_1"/>
        <Label Content="Contacts" Grid.Column="1" Margin="22,5,10,10"/>
        <ListBox Name="GroupContacts_ListBox" Grid.Column="1" Height="260" Width="200"/>
    </Grid>
</Window>
```

The following example is the interaction logic for the window declared in the previous example.

```csharp
using System.Collections.Generic;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Documents;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;

namespace MyContactList
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        LyncClient _LyncClient;
        ContactSubscription groupContactSubscription = null;
        public MainWindow()
        {
            InitializeComponent();
        }

        private void MyGroups_ListBox_Selected_1(object sender, RoutedEventArgs e)
        {
            ListBox listBox = (ListBox)sender;
            GroupWrapper selectedGroup = (GroupWrapper)listBox.SelectedItem;

            groupContactSubscription = null;
            groupContactSubscription = _LyncClient.ContactManager.CreateSubscription();
            List<ContactInformationType> information = new List<ContactInformationType>();
            information.Add(ContactInformationType.Activity);

            FillContactList(selectedGroup);

            groupContactSubscription.Subscribe(ContactSubscriptionRefreshRate.High, information);
        }

        private delegate void FillContactListDelegate(GroupWrapper selectedGroup);
        /// <summary>
        /// Fills the contact list with contacts from the group selected in the group list
        /// </summary>
        /// <param name="selectedGroup"></param>
        private void FillContactList(GroupWrapper selectedGroup)
        {
            ContactCollection groupContacts = null;

            GroupContacts_ListBox.Items.Clear();
            if (selectedGroup.LyncGroup.Type == GroupType.DistributionGroup)
            {
                selectedGroup.DGroup.BeginGetAllMembers(
                    (ar) =>
                    {
                        try
                        {
                            groupContacts = selectedGroup.DGroup.EndGetAllMembers(ar);
                            foreach (Contact contact in groupContacts)
                            {
                                groupContactSubscription.AddContact(contact);
                                ContactWrapper groupContact = new ContactWrapper(contact);
                                groupContact.ActivityChanged += groupContact_ActivityChanged;
                                this.Dispatcher.Invoke(new AddListItemDelegate(AddListItem), new object[] { GroupContacts_ListBox, groupContact });
                            }
                        }
                        catch (LyncClientException lce)
                        {
                            System.Diagnostics.Debug.WriteLine("Lync client exception on EndGetAllMembers " + lce.Message);
                        }
                    },
                    null);
            }
            else
            {
                foreach (Contact contact in selectedGroup.LyncGroup)
                {
                    groupContactSubscription.AddContact(contact);
                    ContactWrapper groupContact = new ContactWrapper(contact);
                    groupContact.ActivityChanged += groupContact_ActivityChanged;
                    this.Dispatcher.Invoke(new AddListItemDelegate(AddListItem), new object[] { GroupContacts_ListBox, groupContact });
                }
            }

        }
        void groupContact_ActivityChanged()
        {
            this.Dispatcher.Invoke(new RefreshListDelegate(RefreshList));
        }

        private delegate void RefreshListDelegate();
        private void RefreshList()
        {
            GroupContacts_ListBox.Items.Refresh();
        }

        private delegate void AddListItemDelegate(System.Windows.Controls.ListBox boxToLoad, object newItem);
        private void AddListItem(System.Windows.Controls.ListBox boxToLoad, object newItem)
        {
            boxToLoad.Items.Add(newItem);
        }

        private void Window_Loaded_1(object sender, RoutedEventArgs e)
        {
            try
            {
                _LyncClient = LyncClient.GetClient();
                LoadGroups();

            }
            catch (ClientNotFoundException) { System.Diagnostics.Debug.WriteLine("The Lync client is not found"); }
            catch (LyncClientException lce) { System.Diagnostics.Debug.WriteLine("Lync client exception on GetClient: " + lce.Message); }
        }
        private void LoadGroups()
        {
            GroupWrapper newGroup = null;
            foreach (Group dg in _LyncClient.ContactManager.Groups)
            {
                newGroup = new GroupWrapper(dg);
                newGroup.MembershipChanged += newGroup_MembershipChanged;
                MyGroups_ListBox.Items.Add(newGroup);
            }
        }

        void newGroup_MembershipChanged(GroupWrapper thisGroup)
        {
            this.Dispatcher.Invoke(new FillContactListDelegate(FillContactList), new object[] {thisGroup});
        }
    }

    public class ContactWrapper
    {
        Contact _Contact;
        public delegate void activytChangedDelegate();

        public event activytChangedDelegate ActivityChanged;
        public override string ToString()
        {
            string returnValue = string.Empty;
            try
            {
                returnValue = _Contact.GetContactInformation(ContactInformationType.DisplayName).ToString()
                    + ": "
                    + _Contact.GetContactInformation(ContactInformationType.Activity).ToString();

            }
            catch (ItemNotFoundException)
            {
                returnValue = _Contact.Uri.ToString();
                System.Diagnostics.Debug.WriteLine("Contact information item was not found");
            }
            return returnValue;
        }
        public ContactWrapper(Contact contact)
        {
            _Contact = contact;
            _Contact.ContactInformationChanged += _Contact_ContactInformationChanged;
        }

        void _Contact_ContactInformationChanged(object sender, ContactInformationChangedEventArgs e)
        {
            if (e.ChangedContactInformation.Contains(ContactInformationType.Activity))
            {
                if (ActivityChanged != null)
                {
                    ActivityChanged();
                }
            }
        }
    }

    public class GroupWrapper
    {
        DistributionGroup _DistributionGroup;
        Group _Group;
        public delegate void membershipChangedDelegate(GroupWrapper thisGroup);
        public event membershipChangedDelegate MembershipChanged;

        public override string ToString()
        {
            return _Group.Name;
        }
        public Group LyncGroup
        {
            get
            {
                return _Group;
            }
        }
        public DistributionGroup DGroup
        {
            get
            {
                return _DistributionGroup;
            }
        }
        public GroupWrapper(Group group)
        {
            _Group = group;
            _Group.ContactAdded += _Group_ContactAdded;
            _Group.ContactRemoved += _Group_ContactRemoved;
            _Group.NameChanged += _Group_NameChanged;
            if (group.Type == GroupType.DistributionGroup)
            {
                _DistributionGroup = (DistributionGroup)group;
            }
        }

        void _Group_NameChanged(object sender, GroupNameChangedEventArgs e)
        {
            throw new System.NotImplementedException();
        }

        void _Group_ContactRemoved(object sender, GroupMemberChangedEventArgs e)
        {
            if (MembershipChanged != null)
            {
                MembershipChanged(this);
            }

        }

        void _Group_ContactAdded(object sender, GroupMemberChangedEventArgs e)
        {
            if (MembershipChanged != null)
            {
                MembershipChanged(this);
            }
        }
    }
}
```

## See also

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

