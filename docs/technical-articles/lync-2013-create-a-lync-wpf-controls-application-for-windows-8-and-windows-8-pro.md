---
title: 'Lync 2013: Create a Lync WPF Controls application for Windows 8 and Windows 8 Pro'
TOCTitle: 'Lync 2013: Create a Lync WPF Controls application for Windows 8 and Windows 8 Pro'
ms:assetid: 9ae7fe3e-427e-4dc9-99cf-4924ebe7ef1e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn194144(v=office.15)
ms:contentKeyID: 52822157
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Lync 2013: Create a Lync WPF Controls application for Windows 8 and Windows 8 Pro

Learn how to use the Lync 2013 SDK to create a Lync Windows Presentation Foundation (WPF) Controls application for Windows 8 and Windows 8 Pro.


_**Applies to:** Lync 2013 | Lync Server 2013 | Visual Studio | Windows_

**Provided by:**  John Clarkson, Microsoft Corporation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Introduction<br />
Creating the Lync WPF Controls application<br />
Conclusion<br />
Additional resources</p></td>
<td><div class="caption">
Watch the video: Create a Lync WPF Controls application for Windows 8 and Windows 8 Pro
</div>
<br />
&gt; [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/0e8e89a8-b169-4214-ac08-e8cc3790c57e]</td>
</tr>
</tbody>
</table>


## Introduction

Applications that are developed with the Lync 2013 SDK run on the Windows 8 desktop. This article explains how to create a Lync WPF Controls application by using Lync Controls and also discusses how to pin the application to the Windows 8 Start screen.

### Requirements

  - Lync 2013 SDK.

  - Visual Studio 2010 and later versions of Visual Studio.

  - Lync 2013 client.
    

    > [!IMPORTANT]
    > <P>To run the Lync WPF Controls application, you must sign in to the Lync client.</P>



Figure 1.

  
![Windows 8 start screen](images/Dn194144.UC15All_TA_WpfWin8_fig01(Office.15).png "Windows 8 start screen")

## Creating the Lync WPF Controls application

To create the application, use Visual Studio to open a new project using the Lync WPF Application template, and then drag three controls onto the Design pane.

### To create the Lync Controls application

1.  On the Windows 8 Start screen, click **Visual Studio**.

2.  In Visual Studio, use the Lync WPF Application template to create an application.

3.  In the XAML pane, delete the XAML text between the two StackPanel elements.

4.  Set the following StackPanel attributes.
    
      - Orientation='Vertical'
    
      - HorizontalAlignment='Left'
    
      - VerticalAlignment='Top'

5.  In the Visual Studio Toolbox, select the Lync 2013 SDK **Controls** tab, and then drag the MyStatusArea control onto the Design pane. Position the control in the upper-left corner of the Design pane.

6.  Drag the ContactSearch control onto the Design pane. Position the control under the MyStatusArea control on the Design pane.

7.  Drag the ContactList control onto the Design pane. Position the control under the ContactSearch control on the Design pane.

8.  Press F5 to build and run the application.

9.  Before you start the next procedure, close the application.

### To start the application on the Windows 8 Start screen

1.  Use File Explorer to find the application .exe file, located in the bin/Debug folder.

2.  Right-click the .exe file and select **Pin to Start**.

3.  On the Windows 8 Start screen, click the application tile to start the application.

## Conclusion

Using the Lync 2013 SDK to create a Lync WPF Controls application for Windows 8 is similar to creating a Windows 7 application. The extra step is simply to pin the application .exe file to the Start screen.

Like other Windows desktop applications, Lync WPF applications can be installed on and started from the Windows 8 Start screen. But, because the Lync 2013 SDK was built for earlier Windows versions, applications developed with it run on the desktop rather than on the Start screen.

## Additional resources

  - [Lync 2013 SDK documentation](../desktop/lync-2013-sdk-documentation.md)

  - [Get started with Lync Controls](../desktop/get-started-with-lync-controls.md)

  - [Lync Dev Center](http://msdn.microsoft.com/en-us/lync/default.aspx)

  - [Download Center: Lync 2013 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=36824)

