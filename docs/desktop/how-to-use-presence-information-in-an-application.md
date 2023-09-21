---
title: 'How to: Use presence information in an application'
TOCTitle: 'How to: Use presence information in an application'
ms:assetid: f8abd1aa-f2a2-49de-b412-808636d9648a
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933257(v=office.15)
ms:contentKeyID: 50877403
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Use presence information in an application

Learn how to use the presence information published by a Lync 2013 contact to make an application more responsive to changes in a user’s willingness and ability to communicate in specific modes.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Presence overview<br />
Prerequisites<br />
Query for current contact conversation capabilities<br />
Start a conversation with modality selected by the user<br />
Code examples: Start a conversation<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Presence overview

If you have created a WPF or Silverlight page that uses Microsoft Lync 2013 Controls to start conversations with other users, you do not have to have the concepts in this topic. The Lync Controls implement these concepts to allow a new conversation to be started in an available modality if the intended user is willing and able to communicate. If you're creating a window that does not use Lync 2013 Controls, but makes calls into the Microsoft Lync 2013 API to obtain the presence of a user, this topic describes how to do this.

## Prerequisites

The prerequisites for using presence information in an application are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

The following topics explain the nature of enhanced presence, how a user’s communication willingness and capability are expressed in the Microsoft Lync 2013 API, and how to obtain both presence and communication capabilities using the Lync 2013 API.

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
<td><p>Introduces the concept of enhanced presence.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-get-the-enhanced-presence-of-a-lync-user.md">How to: Get the enhanced presence of a Lync user</a></p></td>
<td><p>Shows how to get the enhanced presence of a user.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-get-the-communication-modes-of-a-lync-user.md">How to: Get the communication modes of a Lync user</a></p></td>
<td><p>Shows how to discover the communication modes that a Microsoft Lync 2013 user is currently capable of.</p></td>
</tr>
</tbody>
</table>

## Query for current contact conversation capabilities

