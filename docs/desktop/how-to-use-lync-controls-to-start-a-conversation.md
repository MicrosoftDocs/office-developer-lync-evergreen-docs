---
title: 'How to: Use Lync Controls to start a conversation'
TOCTitle: 'How to: Use Lync Controls to start a conversation'
ms:assetid: 2d4d498a-2469-4b39-884f-8733fc032a26
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937291(v=office.15)
ms:contentKeyID: 50877120
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
- csharp
---

# How to: Use Lync Controls to start a conversation

Learn how to implement a click-to-call feature in your WPF or Silverlight page by using any of several different kinds of Lync Controls.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Lync Controls overview<br />
Create a click-to-call feature<br />
Code examples: Start an IM call<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-start-new-9d1d6e20">Start new conversations from a WPF application</a><br />
<a href="http://code.msdn.microsoft.com/lync-2013-start-new-6e1ca269">Start new conversations from a Silverlight application</a></p></td>
</tr>
</tbody>
</table>

## Lync Controls overview

There are several Lync Controls that let you start a new conversation a single click. In some cases, the control starts a conversation in a single modality. In other cases, a user can select among several Lync 2013 conversation modalities. In general, the Lync Controls that provide this feature are controls whose instance exists in the context of a single SIP URI. For example, the [Microsoft.Lync.Controls.ContactListItem](https://msdn.microsoft.com/library/hh363984\(v=office.15\)) has a source property that takes a SIP or TEL URI that corresponds to a user or a telephone number. When the control is clicked, a conversation is started with the user or a person at the telephone number.

Other Lync Controls, such as the ContactSearch compound control, display individual contact-based elements that can be clicked to start conversations.

## Prerequisites

The prerequisites for using a Lync Controls to start a conversation are as follows:

  - Microsoft Lync 2013 SDK.

  - An available Microsoft Lync Server 2013 to sign a user in to.

  - Microsoft Lync 2013.

  - Supported operating systems: Microsoft Windows Vista, Microsoft Windows 7, Microsoft Windows 8, Microsoft Windows Server 2003, or Microsoft Windows Server 2008.

  - Microsoft Silverlight 4 SDK and Microsoft .NET Framework 4.0.

  - For WPF applications, one of the following editions of Microsoft Visual Studio development system: Visual Studio 2008 SP1 Standard Edition, Professional Edition, or Team Suite, Visual Basic 2008 Express Edition, Visual C\# 2008 Express Edition, Visual Studio 2010, Visual Studio 2012, or Visual C\# 2010 Express.

  - For Silverlight applications: Microsoft Internet Explorer 7, Internet Explorer 8, or Internet Explorer 9. Microsoft Silverlight 4 Tools for Visual Studio 2010 and one of the following editions of Microsoft Visual Studio development system: Visual Studio 2010, Visual Basic 2010 Express, Visual Studio 2012, Visual C\# 2010 Express, or Visual Web Developer 2010 Express.

  - To make voice calls, make sure that your audio device is enabled so that you can make voice calls through Lync 2010.

## Create a click-to-call feature

To create a click-to-call feature, you must have at least one SIP URI or TEL URI that you can provide as the [ContactBase.Source](https://msdn.microsoft.com/library/hh363511\(v=office.15\)) property value of the control that starts the call.

### To populate the control

1.  Inside of the containing element such as a stack panel, add the following XAML declaration.
    
    ```xaml
                    <controls:StartInstantMessagingButton Name="StartIM" Width="20" Height="20"/>
    ```

2.  Set the [ContactBase.Source](https://msdn.microsoft.com/library/hh363511\(v=office.15\)) property to the SIP URI of the user that is to be called.
    
    The following example sets the **Source** property of the **StartInstantMessagingButton** control and the display name of the user to be contacted as the text of the **ContactName** text block.
    
    ```csharp
            private void SetupIMButton(string contactURI)
            {
                ContactName.Text = "IM " + 
                    LyncClient.GetClient().
                    ContactManager.
                    GetContactByUri(contactURI).
                    GetContactInformation(ContactInformationType.DisplayName).ToString() + " " ;
                StartIM.Source = contactURI;
            }
    ```

## Code examples: Start an IM call

The following code declares a XAML window that displays a text box with the name of a user and a [Microsoft.Lync.Controls.StartInstantMessagingButton](https://msdn.microsoft.com/library/hh379340\(v=office.15\)) control that starts an IM conversation with the user.

    <Window x:Class="LyncWpfApplication2.Window1"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
        Title="Custom Contact List - my work group" Height="Auto" Width="Auto" mc:Ignorable="d" xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" SizeToContent="WidthAndHeight" >
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="10*"/>
                <ColumnDefinition Width="30*"/>
            </Grid.ColumnDefinitions>
            <StackPanel Grid.Column="1">
                <StackPanel Grid.Column="1" Orientation="Horizontal">
                    <TextBlock Name="ContactName" Text=""/>
                    <controls:StartInstantMessagingButton Name="StartIM" Width="20" Height="20"/>
                </StackPanel>
            </StackPanel>
        </Grid>
    
    </Window>

The following example sets the text property of the text block in the previous example and then sets the SIP URI **Source** property of the [Microsoft.Lync.Controls.StartInstantMessagingButton](https://msdn.microsoft.com/library/hh379340\(v=office.15\)) control.

```csharp
using System.Windows;
using Microsoft.Lync.Model;

namespace LyncWpfApplication2
{
    /// <summary>
    /// Interaction logic for Window1.xaml
    /// </summary>
    public partial class Window1 : Window
    {
        public Window1()
        {
            InitializeComponent();
            SetupIMButton("DaniloPSolano@contoso.com");
        }
        public Window1(string contactSIPUri)
        {
            InitializeComponent();
            SetupIMButton(contactSIPUri);
        }

        private void SetupIMButton(string contactURI)
        {
            ContactName.Text = "IM " + 
                LyncClient.GetClient().
                ContactManager.
                GetContactByUri(contactURI).
                GetContactInformation(ContactInformationType.DisplayName).ToString() + " " ;
            StartIM.Source = contactURI;
        }
    }
}
```

## See also

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

