---
title: 'How to: Get the communication modes of a Lync user'
TOCTitle: 'How to: Get the communication modes of a Lync user'
ms:assetid: eb736ac7-84f1-4633-b3d3-1aa114e2c735
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933249(v=office.15)
ms:contentKeyID: 50877396
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Get the communication modes of a Lync user

Learn how use Microsoft Lync 2013 SDK to get the communication modalities that a Microsoft Lync 2013 user can use to participate in conversations.



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
Get the current communication capabilities of a Lync 2013 user<br />
Get updates to the communication capabilities of a Lync 2013 user<br />
Code examples: User capability page<br />
Next steps<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for getting the communication modes of a Lync user are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

Before you learn how to discover the modalities of a Lync 2013 user, you should be familiar with what a modality is and how to obtain a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) that represents a Lync 2013 user.

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
<td><p><a href="conversation-modalities.md">Conversation modalities</a></p></td>
<td><p>Introduces the concept of communication modes in Microsoft Lync 2013 conversations.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj933159(v=office.15)">How to: Search for a contact or distribution group in Lync SDK</a></p></td>
<td><p>Shows how to find a contact or distribution group by using the search capability of the Lync 2013 API.</p></td>
</tr>
</tbody>
</table>

## Get the current communication capabilities of a Lync 2013 user

When a user is not signed out of Lync 2013, the Lync 2013 client publishes communication capabilities in three formats on behalf of the user. These formats include the following:

  - A summary of the current capabilities.

  - A detailed list of each capability, including the ability to capture or render the modality.

  - An enumeration of the capabilities without details.

The following procedures show how to get the first two formats.

### To get the capability summary

1.  Get a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object by searching or obtaining the object from the user’s contact list.

