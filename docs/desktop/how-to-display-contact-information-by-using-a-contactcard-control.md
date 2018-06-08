---
title: 'How to: Display contact information by using a ContactCard control'
TOCTitle: 'How to: Display contact information by using a ContactCard control'
ms:assetid: 1b33e2d8-8df1-40e8-9354-9dedefa0b22e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937272(v=office.15)
ms:contentKeyID: 50877092
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# How to: Display contact information by using a ContactCard control

Learn how to use the Lync Controls ContactCard in a WPF window or Silverlight page to display contact information for a Lync user.

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
Create a Silverlight application<br />
Create a WPF application<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for displaying contact information are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

The [Microsoft.Lync.Controls.ContactCard](https://msdn.microsoft.com/en-us/library/hh379168\(v=office.15\)) control is dragged from the Lync toolbox onto the Visual Studio design surface and dropped into a container control such as a **Grid** or **StackPanel**. After setting the [Source](https://msdn.microsoft.com/en-us/library/hh363511\(v=office.15\)) property, the ContactCard control displays the contact information of a user.

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
<td><p><a href="control-source-property.md">Control Source property</a></p></td>
<td><p>Describes how to use the <a href="https://msdn.microsoft.com/en-us/library/hh363511(v=office.15)">Source</a> property to set the identity of the user whose contact card is to be shown.</p></td>
</tr>
</tbody>
</table>

## Create a Silverlight application

Use a [Grid](http://msdn2.microsoft.com/en-us/library/ms610550) as a container for a group of ContactCard controls.

### To create the Silverlight application

1.  Create a Lync Controls application using the Lync Silverlight Application template.
    
    For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

2.  In Page.xaml, replace the existing Grid control with the following example XAML text.

3.  Edit the Name and Source properties to provide valid values.
    
    ``` xaml
    <Grid>
     <Grid.ColumnDefinitions>
      <ColumnDefinition/>
      <ColumnDefinition/>
      </Grid.ColumnDefinitions>
     <Grid.RowDefinitions>
      <RowDefinition/>
      <RowDefinition/>
     </Grid.RowDefinitions>
     <controls:ContactCard x:Name="contact0"  IsExpanded="False" Source="sip:elise@contoso.com" Grid.Column="0" Grid.Row="0"/>
     <controls:ContactCard x:Name="contact1"  IsExpanded="False" Source="sip:robert@contoso.com" Grid.Column="0" Grid.Row="1"/>
     <controls:ContactCard x:Name="contact3"  IsExpanded="False" Source="sip:mary@contoso.com" Grid.Column="1" Grid.Row="0"/>
     <controls:ContactCard x:Name="contact4"  IsExpanded="False" Source="sip:john@contoso.com" Grid.Column="1" Grid.Row="1"/>
    </Grid>
    ```

4.  Build and run the application.
    
    In the Web page, the four contact cards appear.

## Create a WPF application

Use a Grid as a container for a group of ContactCard controls.

### To create the WPF walkthrough application

1.  Create a Lync Controls application using the Lync WPF Application template.
    
    For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

2.  In Window1.xaml, replace the existing Grid control with the example XAML text from step 2 in the previous procedure, edit the XAML, and then complete the remaining steps as described in that procedure.

## See also

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

