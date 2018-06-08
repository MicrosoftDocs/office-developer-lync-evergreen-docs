---
title: 'How to: Update and publish user telephone numbers in Lync SDK'
TOCTitle: 'How to: Update and publish user telephone numbers'
ms:assetid: 078b5dd3-69f1-4c1e-bea8-91ba9bb54c12
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937252(v=office.15)
ms:contentKeyID: 50877068
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Update and publish user telephone numbers in Lync SDK

Learn how to update and publish a user’s telephone numbers by using Microsoft Lync 2013 SDK to build a custom UI.

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
Custom user telephone list administration UI<br />
Get the telephone number list<br />
Remove a telephone number from the user’s contact card<br />
Add a new telephone number and publish to the user’s contact card<br />
Change a telephone number in the user’s contact card<br />
Remove a telephone number from a user’s telephone list<br />
Code example: Update and publish telephone numbers<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Custom user telephone list administration UI

You can create a simple window that lets users update their telephone numbers when the Microsoft Lync 2013 client UI is suppressed. The window in the following example gets the telephone numbers for the four telephone types that users can publish to their contact cards. The window allows a user to remove a telephone number from the contact card, remove a telephone number from the telephone list, add a new telephone number for one of the four types, or change a telephone number.

**Figure 1. User phone list window**

![Screen shot of a phone manager sample](images/JJ933103.LyncClientSDK_UserPhoneNumberManagement(Office.15).jpg "Screen shot of a phone manager sample")

## Get the telephone number list

The list in the upper left corner of the window is fixed at four items. When a user has not entered a telephone number for a given type, only the type name appears in the list. Otherwise, both the type name and the telephone number appear.

### To get a user’s telephone numbers

