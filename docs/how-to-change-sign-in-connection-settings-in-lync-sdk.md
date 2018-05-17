---
title: 'How to: Change sign-in connection settings in Lync SDK'
TOCTitle: 'How to: Change sign-in connection settings'
ms:assetid: 7ab1a37b-5784-4e36-b9ef-25c439d22dc5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933091(v=office.15)
ms:contentKeyID: 50877222
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Change sign-in connection settings in Lync SDK

Learn how use the Microsoft Lync 2013 API to obtain and set Microsoft Lync Server 2013 connection settings that let a user sign in to different Lync front-end servers.


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
Read sign-in connection settings<br />
Lync sign-in screen<br />
Code examples: Lync sign-in utility<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Prerequisites

You should know how Lync 2013 discovers and signs in to Lync Server 2013 before you create an application UI that lets a user change any connection settings.

### Core concepts to know

The following topics explain how server auto-discovery works in Lync 2013.

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
<td><p><a href="http://technet.microsoft.com/en-us/library/dd637152(office.13).aspx">Office Communicator Sign-in and Discovery</a></p></td>
<td><p>Describes the Lync 2013 sign-in and auto discovery process.</p>
<div class="alert">

> [!IMPORTANT]
> <P>The referenced article describes auto discovery in Communicator 2007 but is valid for Lync 2013 with the following exceptions:</P>
> <UL>
> <LI>
> <P>HTTP-based auto-discovery is supported in Lync 2013.</P>
> <LI>
> <P>TCP connections are not supported in Lync 2013. Only TLS is supported.</P></LI></UL>


</div></td>
</tr>
<tr class="even">
<td><p><a href="http://technet.microsoft.com/en-us/library/gg398758.aspx">Determining NS Requirements</a></p></td>
<td><p>Explains how to enable automatic configuration server location services by configuring DNS records for internal and external access.</p></td>
</tr>
</tbody>
</table>


## Read sign-in connection settings

The sign-in connection settings are exposed by the [Microsoft.Lync.Model.SignInConfiguration](signinconfiguration-class-microsoft-lync-model_2.md) class. It is not necessary to be signed in to Microsoft Lync 2013 to get this object and read the exposed properties.

### To read sign-in connection settings

1.  Get an instance of [Microsoft.Lync.Model.LyncClient](lyncclient-class-microsoft-lync-model_2.md) by calling the static [LyncClient.GetClient](lyncclient-getclient-method-microsoft-lync-model_1.md) method.
    
    ``` csharp
    LyncClient _LyncClient = LyncClient.GetClient();
    ```

2.  Read the [LyncClient.SignInConfiguration](lyncclient-signinconfiguration-property-microsoft-lync-model_2.md) property to get the [Microsoft.Lync.Model.SignInConfiguration](signinconfiguration-class-microsoft-lync-model_2.md) object.
    
    ``` csharp
    SignInConfiguration signInConfiguration = _LyncClient.SignInConfiguration;
    ```

3.  Read the configuration settings.
    
    The following example reads the configuration settings.
    
    ``` csharp
    InternalUrl_textbox.Text = signInConfiguration.InternalServerUrl;
    ExternalUrl_textbox.Text = signInConfiguration.ExternalServerUrl;
    SigedInFromInternetValue_label.Content = signInConfiguration.SignedInFromIntranet.ToString();
    SignedInAsAvailableValue_label.Content = signInConfiguration.SignInAsAvailability.ToString();
    SignInAutoRetryValue_Label.Content = signInConfiguration.SignInAutoRetry.ToString();
    UserName_textbox.Text = signInConfiguration.UserName;
    if (signInConfiguration.Mode == LyncClientConfigurationMode.Auto)
    {
        Auto_radio.IsChecked = true;
        Manual_radio.IsChecked = false;
    }
    else
    {
        Auto_radio.IsChecked = false;
        Manual_radio.IsChecked = true;
    }
    ```

