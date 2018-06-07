---
title: 'Lync 2013: Create a Lync Silverlight Controls application for Windows 8 and Windows 8 Pro'
TOCTitle: 'Lync 2013: Create a Lync Silverlight Controls application for Windows 8 and Windows 8 Pro'
ms:assetid: e7a3e9c5-e259-43f5-85ab-1f245a7f9ce9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn194313(v=office.15)
ms:contentKeyID: 52825045
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Lync 2013: Create a Lync Silverlight Controls application for Windows 8 and Windows 8 Pro

Learn how to use the Lync 2013 SDK to create a Lync Silverlight Controls application for Windows 8 and Windows 8 Pro.


_**Applies to:** Lync 2013 | Lync Server 2013 | Visual Studio | Windows_

**Provided by:**  John Clarkson, Microsoft Corporation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Introduction<br />
Creating the Lync Silverlight Controls application<br />
Conclusion<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

<div class="caption">
Watch the video: Create a Lync Silverlight Controls application for Windows 8 and Windows 8 Pro
</div>
<br />
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/e7a3e9c5-e259-43f5-85ab-1f245a7f9ce9]

## Introduction

Applications that are developed with the Lync 2013 SDK run on the Windows 8 desktop. This article describes how to create a Lync Silverlight Controls application by using Lync Controls and also discusses how to open the Silverlight application in Internet Explorer.

### Requirements

  - Lync 2013 SDK.

  - Visual Studio 2010 and later versions of Visual Studio.


> [!NOTE]
> <P>To run the Lync Silverlight Controls application, you must sign in to the Lync client.</P>



Figure 1.

  
![Internet Explorer and Silverlight application](images/Dn194313.UC15All_TA_SilverlightWin8_fig01(Office.15).png "Internet Explorer and Silverlight application")

## Creating the Lync Silverlight Controls application

To create the application, use Visual Studio to open a new project by using the Lync Silverlight Application template, and then drag three controls onto the Design pane.

### To create the Lync Controls application

1.  On the Windows 8 Start Screen, click **Visual Studio**.

2.  In Visual Studio, use the Lync Silverlight Application template to create an application.

3.  In the XAML pane, delete the XAML text between the two StackPanel elements.

4.  Set the following StackPanel attributes.
    
      - Orientation='Vertical'
    
      - HorizontalAlignment='Left'
    
      - VerticalAlignment='Top'

5.  Add attributes for Height and Width, and then set both to 300.

6.  In the Visual Studio Toolbox, in the Lync 2013 SDK **Controls** tab, drag the MyStatusArea control onto the Design pane. Position the control in the upper-left corner of the Design pane.

7.  Drag the ContactSearch control onto the Design pane. Position the control under the MyStatusArea control on the Design pane.

8.  Drag the ContactList control onto the Design pane. Position the control under the ContactSearch control on the Design pane. This creates the XAML code in the following example.
    
    ``` xaml
    <UserControl x:Class="LyncSilverlightApplication.MainPage"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
        mc:Ignorable="d">
            <Grid x:Name="LayoutRoot">
            <StackPanel Width="300" Height="300" Orientation="Vertical" HorizontalAlignment="Left" VerticalAlignment="Top">
                <controls:MyStatusArea/>
                <controls:ContactSearch/>
                <controls:ContactList Height="102"/>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

9.  Press F5 to build and run the application.

10. Before you start the next procedure, close the application.

### To open the application

1.  On the Windows 8 desktop, start Internet Explorer.

2.  In the browser history, click the Silverlight application that was created in the previous procedure.

## Conclusion

Using the Lync 2013 SDK to create a Lync Silverlight Controls application for Windows 8 resembles creating a Windows 7 application. Like Silverlight applications in earleir versions of Windows, it is possible to start a Windows 8 Silverlight application from the browser history list.

## Additional resources

  - [Lync 2013 SDK documentation](../desktop/lync-2013-sdk-documentation.md)

  - [Get started with Lync Controls](../desktop/get-started-with-lync-controls.md)

  - [Lync Dev Center](http://msdn.microsoft.com/en-us/lync/default.aspx)

  - [Download Center: Lync 2013 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=36824)