### To get the current capabilities of the contact

  - Call the [Contact.GetContactInformation](https://msdn.microsoft.com/library/jj294012\(v=office.15\)) method and pass the [ContactInformationType](https://msdn.microsoft.com/library/jj277212\(v=office.15\))**.CapabilityDetails** enumerator.
    
    A **List\<object\>** is returned.
    
        List<object> details = (List<object>)_contact.GetContactInformation(ContactInformationType.CapabilityDetails);

### To parse the capability details

1.  For each object in the list obtained in the previous procedure, cast an object to [Microsoft.Lync.Model.PresenceCapability](https://msdn.microsoft.com/library/jj277156\(v=office.15\)).

2.  Read the [PresenceCapability.Type](https://msdn.microsoft.com/library/jj267678\(v=office.15\)) property to see the modality type detailed in this **PresenceCapability** object.
    
    A radio button on the page UI is declared for each capability type.

3.  Read the [PresenceCapability.CanCapture](https://msdn.microsoft.com/library/jj277270\(v=office.15\)), [PresenceCapability.CanRender](https://msdn.microsoft.com/library/jj276353\(v=office.15\)), and [PresenceCapability.Availability](https://msdn.microsoft.com/library/jj276568\(v=office.15\)) properties.
    
    If the first two properties return true and the third property returns a value between 0 and 9500 ([ContactAvailability](https://msdn.microsoft.com/library/jj293978\(v=office.15\))**.BusyIdle**), enable the radio button that corresponds to the capability type.

The following example parses the capability details published by a contact and enables or disables radio buttons on the page UI according to the availability of a modality.

```csharp
            foreach (object capabilityObj in details)
            {
                PresenceCapability capability = (PresenceCapability)capabilityObj;

                switch (capability.Type)
                { 
                    case PresenceCapabilityType.InstantMessaging:
                        if (capability.CanCapture && capability.CanRender && capability.Availability < 9500)
                        {
                            IM_Radio.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                    case PresenceCapabilityType.Audio:
                        if (capability.CanRender && capability.CanCapture && capability.Availability < 9500)
                        {
                            Audio.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                    case PresenceCapabilityType.Video:
                        if (capability.CanCapture && capability.CanRender && capability.Availability < 9500)
                        {
                            Video.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                    case PresenceCapabilityType.AppShare:
                        if (capability.CanRender && capability.CanRender && capability.Availability < 9500)
                        {
                            Sharing.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                }

            }
```

### To respond to capability update publications

1.  Register an event handler for the [Contact.ContactInformationChanged](https://msdn.microsoft.com/library/jj275543\(v=office.15\)) event on the contact whose presence updates that you want.

2.  In the event handler, examine the [ContactInformationChangedEventArgs.ChangedContactInformation](https://msdn.microsoft.com/library/jj274485\(v=office.15\)) property to see what contact information type is updated.
    
    The property value returns a collection of [Microsoft.Lync.Model.ContactInformationType](https://msdn.microsoft.com/library/jj277212\(v=office.15\)) enumerators representing the contact information types that have been updated.

3.  If the collection obtained in the previous step contains the [ContactInformationType](https://msdn.microsoft.com/library/jj277212\(v=office.15\))**.CapabilityDetails**, the contact communication capabilities have changed. Update the radio buttons on the UI accordingly.
    
    The following example examines the collection of changed contact information types and updates radio buttons if the **CapabilityDetails** type is in the collection.
    
    ```csharp
                if (e.ChangedContactInformation.Contains(ContactInformationType.CapabilityDetails) )
                {
                    this.Dispatcher.Invoke(new NoParamDelegate(GetCapabilityDetails));
                }
    ```

## Start a conversation with modality selected by the user

### To start a new conversation

1.  Get an [Microsoft.Lync.Model.Extensibility.Automation](https://msdn.microsoft.com/library/jj293816\(v=office.15\)) object by calling the [LyncClient.GetAutomation](https://msdn.microsoft.com/library/jj266970\(v=office.15\)) method.

2.  Declare a new **List\<string\>** to hold a list of SIP addresses of users to invite to the conversation.
    
    In the sample, the SIP address that is passed in the page constructor is used.
    
    The following example declares a list of strings and adds a contact SIP address.
    
    ```csharp
                List<string> invitedParticpants = new List<string>();
                invitedParticpants.Add(_contact.Uri);
    ```

3.  Call the [Automation.BeginStartConversation](https://msdn.microsoft.com/library/jj276136\(v=office.15\)) method passing the selected modality and list of SIP addresses.
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>If you pass a modality type that is not published as available, the conversation window does not open. Instead, a selection list of contacts that are in the user’s contact list is displayed. To avoid this, always check the contact’s available modalities before you try to start a conversation.</p></td>
    </tr>
    </tbody>
    </table>
    
    ```csharp
    automation.BeginStartConversation(selectedModality, invitedParticpants,null, null, null);
    ```

## Code examples: Start a conversation

The following example declares a WPF page that shows the conversation modalities available for a given contact. The page lets the user select a modality and then start a conversation.

```xaml
<Page x:Class="ContactCapabilities.StartConversation"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
      mc:Ignorable="d" 
      d:DesignHeight="300" d:DesignWidth="340"
Title="StartConversation" Background="AntiqueWhite">

    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="90*"/>
            <RowDefinition Height="40"/>
        </Grid.RowDefinitions>
        <Grid Name="TopGrid" Grid.Row="0">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="138"/>
                <ColumnDefinition Width="200*"/>
            </Grid.ColumnDefinitions>
            <StackPanel Grid.Column="0" Margin="10,10,10,10">
                <RadioButton Name="IM_Radio" Content="IM" Foreground="CadetBlue" Grid.Column="0"  FlowDirection="LeftToRight"/>
                <RadioButton Name="Audio" Content="Audio" Foreground="CadetBlue" Grid.Column="0"/>
                <RadioButton Name="Video" Content="Video" Foreground="CadetBlue" Grid.Column="0"/>
                <RadioButton Name="Sharing" Content="Sharing" Foreground="CadetBlue" Grid.Column="0"/>
                <Button Name="Start" Content="Start Conversation" Click="Start_Click_1" Width="110" Margin="0,10,0,0"/>
            </StackPanel>
            <Image Name="ContactGuy" Grid.Column="1" Width="160" Height="180"/>
            
        </Grid>
        <Button Name="Close" Content="Back" Grid.Row="1" Width="80" Height="26" Click="Close_Click_1"/>
    </Grid>
</Page>
```

The following example takes the SIP address of a Lync 2013 user, gets a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) object, queries for current capabilities, enables appropriate radio buttons, and starts a conversation with the contact using the selected modality.

```csharp
using System.Collections.Generic;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Documents;
using System.Windows.Media.Imaging;
using Microsoft.Lync.Model;
using System.IO;
using Microsoft.Lync.Model.Extensibility;

namespace ContactCapabilities
{
    /// <summary>
    /// Interaction logic for StartConversation.xaml
    /// </summary>
    public partial class StartConversation : Page
    {
        LyncClient _LyncClient;
        Contact _contact;
        object _ParentContent;
        public StartConversation()
        {
            InitializeComponent();
        }
        public StartConversation(string SIPAddy, object parentContent)
        {
            InitializeComponent();
            _LyncClient = LyncClient.GetClient();

            //Get the Contact whose SIP address is passed in this constructor
            _contact = _LyncClient.ContactManager.GetContactByUri(SIPAddy);

            //Cache the original parent window content to be restored when this page closes
            _ParentContent = parentContent;

            //Register for event to be raised when contact capabilities change
            _contact.ContactInformationChanged +=_contact_ContactInformationChanged;

            //Get the current communication capabilities of the Contact
            GetCapabilityDetails();

            //Show the contact's photo
            DisplayContactPhoto();
        }

        /// <summary>
        /// raised when the contact publishes enhanced presence updates. This handler ignores all 
        /// publications except for updated communication capability details.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void _contact_ContactInformationChanged(object sender, ContactInformationChangedEventArgs e)
        {
            if (e.ChangedContactInformation.Contains(ContactInformationType.CapabilityDetails) )
            {
                this.Dispatcher.Invoke(new NoParamDelegate(GetCapabilityDetails));
            }
        }

        private delegate void NoParamDelegate();

        /// <summary>
        /// Gets the details of capability to communicate in all possible modalities and displays the
        /// details in the list.
        /// </summary>
        private void GetCapabilityDetails()
        {
            List<object> details = (List<object>)_contact.GetContactInformation(ContactInformationType.CapabilityDetails);
            IM_Radio.IsEnabled = false;
            Audio.IsEnabled = false;
            Video.IsEnabled = false;
            Sharing.IsEnabled = false;
            Start.IsEnabled = false;

            foreach (object capabilityObj in details)
            {
                PresenceCapability capability = (PresenceCapability)capabilityObj;

                switch (capability.Type)
                { 
                    case PresenceCapabilityType.InstantMessaging:
                        if (capability.CanCapture && capability.CanRender && capability.Availability < 9500)
                        {
                            IM_Radio.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                    case PresenceCapabilityType.Audio:
                        if (capability.CanRender && capability.CanCapture && capability.Availability < 9500)
                        {
                            Audio.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                    case PresenceCapabilityType.Video:
                        if (capability.CanCapture && capability.CanRender && capability.Availability < 9500)
                        {
                            Video.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                    case PresenceCapabilityType.AppShare:
                        if (capability.CanRender && capability.CanRender && capability.Availability < 9500)
                        {
                            Sharing.IsEnabled = true;
                            Start.IsEnabled = true;
                        }
                        break;
                }

            }
        }
 
        private void DisplayContactPhoto()
        {
            try
            {
                using (Stream photoStream = _contact.GetContactInformation(ContactInformationType.Photo) as Stream)
                {
                    if (photoStream != null)
                    {
                        System.Windows.Media.Imaging.BitmapImage bm = new BitmapImage();
                        bm.BeginInit();
                        bm.StreamSource = photoStream;
                        bm.EndInit();
                        ContactGuy.Source = bm;
                    }
                }
            }
            catch (InvalidStateException) { System.Diagnostics.Debug.WriteLine("Invalid State on get photo stream"); }
        }

        /// <summary>
        /// Close the page and restore original window content
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Close_Click_1(object sender, RoutedEventArgs e)
        {
            Window win = (Window)this.Parent;
            win.Content = _ParentContent;

        }

        /// <summary>
        /// Start a new conversation with the selected modality
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Start_Click_1(object sender, RoutedEventArgs e)
        {
            Microsoft.Lync.Model.Extensibility.Automation automation = LyncClient.GetAutomation();
            Microsoft.Lync.Model.Extensibility.AutomationModalities selectedModality = Microsoft.Lync.Model.Extensibility.AutomationModalities.Invalid;
            if (IM_Radio.IsChecked == true)
            {
                selectedModality = Microsoft.Lync.Model.Extensibility.AutomationModalities.InstantMessage;
            }
            else if (Audio.IsChecked == true)
            {
                selectedModality = Microsoft.Lync.Model.Extensibility.AutomationModalities.Audio;
            }
            else if (Video.IsChecked == true)
            {
                selectedModality = Microsoft.Lync.Model.Extensibility.AutomationModalities.Video;
            }
            else if (Sharing.IsChecked == true)
            {
                selectedModality = Microsoft.Lync.Model.Extensibility.AutomationModalities.ApplicationSharing;
            }
            List<string> invitedParticpants = new List<string>();
            invitedParticpants.Add(_contact.Uri);
            automation.BeginStartConversation(selectedModality, invitedParticpants,null, null, null);
        }
    }
}
```

## See also

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

