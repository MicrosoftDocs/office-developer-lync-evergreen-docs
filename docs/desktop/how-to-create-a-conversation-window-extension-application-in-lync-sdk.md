---
title: 'How to: Create a Conversation Window Extension application in Lync SDK'
TOCTitle: 'How to: Create a Conversation Window Extension application'
ms:assetid: 7aef4337-06f6-4857-8d2c-a0d1e261b7a5
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933100(v=office.15)
ms:contentKeyID: 50877232
ms.date: 06/09/2015
mtps_version: v=office.15
dev_langs:
- csharp
- html
- xaml
---

# How to: Create a Conversation Window Extension application in Lync SDK

Learn how to create a simple Microsoft Silverlight application that sends and receives information in conversation context and use Microsoft Lync 2013 SDK to run it in Microsoft Lync 2013 Conversation Window Extension (CWE).



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
Create a sample Silverlight application<br />
Create a simple HTML page<br />
Register the application<br />
Code examples: Simple CWE with context<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for creating a CWE application are as follows:

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
<td><p><a href="lync-conversation-window-extension.md">Lync Conversation Window Extension</a></p></td>
<td><p>Introduces the Conversation Window Extension (CWE) feature of the Microsoft Lync 2013 client conversation window by explaining how a CWE is opened, closed, and sized.</p></td>
</tr>
<tr class="even">
<td><p><a href="contextual-lync-conversations.md">Contextual Lync conversations</a></p></td>
<td><p>Introduces the concept of contextual conversations in Microsoft Lync 2013 by describing application scenarios, application development models, and contextual extension application package registration.</p></td>
</tr>
</tbody>
</table>

## Create a sample Silverlight application

### To create a Silverlight application to run in Lync 2013 CWE

1.  In Visual Studio, create a new project, and then choose the **Silverlight Application** template.

2.  Add references to Microsoft.Lync.Model and Microsoft.Lync.Utilities in the \\Program Files (x86)\\Microsoft Office 2013\\LyncSDK\\Assemblies\\Silverlight folder.

3.  Add a **TextBox** control to the page that accepts a string to be sent as contextual data.

4.  Add a **Button** control that commands the string to be sent to other conversation participants as contextual data.

5.  Add a **TextBlock** control that displays a string sent to the local conversation as contextual data.
    
    The following XAML grid declaration adds the controls in this procedure to the Silverlight page.
    
    ``` 
        <Grid x:Name="LayoutRoot" Background="White">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="60*"/>
                <ColumnDefinition Width="60*"/>
            </Grid.ColumnDefinitions>
            <StackPanel Grid.Column="0" Orientation="Vertical">
                <TextBlock Text="Your question" Margin="10,10,0,0"/>
                <TextBox Name="Question_Textbox" Width="170" Height="26" Margin="10,10,0,0" HorizontalAlignment="Left"/>
                <Button Name="SendQuestion_Button" Content="Send Question" Width="170" Margin="10,10,0,0" HorizontalAlignment="Left" Click="SendQuestion_Button_Click"/>
                <ListBox Name="eventlog_Listbox" Width="150" Height="160" Margin="6,10,10,10" />
            </StackPanel>
            <StackPanel Grid.Column="1">
                <TextBlock Text="Their answer" Margin="10,10,0,0"/>
                <TextBlock Text="" Name="TheirAnswer_Textblock" Width="160" Height="26" Margin="10,10,0,0" HorizontalAlignment="Left"/>
            </StackPanel>
        </Grid>
    ```

### To add contextual information logic to the code interaction logic file

