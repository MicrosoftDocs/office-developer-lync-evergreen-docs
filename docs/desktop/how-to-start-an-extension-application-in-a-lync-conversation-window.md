---
title: 'How to: Start an extension application in a Lync conversation window'
TOCTitle: 'How to: Start an extension application in a conversation window'
ms:assetid: a31d8832-bfa4-4f2d-98ae-479dea5cd081
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933131(v=office.15)
ms:contentKeyID: 50877261
ms.date: 06/09/2015
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Start an extension application in a Lync conversation window

Learn how to set Microsoft Lync 2013 Conversation Window Extension (CWE) properties, set CWE size and hosting location at runtime, and then start an IM conversation.



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
Create a CWE application<br />
Register the new CWE application<br />
Create an automation application<br />
Code examples: Automation IM conversations with a CWE application<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for starting an extension application in a Lync 2013 conversation window are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

  - Internet Information Services (IIS) must be installed on the sending and receiving client computers.

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
<td><p><a href="contextual-lync-conversations.md">Contextual Lync conversations</a></p></td>
<td><p>Introduces the concept of contextual conversations in Microsoft Lync 2013 by describing application scenarios, application development models, and contextual extension application package registration.</p></td>
</tr>
<tr class="even">
<td><p><a href="understand-the-role-of-the-default-cwe-application-registration-package.md">Understand the role of the default CWE application registration package</a></p></td>
<td><p>Shows how to set the install-time default CWE application registration package in custom Lync 2013 automation applications to set up a default CWE application.</p></td>
</tr>
<tr class="odd">
<td><p><a href="understand-the-purpose-of-runtime-application-registration.md">Understand the purpose of runtime application registration</a></p></td>
<td><p>Explains the purpose of runtime registration of Conversation Window Extension applications in Microsoft Lync 2013 SDK.</p></td>
</tr>
<tr class="even">
<td><p><a href="how-to-create-a-conversation-window-extension-application-in-lync-sdk.md">How to: Create a Conversation Window Extension application in Lync SDK</a></p></td>
<td><p>Shows how to create a Silverlight application to send and receive information in conversation context and run it in Lync 2013 CWE.</p></td>
</tr>
<tr class="odd">
<td><p><a href="how-to-install-a-cwe-application-in-lync-sdk.md">How to: Install a CWE application in Lync SDK</a></p></td>
<td><p>Shows how to register a Lync 2013 CWE so the CWE can be opened in a Lync 2013 conversation window.</p></td>
</tr>
</tbody>
</table>

## Create a CWE application

Create and install a simple HTML page to represent a context application packaged in a conversation. In a production environment, substitute an application install procedure that installs the application on the appropriate client computers. The context application must be installed and registered on each sending and receiving client computer. For more information, see the "Create a sample context application" section in [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md).

## Register the new CWE application

Use registry entries to register the context application together with Lync 2013. The context application must be registered on each sending and receiving client computer. For more information, see the "Add registry entries" section in [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md). The GUID that you add to the registry must match the value that you specify in the code that appears in the next section.

## Create an automation application

The following procedure shows how to create a WPF window that is used to start an IM conversation and start the CWE application that runs in Lync 2013 CWE.

### To create the automation application

1.  In the Microsoft Visual Studio, create a new application.
    
    The application can be any kind of managed code application.

2.  Add a project reference to Microsoft.Lync.Model.
    
    The default location is *%ProgramFiles%*\\Microsoft Office 2013\\LyncSDK\\Assemblies\\desktop.

3.  In MainWindow.xaml.cs, add the following using statements.
    
    ```csharp
    using Microsoft.Lync.Model;
    using Microsoft.Lync.Model.Extensibility;
    ```

4.  Add the following declarations to the **Window** class.
    
    ```csharp
    ApplicationRegistration myApplicationRegistration;
    bool _UseRuntimeReg = false;
    ConversationWindow cWindow;
    ```

