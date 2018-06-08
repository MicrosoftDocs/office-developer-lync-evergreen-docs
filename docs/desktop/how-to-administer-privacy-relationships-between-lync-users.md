---
title: 'How to: Administer privacy relationships between Lync users'
TOCTitle: 'How to: Administer privacy relationships between Lync users'
ms:assetid: 52067756-a8a5-4a81-ad3e-b43d7913edb7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933049(v=office.15)
ms:contentKeyID: 50877177
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Administer privacy relationships between Lync users

Learn how to set the privacy relationship between the signed-in Lync 2013 user and another Lync user by calling a single method in the Microsoft Lync 2013 API.

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
Set a privacy relationship with a Lync contact<br />
Sample application: Privacy Relationship Manager<br />
Code examples: Set a privacy relationship<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for administering privacy relationships between Lync users are as follows:

  - User must be signed in to Lync. For information, see [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md).

  - Understand privacy relationships. For information, see [Contact privacy relationship administration](contact-privacy-relationship-administration.md).

## Set a privacy relationship with a Lync contact

### To set a privacy relationship

1.  Get the SIP URI strings of Lync users whom are selected in the UI contact list.
    
    ```csharp
            /// <summary>
            /// Sets the selected privacy relationship level for all selected contacts
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void SetRelationship_Button_Click(object sender, RoutedEventArgs e)
            {
                //iterate on the collection of selected contact Uri strings from the 
                //UI ContactList control.
                foreach (string contactURI in myContactList.SelectedContactUris)
                {
                    SetPrivacyLevelOnAContact(contactURI);
                }
     
            }
    ```

