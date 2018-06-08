---
title: ShareDesktopButton style and template
TOCTitle: ShareDesktopButton style and template
ms:assetid: 4fffb5e9-2075-4fd8-a79c-cd340ac9d839
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933043(v=office.15)
ms:contentKeyID: 50877172
ms.date: 07/24/2014
mtps_version: v=office.15
---

# ShareDesktopButton style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [ShareDesktopButton](https://msdn.microsoft.com/en-us/library/hh363609\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.

**Last modified:** November 27, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

**In this article**  
ShareDesktopButton parts  
Default style and template  
Additional resources  

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the ShareDesktopButton control.

![ShareDesktopButton Control](images/JJ945561.ShareDesktopButtonControl(Office.15).png "ShareDesktopButton Control")

## ShareDesktopButton parts

The following table lists the named parts for the ShareDesktopButton control.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Part</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CommandControl</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.control.aspx">Control</a></p></td>
<td><p>Launches desktop sharing between the user who activated the control, and another user or group.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the ShareDesktopButton control.

    <Style x:Key="ShareDesktopButtonStyle1" TargetType="{x:Type controls:ShareDesktopButton}">
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:ShareDesktopButton}">
        <Microsoft_Lync_Controls_Internal:SplitButton Grid.Row="1" x:Name="PART_CommandControl" AutomationProperties.Name="Share desktop split button" Style="{StaticResource SplitButtonSecondaryWithoutDefaultStyle}" Background="{TemplateBinding Background}" Padding="{TemplateBinding Padding}">
         <Microsoft_Lync_Controls_Internal:SplitButton.DropDown>
          <Microsoft_Lync_Controls_Internal:ContextMenu ItemsSource="{TemplateBinding ContextInformationModels}" ItemContainerStyle="{StaticResource ShareDesktopMenuItemStyle}" FontFamily="{TemplateBinding FontFamily}" FontWeight="{TemplateBinding FontWeight}" FontStyle="{TemplateBinding FontStyle}" />
         </Microsoft_Lync_Controls_Internal:SplitButton.DropDown>
         <ToolTipService.ToolTip>
          <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ToolTipShareDesktop, Source={StaticResource ResourcesWrapper}}" />
         </ToolTipService.ToolTip>
         <Binding Path="Content" RelativeSource="{RelativeSource TemplatedParent}">
          <Binding.TargetNullValue>
           <ContentControl Style="{StaticResource IconStyle.StartShare}" />
          </Binding.TargetNullValue>
         </Binding>
        </Microsoft_Lync_Controls_Internal:SplitButton>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