### To update connection settings

  - Update a connection setting by writing a value of the correct type to the [Microsoft.Lync.Model.SignInConfiguration](signinconfiguration-class-microsoft-lync-model_2.md) property that you want to update. If the user is signed in to Lync 2013 when the settings are changed, the changes take effect the next time that a user signs in to Lync.
    

    > [!IMPORTANT]
    > <P>The <A href="signinconfiguration-transportmode-property-microsoft-lync-model_2.md">SignInConfiguration.TransportMode</A> property is read/write although you cannot write to the property and change the transport mode with Lync 2013. Only <A href="transportmode-enumeration-microsoft-lync-model_2.md">TransportMode</A><STRONG>.TlsTransport</STRONG> is supported.</P>

    
    The following example updates each of the writable connection settings with the value typed in the UI. Before writing the property, the sample calls the [SignInConfiguration.CanSet](signinconfiguration-canset-method-microsoft-lync-model_2.md) method. If **true** is returned, the example updates the property value.
    
    ``` csharp
            /// <summary>
            /// Updates the sign-in configuration object with an InternalURL supplied by user
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void InternalUrl_textbox_LostFocus(object sender, RoutedEventArgs e)
            {
                if (_LyncClient.SignInConfiguration.CanSet(SignInConfigurationType.InternalServer))
                {
                    _LyncClient.SignInConfiguration.InternalServerUrl = InternalUrl_textbox.Text;
                }
            }
    
            /// <summary>
            /// Updates the sign-in configuration object with an ExternalURL supplied by user
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void ExternalUrl_textbox_LostFocus(object sender, RoutedEventArgs e)
            {
                if (_LyncClient.SignInConfiguration.CanSet(SignInConfigurationType.ExternalServer))
                {
                    _LyncClient.SignInConfiguration.ExternalServerUrl = ExternalUrl_textbox.Text;
                }
            }
    
            /// <summary>
            /// Sets the sign-in mode to the user's choice of auto or manual
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void Auto_radio_Checked(object sender, RoutedEventArgs e)
            {
                if (_LyncClient.SignInConfiguration.CanSet(SignInConfigurationType.Mode))
                {
                    if (Auto_radio.IsChecked == true)
                    {
                        _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Auto;
                    }
                    else
                    {
                        _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Manual;
                    }
                }
            }
    
            /// <summary>
            /// Sets the sign-in mode to the user's choice of auto or manual
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void Manual_radio_Checked(object sender, RoutedEventArgs e)
            {
                if (_LyncClient.SignInConfiguration.CanSet(SignInConfigurationType.Mode))
                {
                    if (Manual_radio.IsChecked == true)
                    {
                        _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Manual;
                    }
                    else
                    {
                        _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Auto;
                    }
                }
            }
    ```

## Lync sign-in screen

The following example shows a custom screen for connection settings.

  
![Sign in configuration dialog sample UI](images/JJ933176.LyncClientSDK_ConnectionSettings_ConversationEvents(Office.15).jpg "Sign in configuration dialog sample UI")

## Code examples: Lync sign-in utility

The following example declares a WPF window that displays and accepts changes to Microsoft Lync Server 2013 sign-in connection settings and signs a user in to Lync.

``` xaml
<Window x:Class="ConnectionSettings.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
    Title="Lync Connection Cettings" Height="Auto" Width="Auto" mc:Ignorable="d" 
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
        d:DesignHeight="533" d:DesignWidth="813" SizeToContent="WidthAndHeight" Loaded="Window_Loaded">
    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="20"/>
            <RowDefinition Height="294"/>
            <RowDefinition Height="147" />
            <RowDefinition Height="210*" />
        </Grid.RowDefinitions>
        <StackPanel Height="285" HorizontalAlignment="Left" 
                    Name="stackPanel1" 
                    VerticalAlignment="Top" 
                    Width="189" 
                    Grid.Row="1" 
                    Background="#FFEFC7C7">
            <Label Content="Internal Uri" Height="28" Name="label1" />
            <Label Content="External Uri" Height="28" Name="label2" />
            <Label Content="Mode" Height="28" Name="label3" />
            <Label Content="Password saved" Height="28" Name="label4" />
            <Label Content="Signed in from intranet" Height="28" Name="label5" />
            <Label Content="Sign in as available" Height="28" Name="label6" />
            <Label Content="Sign in auto-retry" Height="28" Name="label7" />
            <Label Content="Transport mode" Height="28" Name="label8" />
            <Label Content="User name" Height="28" Name="label9" />
            <Label Content="Password" Height="28" Name="label10" />
        </StackPanel>
        <StackPanel Grid.Row="1" 
                    Height="285" 
                    HorizontalAlignment="Left" 
                    Margin="195,0,0,0" 
                    Name="stackPanel2" 
                    VerticalAlignment="Top" 
                    Width="596" Background="#FFC0EFB5">
            <TextBox Height="23" Name="InternalUrl_textbox" Width="579" Margin="0,6,0,0" LostFocus="InternalUrl_textbox_LostFocus"/>
            <TextBox Height="23" Name="ExternalUrl_textbox" Width="579" Margin="0,6,0,0" LostFocus="ExternalUrl_textbox_LostFocus"/>
            <Grid Name="ModeRadioButtons">
                <RadioButton Content="Auto" Height="16" 
                             HorizontalAlignment="Left" Margin="10,6,0,0" Name="Auto_radio" VerticalAlignment="Top" Checked="Auto_radio_Checked"/>
                <RadioButton Content="Manual" 
                             Height="16" 
                             HorizontalAlignment="Left" 
                             Margin="100,6,0,0" Name="Manual_radio" VerticalAlignment="Top" Checked="Manual_radio_Checked"/>
            </Grid>
            <Grid Name="PasswordRadioButtons">
                <RadioButton Content="Yes" Height="16" Name="PasswordYes_radio" Margin="10,6,0,0"/>
                <RadioButton Content="No" Height="16" Name="PasswordNo_radio" Margin="100,6,0,0"/>
            </Grid>
            <Label Content="true" Height="28" Name="SigedInFromInternetValue_label" Margin="10,4,0,0"/>
            <Label Content="Yes" Height="28" Name="SignedInAsAvailableValue_label" Margin="10,4,0,0"/>
            <Label Content="Yes" Height="28" Name="SignInAutoRetryValue_Label" Margin="10,4,0,0"/>
            <Grid Name="TransportModeRadioButtons">
                <RadioButton Content="Tcp" Height="16" Name="TcpMode_radio" Margin="10,6,0,0"/>
                <RadioButton Content="Tls" Height="16" Name="TlsMode_radio" Margin="100,6,0,0"/>
            </Grid>
            <TextBox Height="23" Name="UserName_textbox" Width="579" Margin="0,6,0,0" />
            <PasswordBox Height="23" Name="Password_passwordBox" Width="579" Margin="0,6,0,0"/>
        </StackPanel>
        <StackPanel Grid.Row="2" Margin="0,0,602,0">
            <Button Content="Sign in" Height="23" Margin="0,30,0,0" Name="button1" Width="75" Click="SignInButton_Click"/>
            <Button Content="Refresh settings" Height="23" Margin="0,26,0,0" Name="RefreshSetting_button" Width="94" Click="RefreshSetting_button_Click"/>

        </StackPanel>
        <StackPanel Orientation="Horizontal" HorizontalAlignment="Left" VerticalAlignment="Center" Grid.Row="2" Margin="195,0,-4,0" Width="600" Height="147">
            <controls:MyStatusArea Grid.Row="2" Margin="016,28,0,0" Name="myStatusArea1" />
        </StackPanel>
    </Grid>

</Window>
```