1.  Create a GUID for the Silverlight application.
    
    For more information, see [Create GUID (guidgen.exe)](http://go.microsoft.com/fwlink/?linkid=192728%26clcid=0x409).

2.  Declare a private string that holds the GUID created in step 1.
    
    ```csharp
            private const string ApplicationGuid = "{FA44026B-CC48-42DA-AAA8-B849BCB43A21}";
    ```

3.  Get the hosting [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) object.
    
    ```csharp
    Conversation _conversation = (Conversation)LyncClient.GetHostingConversation();
    ```

4.  Register an event handler for the [Conversation.ContextDataReceived](https://msdn.microsoft.com/library/jj275926\(v=office.15\)) event.
    
    ```csharp
    _conversation.ContextDataReceived += _conversation_ContextDataReceived;
    ```

5.  Add an event handler method for the [Conversation.ContextDataReceived](https://msdn.microsoft.com/library/jj275926\(v=office.15\)) event.
    
    ```csharp
            /// <summary>
            /// Local CWE receives context data from a one of three possible active CWE applications
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void  _conversation_ContextDataReceived(object sender, ContextEventArgs e)
            {
                //Does the application Id sent with the context data match the application GUID of this 
                //application?
                if (e.ApplicationId == ApplicationGuid)
                {
                    if (e.ContextDataType == "string")
                    {
                        this.Dispatcher.BeginInvoke(new UpdateLogDelegate(UpdateLog), new object[] { e.ContextData.ToString() + " received" });
                        TheirAnswer_Textblock.Text = e.ContextData.ToString();
                    }
                }
            }
    ```

6.  Add an event handler for the command button that is declared in the previous XAML Silverlight page.
    
    ```csharp
            /// <summary>
            /// Sends the locally typed string to other conversation participants as
            /// contextual data
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            private void SendQuestion_Button_Click(object sender, RoutedEventArgs e)
            {
                if (Question_Textbox.Text.Length == 0)
                {
                    return;
                }
                if (_conversation == null)
                {
                    return;
                }
                _conversation.BeginSendContextData(
                    ApplicationGuid,
                    "string",
                    Question_Textbox.Text,
                    (ar) =>
                    {
                        _conversation.EndSendContextData(ar);
                        this.Dispatcher.BeginInvoke(new UpdateLogDelegate(UpdateLog), new object[] { Question_Textbox.Text + " sent" });
                    },
                    null);
                
            }
    ```

## Create a simple HTML page

You can use your own Web application or create one using the following HTML. The object tag contains the Silverlight application and determines how much space it occupies on the HTML page. Note that the values of the width and height parameters of the object tag should be greater than the UserControl.DesignHeight and UserControl.DesignWidth properties of the Silverlight application.

### To create a simple HTML page

1.  Create a new .html file using the following HTML text.
    
    ```html
    <html>
    <head>
    </head>
    <body>
    <object width="300" height="300" 
    data="data:application/x-silverlight-2," 
    type="application/x-silverlight-2" >
    <param name="source" value="GenericCWEApp.xap.xap"/>
    </object>
    <p>Text in an HTML paragraph element</p>
    </body>
    </html>
    ```

2.  Save the .html file.

3.  Copy the .xap file from the Debug/Bin file of the Silverlight project to the same folder as the HTML file.

4.  In the HTML file, edit the value element of the param tag to match the .xap file name.

## Register the application

Use registry entries to register the Silverlight application with Lync 2013. For more information, see the Adding Registry Entries section in [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md). The GUID you add to the registry must match the value for the Silverlight application you created.

The following example creates new registry keys when needed, adds the CWE to the local computer registry, and adds the CWE hosting server to the list of trusted sites.

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
<td><p>The <strong>[HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages]</strong> and <strong>[HKEY_CURRENT_USER\Software\Microsoft\Office\Lync\Security\Trusted Sites]</strong> keys might not exist in a local computer registry before the following registry file is run.</p></td>
</tr>
</tbody>
</table>

    Windows Registry Editor Version 5.00
    
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Lync\Security\Trusted Sites]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Lync\Security\Trusted Sites\http://contoso/GenericCWEAppTestPage.html]
    "https"=dword:00000000
    "http"=dword:00000001
    
    [HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages]
    
    [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings\ZoneMap\Domains\ServerName]
    "file"=dword:00000002
    
    [HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages\{FA44026B-CC48-42DA-AAA8-B849BCB43A21}]
    "Name"="Generic CWE App"
    "InternalURL"="http://contoso/GenericCWEAppTestPage.html"
    "ExternalURL"="http://contoso/GenericCWEAppTestPage.html"
    "InstallLink"="http://contoso/GenericCWEApp.reg"
    "ExtensibilityWindowSize"=dword:00000000

## Code examples: Simple CWE with context

The following example declares a Silverlight page that hosts two text controls that let the local conversation participant send text through the conversation contextual data methods.

```xaml
<UserControl x:Class="GenericCWEApp.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    d:DesignHeight="300" d:DesignWidth="400">

    <Grid x:Name="LayoutRoot" Background="White">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="60*"/>
            <ColumnDefinition Width="60*"/>
        </Grid.ColumnDefinitions>
        <StackPanel Grid.Column="0" Orientation="Vertical">
            <TextBlock Text="Your question" Margin="10,10,0,0"/>
            <TextBox Name="Question_Textbox" Width="170" Height="26" Margin="10,10,0,0" HorizontalAlignment="Left"/>
            <Button Name="SendQuestion_Button" Content="Send Question" Width="170" Margin="10,10,0,0" HorizontalAlignment="Left" Click="SendQuestion_Button_Click"/>
            <ListBox Name="eventlog_Listbox" Width="150" Height="160" Margin="6,10,10,10" />
        </StackPanel>
        <StackPanel Grid.Column="1">
            <TextBlock Text="Their answer" Margin="10,10,0,0"/>
            <TextBlock Text="" Name="TheirAnswer_Textblock" Width="160" Height="26" Margin="10,10,0,0" HorizontalAlignment="Left"/>
        </StackPanel>
    </Grid>
</UserControl>
```

The following HTML page is generated by Visual Studio to host the Silverlight page that is declared in this sample.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" >
<!-- saved from url=(0014)about:internet -->
<head>
    <title>GenericCWEApp</title>
    <style type="text/css">
    html, body {
    height: 100%;
    overflow: auto;
    }
    body {
    padding: 0;
    margin: 0;
    }
    #silverlightControlHost {
    height: 100%;
    text-align:center;
    }
    </style>
    
    <script type="text/javascript">
        function onSilverlightError(sender, args) {
            var appSource = "";
            if (sender != null && sender != 0) {
              appSource = sender.getHost().Source;
            }
            
            var errorType = args.ErrorType;
            var iErrorCode = args.ErrorCode;

            if (errorType == "ImageError" || errorType == "MediaError") {
              return;
            }

            var errMsg = "Unhandled Error in Silverlight Application " +  appSource + "\n" ;

            errMsg += "Code: "+ iErrorCode + "    \n";
            errMsg += "Category: " + errorType + "       \n";
            errMsg += "Message: " + args.ErrorMessage + "     \n";

            if (errorType == "ParserError") {
                errMsg += "File: " + args.xamlFile + "     \n";
                errMsg += "Line: " + args.lineNumber + "     \n";
                errMsg += "Position: " + args.charPosition + "     \n";
            }
            else if (errorType == "RuntimeError") {           
                if (args.lineNumber != 0) {
                    errMsg += "Line: " + args.lineNumber + "     \n";
                    errMsg += "Position: " +  args.charPosition + "     \n";
                }
                errMsg += "MethodName: " + args.methodName + "     \n";
            }

            throw new Error(errMsg);
        }
    </script>
</head>
<body>
    <form id="form1" runat="server" style="height:100%">
    <div id="silverlightControlHost">
        <object data="data:application/x-silverlight-2," type="application/x-silverlight-2" width="100%" height="100%">
  <param name="source" value="GenericCWEApp.xap"/>
  <param name="onError" value="onSilverlightError" />
  <param name="background" value="white" />
  <param name="minRuntimeVersion" value="4.0.50826.0" />
  <param name="autoUpgrade" value="true" />
  <a href="http://go.microsoft.com/fwlink/?LinkID=149156&v=4.0.50826.0" style="text-decoration:none">
   <img src="http://go.microsoft.com/fwlink/?LinkId=161376" alt="Get Microsoft Silverlight" style="border-style:none"/>
  </a>
    </object><iframe id="_sl_historyFrame" style="visibility:hidden;height:0px;width:0px;border:0px"></iframe></div>
    </form>
</body>
</html>
```

The following example gets the hosting [Microsoft.Lync.Model.Conversation.Conversation](https://msdn.microsoft.com/library/jj276988\(v=office.15\)) object, sends a string to other conversation participants as contextual data, and displays any contextual data string sent by other conversation participants.

```csharp
using System;
using System.Windows;
using System.Windows.Controls;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Conversation;
using System.Diagnostics;

namespace GenericCWEApp
{
    public partial class MainPage : UserControl
    {
        //The GUID specifies the project. For a new application you should create another GUID
        //and then modify the reg file to reflect your new GUID. See SDK documentation for details.
        private const string ApplicationGuid = "{FA44026B-CC48-42DA-AAA8-B849BCB43A21}";
        private readonly Conversation _conversation;
        private readonly String _appData;

        public MainPage()
        {
            InitializeComponent();
            //Get the conversation from the Lync client
            try
            {
                _conversation = (Conversation)LyncClient.GetHostingConversation();
                this.Dispatcher.BeginInvoke(new UpdateLogDelegate(UpdateLog), new object[] { "Got hosting conversation" });
            }
            catch (LyncClientException lyncClientException)
            {
                this.Dispatcher.BeginInvoke(new UpdateLogDelegate(UpdateLog), new object[] { "Exception on GetHostingConversation "  + lyncClientException.Message});
                Debug.WriteLine(lyncClientException);
            }

            if (_conversation != null)
            {
                //Get the appdata from the conversation. 
                try
                {
                    _appData = _conversation.GetApplicationData(ApplicationGuid);
                }
                catch (LyncClientException lyncClientException)
                {
                    Debug.WriteLine(lyncClientException);
                }

                //Event to get fired when a context is received from other participants.
                _conversation.ContextDataReceived += new EventHandler<ContextEventArgs>(_conversation_ContextDataReceived);

            }
        }
        /// <summary>
        /// Local CWE receives context data from a one of three possible active CWE applications
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void  _conversation_ContextDataReceived(object sender, ContextEventArgs e)
        {
            //Does the application Id sent with the context data match the application GUID of this 
            //application?
            if (e.ApplicationId == ApplicationGuid)
            {
                if (e.ContextDataType == "string")
                {
                    this.Dispatcher.BeginInvoke(new UpdateLogDelegate(UpdateLog), new object[] { e.ContextData.ToString() + " received" });
                    TheirAnswer_Textblock.Text = e.ContextData.ToString();
                }
            }
        }

        private void SendQuestion_Button_Click(object sender, RoutedEventArgs e)
        {
            if (Question_Textbox.Text.Length == 0)
            {
                return;
            }
            if (_conversation == null)
            {
                return;
            }
            _conversation.BeginSendContextData(
                ApplicationGuid,
                "string",
                Question_Textbox.Text,
                (ar) =>
                {
                    _conversation.EndSendContextData(ar);
                    this.Dispatcher.BeginInvoke(new UpdateLogDelegate(UpdateLog), new object[] { Question_Textbox.Text + " sent" });
                },
                null);
            
        }

        private delegate void UpdateLogDelegate(string newValue);

        private void UpdateLog(string newValue)
        {
            eventlog_Listbox.Items.Add(newValue);
        }
    }

}
```

## Next steps

[How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md)

[How to: Start an extension application in a Lync conversation window](how-to-start-an-extension-application-in-a-lync-conversation-window.md)

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

