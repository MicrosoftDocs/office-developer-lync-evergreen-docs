---
title: StartVideoCallButton style and template
TOCTitle: StartVideoCallButton style and template
ms:assetid: 35cd9bb5-6502-4b67-9002-c66fbe99c313
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937301(v=office.15)
ms:contentKeyID: 50877127
ms.date: 07/24/2014
mtps_version: v=office.15
---

# StartVideoCallButton style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [StartVideoCallButton](https://msdn.microsoft.com/en-us/library/hh379584\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013

 

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the StartVideoCallButton control.

![StartVideoCallButton Control](images/JJ937301.StartVideoCallButtonControl(Office.15).png "StartVideoCallButton Control")

## StartVideoCallButton parts

The following table lists the named parts for the StartVideoCallButton control.

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
<td><p>Launches a video conversation.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the StartVideoCallButton control.

    <Style x:Key="StartVideoCallButtonStyle1" TargetType="{x:Type controls:StartVideoCallButton}">
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:StartVideoCallButton}">
        <Button x:Name="PART_CommandControl" AutomationProperties.AutomationId="StartVideoCallButton" AutomationProperties.Name="Start video call button" Microsoft_Lync_Controls_Internal_Framework_Commands:Command.Click="{Binding Model.StartVideoCommand, RelativeSource={RelativeSource TemplatedParent}}" Microsoft_Lync_Controls_Internal_Framework_Commands:Command.CommandParameter="{Binding ContextualInformation, Converter={StaticResource ConversationContextToContextModelConverter}, RelativeSource={RelativeSource TemplatedParent}}" Style="{StaticResource GlobalIconButtonStyle}" Background="{TemplateBinding Background}" Padding="{TemplateBinding Padding}">
         <ToolTipService.ToolTip>
          <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ToolTipStartVideo, Source={StaticResource ResourcesWrapper}}" />
         </ToolTipService.ToolTip>
         <Binding Path="Content" RelativeSource="{RelativeSource TemplatedParent}">
          <Binding.TargetNullValue>
           <ContentControl Style="{StaticResource IconStyle.StartVideo}" />
          </Binding.TargetNullValue>
         </Binding>
        </Button>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

