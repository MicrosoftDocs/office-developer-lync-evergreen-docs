---
title: StartAudioCallButton style and template
TOCTitle: StartAudioCallButton style and template
ms:assetid: 43ab7dd2-d51a-497f-b0e7-982368e51aaf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937323(v=office.15)
ms:contentKeyID: 50877154
ms.date: 07/24/2014
mtps_version: v=office.15
---

# StartAudioCallButton style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [StartAudioCallButton](https://msdn.microsoft.com/en-us/library/hh378744\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013



There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the StartAudioCallButton control.

![StartAudioCallButton Control](images/JJ945562.StartAudioCallButtonControl(Office.15).png "StartAudioCallButton Control")

## StartAudioCallButton parts

The following table lists the named parts for the StartAudioCallButton control.

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
<td><p>Opens a Microsoft Lync 2010 conversation window and starts a voice conversation.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the StartAudioCallButton control.

    <Style x:Key="StartAudioCallButtonStyle1" TargetType="{x:Type controls:StartAudioCallButton}">
     <Setter Property="HorizontalContentAlignment" Value="Center" />
     <Setter Property="VerticalContentAlignment" Value="Center" />
     <Setter Property="FontWeight" Value="Normal" />
     <Setter Property="Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper.PropertyBindingCollection">
      <Setter.Value>
       <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Property="Content" Binding="{Binding Model.DefaultEndpoint, Converter={StaticResource EndpointTypeToControlConverter}, RelativeSource={RelativeSource Self}}" />
       </Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
      </Setter.Value>
     </Setter>
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:StartAudioCallButton}">
        <Microsoft_Lync_Controls_Internal:SplitButton x:Name="PART_CommandControl" AutomationProperties.AutomationId="StartAudioVideoButton" DataContext="{TemplateBinding Model}" Command="{Binding StartAudioVideoCommand}" CommandParameter="{Binding ContextualInformation, Converter={StaticResource ConversationContextToContextModelConverter}, RelativeSource={RelativeSource TemplatedParent}}" IsEnabled="False" Content="{TemplateBinding Content}" Background="{TemplateBinding Background}" Padding="{TemplateBinding Padding}" HorizontalContentAlignment="{TemplateBinding HorizontalContentAlignment}" VerticalContentAlignment="{TemplateBinding VerticalContentAlignment}">
         <Microsoft_Lync_Controls_Internal:SplitButton.LeftToolTip>
          <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Model.DefaultEndpoint, Converter={StaticResource EndpointTypeToStartAudioCallButtonToolTipConverter}, RelativeSource={RelativeSource TemplatedParent}}" />
         </Microsoft_Lync_Controls_Internal:SplitButton.LeftToolTip>
         <Microsoft_Lync_Controls_Internal:SplitButton.RightToolTip>
          <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.StartAudioCallButtonRightToolTip, Source={StaticResource ResourcesWrapper}}" />
         </Microsoft_Lync_Controls_Internal:SplitButton.RightToolTip>
         <Microsoft_Lync_Controls_Internal:SplitButton.DropDown>
          <Microsoft_Lync_Controls_Internal:ContextMenu Style="{StaticResource ContextMenuDefaultStyle}" ItemsSource="{TemplateBinding ContextInformationModels}" ItemContainerStyle="{StaticResource ContactDropDownMenuItemStyle}" FontStyle="{TemplateBinding FontStyle}" FontSize="10.6" FontFamily="{TemplateBinding FontFamily}" FontWeight="{TemplateBinding FontWeight}" />
         </Microsoft_Lync_Controls_Internal:SplitButton.DropDown>
        </Microsoft_Lync_Controls_Internal:SplitButton>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