2.  Get a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object by calling the [ContactManager.GetContactByUri](https://msdn.microsoft.com/en-us/library/jj274481\(v=office.15\)) method.
    
    The following example gets a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object from the SIP URI of a selected user.
    
                    //Get a contact object that represents the selected contact Uri
                    Contact selectedContact = LyncClient.GetClient().ContactManager.GetContactByUri(contactURI);

3.  Check to see whether the state of the **Contact** object lets you set the privacy relationship by calling the [Contact.CanChangeSetting](https://msdn.microsoft.com/en-us/library/jj294134\(v=office.15\)) method.

4.  Set the privacy relationship rule for the selected contact.
    
    The following example sets the privacy relationship rule by calling the [Contact.BeginChangeSetting](https://msdn.microsoft.com/en-us/library/jj275533\(v=office.15\)) method.
    
    ```csharp
            /// <summary>
            /// Sets the privacy relationship for a Lync user specified by URI
            /// </summary>
            /// <param name="contactURI">string. The SIP URI of a Lync user</param>
            private void SetPrivacyLevelOnAContact(string contactURI)
            {
                //Get a contact object that represents the selected contact Uri
                Contact selectedContact = LyncClient.GetClient().ContactManager.GetContactByUri(contactURI);
     
                //Check to see if the contact object state allows you to set the privacy level
                if (selectedContact.CanChangeSetting(ContactSetting.AccessLevel))
                {
                    //Set the privacy relationship contact setting
                    selectedContact.BeginChangeSetting(
                        ContactSetting.AccessLevel,
                        GetRadioChoice(),
                        (ar) =>
                        {
                            selectedContact.EndChangeSetting(ar);
                        },
                        null);
                }
            }
    ```

## Sample application: Privacy Relationship Manager

The following example shows a sample application that lets a signed-in user set privacy relationships for any user in his or her contact list. The form contains a [Microsoft.Lync.Controls.PresenceIndicator](https://msdn.microsoft.com/en-us/library/hh345947\(v=office.15\)) control to display the signed-in user’s presence and picture, a [Microsoft.Lync.Controls.ContactList](https://msdn.microsoft.com/en-us/library/hh363781\(v=office.15\)) control to show the user’s contact list, a set of radio buttons that let the user select a privacy relationship rule to set, and a command button to set the selected privacy relationship for all contacts selected in the list.

**Figure 1. Privacy relationship manager**

![Screen shot of privacy relationship manager UI](images/JJ933203.LyncClientSDK_PrivacyRelationshipManagement(Office.15).jpg "Screen shot of privacy relationship manager UI")

## Code examples: Set a privacy relationship

The sample application shown in figure 1 is a WPF form with two Lync Controls: a ContactList control and a PresenceIndicator control. In addition, the UI shows a set of radio buttons representing privacy relationship rules, and a command button. The signed-in user expands a group on the contact list, selects one or more contacts, and select a privacy relationship rule. The event on the command button iterates on the selected contact SIP URI strings. For each string, it calls a helper method that sets the privacy relationship for the user represented by the SIP URI.

The following example declares the UI shown in figure 1.

```xaml
<Window x:Class="PrivacyRelationship.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
    Title="Privacy Relationship Manager" 
        Height="Auto" 
        Width="Auto" 
        mc:Ignorable="d" 
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
        d:DesignHeight="353" d:DesignWidth="602" SizeToContent="WidthAndHeight">
    <Grid>
        <StackPanel Orientation="Horizontal" HorizontalAlignment="Center" VerticalAlignment="Center" Margin="12,12,408,142">
            <!-- 
                Show the presence indicator. Hover over the icon to see the contact card.
                Set Source to a valid SIP URI in your organization. 
            -->
            <controls:PresenceIndicator 
                x:Name="Presence" 
                PhotoDisplayMode="Large" 
                />
            <!-- Use the DisplayName property from PresenceIndicator to show the user's name -->
            <TextBlock 
                Text="{Binding DisplayName, ElementName=Presence}" 
                Margin="4,0,0,0" 
                VerticalAlignment="Center"
                />
        </StackPanel>
        <StackPanel Height="281" HorizontalAlignment="Left" Margin="187,12,0,0" Name="stackPanel1" VerticalAlignment="Top" Width="200">
            <controls:ContactList 
                Name="myContactList" 
                GroupViewBySetting="Relationship" 
                ContactLayoutView="OneLine" />
        </StackPanel>
        <StackPanel Height="100" HorizontalAlignment="Left" Margin="411,38,0,0" Name="stackPanel2" VerticalAlignment="Top" Width="124">
            <RadioButton Content="Friends and family" Height="16" Name="FriendsAndFamily_radio" />
            <RadioButton Content="Workgroup" Height="16" Name="Workgroup_radio" />
            <RadioButton Content="Collegues" Height="16" Name="Collegues_radio" />
            <RadioButton Content="External contacts" Height="16" Name="ExternalContacts_radio" />
            <RadioButton Content="Blocked" Height="16" Name="Blocked_radio" />
            <RadioButton Content="Default" Height="16" Name="Default_radio" />
        </StackPanel>
        <Button 
            Content="Set relationship" 
            Height="23" 
            HorizontalAlignment="Left" 
            Margin="411,144,0,0" 
            Name="SetRelationship_Button" 
            VerticalAlignment="Top" 
            Width="100" 
            Click="SetRelationship_Button_Click"/>
    </Grid>
 
</Window>
```

The following example declares a partial class for the UI shown in figure 1.

```csharp
using System;
using System.Windows;
using Microsoft.Lync.Model;
 
namespace PrivacyRelationship
{
    /// <summary>
    /// Interaction logic for Window1.xaml
    /// </summary>
    public partial class Window1 : Window
    {
        LyncClient _lyncClient;
        public Window1()
        {
            InitializeComponent();
            try
            {
                _lyncClient = LyncClient.GetClient();

            }
            catch (ClientNotFoundException) { MessageBox.Show("Lync is not running"); }
            catch (LyncClientException lce) { MessageBox.Show("Lync Client exception on GetClient " + lce.Message); }
        }
 
        /// <summary>
        /// Sets the selected privacy relationship level for all selected contacts
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SetRelationship_Button_Click(object sender, RoutedEventArgs e)
        {
            //iterate on the collection of selected contact Uri strings from the 
            //UI ContactList control.
            foreach (string contactURI in myContactList.SelectedContactUris)
            {
                SetPrivacyLevelOnAContact(contactURI);
            }
 
        }
 
        /// <summary>
        /// Sets the privacy relationship for a Lync user specified by URI
        /// </summary>
        /// <param name="contactURI">string. The SIP URI of a Lync user</param>
        private void SetPrivacyLevelOnAContact(string contactURI)
        {
            //Get a contact object that represents the selected contact Uri
            Contact selectedContact = _lyncClient.ContactManager.GetContactByUri(contactURI);
 
            //Check to see if the contact object state allows you to set the privacy level
            if (selectedContact.CanChangeSetting(ContactSetting.AccessLevel))
            {
                //Set the privacy relationship contact setting
                selectedContact.BeginChangeSetting(
                    ContactSetting.AccessLevel,
                    GetRadioChoice(),
                    (ar) =>
                    {
                        selectedContact.EndChangeSetting(ar);
                    },
                    null);
            }
        }
        /// <summary>
        /// Return an enumertor of AccessLevel corresponding to the radio button selected
        /// </summary>
        /// <returns></returns>
        private AccessLevel GetRadioChoice()
        {
            if (FriendsAndFamily_radio.IsChecked == true)
            {
                return AccessLevel.Friends;
            }
            if (Workgroup_radio.IsChecked == true)
            {
                return AccessLevel.Workgroup;
            }
            if (Collegues_radio.IsChecked == true)
            {
                return AccessLevel.Colleague;
            }
            if (ExternalContacts_radio.IsChecked == true)
            {
                return AccessLevel.External;
            }
            if (Blocked_radio.IsChecked == true)
            {
                return AccessLevel.Blocked;
            }
            if (Default_radio.IsChecked == true)
            {
                return AccessLevel.Default;
            }
            return AccessLevel.Invalid;
 
        }
        private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            //Set the PresenceIndicator source to the signed-in user URI
            Presence.Source = _lyncClient.Self.Contact.Uri;
         }
    }
}
```

## See also

  - [What you can do in Lync SDK](what-you-can-do-in-lync-sdk.md)

  - [How to: Publish enhanced presence information](how-to-publish-enhanced-presence-information.md)

  - [How to: Subscribe to enhanced presence content](how-to-subscribe-to-enhanced-presence-content.md)

