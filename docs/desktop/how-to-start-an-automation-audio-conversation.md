---
title: 'How to: Start an automation audio conversation'
TOCTitle: 'How to: Start an automation audio conversation'
ms:assetid: 7d89f1a6-8b42-4532-96cf-b85a5c3c3009
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933093(v=office.15)
ms:contentKeyID: 50877225
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
- xaml
---

# How to: Start an automation audio conversation

Learn how to use Microsoft Lync 2013 SDK to automate opening a new Microsoft Lync 2013 conversation window to host an audio conversation with another Lync 2013 client.

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
Create an audio conversation application<br />
Code examples: Automation conversation starter<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for starting an automation audio conversation are as follows:

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
<td><p><a href="conversation-window-automation-in-lync-sdk.md">Conversation window automation in Lync SDK</a></p></td>
<td><p>Describes the scope of automation through the <a href="https://msdn.microsoft.com/en-us/library/jj278382(v=office.15)">Microsoft.Lync.Model.Extensibility</a> namespace.</p></td>
</tr>
</tbody>
</table>

## Create an audio conversation application

Conversations can only be started when the user is signed in to Lync 2013. Read about [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before adding an audio conversation to your UI.

To start an audio conversation, get a [Microsoft.Lync.Model.Extensibility.Automation](https://msdn.microsoft.com/en-us/library/jj293816\(v=office.15\)) object, create IEnumerable objects to contain a URI or a phone number, set instances of [Microsoft.Lync.Model.Extensibility.AutomationModalities](https://msdn.microsoft.com/en-us/library/jj266471\(v=office.15\)) and [Microsoft.Lync.Model.Extensibility.AutomationModalitySettings](https://msdn.microsoft.com/en-us/library/jj276319\(v=office.15\)), and then call the [Automation.BeginStartConversation](https://msdn.microsoft.com/en-us/library/jj276136\(v=office.15\)) method.

### To create the audio conversation application

1.  Sign in to Microsoft Lync 2013.

2.  In Microsoft Visual Studio, create a new Windows Forms application.

3.  Select .NET Framework 3.5 or 4.0 as the target framework.
    
    For more information, see [How to: Target a Specific .NET Framework](http://go.microsoft.com/fwlink/?linkid=168798).

4.  Add a reference to the assembly **Microsoft.Lync.Model**.

5.  In Form1.cs, add the following using statement.
    
    ``` csharp
    using Microsoft.Lync.Model;
    using Microsoft.Lync.Model.Extensibility;
    ```

6.  In the command button click event handler, add the following code.
    
    ``` csharp
    // Create a generic List object to contain the URI to call.
    // Edit this to provide a valid URI.
    List<string> participantUri = new List<string>();
    participantUri.Add(GetSip.Text);
    
    // Start the conversation.
    LyncClient.GetAutomation().BeginStartConversation(
        AutomationModalities.Audio,
        participantUri,
        null,
        (ar) =>
        {
            try
            {
                ConversationWindow newWindow = LyncClient.GetAutomation().EndStartConversation(ar);
            }
            catch (OperationException oe) { MessageBox.Show("Operation exception on start conversation " + oe.Message); };
        },
        null);
    ```

7.  Build and run the application.

8.  Listen to the ringtone from Microsoft Lync 2013 on the calling computer and see the accept call request on the computer you called.

## Code examples: Automation conversation starter

The following sample is a WPF window that accepts a SIP URI and automates the starting of a Lync 2013 conversation window that hosts a conversation between the local user and the user or telephone number whose URI the input value is resolved to.

The following example declares a WPF window that accepts a string URI and shows a command button that opens a new conversation window with a person or a PSTN phone.

``` xaml
<Window x:Class="AutomationPhoneCall.Page1"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="100" Width="300">
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="140"/>
            <ColumnDefinition Width="80*"/>
        </Grid.ColumnDefinitions>
        <StackPanel Grid.Column="0">
            <TextBox Name="GetSip" Text="enter SIP" Margin="20,20,20,0"/>
        </StackPanel>
        <Button Grid.Column="1" Name="Go_Button" Content="Call" Margin="10,10,10,10" Click="Go_Button_Click"/>
    </Grid>
</Window>
```

The following example automates a new Lync 2013 conversation window with the audio modality and connects to the user that was resolved by the supplied SIP URI.

``` csharp
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
        public Page1()
        {
            InitializeComponent();
        }

        private void Go_Button_Click(object sender, RoutedEventArgs e)
        {
            if ( GetSip.Text.Length == 0)
            {
                return;
            }
            List<string> participantUri = new List<string>();
            participantUri.Add(GetSip.Text);
            LyncClient.GetAutomation().BeginStartConversation(
                AutomationModalities.Audio,
                participantUri,
                null,
                (ar) =>
                {
                    try
                    {
                        ConversationWindow newWindow = LyncClient.GetAutomation().EndStartConversation(ar);
                    }
                    catch (OperationException oe) { MessageBox.Show("Operation exception on start conversation " + oe.Message); };
                },
                null);
        }
    }
}
```

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