5.  Add the following code to a click event handler for a command button in the WPF window.
    
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
    <td><p>If a default CWE application is registered on the local computer, it loads in an extension tab even if your code has loaded a different CWE application in another tab.</p></td>
    </tr>
    </tbody>
    </table>
    
    This example overrides the install-time registration CWE application by creating an [Microsoft.Lync.Model.Extensibility.ApplicationRegistration](https://msdn.microsoft.com/library/jj293820\(v=office.15\)) object, setting property values appropriately, and adding the registration.
    
    ``` 
                string appId = "{FA44026B-CC48-42DA-AAA8-B849BCB43A21}";
    
                //Does the user want to start a different version of the CWE?
                if (RuntimeReg_Check.IsChecked == true)
                {
                    string appname = "Contoso Internal Sales View";
                    myApplicationRegistration = LyncClient.GetClient().CreateApplicationRegistration(
                        appId,
                        appname);
    
                    // Set the Conversation Window Extension properties.
                    // Ensure that the internalURL parameter is valid on your computer.
                    myApplicationRegistration.SetExtensibilityWindowProperties(
                      @"\\contoso\SalesView\GenericCWEAppTestPage.html",
                      "",
                      ConversationWindowExtensionSize.Large);
    
                    // Register the application.
                    this.myApplicationRegistration.AddRegistration();
                    _UseRuntimeReg = true;
                }
    ```
    
    The following example automates the start of a new Lync 2013 conversation window using runtime CWE application registration set in the previous example. After the conversation window is opened, the runtime registration override must be removed with a call to the [ApplicationRegistration.RemoveRegistration](https://msdn.microsoft.com/library/jj276189\(v=office.15\)) method.
    
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
    <td><p>You must always set the <a href="https://msdn.microsoft.com/library/jj276319(v=office.15)">AutomationModalitySettings</a><strong>.ApplicationId</strong> modality property before you can open a non-default CWE application. Only create an <strong>ApplicationRegistration</strong> object if you're overriding the install-time registration. If a default CWE application is registered on a computer, it starts for every new conversation, even if no application ID is set. A default CWE application cannot be overridden by a runtime <strong>ApplicationRegistration</strong> object.</p></td>
    </tr>
    </tbody>
    </table>
    
    ```csharp
                Dictionary<AutomationModalitySettings, object> modalitySettings = new Dictionary<AutomationModalitySettings, object>();
    
                //Set the GUID of the CWE to be opened in the conversation window.
                modalitySettings.Add(AutomationModalitySettings.ApplicationId,appId);
    
                modalitySettings.Add(AutomationModalitySettings.FirstInstantMessage, "testing CWE");
                modalitySettings.Add(AutomationModalitySettings.SendFirstInstantMessageImmediately, true);
    
                LyncClient.GetAutomation().BeginStartConversation(
                    AutomationModalities.InstantMessage,
                    participantUri,
                    modalitySettings,
                    (ar) =>
                    {
                        try
                        {
                            ConversationWindow newWindow = LyncClient.GetAutomation().EndStartConversation(ar);
                            newWindow.BeginOpenExtensibilityWindow(
                                appId, 
                                (ar2) => 
                                {
                                    newWindow.EndOpenExtensibilityWindow(ar2);
                                },
                                null);
                            if (_UseRuntimeReg == true)
                            {
                                myApplicationRegistration.RemoveRegistration();
                            }
                        }
                        catch (OperationException oe) 
                        {
                            MessageBox.Show("Operation exception on start conversation " + oe.Message); 
                        }
                        catch (LyncClientException lce) 
                        {
                            MessageBox.Show("Lync client exception on start conversation " + lce.Message);
                        }
                    },
                    null);
    ```

6.  Build and run the application.
    
    In the conversation window on the sending and receiving clients, the CWE appears with the context application inside it. The receiving client loads the install-time CWE application and the sending client loads the runtime CWE application if overriding the install-time application.

## Code examples: Automation IM conversations with a CWE application

The following example declares a WPF window that starts a new IM conversation and opens a CWE application in the new conversation window.

```xaml
<Window x:Class="AutomationPhoneCall.Page1"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="130" Width="298">
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="140"/>
            <ColumnDefinition Width="80*"/>
        </Grid.ColumnDefinitions>
        <StackPanel Grid.Column="0">
            <TextBox Name="GetSip" Text="enter SIP or TEL" Margin="20,20,20,0"/>
            <CheckBox Name="RuntimeReg_Check" Content="Runtime?" Margin="20,10,5,5"/>
        </StackPanel>
        <Button Grid.Column="1" Name="Go_Button" Content="Call" Margin="10,10,10,10" Click="Go_Button_Click" Height="26"/>
    </Grid>
</Window>
```

The following example is the interaction logic for the previous window declaration. The example opens a starts a new conversation by opening a [Microsoft.Lync.Model.Extensibility.ConversationWindow](https://msdn.microsoft.com/library/jj293606\(v=office.15\)) and then opening an extensibility pane with a CWE application that is loaded from its default host server or a server specified at runtime.

```csharp
using System.Collections.Generic;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Documents;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Extensibility;

namespace AutomationPhoneCall
{
    /// <summary>
    /// Interaction logic for Page1.xaml
    /// </summary>
    public partial class Page1 : Window
    {
        ApplicationRegistration myApplicationRegistration;
        bool _UseRuntimeReg = false;
        public Page1()
        {
            InitializeComponent();
        }

        /// <summary>
        /// Starts an IM conversation, opens a CWE, and sends a 
        /// request to other user to open CWE on remote endpoint from same
        /// hosting location.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void Go_Button_Click(object sender, RoutedEventArgs e)
        {
            if ( GetSip.Text.Length == 0)
            {
                return;
            }
            List<string> participantUri = new List<string>();
            participantUri.Add(GetSip.Text);

            string appId = "{FA44026B-CC48-42DA-AAA8-B849BCB43A21}";

            //Does user want to start the CWE from a different hosting location?
            if (RuntimeReg_Check.IsChecked == true)
            {
                // Ensure that this GUID matches the registry value entered in the previous section.
                string appname = "Contoso Internal Sales View";
                myApplicationRegistration = LyncClient.GetClient().CreateApplicationRegistration(
                    appId,
                    appname);

                // Set the Conversation Window Extension properties.
                // Ensure that the internalURL parameter is valid on your computer.
                myApplicationRegistration.SetExtensibilityWindowProperties(
                  @"\\contoso\SalesView\GenericCWEApp\GenericCWEAppTestPage.html",
                  "",
                  ConversationWindowExtensionSize.Large);

                // Register the application.
                this.myApplicationRegistration.AddRegistration();
                _UseRuntimeReg = true;
            }

            Dictionary<AutomationModalitySettings, object> modalitySettings = new Dictionary<AutomationModalitySettings, object>();

            //Set the GUID of the CWE to be opened in the conversation window.
            modalitySettings.Add(AutomationModalitySettings.ApplicationId,appId);

            modalitySettings.Add(AutomationModalitySettings.FirstInstantMessage, "testing CWE");
            modalitySettings.Add(AutomationModalitySettings.SendFirstInstantMessageImmediately, true);

            LyncClient.GetAutomation().BeginStartConversation(
                AutomationModalities.InstantMessage,
                participantUri,
                modalitySettings,
                (ar) =>
                {
                    try
                    {
                        ConversationWindow newWindow = LyncClient.GetAutomation().EndStartConversation(ar);
                        newWindow.BeginOpenExtensibilityWindow(
                            appId, 
                            (ar2) => 
                            {
                                newWindow.EndOpenExtensibilityWindow(ar2);
                            },
                            null);
                        if (_UseRuntimeReg == true)
                        {
                            myApplicationRegistration.RemoveRegistration();
                        }
                    }
                    catch (OperationException oe) 
                    {
                        MessageBox.Show("Operation exception on start conversation " + oe.Message); 
                    }
                    catch (LyncClientException lce) 
                    {
                        MessageBox.Show("Lync client exception on start conversation " + lce.Message);
                    }
                },
                null);

        }
    }
}
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

