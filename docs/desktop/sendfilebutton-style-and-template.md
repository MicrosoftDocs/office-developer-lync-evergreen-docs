---
title: SendFileButton style and template
TOCTitle: SendFileButton style and template
ms:assetid: 01f17d58-e770-4984-87dd-c0fa6ab60931
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937245(v=office.15)
ms:contentKeyID: 50877058
ms.date: 07/24/2014
mtps_version: v=office.15
---

# SendFileButton style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [SendFileButton](https://msdn.microsoft.com/en-us/library/hh347610\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.

**Last modified:** November 27, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

**In this article**  
SendFileButton parts  
Default style and template  
Additional resources  

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the SendFileButton control.

![SendFileButton Control](images/JJ945566.SendFileButtonControl(Office.15).png "SendFileButton Control")

## SendFileButton parts

The following table lists the named parts for the SendFileButton control.

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
<td><p>Launches a conversation with a specified contact, and opens a file selection dialog box.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the SendFileButton control.

    <Style x:Key="SendFileButtonStyle1" TargetType="{x:Type controls:SendFileButton}">
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:SendFileButton}">
        <Button x:Name="PART_CommandControl" AutomationProperties.AutomationId="SendFileButton" AutomationProperties.Name="Send file button" Microsoft_Lync_Controls_Internal_Framework_Commands:Command.Click="{Binding Model.SendFileCommand, RelativeSource={RelativeSource TemplatedParent}}" Microsoft_Lync_Controls_Internal_Framework_Commands:Command.CommandParameter="{Binding ContextualInformation, Converter={StaticResource ConversationContextToContextModelConverter}, RelativeSource={RelativeSource TemplatedParent}}" Style="{StaticResource GlobalIconButtonStyle}" Background="{TemplateBinding Background}" Padding="{TemplateBinding Padding}">
         <ToolTipService.ToolTip>
          <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ToolTipSendFile, Source={StaticResource ResourcesWrapper}}" />
         </ToolTipService.ToolTip>
         <Binding Path="Content" RelativeSource="{RelativeSource TemplatedParent}">
          <Binding.TargetNullValue>
           <ContentControl Style="{StaticResource IconStyle.ShareFile}" />
          </Binding.TargetNullValue>
         </Binding>
        </Button>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