The following example fills the content and text values of the UI controls declared in the previous example.

``` csharp
using System.Windows;
using Microsoft.Lync.Model;

namespace ConnectionSettings
{
    /// <summary>
    /// Interaction logic for Window1.xaml
    /// </summary>
    public partial class Window1 : Window
    {
        LyncClient _LyncClient;
        public Window1()
        {
            InitializeComponent();
            _LyncClient = LyncClient.GetClient();
        }

        private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            LoadSettings();
        }

        /// <summary>
        /// Reads sign-in configuration settings from the client platform and updates UI controls
        /// </summary>
        private void LoadSettings()
        {
            InternalUrl_textbox.Text = _LyncClient.SignInConfiguration.InternalServerUrl;
            ExternalUrl_textbox.Text = _LyncClient.SignInConfiguration.ExternalServerUrl;
            SigedInFromInternetValue_label.Content = _LyncClient.SignInConfiguration.SignedInFromIntranet.ToString();
            SignedInAsAvailableValue_label.Content = _LyncClient.SignInConfiguration.SignInAsAvailability.ToString();
            SignInAutoRetryValue_Label.Content = _LyncClient.SignInConfiguration.SignInAutoRetry.ToString();
            UserName_textbox.Text = _LyncClient.SignInConfiguration.UserName;
        }

        /// <summary>
        /// Signs a user in to Lync by using the settings, user name, and password supplied by user.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void SignInButton_Click(object sender, RoutedEventArgs e)
        {
            if (_LyncClient.State == ClientState.SignedOut)
            {
                _LyncClient.BeginSignIn(UserName_textbox.Text, UserName_textbox.Text,
                    Password_passwordBox.Password, 
                    (ar) =>
                {
                    _LyncClient.EndSignIn(ar);
                }
                , null);
            }
        }

        /// <summary>
        /// Reloads the current settings
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void RefreshSetting_button_Click(object sender, RoutedEventArgs e)
        {
            LoadSettings();
        }

        /// <summary>
        /// Updates the sign-in configuration object with an InternalURL supplied by user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void InternalUrl_textbox_LostFocus(object sender, RoutedEventArgs e)
        {
            _LyncClient.SignInConfiguration.InternalServerUrl = InternalUrl_textbox.Text;
        }

        /// <summary>
        /// Updates the sign-in configuration object with an ExternalURL supplied by user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ExternalUrl_textbox_LostFocus(object sender, RoutedEventArgs e)
        {
            _LyncClient.SignInConfiguration.ExternalServerUrl = ExternalUrl_textbox.Text;
        }

        /// <summary>
        /// Sets the sign-in mode to the user's choice of auto or manual
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Auto_radio_Checked(object sender, RoutedEventArgs e)
        {
            if (Auto_radio.IsChecked == true)
            {
                _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Auto;
            }
            else
            {
                _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Manual;
            }
        }

        /// <summary>
        /// Sets the sign-in mode to the user's choice of auto or manual
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Manual_radio_Checked(object sender, RoutedEventArgs e)
        {
            if (Manual_radio.IsChecked == true)
            {
                _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Manual;
            }
            else
            {
                _LyncClient.SignInConfiguration.Mode = LyncClientConfigurationMode.Auto;
            }

        }
    }
}
```

## Additional resources

  - [What you can do in Lync SDK](what-you-can-do-in-lync-sdk.md)

