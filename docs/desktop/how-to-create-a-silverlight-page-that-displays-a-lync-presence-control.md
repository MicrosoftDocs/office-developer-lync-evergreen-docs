---
title: 'How to: Create a Silverlight page that displays a Lync presence control'
TOCTitle: 'How to: Create a Silverlight page that displays a Lync presence control'
ms:assetid: fb4bde62-9358-4c6f-af44-b84fa929f006
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933234(v=office.15)
ms:contentKeyID: 50877379
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Create a Silverlight page that displays a Lync presence control

Learn how to add a Microsoft Lync 2013 SDK PresenceIndicator control to a Silverlight page or WPF window and then publish the presence of a Lync user.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

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
Create a Silverlight application<br />
Create a WPF application<br />
Code example: Silverlight presence display page<br />
Additional resources</p></td>
<td><p><br />
</p>
<p></p></td>
</tr>
</tbody></tabe>

<div class="caption">
Watch the video: Add Presence to a WPF Application
</div>
<br />
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/04c69a9d-11bc-4750-b1aa-238bc8c7f5de]
<p></p></td>
</tr>

<table><tbody>
<tr class="even">
<td><p></p></td>
<td><p><img src="images/JJ933112.mod_icon_CodeGallery(Office.15).png" title="Code samples" alt="Code samples" /></p></td>
<td><p><a href="http://code.msdn.microsoft.com/lync-2013-use-a-silverlight-18a585be">Use a Silverlight control to indicate the presence of participants</a></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for creating a Silverlight page with a PresenceIndicator control are as follows:

  - Microsoft Lync 2013 SDK.

  - An available Microsoft Lync Server 2013 to sign a user in to.

  - Microsoft Lync 2013.

  - Supported operating systems: Microsoft Windows Vista, Microsoft Windows 7, Microsoft Windows 8, Microsoft Windows Server 2003, or Microsoft Windows Server 2008.

  - Microsoft Silverlight 4 SDK and Microsoft .NET Framework 4.0.

  - For WPF applications, one of the following editions of Microsoft Visual Studio development system: Visual Studio 2008 SP1 Standard Edition, Professional Edition, or Team Suite, Visual Basic 2008 Express Edition, Visual C\# 2008 Express Edition, Visual Studio 2010 , Visual Studio 2012, or Visual C\# 2010 Express.

  - For Silverlight applications: Microsoft Internet Explorer 7, Internet Explorer 8, or Internet Explorer 9. Microsoft Silverlight 4 Tools for Visual Studio 2010 and one of the following editions of Microsoft Visual Studio development system: Visual Studio 2010, Visual Basic 2010 Express, Visual Studio 2012, Visual C\# 2010 Express, or Visual Web Developer 2010 Express.

  - To make voice calls, make sure that your audio device is enabled so that you can make voice calls through Lync 2010.

## Create a Silverlight application

To display presence in a Silverlight application, use the Lync Silverlight Application template in Microsoft Visual Studio to create an application.

Security settings for Microsoft Lync 2013 SDK applications require that the host URL for Lync Control Silverlight applications be added to the Conversation window application trusted site list in the local system registry. For information about how to add a Silverlight application to the Trusted sites list, see [Lync 2013 system registry keys](lync-2013-system-registry-keys.md). Only Microsoft Internet Explorer 7 and later versions of Internet Explorer support Lync 2010 Silverlight controls.

### To create the Silverlight walkthrough application

1.  Sign in to Lync 2010.

2.  In Visual Studio, point to **New** on the **File** menu, and then click **Project**.

3.  In the **New Project** dialog box, expand **Visual C\#** in the **Installed Templates** pane, and then click **Silverlight**.

4.  In the center pane, click **Lync Silverlight Application**.

5.  In the **Name** and **Location** boxes, enter a name and path for the project, and then click **OK**.

6.  In the **New Silverlight Application** dialog box, clear the **Host the Silverlight application in a new Web site** check box, and then click **OK**.

7.  In Page.xaml, in the XAML pane, find the [PresenceIndicator](https://msdn.microsoft.com/en-us/library/hh345947\(v=office.15\)) control, and then edit the Source property to provide a valid value.

8.  Build and run the application.
    
    On the Web page, the PresenceIndicator control displays presence for the contact specified by the [Source](https://msdn.microsoft.com/en-us/library/hh363511\(v=office.15\)) property.

## Create a WPF application

To display presence in a WPF application, use the Lync WPF Application template in Microsoft Visual Studio to create an application.

### To create the WPF walkthrough application

1.  In the previous procedure, follow steps 1 through 3.

2.  In step 4, expand **Visual C\#** in the **Installed Templates** pane, and then click **Windows**.

3.  In the center pane, click **Lync WPF Application**.

4.  In the **Name** and **Location** boxes, enter a name and path for the project, and then click **OK**.

5.  In Window1.xaml, in the XAML pane, find the PresenceIndicator control, and then edit the Source property to provide a valid value.

6.  Build and run the application.
    
    In the active window, the PresenceIndicator control displays presence for the contact specified by the [Source](https://msdn.microsoft.com/en-us/library/hh363511\(v=office.15\)) property.

## Code example: Silverlight presence display page

The following example shows a Silverlight presence display page.

    <UserControl x:Class="LyncSilverlightApplication3.Page"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" 
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
        xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls" 
        mc:Ignorable="d" d:DesignWidth="640" d:DesignHeight="480">
        <Grid x:Name="LayoutRoot">
            <StackPanel Orientation="Horizontal" HorizontalAlignment="Center" VerticalAlignment="Center">
                <!-- 
                    Show the presence indicator. Hover over the icon to see the contact card.
                    Set Source to a valid SIP URI in your organization. 
                -->
                <controls:PresenceIndicator 
                    x:Name="Presence" 
                    Source="sip:john@contoso.com" 
                    PhotoDisplayMode="Large" 
                    />
                <!-- Use the DisplayName property from PresenceIndicator to show the user's name -->
                <TextBlock 
                    Text="{Binding DisplayName, ElementName=Presence}" 
                    Margin="4,0,0,0" 
                    VerticalAlignment="Center"
                    />
            </StackPanel>
        </Grid>
    </UserControl>

## Additional resources

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [Beyond the basics: Lync Controls](beyond-the-basics-lync-controls.md)

