---
title: 'How to: Display a customized list of team contacts in Lync SDK'
TOCTitle: 'How to: Display a customized list of team contacts'
ms:assetid: d827a477-b314-4365-881c-a94db022631c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933206(v=office.15)
ms:contentKeyID: 50877348
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# How to: Display a customized list of team contacts in Lync SDK

Learn how to use the [CustomContactList](https://msdn.microsoft.com/en-us/library/hh346321\(v=office.15\)) control in Microsoft Lync Control applications to display an arbitrary customized list of contacts, using Microsoft Silverlight or Microsoft Windows Presentation Foundation (WPF). Each item in the contacts list is provided by a [CustomContactListItem](https://msdn.microsoft.com/en-us/library/hh346017\(v=office.15\)) control.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

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
Display a custom contact list on a Silverlight page<br />
Create a WPF page<br />
Code example: Custom contact group page<br />
Additional resources</p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-customize-the-1ad7a5d3">Customize the contact list view in a WPF application</a></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for displaying a custom contact list are as follows:

  - Microsoft Lync 2013 SDK.

  - An available Microsoft Lync Server 2013 to sign a user in to.

  - Microsoft Lync 2013.

  - Supported operating systems: Microsoft Windows Vista, Microsoft Windows 7, Microsoft Windows 8, Microsoft Windows Server 2003, or Microsoft Windows Server 2008.

  - Microsoft Silverlight 4 SDK and Microsoft .NET Framework 4.0.

  - For WPF applications, one of the following editions of Microsoft Visual Studio development system: Visual Studio 2008 SP1 Standard Edition, Professional Edition, or Team Suite, Visual Basic 2008 Express Edition, Visual C\# 2008 Express Edition, Visual Studio 2010 , Visual Studio 2012, or Visual C\# 2010 Express.

  - For Silverlight applications: Microsoft Internet Explorer 7, Internet Explorer 8, or Internet Explorer 9. Microsoft Silverlight 4 Tools for Visual Studio 2010 and one of the following editions of Microsoft Visual Studio development system: Visual Studio 2010, Visual Basic 2010 Express, Visual Studio 2012, Visual C\# 2010 Express, or Visual Web Developer 2010 Express.

  - To make voice calls, make sure that your audio device is enabled so that you can make voice calls through Lync 2010.

## Display a custom contact list on a Silverlight page

### To create a Silverlight page

1.  Use the Lync Silverlight Application template to create a new Microsoft Silverlight Lync Control application.
    
    For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

2.  In Page.xaml, replace the contents of the [Grid](http://msdn2.microsoft.com/en-us/library/ms610550) control with the following XAML.
    
    ``` xaml
    <StackPanel>
      <controls:CustomContactList Height="300" ContactLayoutView="TwoLines">
          <controls:CustomContactListItem Source="sip:elise@contoso.com"/>
          <controls:CustomContactListItem Source="tel:12065550100"/>
          <controls:CustomContactListItem Source="administrators@contoso.com"/>
      </controls:CustomContactList>
    </StackPanel>
    ```

3.  Edit the [Source](https://msdn.microsoft.com/en-us/library/hh363511\(v=office.15\)) properties on the CustomContactListItem controls to provide valid values.

4.  Build and run the application.
    
    The Web page displays three contacts.

## Create a WPF page

### To create a WPF walkthrough application

1.  Use the Lync WPF Application template to create a new WPF Lync Control application.
    
    For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

2.  Edit the Window1.xaml page as described in step 2 in the previous procedure, and then follow steps 3 and 4 in that procedure.

## Code example: Custom contact group page

The following example declares a WPF page that contains a [Microsoft.Lync.Controls.CustomContactList](https://msdn.microsoft.com/en-us/library/hh346321\(v=office.15\)) that includes several nested [Microsoft.Lync.Controls.CustomContactListItem](https://msdn.microsoft.com/en-us/library/hh346017\(v=office.15\)) objects.

``` xaml
<Window x:Class="LyncWpfApplication2.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
    Title="Custom Contact List - my work group" Height="Auto" Width="Auto">
    <Grid>
        <StackPanel>
            <controls:CustomContactList Height="300" ContactLayoutView="TwoLines">
                <controls:CustomContactListItem Source="sip:elise@contoso.com"/>
                <controls:CustomContactListItem Source="tel:12065550100"/>
                <controls:CustomContactListItem Source="administrators@contoso.com"/>
            </controls:CustomContactList>
        </StackPanel>
    </Grid>

</Window>
```

## Additional resources

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