1.  The following example gets the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) object by calling the static [LyncClient.GetClient](https://msdn.microsoft.com/en-us/library/jj278213\(v=office.15\)) method.
    
    ``` csharp
    _LyncClient = LyncClient.GetClient();
    ```

2.  The following example registers for event raised when a user adds, changes, or removes a telephone number.
    
    ``` csharp
    _LyncClient.Self.PhonesChanged += Self_PhonesChanged;
    ```

3.  Get a [Microsoft.Lync.Model.Phone](https://msdn.microsoft.com/en-us/library/jj275506\(v=office.15\)) object by calling the [Self.GetPhone](https://msdn.microsoft.com/en-us/library/jj266043\(v=office.15\)) method.  
    
    The following example gets the user’s home telephone number. Get the other three telephone numbers by passing each enumerator of the [Microsoft.Lync.Model.ContactEndpointType](https://msdn.microsoft.com/en-us/library/jj275544\(v=office.15\)) in successive calls to the [Self.GetPhone](https://msdn.microsoft.com/en-us/library/jj266043\(v=office.15\)) method.
    
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
    <td><p>A given telephone number might not exist at the time that you call the <strong>GetPhone</strong> method. In this case, you handle the <a href="https://msdn.microsoft.com/en-us/library/jj267360(v=office.15)">Microsoft.Lync.Model.ItemNotFoundException</a> exception and update the UI accordingly.</p></td>
    </tr>
    </tbody>
    </table>
    
    ``` csharp
                try
                {
                    phoneType = ContactEndpointType.HomePhone.ToString();
                    aPhone = _LyncClient.Self.GetPhone(ContactEndpointType.HomePhone);
                    myPhones.Add(ContactEndpointType.HomePhone.ToString(), aPhone);
                    myPhoneList_listbox.Items.Add(aPhone.Endpoint.Type.ToString() + " " + aPhone.Endpoint.Uri.ToString());
                }
                catch (ItemNotFoundException) 
                { 
                    //Add telephone type string as placeholder when no telephone number is
                    //present for the type
                    myPhoneList_listbox.Items.Add(phoneType); 
                }
    ```

## Remove a telephone number from the user’s contact card

If a user wants to remove a telephone number from the Lync 2013 contact card that other users see, the user selects a telephone number from the list shown in the Custom user telephone list administration UI section, clears the **Publish to contact card check** box, and then clicks the **Save edits** button in the window.

The following procedure describes how to clear the Boolean true value in the [Phone.Published](https://msdn.microsoft.com/en-us/library/jj294078\(v=office.15\)) property of the selected telephone number and then save the change to the telephone.

### To remove a telephone number from the user’s contact card

1.  Get the [Microsoft.Lync.Model.ContactEndpointType](https://msdn.microsoft.com/en-us/library/jj275544\(v=office.15\)) enumeration for the kind of the telephone number to remove from the contact card.  
    
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
    <td><p>If you have the <a href="https://msdn.microsoft.com/en-us/library/jj275506(v=office.15)">Microsoft.Lync.Model.Phone</a> object for the telephone number to remove, pass the <a href="https://msdn.microsoft.com/en-us/library/jj294021(v=office.15)">ContactEndpoint.Type</a> property in the first argument.</p></td>
    </tr>
    </tbody>
    </table>

2.  Call the [Self.BeginSetPhone](https://msdn.microsoft.com/en-us/library/jj293545\(v=office.15\)) method and pass the contact endpoint type enumerator, the current telephone number as a string, a Boolean false value, the callback method or lambda expression, and the asynchronous state value or null. The Boolean argument is passed as false to indicate that the telephone number is to be removed from the contact card.
    
    The following example removes a telephone number from the user’s contact card.
    
    ``` csharp
                    if (_LyncClient.Self.CanSetPhone(selectedPhone.Endpoint.Type))
                    {
                        _LyncClient.Self.BeginSetPhone(
                            selectedPhone.Endpoint.Type,
                            Edit_textbox.Text,
                            false,
                            (ar) =>
                            {
                                _LyncClient.Self.EndSetPhone(ar);
                            },
                            null);
                    }
    ```

## Add a new telephone number and publish to the user’s contact card

A user might not have associated a telephone number to one of the four telephone endpoint types that can be published on the contact card. If the user wants to add a missing telephone number, you code the following procedure to run in your UI when the user types a telephone number and selects the telephone endpoint type to associate.

Adding the telephone number and publishing it on the contact card is performed by making a single method call and passing the correct argument values.

### To add a telephone number

  - Call the [Self.BeginSetPhone](https://msdn.microsoft.com/en-us/library/jj293545\(v=office.15\)) method and pass the endpoint type in the first argument, the new telephone number to associate with the type in the second argument, a **true** value in the third to specify the telephone number is to be published.
    
    The following example publishes a new telephone number to the user’s contact card.
    
    ``` csharp
                    if (_LyncClient.Self.CanSetPhone(selectedPhone.Endpoint.Type))
                    {
                        _LyncClient.Self.BeginSetPhone(
                            selectedPhone.Endpoint.Type,
                            Edit_textbox.Text,
                            true,
                            (ar) =>
                            {
                                _LyncClient.Self.EndSetPhone(ar);
                            },
                            null);
                    }
    ```
    
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
    <td><p>You can add a new telephone number without publishing it to the contact card by setting the third argument to <strong>false</strong>.</p></td>
    </tr>
    </tbody>
    </table>

## Change a telephone number in the user’s contact card

If a user has already added a telephone number to the telephone number list but wants to change the number, this operation is complete with a single call to the [Self.BeginSetPhone](https://msdn.microsoft.com/en-us/library/jj293545\(v=office.15\)) method.

### To change an existing telephone number

  - 
    
    The following example publishes the selected endpoint type, the contents of the telephone number text box, and the current **IsChecked** state of the **Publish to contact card** check box.
    
    ``` 
                    if (_LyncClient.Self.CanSetPhone(selectedPhone.Endpoint.Type))
                    {
                        _LyncClient.Self.BeginSetPhone(
                            selectedPhone.Endpoint.Type,
                            Edit_textbox.Text,
                            (bool)Publish_check.IsChecked,
                            (ar) =>
                            {
                                _LyncClient.Self.EndSetPhone(ar);
                            },
                            null);
                    }
    ```

## Remove a telephone number from a user’s telephone list

A user can clear the telephone number that is associated to a telephone type. If the telephone number was published to the contact card, it is also removed from the contact card.

### To remove an existing telephone number

  - 
    
    The following example clears a telephone number from the specified telephone number type.
    
    ``` 
                    _LyncClient.Self.BeginRemovePhone(
                        selectedPhone.Endpoint.Type,
                        (ar) => { _LyncClient.Self.EndRemovePhone(ar); },
                        null);
    ```

## Code example: Update and publish telephone numbers

The following example declares the window shown in figure 1.

``` xaml
<Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls" 
    x:Class="TelephoneNumberAdmin.MainWindow"
        Title="User Phone List Manager" Height="350" Width="525" Loaded="MainWindow_Loaded_1">
    <Grid>
<Grid.RowDefinitions>
    <RowDefinition Height="10"/>
    <RowDefinition Height="190"/>
    <RowDefinition Height="200*"/>
</Grid.RowDefinitions>
        <StackPanel Grid.Row="1" Margin="0,0,258,0">
            <ListBox HorizontalAlignment="Left" Height="189" Width="251" Name="myPhoneList_listbox" 
                     SelectionChanged="myPhoneList_listbox_SelectionChanged_1"/>
        </StackPanel>
        <StackPanel Grid.Row="1" Margin="258,0,0,0">
            <TextBox Name ="Edit_textbox" HorizontalAlignment="Left" Height="23" TextWrapping="Wrap" Text="TextBox" Width="251"/>
            <CheckBox Name="Publish_check" Content="Publish to contact card" HorizontalAlignment="Left" Width="251"/>
            <Button Name="SaveEdits_button" Height="20" Content="Save edits" HorizontalAlignment="Left" 
                    Width="251" Margin="0,6,0,0" Click="SaveEdits_button_Click_1"/>
            <Button Name="RemovePhone_button" Content="Remove phone" HorizontalAlignment="Left" 
                    Width="251" Margin="0,6,0,0" Click="RemovePhone_button_Click_1"/>
        </StackPanel>
        <controls:MyStatusArea HorizontalAlignment="Center" Margin="1,1,0,0" VerticalAlignment="Center" Grid.Row="2"/>

    </Grid>
</Window>
```

The following example declares the application logic layer of the window in figure 1.

``` csharp
using System;
using System.Collections.Generic;
using System.Windows;
using System.Windows.Controls;
using Microsoft.Lync.Model;

namespace TelephoneNumberAdmin
{

    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        LyncClient _LyncClient;
        Dictionary<string, Phone> myPhones = new Dictionary<string, Phone>();

        public MainWindow()
        {
            InitializeComponent();
        }

        private void MainWindow_Loaded_1(object sender, RoutedEventArgs e)
        {
            _LyncClient = LyncClient.GetClient();

            //Register for event raised when user adds, changes, or removes a telephone number
            _LyncClient.Self.PhonesChanged += Self_PhonesChanged;
            if (_LyncClient.State == ClientState.SignedIn)
            {
                //Load UI list with user self-user telephone numbers
                LoadPhones();
            }
        }

        private delegate void CallMethodDelegate();

        /// <summary>
        /// Loads UI listbox with self-user telephone numbers
        /// </summary>
        private void LoadPhones()
        {
            Phone aPhone;
            myPhones.Clear();
            myPhoneList_listbox.Items.Clear();
            string phoneType = string.Empty;
            try
            {
                phoneType = ContactEndpointType.HomePhone.ToString();
                aPhone = _LyncClient.Self.GetPhone(ContactEndpointType.HomePhone);
                myPhones.Add(ContactEndpointType.HomePhone.ToString(), aPhone);
                myPhoneList_listbox.Items.Add(aPhone.Endpoint.Type.ToString() + " " + aPhone.Endpoint.Uri.ToString());
            }
            catch (ItemNotFoundException) 
            { 
                //Add telephone type string as placeholder when no telephone number is
                //present for the type
                myPhoneList_listbox.Items.Add(phoneType); 
            }

            try
            {
                phoneType = ContactEndpointType.MobilePhone.ToString();
                aPhone = _LyncClient.Self.GetPhone(ContactEndpointType.MobilePhone);
                myPhones.Add(ContactEndpointType.MobilePhone.ToString(), aPhone);
                myPhoneList_listbox.Items.Add(aPhone.Endpoint.Type.ToString() + " " + aPhone.Endpoint.Uri.ToString());
            }
            catch (ItemNotFoundException) 
            { 
                //Add telephone type string as placeholder when no telephone number is
                //present for the type
                myPhoneList_listbox.Items.Add(phoneType); 
            }

            try
            {
                phoneType = ContactEndpointType.WorkPhone.ToString();
                aPhone = _LyncClient.Self.GetPhone(ContactEndpointType.WorkPhone);
                myPhones.Add(ContactEndpointType.WorkPhone.ToString(), aPhone);
                myPhoneList_listbox.Items.Add(aPhone.Endpoint.Type.ToString() + " " + aPhone.Endpoint.Uri.ToString());
            }
            catch (ItemNotFoundException) 
            { 
                //Add telephone type string as placeholder when no telephone number is
                //present for the type
                myPhoneList_listbox.Items.Add(phoneType); 
            }

            try
            {
                phoneType = ContactEndpointType.OtherPhone.ToString();
                aPhone = _LyncClient.Self.GetPhone(ContactEndpointType.OtherPhone);
                myPhones.Add(ContactEndpointType.OtherPhone.ToString(), aPhone);
                myPhoneList_listbox.Items.Add(aPhone.Endpoint.Type.ToString() + " " + aPhone.Endpoint.Uri.ToString());
            }
            catch (ItemNotFoundException) 
            { 
                //Add telephone type string as placeholder when no telephone number is
                //present for the type
                myPhoneList_listbox.Items.Add(phoneType); 
            }
        }

        void Self_PhonesChanged(object sender, PhonesChangedEventArgs e)
        {
            //Reload telephone numbers in list
            this.Dispatcher.Invoke(new CallMethodDelegate(LoadPhones));
        }

        private void myPhoneList_listbox_SelectionChanged_1(object sender, SelectionChangedEventArgs e)
        {
            if (myPhoneList_listbox.SelectedItem != null)
            {
                try
                {
                    Phone selectedPhone = (Phone)GetSelectedPhone(myPhoneList_listbox.SelectedItem.ToString());
                    Publish_check.IsChecked = selectedPhone.Published;
                    Edit_textbox.Text = selectedPhone.Endpoint.Uri;
                }
                catch (InvalidCastException)
                {
                    Edit_textbox.Text = string.Empty;
                    Publish_check.IsChecked = false;
                }
            }
        }

        private void SaveEdits_button_Click_1(object sender, RoutedEventArgs e)
        {
            //(bool)Publish_check.IsChecked
            object selectedPhoneObject = GetSelectedPhone(myPhoneList_listbox.SelectedItem.ToString());
            if (selectedPhoneObject.GetType().Name == "Phone")
            {
                Phone selectedPhone = selectedPhoneObject as Phone;
                if (_LyncClient.Self.CanSetPhone(selectedPhone.Endpoint.Type))
                {
                    _LyncClient.Self.BeginSetPhone(
                        selectedPhone.Endpoint.Type,
                        Edit_textbox.Text,
                        (bool)Publish_check.IsChecked,
                        (ar) =>
                        {
                            _LyncClient.Self.EndSetPhone(ar);
                        },
                        null);
                }
            }
            else if (selectedPhoneObject.GetType().Name == "ContactEndpointType")
            { 
                ContactEndpointType selectedPhoneType = (ContactEndpointType)selectedPhoneObject;
                if (_LyncClient.Self.CanSetPhone(selectedPhoneType))
                {
                    _LyncClient.Self.BeginSetPhone(selectedPhoneType,
                    Edit_textbox.Text,
                    (bool)Publish_check.IsChecked,
                    (ar) => 
                    {
                        _LyncClient.Self.EndSetPhone(ar); 
                    },
                    null);
                }

            }
        }

        private Object GetSelectedPhone(string selectedString)
        {
            Object returnValue = null;
            string fullText = myPhoneList_listbox.SelectedItem.ToString();
            string typePortion;

            //If selected item is type + telephone number, there is a space
            //between the two elements.
            if (fullText.IndexOf(" ") > 0)
            {
                typePortion = fullText.Substring(0, fullText.IndexOf(" "));
                Phone selectedPhone;

                if (myPhones.TryGetValue(typePortion, out selectedPhone))
                {
                    returnValue = selectedPhone;
                }
            }
            //Otherwise there is only a type
            else
            {
                typePortion = fullText;
                switch (typePortion)
                {
                    case "HomePhone":
                        returnValue = ContactEndpointType.HomePhone;
                        break;
                    case "MobilePhone":
                        returnValue = ContactEndpointType.MobilePhone;
                        break;
                    case "WorkPhone":
                        returnValue = ContactEndpointType.WorkPhone;
                        break;
                    case "OtherPhone":
                        returnValue = ContactEndpointType.OtherPhone;
                        break;
                }
            }

            return returnValue;
        }

        private void RemovePhone_button_Click_1(object sender, RoutedEventArgs e)
        {
            try
            {
                Phone selectedPhone = (Phone)GetSelectedPhone(myPhoneList_listbox.SelectedItem.ToString());
                _LyncClient.Self.BeginRemovePhone(
                    selectedPhone.Endpoint.Type,
                    (ar) => { _LyncClient.Self.EndRemovePhone(ar); },
                    null);
            }
            catch (InvalidCastException) { }
        }

    }
}
```

## See also

  - [What you can do in Lync SDK](what-you-can-do-in-lync-sdk.md)

  - [User telephone number administration](user-telephone-number-administration.md)

