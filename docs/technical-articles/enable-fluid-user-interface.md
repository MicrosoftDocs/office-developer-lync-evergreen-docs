---
title: Enable fluid user interface
TOCTitle: Enable fluid user interface
ms:assetid: bc745dd7-e79b-4d67-b029-bad43b74107d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn551189(v=office.15)
ms:contentKeyID: 60829946
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- xaml
- csharp
---

# Enable fluid user interface

Windows Store apps are subject to frequent interruptions because idle ones are suspended or terminated to make up rooms for the most active ones. When reactivated, they are expected to resume from the previously deactivated state without noticeable interruptions, as if they have never been idle or terminated. This is known as maintaining fluid user experiences.

Fluid user experience requires that the app follow the Windows Store app lifecycle management practices by caching or persisting relevant application data at appropriate time. For a Windows Store app to be fluid, it must also be responsive. This means that most of the UCWA operations must be asynchronous so that they do not block UI threads.


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Configure UI elements in MainPage.xaml for taking user input  
Manage application lifecycle to ensure fluid user experiences  
Manage app data caching to facilitate fluid user experience  
Configure UI elements in MePage.xaml for displaying output  
Additional resources  

To illustrate enabling fluid user experience in our UCWA Windows Store app, we will add UI elements in two XAML pages. The first XAML page is MainPage.xaml that was added as part of Create a Windows Store App Project Using Visual Studio. It will contain the UI elements such as **TextBox**, **PasswordBox**, **CheckBox** and **Button** for accepting user input. We will then add a second XAML page named MePage.xaml. It will contain UI elements, such as **TextBlock**, to display the display name, presence status, personal note, and listed phone numbers of the user. This MePage.xaml can be thought of as a simplified version of the [me dashboard](http://ucwa.skype.com/documentation/dashboard-me) of UCWA.

## Configure UI elements in MainPage.xaml for taking user input

1.  In **Solution Explorer**, double click the MainPage.xaml item to open the main UI page.

2.  In the UI designer, click the "My Application" text. This selects the **TextBlock** element named pageTitle.

3.  In the **Properties** window and under the **Common** category, click the drop-down list in the **Text** field.

4.  Click the **Edit Resource…** item.

5.  Change the page title from "My Application" to "My UCWA RT App". Notice that the title of this page is tied to the system resource of AppName.

6.  Click the **Document Outline** tab of Visual Studio and highlight the first **Grid** element. We will add to the second row of this **Grid** a **StackPanel** element to organize the text input fields.

7.  Click the **Toolbox** tab in Visual Studio and drag and drop the **StackPanel** to the second row of the main **Grid** element.

8.  Scale the **StackPanel** element.

9.  From the **Toolbox**, drag four **TextBlock** elements, plus one **TextBox**, one **PasswordBox** one **CheckBox** and one **Button**, to the **StackPanel** element. We will set the layout of the UI elements in the next step.

10. Configure the newly added UI elements and style their layout using the following XAML code:
    
    ``` xaml
    <TextBlock x:Name="textBlockIntro" TextWrapping="Wrap" Text="TextBlock" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="10,20" FontSize="16"/>
    <TextBlock x:Name="textBlockUserName" TextWrapping="Wrap" Text="User name (e.g., john@contoso.com)" VerticalAlignment="Top" HorizontalAlignment="Left" Margin="20,0" ToolTipService.ToolTip="A Lync user account" FontSize="16"/>
    <TextBox x:Name="textBoxUserName" TextWrapping="Wrap" ToolTipService.ToolTip="Lync user account name" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="20,0,0,20" Width="250"/>
    <TextBlock x:Name="textBlockPassword" TextWrapping="Wrap" Text="Password:" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="20,0,0,0" FontSize="16"/>
    <PasswordBox x:Name="passwordBox" PlaceholderText="" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="20,0,0,20" Width="250"/>
    <CheckBox x:Name="checkBoxSaveUserInfo" Content="Save user info" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="20,0,0,0" FlowDirection="RightToLeft"/>
    <Button x:Name="buttonSignIn" Content="Sign in" HorizontalAlignment="Left" VerticalAlignment="Top" Width="88" Margin="172,0,0,0" RenderTransformOrigin="1.056,0.254"FontSize="16"/>
    <TextBlock x:Name="textBlockError" TextWrapping="Wrap" Text="Status" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="30,30,0,0" MinWidth="160" MinHeight="60" Height="84" Width="227" FontSize="14"/>
    ```
    
    You can also configure the UI elements in the **Properties** window in Visual Studio. See [Create you first Windows Store app using C\# or Visual Basic](http://msdn.microsoft.com/en-us/library/windows/apps/hh974581.aspx).

11. Click the **Sign In** button. Go to the **Properties** window and select the events setting tab. Enter "buttonSignIn\_Clicked" string in the **Click** event field and then press carriage return.
    
    You should see an empty event handler code in the code behind file, MainPage.xaml.cs, as inserted by Visual Studio:
    
    ``` csharp
    private void buttonSignIn_Clicked(object sender, RoutedEventArgs e)
    {
    
    }
    ```
    
    We will come back to hook up this event later in the Put it all together section, once we go through implementing the necessary HTTP operations.

12. Press **F5** to verify that the project can be built and debugged without errors.

We now move on to handling the application’s state-transition events and data caching or storing that are unique to a Windows Store app.

The state-transition events are raised by Windows Runtime and include [OnLaunched](http://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.application.onlaunched.aspx) and [Suspending](http://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.application.suspending.aspx). At minimum, an application must handle these two events, respectively, to load application states from a previous run and to save the application state for a future run. The following steps demonstrate how to manage the life cycle of our UCWA Windows Store app.

## Manage application lifecycle to ensure fluid user experiences

1.  In **Solution Explorer**, click **App.xaml.cs** to open the code-behind source file.

2.  Locate the OnLaunched event handler code block and do the following:
    
      - Insert the async keyword into the signature of the onLaunched method to support calling wait-able statements prefixed with the await keyword.
        
        ``` csharp
        protected async override void OnLaunched(LaunchActivatedEventArgs e)
        ```
    
      - Inside the OnLaunched event handler code listing, insert the code to register the application root frame with the suspension manager, after the application’s root frame is instantiated.
        
        ``` csharp
        rootFrame = new Frame();
        WinStoreUcwaAppHello.Common.SuspensionManager.RegisterFrame(rootFrame, "appFrame");   // app-specific
        ```
    
      - Further down inside the OnLaunched code-listing, insert to the state-loading code a call to the RestoreAsync method on the SuspensionManager class
        
        ``` csharp
        if (e.PreviousExecutionState == ApplicationExecutionState.Terminated)
        {
            //TODO: Load state from previously suspended application
            await WinStoreUcwaAppHello.Common.SuspensionManager.RestoreAsync();  // app-specific
        }
        ```
        
        SuspensionManager is a helper class generated by Visual Studio for managing application lifecycle in a Windows Store app with UI elements. The RestoreAsync method will instruct a reactivated page to load the cached or stored data by calling that page’s navigationHelper\_LoadState event hander method. A placeholder for this event handler is generated by Visual Studio in the code-behind file of a XAML file and an application must provide an implementation. We will come back to the implementation of this event handler in the *MainPage.xaml.cs* file later.

3.  Locate the OnSuspending event handler code-listing at the bottom of the App.xaml.cs file and do the following:
    
      - Insert the async keyword into the signature of the OnSuspending method.
        
        ``` csharp
        protected async override void OnSuspending(object sender, SuspendingEventArgs e)
        ```
    
      - Iinside the OnSuspending code listing, insert to the state saving code block a call to the SaveAsync method on the SuspensionManager class
        
        ``` csharp
        private async void OnSuspending(object sender, SuspendingEventArgs e)
        {
            var deferral = e.SuspendingOperation.GetDeferral();
            //TODO: Save application state and stop any background activity
            await WinStoreUcwaAppHello.Common.SuspensionManager.SaveAsync();  // app-specific, 
            deferral.Complete();
        }
        ```
        
        The SaveAsync method will instruct a suspending page to save relevant application data by calling that page’s navigationHelper\_SaveState event hander method. A placeholder for this event handler is generated by Visual Studio in the code-behind file of a XAML file and an application must provide an implementation. We will come back to the implementation of this event handler in the *MainPage.xaml.cs* file later.

Window Store app API facilitates saving app state information by exposing the [ApplicationDataContainer](http://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.applicationdatacontainer.aspx) class for an app to cache app data locally across different app components or sessions. It also let an app save state information remotely across multiple devices or processes.

For our UCWA Windows Store app, we will use the MainPage.xaml as the landing page, where the user is prompted to enter her account information. The user may be interrupted during or after entering the user information. When she comes back to the application, the user may not want to retype whatever she has already entered, especially she has already checked the option to save user info. We will, thus, save the user name and password as well as the **CheckBox** setting when the data is entered and restore the data when the page is loaded. Using the Basic Page template provided by Visual Studio, a place holder is already generated for you to add the data-loading code. This placeholder is the empty event handler named navigationHelper\_LoadState. A similar placeholder method is generated for saving data before the page is unloaded. This is the navigationHelper\_SaveSate method. However, because a Windows Store app transition from suspending to suspended or terminated rather quickly. It is recommended that important state information be saved whenever it is entered. In the steps below, we will use a set of event handlers to handle data caching.

## Manage app data caching to facilitate fluid user experience

The following steps demonstrate how to manage app data caching for our UCWA Windows Store app.

1.  In **Solution Explorer**, double click **MainPage.xaml.cs** to open the UI elements in the Visual Studio Designer. We will leverage Visual Studio to add event handlers to the data-inputting elements (**TextBox**, **PasswordBox** and **CheckBox**) to save user account information and operational preference whenever new data is entered and new setting specified.

2.  Select the **TextBox** element for user name in the designer and perform the following.
    
    1.  Click the event tab in the **Properties** window, scroll down to the **TextChanged** item in the available event lists, enter the "UserName\_Changed" string as the event handler name for this TextChanged event, and then press the carriage return. As the result, an empty UserName\_Changed method is generated in the code-behind file (MainPage.xaml.cs).
    
    2.  In the MainPage.xaml.cs file, add the following code to the newly generated UserName\_Changed method.
        
        ``` csharp
        private void UserName_Changed(object sender, TextChangedEventArgs e)
        {
            if (checkBoxSaveUserInfo.IsChecked == true)
            {
                Windows.Storage.ApplicationData.Current.RoamingSettings.Values["userName"] = textBoxUserName.Text;
            }
        }
        ```
        
        Here, we save the user name in an associated array (or dictionary) with a key of your choosing. And we do this only if the user has instructed so. We will use the same key to retrieve the saved user name when the data is loaded. For illustrative purposes, we chose to save the user name for use across multiple devices of the user. You may want to implement a different logic according to your application needs or requirements.

3.  In the MainPage.xaml, select the **PasswordBox** element for the password in the designer and perform the following.
    
    1.  Click the event tab in the **Properties** window, scroll down to the **PasswordChanged** item in the available event lists, enter the "Password\_Changed" string as the event handler name for this PasswordChanged event, and then press the carriage return. As the result, an empty Password\_Changed method is generated in the code-behind source file (MainPage.xaml.cs).
    
    2.  In the MainPage.xaml.cs file, add the following code to the newly generated Password\_Changed method.
        
        ``` csharp
        private void Password_Changed(object sender, RoutedEventArgs e)
        {
            if (checkBoxSaveUserInfo.IsChecked == true)
            {
                Windows.Storage.ApplicationData.Current.LocalSettings.Values["password"] = passwordBox.Password;
            }
        }
        ```
        
        Here, we save the password text, only if the user has explicitly instructed so, in an associated array (or dictionary) with a key of our choosing ("password"). We will use the same key to retrieve the saved password when the data is loaded. For illustrative purposes, we chose to save the password for use across different application processes or components on a local machine of the user. You may want to implement a different logic according to your application needs or requirements.

4.  Following the same operational patterns shown above, we set up two other event handlers, SaveUserInfo\_Checked and SaveUserInfo\_Unchecked, for the Checked and Unchecked events, respectively, on the **CheckBox** UI element in the MainPage.xaml. The event handling codes are shown as follows:
    
        private void SaveUserInfo_Checked(object sender, RoutedEventArgs e)
        {
            Windows.Storage.ApplicationData.Current.RoamingSettings.Values["saveUserInfo"] = "checked";
            UserName_Changed(null, null);
            Password_Changed(null, null);
        }
        
        private void SaveUserInfo_Unchecked(object sender, RoutedEventArgs e)
        {
            if (Windows.Storage.ApplicationData.Current.RoamingSettings.Values.ContainsKey("userName"))
                Windows.Storage.ApplicationData.Current.RoamingSettings.Values.Remove("userName");
            if (Windows.Storage.ApplicationData.Current.RoamingSettings.Values.ContainsKey("saveUserInfo"))
                Windows.Storage.ApplicationData.Current.RoamingSettings.Values.Remove("saveUserInfo");
            if (Windows.Storage.ApplicationData.Current.LocalSettings.Values.ContainsKey("password"))
                Windows.Storage.ApplicationData.Current.LocalSettings.Values.Remove("password");
        }
    
    When the user checks to save the user info, the SaveUserInfo\_Checked event handler saves the **CheckBox** state as "checked". In the meantime, it also tries to save any values already entered in the **TextBox** and **PasswordBox** for the user name and password. When the user unchecks the **CheckBox**, all the previously saved data are removed the application storage.
    
    The saved data now need to be retrieved from the application storage when the application is reactivated and the page is reloaded. We will illustrate how to do this in the next step.

5.  In the MainPage.xaml.cs code behind file, add the following code to the Visual Studio-generated navigationHelper\_LoadState method.
    
        private void navigationHelper_LoadState(object sender, LoadStateEventArgs e)
        {
            // Restore values stored in app data container.
            if (Windows.Storage.ApplicationData.Current.LocalSettings.Values.ContainsKey("password"))
            {
                passwordBox.Password = Windows.Storage.ApplicationData.Current.LocalSettings.Values["password"].ToString();
            }
            if (Windows.Storage.ApplicationData.Current.RoamingSettings.Values.ContainsKey("userName"))
            {
                textBoxUserName.Text = Windows.Storage.ApplicationData.Current.RoamingSettings.Values["userName"].ToString();
            }
            if (Windows.Storage.ApplicationData.Current.RoamingSettings.Values.ContainsKey("saveUserInfo") &&
                Windows.Storage.ApplicationData.Current.RoamingSettings.Values["saveUserInfo"].ToString() == "checked")
                checkBoxSaveUserInfo.IsChecked = true;
        
            if (checkBoxSaveUserInfo.IsChecked != true)
            {
                SaveUserInfo_Unchecked(this, null);
            }
        }
    
    This completes our planned tasks for managing application lifecycle and state to enable fluid user experience. You can test it by pressing F5 to build and debug the application. When the application is launched successfully, enter some texts in the **TextBox** and **PasswordBox** input fields, check the **CheckBox**, and then suspend or quit the application. When you re-launch the application, you should see the previous entered texts showing up in the text input fields and the **CheckBox** remains to be checked. It’s as if you had never quit the application.

## Configure UI elements in MePage.xaml for displaying output

Before moving on to enabling UCWA features, let us finish setting up the remaining UI elements to be used to display the application’s output.

1.  In **Solution Explorer**, right click the project name (**WinStoreUcwaAppHello**) to select the **Add-\>New Item** menu option.

2.  In the **Add New Item** window, select **Basic Page** template for **Windows Store** apps in **C\#**, type "MePage.xaml" as the XAML file name for this page, and then click the **Add** button.

3.  Change the \<Page.Resources\> element in the newly generated MePage.xaml file as follows.
    
        <Page.Resources>
            <!-- TODO: Delete this line if the key AppName is declared in App.xaml -->
            <x:String x:Key="AppName">UCWA RT App.Me</x:String>
        </Page.Resources>

4.  Add five **TextBlock**, four **TextBox**, one **Image** and one **Grid** UI elements and arrange them inside the root **Grid** element as shown as follows.
    
        <Grid Margin="138,85,0,0" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Width="701">
            <Grid.RowDefinitions>
                <RowDefinition Height="74*"/>
                <RowDefinition Height="89*"/>
                <RowDefinition Height="96*"/>
                <RowDefinition Height="101*"/>
                <RowDefinition Height="248*"/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="231*"/>
                <ColumnDefinition Width="850*"/>
                <ColumnDefinition Width="265*"/>
            </Grid.ColumnDefinitions>
            <TextBlock Margin="29,26,10,10" TextWrapping="Wrap" Text="Location:" FontSize="18" FontWeight="Bold"/>
            <TextBlock Margin="29,28,26,10" TextWrapping="Wrap" Text="Note:" FontSize="18" FontWeight="Bold" Grid.Row="1"/>
            <TextBlock Margin="29,35,0,10" TextWrapping="Wrap" Text="Presence" FontSize="18" FontWeight="Bold" Grid.Row="2"/>
            <TextBlock Margin="29,22,10,28" TextWrapping="Wrap" Text="Phones:" FontSize="18" FontWeight="Bold" Grid.Row="3"/>
            <TextBlock Margin="29,38,26,159" TextWrapping="Wrap" Text="Photo:" FontSize="18" FontWeight="Bold" Grid.Row="4"/>
            <Image x:Name="imagePhoto" Grid.Column="1" HorizontalAlignment="Left" Height="200" Margin="10,10,0,0" Grid.Row="4" VerticalAlignment="Top" Width="316"/>
            <TextBox x:Name="textBoxLocation" Grid.Column="1" HorizontalAlignment="Left" Margin="10,10,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="433" Height="54"/>
            <TextBox x:Name="textBoxNote" Grid.Column="1" HorizontalAlignment="Left" Margin="10,10,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="433" Height="54" Grid.Row="1"/>
            <TextBox x:Name="textBoxPresence" Grid.Column="1" HorizontalAlignment="Left" Margin="10,10,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="433" Height="66" Grid.Row="2"/>
            <TextBox x:Name="textBoxPhones" Grid.Column="1" HorizontalAlignment="Left" Margin="10,10,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Width="433" Height="71" Grid.Row="3"/>
        </Grid>
        <TextBlock x:Name="textBlockMyName" Margin="113,10,562,560" TextWrapping="Wrap" Text="Name:" FontSize="24" FontWeight="Bold" Grid.Row="1"/>
    
    We will use these UI elements to show the properties of the UCWA me resource. This will be shown in the Inspect Local Presence and User Data section. Before we do that, we need to [Ensure responsive HTTP operations](ensure-responsive-http-operations.md).

## Additional resources

  - [Start creating UCWA Windows Store apps](start-creating-ucwa-windows-store-apps.md)

  - [Create your first Windows Store app using C\# or Visual Basic](http://msdn.microsoft.com/en-us/library/windows/apps/hh974581.aspx)

  - [Create a UCWA Windows Store app project](create-a-ucwa-windows-store-app-project.md)

  - [Ensure responsive HTTP operations](ensure-responsive-http-operations.md)

  - [Implement the UCWA sign-in workflow](implement-the-ucwa-sign-in-workflow.md)

  - [Putting it all together](putting-it-all-together.md)

