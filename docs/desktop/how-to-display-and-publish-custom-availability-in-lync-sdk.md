---
title: 'How to: Display and publish custom availability in Lync SDK'
TOCTitle: 'How to: Display and publish custom availability'
ms:assetid: 469d0d64-620d-4d70-b719-53c2ccb7b4bb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937312(v=office.15)
ms:contentKeyID: 50877144
ms.date: 02/11/2016
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
- xml
---

# How to: Display and publish custom availability in Lync SDK

Learn how to display and publish custom Microsoft Lync 2013 presence in an application by using Microsoft Lync 2013 SDK.

**Last modified:** December 07, 2015

***Applies to:** Lync 2013 | Lync Server 2013*

**In this article**  
Prerequisites  
Custom user activity window  
Get custom presence states  
Publish a custom presence state  
Code examples: Custom user activity window  
Additional resources  

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for displaying and publishing custom availability are as follows:

  - An administrator must configure custom presence states on the Microsoft Lync Server 2013 computer that a user signs in to from your application. For more information, see [Configuring Custom Presence States](http://technet.microsoft.com/en-us/library/gg398997.aspx).

  - The Microsoft Lync 2013 client must be signed in.

## Custom user activity window

Figure 1 shows a sample application window that lets a user see current presence and custom presence activity. The list on the right side shows the possible custom presence states and the **Publish** button publishes the custom presence selected by a user.

**Figure 1. Custom user activity window**

  
![Screen shot of sample that shows custom activity](images/JJ937312.LyncClientSDK_CustomActivityStrings(Office.15).jpg "Screen shot of sample that shows custom activity")

## Get custom presence states

The current localized presence state is the last state that was published by a contact.

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
<td><p>The logic in this procedure is used for any <a href="https://msdn.microsoft.com/en-us/library/hh365096(v=office.15)">Microsoft.Lync.Model.Contact</a> object. The contact can be the signed-in user <strong>Self</strong> contact, any contact in the user’s contact list, or any contact found by a contact search.</p></td>
</tr>
</tbody>
</table>

### To display the user’s current localized or customized presence state

1.  To get the current state, call the [Contact.GetContactInformation](https://msdn.microsoft.com/en-us/library/hh348218\(v=office.15\)) method on the [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/hh365096\(v=office.15\)) object value of the [Self.Contact](https://msdn.microsoft.com/en-us/library/hh365190\(v=office.15\)) property, passing the [ContactInformationType.CustomActivity](https://msdn.microsoft.com/en-us/library/gg279606\(v=office.15\)) enumerator.
    
    ```csharp
                //Get list of all LocaleString objects - list encapsulates the customized and localized activity strings
                List<object> states = (List<object>)_LyncClient.Self.
                    Contact.GetContactInformation(ContactInformationType.CustomActivity);
    ```
    
    A list of [Microsoft.Lync.Model.LocaleString](https://msdn.microsoft.com/en-us/library/hh365116\(v=office.15\)) objects is returned as **system.object**.

2.  Iterate on the list of objects, casting each object to type [Microsoft.Lync.Model.LocaleString](https://msdn.microsoft.com/en-us/library/hh365116\(v=office.15\)).
    
      - Inside of the foreach loop, compare the [LocaleString.LocaleId](https://msdn.microsoft.com/en-us/library/hh379982\(v=office.15\)) property value to the current UI culture LCID. If they match, display the [LocaleString.Value](https://msdn.microsoft.com/en-us/library/hh348182\(v=office.15\)) property as the current custom activity in the user’s language.
        
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
        <td><p>If activity strings have not been localized for a particular culture, you should define a default locale ID value to display. For example, in North America, locale ID 1033 is frequently used. If the signed-in user has selected 1036 (French, France) as the UI culture, but no localized strings have been configured on the server for 1036, you would display strings for 1033.</p></td>
        </tr>
        </tbody>
        </table>
        
        The following example compares the LCID of the current culture to the LCID of a custom presence activity. If they match, the custom presence activity is displayed. If no match is found, the **LocaleString** collection is search for a default LCID. The **CultureInfo.DefaultThreadCurrentUICulture** property is available in the .NET Framework 4.5.
        
        The following example iterates on the custom presence objects and casts the objects to **LocaleString**.
        
        ```csharp
                    //Iterate on the locale strings
                    Boolean localizeStringsFound = false;
                    foreach (object o in states)
                    {
        
                        LocaleString lString = (LocaleString)o;
                        //If the LCID of a Locale string matches the LCID of the current UI culture, display
                        //the custom string
                        if (System.Globalization.CultureInfo.CurrentUICulture.LCID == lString.LocaleId)
                        {
                            Customactivity_Label.Content = lString.Value;
                            localizeStringsFound = true;
                            break;
                        }
                    }
                    if (localizeStringsFound == false)
                    {
                        foreach (object o in states)
                        {
        
                            LocaleString lString = (LocaleString)o;
                            //If the lcid of a Locale string matches the lcid of the current UI culture, display
                            //the custom string
                            if (System.Globalization.CultureInfo.DefaultThreadCurrentUICulture.LCID == lString.LocaleId)
                            {
                                Customactivity_Label.Content = lString.Value;
                                break;
                            }
                        }
        
                    }
        ```

## Publish a custom presence state

You can only publish custom presence states that have been configured on the Microsoft Lync Server 2013 computer on which a user is signed in. Before publishing one of these custom presence states, query for the available states and then publish the ID of the desired state.

A Lync Server 2013 computer can be configured to have custom presence states in multiple languages. When you query for the collection of custom presence states, you specify a culture LCID. Only custom presence states that belong to the specified culture are returned.

### To query for publishable custom presence states

1.  Get the current UI culture.
    
    The following example gets the current culture.
    
    ```csharp
    int currentLCID = System.Globalization.CultureInfo.CurrentUICulture.LCID;
    ```

2.  Get the collection of publishable presence stated for the specified culture.
    
    ```csharp
    IList<CustomAvailabilityState> customStates = _LyncClient.Self.GetPublishableCustomAvailabilityStates(currentLCID);
    ```

3.  Get the custom presence state ID and activity string for each custom presence state in the collection.
    
        foreach (CustomAvailabilityState customState in customStates)
        {
            CustomAvailability_List.Items.Add(customState.Id.ToString() + " " + customState.Activity + " " + customState.Availability.ToString());
        }

### To publish a custom presence state

1.  Declare a Dictionary\<PublishableContactInformationType, object\> to hold the information type and value to be published.
    
    ```csharp
    Dictionary<PublishableContactInformationType, object> stuffToPublish = new Dictionary<PublishableContactInformationType,object>();
    ```

2.  Add an item to the dictionary where the key is [PublishableContactInformationType](https://msdn.microsoft.com/en-us/library/hh348070\(v=office.15\))**.CustomActivityId** and the value is the ID of the custom presence state to be published.
    
    ```csharp
    stuffToPublish.Add(PublishableContactInformationType.CustomActivityId, _SelectedCustomAvailabilityId);
    ```

3.  Publish the custom presence state by calling the [Self.BeginPublishContactInformation](https://msdn.microsoft.com/en-us/library/hh380629\(v=office.15\)) method.
    
    The following example publishes the selected custom presence. If an invalid custom presence ID is used, the [Microsoft.Lync.Model.ItemNotFoundException](https://msdn.microsoft.com/en-us/library/hh379971\(v=office.15\)) is raised.
    
    ```csharp
                try
                {
                    _LyncClient.Self.BeginPublishContactInformation(
                        stuffToPublish,
                        (ar) =>
                        {
                                _LyncClient.Self.EndPublishContactInformation(ar);
                        },
                        null);
                }
                catch (ItemNotFoundException) { MessageBox.Show(_SelectedCustomAvailabilityId.ToString() + " Item not found"); }
    ```

## Code examples: Custom user activity window

The following code declares the window show in figure 1.

```xaml
<Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls" 
            x:Class="CustomAvailabilityStates.MainWindow"
        Title="Custom user activity" Height="350" Width="639" Loaded="MainWindow_Loaded_1">
    <Grid>
<Grid.RowDefinitions>
        <RowDefinition Height="20"/>
        <RowDefinition Height="120"/>
         <RowDefinition Height="100*"/>
</Grid.RowDefinitions>
        <Label Content="Custom Presence" Height="120" VerticalAlignment="Top" Grid.Row="0" Margin="270,0,0,0"/>
        <StackPanel Grid.Row="1" Width="108" HorizontalAlignment="Left" Margin="1,0,0,0">
            <Label Content="Availability" HorizontalAlignment="Left"/>
            <Label Content="Activity"/>
            <Label Content="Activity Id"/>
            <Label Content="Custom activity"/>
        </StackPanel>
        <StackPanel Grid.Row="1" Width="176" HorizontalAlignment="Left" Margin="100,0,0,0">
            <Label Name="Availability_Label" Content="Availability" HorizontalAlignment="Left"/>
            <Label Name="Activity_Label" Content="Activity"/>
            <Label Name="ActivityId_Label"  Content="Activity Id"/>
            <Label Name="Customactivity_Label" Content="Custom activity"/>

        </StackPanel>
        <controls:MyStatusArea HorizontalAlignment="Center" Margin="1,51,0,0" VerticalAlignment="Top" 
                               Grid.Row="2"/>
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="276,0,0,0" VerticalAlignment="Top" 
                    Width="337" Orientation="Horizontal" Grid.Row="1">
            <ListBox x:Name="CustomAvailability_List" HorizontalAlignment="Left" Height="118" Width="258" 
                     SelectionChanged="CustomAvailability_List_SelectionChanged_1" Margin="0,0"/>
            <Button x:Name="Publish_button" Content="Publish" HorizontalAlignment="Left" Margin="5,50" 
                    VerticalAlignment="Center" Width="70" Click="Publish_button_Click_1"/>
        </StackPanel>
    </Grid>
</Window>
```

The following example declares interaction logic for MainWindow.xaml.

```csharp
using System.Windows;
using Microsoft.Lync.Model;
using System.Collections.Generic;
using System;
using System.Text;
namespace CustomAvailabilityStates
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        LyncClient _LyncClient;
        int _SelectedCustomAvailabilityId = 0;
        public MainWindow()
        {
            InitializeComponent();
        }

        private delegate void DisplayCurrentStateDelegate();

        /// <summary>
        /// Display the availability, activity, activity ID, and custom activity 
        /// of the currently signed in user.
        /// </summary>
        private void DisplayCurrentState()
        {
            //Current availability
            Availability_Label.Content = ((ContactAvailability)_LyncClient.Self.
                Contact.GetContactInformation(ContactInformationType.Availability)).ToString();

            //current activity string
            Activity_Label.Content = _LyncClient.Self.
                Contact.GetContactInformation(ContactInformationType.Activity).ToString();

            //Activity token for displayed activity string
            ActivityId_Label.Content = _LyncClient.Self.
                Contact.GetContactInformation(ContactInformationType.ActivityId).ToString();

            //Get list of all LocaleString objects - list encapsulates the customized and localized activity strings
            List<object> states = (List<object>)_LyncClient.Self.
                Contact.GetContactInformation(ContactInformationType.CustomActivity);

            //Iterate on the locale strings
            foreach (object o in states)
            {

                LocaleString lString = (LocaleString)o;
                //If the lcid of a Locale string matches the lcid of the current UI culture, display
                //the custom string
                if (System.Globalization.CultureInfo.CurrentUICulture.LCID == lString.LocaleId)
                {
                    Customactivity_Label.Content = lString.Value;
                    break;
                }
            }

            //Get the list of custom presence states for the current LCID
            FillCustomAvailabilityList();

        }

        private void MainWindow_Loaded_1(object sender, RoutedEventArgs e)
        {
            try
            {
                _LyncClient = LyncClient.GetClient();

                //Register for event that is raised when user availablity changes
                _LyncClient.Self.Contact.ContactInformationChanged += Contact_ContactInformationChanged;
                DisplayCurrentState();
            }
            catch (ClientNotFoundException) { MessageBox.Show("client is not running"); }
        }

        void Contact_ContactInformationChanged(object sender, ContactInformationChangedEventArgs e)
        {
            if (e.ChangedContactInformation.Contains(ContactInformationType.Availability))
            {
                //update the UI with the current state of the user
                this.Dispatcher.Invoke(new DisplayCurrentStateDelegate(DisplayCurrentState));
            }
        }

        /// <summary>
        /// Fills a UI list with all of the custom presence defined for the current UI culture.
        /// </summary>
        private void FillCustomAvailabilityList()
        {
            IList<CustomAvailabilityState> customStates = _LyncClient.Self.GetPublishableCustomAvailabilityStates(
                System.Globalization.CultureInfo.CurrentUICulture.LCID);

            CustomAvailability_List.Items.Clear();
            foreach (CustomAvailabilityState customState in customStates)
            {
                CustomAvailability_List.Items.Add(customState.Id.ToString() + 
                    " " + 
                    customState.Activity + 
                    " " + 
                    customState.Availability.ToString());
            }
        }

        private void Publish_button_Click_1(object sender, RoutedEventArgs e)
        {
            Dictionary<PublishableContactInformationType, object> stuffToPublish = new Dictionary<PublishableContactInformationType,object>();
            stuffToPublish.Add(PublishableContactInformationType.CustomActivityId, _SelectedCustomAvailabilityId);
            try
            {
                _LyncClient.Self.BeginPublishContactInformation(
                    stuffToPublish,
                    (ar) =>
                    {
                       _LyncClient.Self.EndPublishContactInformation(ar);
                    },
                    null);
            }
            catch (ItemNotFoundException) { MessageBox.Show(_SelectedCustomAvailabilityId.ToString() + " Item not found"); }
        }

        private void CustomAvailability_List_SelectionChanged_1(object sender, System.Windows.Controls.SelectionChangedEventArgs e)
        {
            string selectedItem = CustomAvailability_List.SelectedItem.ToString();
            string customId = selectedItem.Substring(0, selectedItem.IndexOf(" "));
            _SelectedCustomAvailabilityId = Convert.ToInt32(customId);
        }
    }
}
```

The following example is an XML file that declares a set of custom presence states for multiple UI culture LCID values. This XML file must be available for all Lync clients to access.

```xml
<customStates xmlns="http://schemas.microsoft.com/09/2005/communicator/customStates" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/09/2005/communicator/customStates
http://contos/sites/main/CustomActivities.xsd">
<customState ID="1" availability="online">
<activity LCID="1033">Working from Home, eh?</activity>
<activity LCID="1044">activity 2 for 1044</activity>
<activity LCID="1055">activity 3 for 1055</activity>
</customState>
<customState ID="2" availability="busy">
<activity LCID="1033">SHOW ME AS - In a Live Meeting - SHOW ME AS</activity>
</customState>
<customState ID="3" availability="busy">
<activity LCID="1033">Meeting with Customer, important!</activity>
<activity LCID="1055">meeting with client, important</activity>
<activity LCID="1036">Je suis tres bizet</activity>
</customState>
<customState ID="4" availability="do-not-disturb">
<activity LCID="1033">Interviewing</activity>
</customState>
</customStates>
```

## See also

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

  - [Custom presence states](custom-presence-states.md)

  - [Configuring Custom Presence States](http://technet.microsoft.com/en-us/library/gg398997.aspx)

