---
title: 'How to: Subscribe to enhanced presence content'
TOCTitle: 'How to: Subscribe to enhanced presence content'
ms:assetid: 28e8bd5d-14ea-4bb1-809f-1dec9f36c86f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937284(v=office.15)
ms:contentKeyID: 50877103
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Subscribe to enhanced presence content

Learn how to use Microsoft Lync 2013 SDK to create a subscription to the enhanced presence published by a user.



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
Subscribe to user presence information publications<br />
Suspend a presence subscription<br />
Modify an existing subscription contact information items list<br />
Code examples: Contact subscription log<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for subscribing to presence information are as follows:

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
<td><p><a href="enhanced-presence-content-in-lync-sdk.md">Enhanced presence content in Lync SDK</a></p></td>
<td><p>Explains the concept of enhanced presence in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="presence-publication-and-subscription-in-lync-sdk.md">Presence publication and subscription in Lync SDK</a></p></td>
<td><p>Explains what it means to publish or subscribe to presence.</p></td>
</tr>
</tbody>
</table>

## Subscribe to user presence information publications

### To subscribe to presence publications

1.  Create a new [Microsoft.Lync.Model.ContactSubscription](https://msdn.microsoft.com/en-us/library/jj268195\(v=office.15\)).
    
    ```csharp
    _contactSubscription = LyncClient.GetClient().ContactManager.CreateSubscription();
    ```

2.  Create a **List\<ContactInformationType\>** object to hold an enumerated collection of the information types that are to be subscribed.
    
    ```csharp
    _ContactInformationList = new List<ContactInformationType>();
    ```

3.  Add an [Microsoft.Lync.Model.ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\)) enumerator for each kind of enhanced presence information that you want to be notified about when it is updated.

