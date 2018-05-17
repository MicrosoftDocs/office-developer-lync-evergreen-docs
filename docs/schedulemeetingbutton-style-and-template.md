---
title: ScheduleMeetingButton style and template
TOCTitle: ScheduleMeetingButton style and template
ms:assetid: f3cacba0-caf2-47c0-a395-80f82eba9c54
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933230(v=office.15)
ms:contentKeyID: 50877374
ms.date: 07/24/2014
mtps_version: v=office.15
---

# ScheduleMeetingButton style and template

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [ScheduleMeetingButton](schedulemeetingbutton-class-microsoft-lync-controls_1.md) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
ScheduleMeetingButton parts  
Default style and template  
Additional resources  

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the ScheduleMeetingButton control.

![ScheduleMeetingButton Control](images/JJ933230.ScheduleMeetingButtonControl(Office.15).png "ScheduleMeetingButton Control")

## ScheduleMeetingButton parts

The following table lists the named parts for the ScheduleMeetingButton control.

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
<td><p>Launches the Microsoft Outlook dialog to initiate the desired action.</p></td>
</tr>
</tbody>
</table>


## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the ScheduleMeetingButton control.

    <Style x:Key="ScheduleMeetingButtonStyle1" TargetType="{x:Type controls:ScheduleMeetingButton}">
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:ScheduleMeetingButton}">
        <Button x:Name="PART_CommandControl" AutomationProperties.AutomationId="ScheduleMeetingButton" AutomationProperties.Name="Schedule meeting button" Microsoft_Lync_Controls_Internal_Framework_Commands:Command.Click="{Binding Model.ScheduleMeetingCommand, RelativeSource={RelativeSource TemplatedParent}}" Style="{StaticResource GlobalIconButtonStyle}" Background="{TemplateBinding Background}" Padding="{TemplateBinding Padding}">
         <ToolTipService.ToolTip>
          <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ToolTipScheduleMeeting, Source={StaticResource ResourcesWrapper}}" />
         </ToolTipService.ToolTip>
         <Binding Path="Content" RelativeSource="{RelativeSource TemplatedParent}">
          <Binding.TargetNullValue>
           <ContentControl Style="{StaticResource IconStyle.ScheduleMeetings}" />
          </Binding.TargetNullValue>
         </Binding>                    
        </Button>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