2.  Call the [Contact.GetContactInformation](https://msdn.microsoft.com/en-us/library/jj294012\(v=office.15\)) method, passing the [ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\))**.CapabilityString** enumerator.
    
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
    <td><p>The summary string is not filled unless the communication capabilities of the user are in an exceptional state. For example, if the user is signed in to Lync on a mobile device, the user is IM capable but the capabilities summary is &quot;Mobile.&quot;</p></td>
    </tr>
    </tbody>
    </table>
    
    The following example calls the **GetContactInformation** method and adds the returned string value to a list on the WPF page.
    
    ```csharp
    Capability_List.Items.Add("Summary: " + _contact.GetContactInformation(ContactInformationType.CapabilityString));
    ```

### To get a detailed capability list

1.  Get a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object by searching or obtaining the object from the user’s contact list.

2.  Call the [Contact.GetContactInformation](https://msdn.microsoft.com/en-us/library/jj294012\(v=office.15\)) method, passing the [ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\))**.CapabilityDetails** enumerator.
    
    A **List\<System.Object\>** is returned.

3.  Iterate on the object list, casting each object to [Microsoft.Lync.Model.PresenceCapability](https://msdn.microsoft.com/en-us/library/jj277156\(v=office.15\)).

4.  For each **PresenceCapability** object, read the following properties:
    
      - [PresenceCapability.Type](https://msdn.microsoft.com/en-us/library/jj267678\(v=office.15\))
    
      - [PresenceCapability.Availability](https://msdn.microsoft.com/en-us/library/jj276568\(v=office.15\))
    
      - [PresenceCapability.CanCapture](https://msdn.microsoft.com/en-us/library/jj277270\(v=office.15\))
    
      - [PresenceCapability.CanRender](https://msdn.microsoft.com/en-us/library/jj276353\(v=office.15\))
    
    The following example iterates on the collection of **PresenceCapability** objects and reads each of the properties in the previous list. The property values are concatenated and added to a list on the WPF page UI.
    
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
    <td><p>The <a href="https://msdn.microsoft.com/en-us/library/jj276568(v=office.15)">PresenceCapability.Availability</a> property returns an integer value that corresponds to one of the enumerators of <a href="https://msdn.microsoft.com/en-us/library/jj293978(v=office.15)">Microsoft.Lync.Model.ContactAvailability</a>. This example calls a helper method that converts the integer to the correct enumerator.</p></td>
    </tr>
    </tbody>
    </table>
    
    ```csharp
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
    ```

## Get updates to the communication capabilities of a Lync 2013 user

When a user’s availability changes or the user signs in to Lync 2013 from a device with limited capabilities, the new capabilities of the user are automatically published and all subscribing users are notified of the new capabilities.

### To get communication capability updates

1.  Get a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object by searching or obtaining the object from the user’s contact list.

2.  Register for the [Contact.ContactInformationChanged](https://msdn.microsoft.com/en-us/library/jj275543\(v=office.15\)) event on the contact.

3.  In the event handler, verify that the [ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\))**.CapabilityString** or [Microsoft.Lync.Model.ContactInformationType](https://msdn.microsoft.com/en-us/library/jj277212\(v=office.15\))**.CapabilityDetails** have changed.

4.  If one of these contact information types has changed, get the new values and display them.
    
    ```csharp
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
    
            }
    ```
    
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
    <td><p>The <strong>GetCapabilityString</strong> helper method is listed in the example in the next section.</p></td>
    </tr>
    </tbody>
    </table>

## Code examples: User capability page

This example is a WPF window that hosts a [Microsoft.Lync.Controls.ContactList](https://msdn.microsoft.com/en-us/library/hh363781\(v=office.15\)) control. When a user clicks a contact in the list, a WPF page is created and set as the content of the main window. The WPF page displays the details of the selected contact’s ability to communicate on all Lync 2013 conversation modalities.

The following example declares a WPF window that hosts the contact list control.

```xaml
<Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls" x:Class="ContactCapabilities.MainWindow"
        Title="MainWindow" Height="616" Width="525">
    <Grid>

        <controls:ContactList 
            Name="myContactList"
            HorizontalAlignment="Left" 
            Margin="0,10,0,0" 
            VerticalAlignment="Top" 
            SelectedContactUrisChanged="ContactList_SelectedContactUrisChanged_1"/>

    </Grid>
</Window>
```

The following example provides the code-behind logic for the main window. When a user is selected from the contact list, a new WPF page is created and set as the content of the main window.

```csharp
using System;
using System.Windows;
using Microsoft.Lync.Model;

namespace ContactCapabilities
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        LyncClient _LyncClient;
        public MainWindow()
        {
            InitializeComponent();
            _LyncClient = LyncClient.GetClient();
        }

        private void ContactList_SelectedContactUrisChanged_1(object sender, EventArgs e)
        {
            object content = this.Content;
            foreach (String s in myContactList.SelectedContactUris)
            {
                Contact contact = _LyncClient.ContactManager.GetContactByUri(s);
                CapabilityPage cPage = new CapabilityPage(contact, this.Content);
                this.Content = cPage;
                break;
            }
        }
    }
}
```

The following example declares a WPF page that displays the communication modality capabilities of the selected user.

```xaml
<Page
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
      xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls" 
        x:Class="ContactCapabilities.CapabilityPage" 
      mc:Ignorable="d" 
      d:DesignHeight="300" d:DesignWidth="300"
Title="CapabilityPage">

    <Grid>

        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="10*"/>
            <ColumnDefinition Width="20*"/>
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
        <Button Content="Back" 
                Grid.Column="1"
                Grid.Row="2"
                HorizontalAlignment="Left" Margin="10,10,0,0" VerticalAlignment="Top" Width="75" 
                    Click="Button_Click_1"/>

    </Grid>
</Page>
```

The following example provides the code-behind logic for the previous WPF page, gets the current capabilities of the selected user, displays the capabilities in a list, and updates the list when the capabilities change.

```csharp
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
        object _ParentContent;
        public CapabilityPage()
        {
            InitializeComponent();
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
        /// republished by a user as they sign into more or less capable endpoints such as
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

        }

        private delegate void NoParamDelegate();

        private void GetCapabilityString()
        {
            Capability_List.Items.Clear();
            Capability_List.Items.Add("Summary: " + _contact.GetContactInformation(ContactInformationType.CapabilityString));
            GetCapabilityDetails();
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
    }
}
```

## Next steps

Now that you know how to discover the communication modalities of a Lync 2013 user, you can learn how to start a new conversation in the modalities that the user is capable of using.

  - [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md)

## See also

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

  - [Get started with Lync conversations](get-started-with-lync-conversations.md)