4.  Add a **Contact** object to the subscription for each user whose contact information that you want to subscribe to by calling the [ContactSubscription.AddContact](https://msdn.microsoft.com/en-us/library/jj275705\(v=office.15\)) method.

5.  Start the subscription to each contact’s presence publications by calling the [ContactSubscription.Subscribe](https://msdn.microsoft.com/en-us/library/jj277847\(v=office.15\)) method.
    
    ```csharp
                _ContactInformationList = new List<ContactInformationType>();
                _ContactInformationList.Add(ContactInformationType.Activity);
                _ContactInformationList.Add(ContactInformationType.ActivityId);
                _ContactInformationList.Add(ContactInformationType.AttributionString);
                _ContactInformationList.Add(ContactInformationType.Availability);
                _ContactInformationList.Add(ContactInformationType.Capabilities);
                _ContactInformationList.Add(ContactInformationType.CapabilityDetails);
                _ContactInformationList.Add(ContactInformationType.CapabilityString);
                _ContactInformationList.Add(ContactInformationType.Company);
                _ContactInformationList.Add(ContactInformationType.ContactEndpoints);
                _ContactInformationList.Add(ContactInformationType.ContactType);
                _ContactInformationList.Add(ContactInformationType.CurrentCalendarState);
                _ContactInformationList.Add(ContactInformationType.PersonalNote);
                _ContactInformationList.Add(ContactInformationType.OutOfficeNote);
                _ContactInformationList.Add(ContactInformationType.Photo);
                _ContactInformationList.Add(ContactInformationType.SourceNetwork);
                _contactSubscription = LyncClient.GetClient().ContactManager.CreateSubscription();
                _contactSubscription.AddContact(_contact);
                _contactSubscription.Subscribe(ContactSubscriptionRefreshRate.High, _ContactInformationList);
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
<td><p>Be sure to call the <a href="https://msdn.microsoft.com/en-us/library/jj277847(v=office.15)">ContactSubscription.Subscribe</a> method. If you register for the <a href="https://msdn.microsoft.com/en-us/library/jj275543(v=office.15)">Contact.ContactInformationChanged</a> event on each <strong>Contact</strong> that you add to a <strong>ContactSubscription</strong>, the event is raised for any new subscribed presence publications by those subscribed contacts. The <strong>ContactSubscription</strong> object itself does not expose subscription or publication events.</p></td>
</tr>
</tbody>
</table>

## Suspend a presence subscription

An application can cache [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) objects for later display in an application UI. For example, an application can get a set of **Contact** objects for the members of a large team of users in an organization. If these contacts are displayed in a collapsible or scrollable list, only a subset of these contacts are displayed in the application UI. To save network bandwidth and increase application performance, you should suspend the subscriptions for those contacts that are not displayed in the UI.

### To suspend and restart a presence subscription

1.  Call the [ContactSubscription.Unsubscribe](https://msdn.microsoft.com/en-us/library/jj276640\(v=office.15\)) method on the subscription whose contact presence publication notifications are to be suspended.

2.  Remove non-displayed contacts by calling the [ContactSubscription.RemoveContact](https://msdn.microsoft.com/en-us/library/jj293450\(v=office.15\)) method for each of these contacts.

3.  Add any displayed contacts that are not in the subscription by calling the [ContactSubscription.AddContact](https://msdn.microsoft.com/en-us/library/jj275705\(v=office.15\)) method.

4.  Get the cached **List\<ContactInformationType\>** object that was used to start the subscription for the first time by reading the [ContactSubscription.LastSubscribedContactInformation](https://msdn.microsoft.com/en-us/library/jj277980\(v=office.15\)) property.

5.  Call the [ContactSubscription.Subscribe](https://msdn.microsoft.com/en-us/library/jj277847\(v=office.15\)) method when the subscription is to be restored and pass the list obtained in the previous step.

## Modify an existing subscription contact information items list

You can change the set of enhanced presence information items that you get notification for by suspending the subscription, modifying the list of **ContactInformationType** objects, and restarting the subscription.

### To modify an existing subscription contact information items list

1.  Get the active [Microsoft.Lync.Model.ContactSubscription](https://msdn.microsoft.com/en-us/library/jj268195\(v=office.15\)) object cached in your application.

2.  Suspend the subscription by calling the [ContactSubscription.Unsubscribe](https://msdn.microsoft.com/en-us/library/jj276640\(v=office.15\)) method.

3.  Get the cached **List\<ContactInformationType\>** object that was used to start the subscription for the first time by reading the [ContactSubscription.LastSubscribedContactInformation](https://msdn.microsoft.com/en-us/library/jj277980\(v=office.15\)) property.

4.  Modify the list by adding or removing the desired items.

5.  Restart the subscription by calling the [Subscribe(ContactSubscriptionRefreshRate, IEnumerable\<ContactInformationType\>)](https://msdn.microsoft.com/en-us/library/jj277847\(v=office.15\)) method and passing the modified **List\<ContactInformationType\>** object.

## Code examples: Contact subscription log

The following example declares a WPF page that displays a list of subscription-related events raised on a subscribed contact object when contact information is republished.

```xaml
<Page
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
      xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls" x:Class="ContactCapabilities.CapabilityPage" 
      mc:Ignorable="d" 
      d:DesignHeight="390" d:DesignWidth="754"
Title="CapabilityPage">

    <Grid>

        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="10*"/>
            <ColumnDefinition Width="20*"/>
            <ColumnDefinition Width="60*"/>
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="22"/>
            <RowDefinition Height="30*"/>
            <RowDefinition Height="40"/>
        </Grid.RowDefinitions>
        <StackPanel Grid.Column="0"
                    Grid.Row="1">
            <Label Name="Contact_Label" Content="Contact" Foreground="CadetBlue"/>
            <Label Name="Availability_Label" Content="Availability" Foreground="CadetBlue"/>
            <Label Name="Capability_Label" Content="Capabilities" Foreground="CadetBlue"/>
        </StackPanel>
        <StackPanel Grid.Column="1" Grid.Row="1">
            <Label Name="ContactName_Label" Content="Name"/>
            <controls:PresenceIndicator 
            Name="pI"
            Grid.Column="1" 
            HorizontalAlignment="Left" 
            Margin="10,10,0,0" 
            Grid.Row="1" 
            VerticalAlignment="Top"/>
            <ListBox Name="Capability_List" Height="140" Margin="10,20,10,10"/>
        </StackPanel>
        <StackPanel Grid.Column="2" Grid.Row="1">
            <ListBox Name="SubscriptionLog_List" Height="303" Margin="10,20,10,10"/>
        </StackPanel>
        <Button Content="Back" 
                Grid.Column="1"
                Grid.Row="2"
                HorizontalAlignment="Left" Margin="10,10,0,0" VerticalAlignment="Top" Width="75" Click="Button_Click_1"/>

        <Button Content="Stop Subscribing" 
               Name="Subscribe_Button"
                Grid.Column="2"
                Grid.Row="2"
                HorizontalAlignment="Left" Margin="10,10,0,0" VerticalAlignment="Top" Width="75" Click="Button_Click_2"/>
    </Grid>
</Page>
```

The following example gets a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object for a supplied SIP address, creates a subscription, adds a collection of [Microsoft.Lync.Model.ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\)) enumerators and the contact object, starts the subscription, and handles events raised when the contact republishes the items that are enumerated in the subscription.

    using System.Collections.Generic;
    using System.Text;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using Microsoft.Lync.Model;
    
    namespace ContactCapabilities
    {
        /// <summary>
        /// Interaction logic for CapabilityPage.xaml
        /// </summary>
        public partial class CapabilityPage : Page
        {
            Contact _contact;
            ContactSubscription _contactSubscription;
            List<ContactInformationType> _ContactInformationList;
            object _ParentContent;
            public CapabilityPage()
            {
                InitializeComponent();
            }
            public CapabilityPage(string SIPAddy, object parentContent)
            {
                InitializeComponent();
    
                _contact = LyncClient.GetClient().ContactManager.GetContactByUri(SIPAddy);
    
                //Register for event raised when selected user contact information
                //is re-published.
                _contact.ContactInformationChanged += _contact_ContactInformationChanged;
    
                //Set presence indicator source to the URI of the selected user.
                pI.Source = _contact.Uri;
    
                //cache the original content of the main window in order to restore it
                //when user clicks the Back button.
                _ParentContent = parentContent;
    
                //Show the name of the user
                ContactName_Label.Content = _contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
    
                //Get the users capabilities to communicate.
                GetCapabilityString();
                _ContactInformationList = new List<ContactInformationType>();
                _ContactInformationList.Add(ContactInformationType.Activity);
                _ContactInformationList.Add(ContactInformationType.ActivityId);
                _ContactInformationList.Add(ContactInformationType.AttributionString);
                _ContactInformationList.Add(ContactInformationType.Availability);
                _ContactInformationList.Add(ContactInformationType.Capabilities);
                _ContactInformationList.Add(ContactInformationType.CapabilityDetails);
                _ContactInformationList.Add(ContactInformationType.CapabilityString);
                _ContactInformationList.Add(ContactInformationType.Company);
                _ContactInformationList.Add(ContactInformationType.ContactEndpoints);
                _ContactInformationList.Add(ContactInformationType.ContactType);
                _ContactInformationList.Add(ContactInformationType.CurrentCalendarState);
                _ContactInformationList.Add(ContactInformationType.PersonalNote);
                _ContactInformationList.Add(ContactInformationType.OutOfficeNote);
                _ContactInformationList.Add(ContactInformationType.Photo);
                _ContactInformationList.Add(ContactInformationType.SourceNetwork);
                _contactSubscription = LyncClient.GetClient().ContactManager.CreateSubscription();
                _contactSubscription.AddContact(_contact);
                _contactSubscription.Subscribe(ContactSubscriptionRefreshRate.High, _ContactInformationList);
            }
            public CapabilityPage(Contact contact, object parentContent)
            {
                InitializeComponent();
                _contact = contact;
    
                //Register for event raised when selected user contact information
                //is re-published.
                _contact.ContactInformationChanged += _contact_ContactInformationChanged;
    
                //Set presence indicator source to the URI of the selected user.
                pI.Source = _contact.Uri;
    
                //cache the original content of the main window in order to restore it
                //when user clicks the Back button.
                _ParentContent = parentContent;
    
                //Show the name of the user
                ContactName_Label.Content = _contact.GetContactInformation(ContactInformationType.DisplayName).ToString();
    
                //Get the users capabilities to communicate.
                GetCapabilityString();
            }
    
            /// <summary>
            /// Raised when user information is republished. This event handler reloads the 
            /// capability list when the capability summary string or capability details are
            /// re-published by a user as they sign into more or less capable endpoints such as
            /// cell phones or computers that have webcams.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void _contact_ContactInformationChanged(object sender, ContactInformationChangedEventArgs e)
            {
                if (e.ChangedContactInformation.Contains(ContactInformationType.CapabilityString) 
                    || e.ChangedContactInformation.Contains(ContactInformationType.CapabilityDetails))
                {
                    this.Dispatcher.Invoke(new NoParamDelegate(GetCapabilityString));
                }
                try
                {
                    foreach (ContactInformationType infoType in e.ChangedContactInformation)
                    {
                        if (!infoType.ToString().StartsWith("Reserved"))
                        {
                            string newValue = _contact.GetContactInformation(infoType).ToString();
                            if (newValue != null)
                            {
                                this.Dispatcher.Invoke(
                                    new Parms1Delegate(WriteToSubscriptionLog), 
                                    new object[] { GetNowString() + " " + infoType.ToString() + " " + newValue });
                            }
                        }
                    }
                }
                catch (ItemNotFoundException inf) 
                {
                    System.Diagnostics.Debug.WriteLine("Item not found " + inf.Message);
                }
    
            }
    
            private string GetNowString()
            {
                return System.DateTime.Now.Hour.ToString() + 
                    ":" + 
                    System.DateTime.Now.Minute.ToString() + 
                    ":" + 
                    System.DateTime.Now.Second.ToString() + 
                    " " + 
                    System.DateTime.Now.Millisecond.ToString();
            }
    
            private delegate void NoParamDelegate();
            private delegate void Parms1Delegate(string logValue);
    
            private void GetCapabilityString()
            {
                Capability_List.Items.Clear();
                Capability_List.Items.Add("Summary: " + _contact.GetContactInformation(ContactInformationType.CapabilityString));
                GetCapabilityDetails();
            }
    
            private void WriteToSubscriptionLog(string logValue)
            {
                SubscriptionLog_List.Items.Add(logValue);
            }
    
            /// <summary>
            /// Gets the details of capability to communicate in all possible modalities and displays the
            /// details in the list.
            /// </summary>
            private void GetCapabilityDetails()
            {
                List<object> details = (List<object>)_contact.GetContactInformation(ContactInformationType.CapabilityDetails);
                foreach (object capabilityObj in details)
                {
                    PresenceCapability capability = (PresenceCapability)capabilityObj;
                    StringBuilder sb = new StringBuilder();
                    string currentAvailability = ConvertAvailabilityIntToEnum(capability.Availability).ToString();
                    sb.Append(capability.Type.ToString() + " is " + currentAvailability + ". ");
                    if (capability.CanRender)
                    {
                        sb.Append("Can render, ");
                    }
                    else
                    {
                        sb.Append("Cannot render, ");
                    }
                    if (capability.CanCapture)
                    {
                        sb.Append("Can capture");
                    }
                    else
                    {
                        sb.Append("Cannot capture");
                    }
    
                    Capability_List.Items.Add(sb.ToString());
                }
            }
    
            private ContactAvailability ConvertAvailabilityIntToEnum(int availability)
            {
                ContactAvailability returnValue = ContactAvailability.None;
                if (availability >= 0 && availability < 5000)
                {
                    returnValue = ContactAvailability.Free;
                }
                if (availability >= 5000 && availability < 6500)
                {
                    returnValue = ContactAvailability.FreeIdle;
                }
                if (availability >= 6500 && availability < 7500)
                {
                    returnValue = ContactAvailability.Busy;
                }
                if (availability >= 7500 && availability < 9500)
                {
                    returnValue = ContactAvailability.BusyIdle;
                }
                if (availability >= 9500 && availability < 12500)
                {
                    returnValue = ContactAvailability.DoNotDisturb;
                }
                if (availability >= 12500 && availability < 15500)
                {
                    returnValue = ContactAvailability.TemporarilyAway;
                }
                if (availability >= 15500 && availability < 18500)
                {
                    returnValue = ContactAvailability.Away;
                }
                if (availability >= 18500)
                {
                    returnValue = ContactAvailability.Offline;
                }
                return returnValue;
            }
    
            /// <summary>
            /// Set the content of the main window back to the original cached content.
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void Button_Click_1(object sender, RoutedEventArgs e)
            {
                Window win = (Window)this.Parent;
                win.Content = _ParentContent;
            }
    
            private void Button_Click_2(object sender, RoutedEventArgs e)
            {
                if (Subscribe_Button.Content.ToString().StartsWith("Stop"))
                {
                    _contactSubscription.Unsubscribe();
                    Subscribe_Button.Content = "Subscribe";
                }
                else
                {
                    _contactSubscription.Subscribe(ContactSubscriptionRefreshRate.High, _ContactInformationList);
                    Subscribe_Button.Content = "Stop Subscribing";
                }
    
            }
        }
    }

## See also

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

