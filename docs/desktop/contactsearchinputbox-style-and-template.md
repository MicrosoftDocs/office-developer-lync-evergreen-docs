---
title: ContactSearchInputBox style and template
TOCTitle: ContactSearchInputBox style and template
ms:assetid: ff41861a-3aa7-45d3-89be-bc05ba69224e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933258(v=office.15)
ms:contentKeyID: 50877404
ms.date: 07/24/2014
mtps_version: v=office.15
---

# ContactSearchInputBox style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [ContactSearchInputBox](https://msdn.microsoft.com/library/hh379719\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013

 

There are no [Style](http://msdn.microsoft.com/library/system.windows.style\(vs.95\).aspx) properties for the ContactSearchInputBox control.

![ContactSearchInputBox Control](images/JJ945549.ContactSearchInputBoxControl(Office.15).png "ContactSearchInputBox Control")

## ContactSearchInputBox parts

The following table lists the named parts for the ContactSearchInputBox control.

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
<td><p>ClearButton</p></td>
<td><p><a href="http://msdn.microsoft.com/library/system.windows.controls.button.aspx">Button</a></p></td>
<td><p>Clears the search string.</p></td>
</tr>
<tr class="even">
<td><p>SearchHint</p></td>
<td><p><a href="http://msdn.microsoft.com/library/system.windows.controls.contentcontrol.aspx">ContentControl</a></p></td>
<td><p>Provides the content of a search hint.</p></td>
</tr>
<tr class="odd">
<td><p>TextSearch</p></td>
<td><p><a href="http://msdn.microsoft.com/library/system.windows.controls.textbox.aspx">TextBox</a></p></td>
<td><p>Use this part to display or edit the search string.</p></td>
</tr>
</tbody>
</table>

## ContactSearchInputBox states

The following table lists the visual states for the ContactSearchInputBox control.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>VisualState Name</p></th>
<th><p>VisualStateGroup Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SearchInUse</p></td>
<td><p>SearchInUseStates</p></td>
<td><p>The ContactSearchInputBox control is in use.</p></td>
</tr>
<tr class="even">
<td><p>SearchNotInUse</p></td>
<td><p>SearchInUseStates</p></td>
<td><p>The ContactSearchInputBox control is not in use.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the ContactSearchInputBox control.

    <Style x:Key="ContactSearchInputBoxStyle1" TargetType="{x:Type controls:ContactSearchInputBox}">
     <Setter Property="Padding" Value="8,6,8,4" />
     <Setter Property="Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper.PropertyBindingCollection">
      <Setter.Value>
       <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Property="Background" Binding="{Binding DefaultControlBackgroundBrush, Source={StaticResource ControlColors}}" />
       </Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
      </Setter.Value>
     </Setter>
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:ContactSearchInputBox}">
        <Border Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}">
         <Rtc_System_Windows:VisualStateManager.VisualStateGroups>
          <Rtc_System_Windows:VisualStateGroup x:Name="SearchInUseStates">
           <Rtc_System_Windows:VisualStateGroup.Transitions>
            <Rtc_System_Windows:VisualTransition GeneratedDuration="00:00:00.2000000" />
           </Rtc_System_Windows:VisualStateGroup.Transitions>
           <Rtc_System_Windows:VisualState x:Name="SearchInUse">
            <Storyboard>
             <DoubleAnimationUsingKeyFrames BeginTime="00:00:00" Duration="00:00:00.0010000" Storyboard.TargetName="PART_SearchHint" Storyboard.TargetProperty="(UIElement.Opacity)">
              <LinearDoubleKeyFrame KeyTime="00:00:00" Value="0" />
             </DoubleAnimationUsingKeyFrames>
             <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" Duration="00:00:00.0010000" Storyboard.TargetName="PART_ClearButton" Storyboard.TargetProperty="(UIElement.Visibility)">
              <DiscreteObjectKeyFrame KeyTime="0">
               <DiscreteObjectKeyFrame.Value>
                <Visibility>Visible</Visibility>
               </DiscreteObjectKeyFrame.Value>
              </DiscreteObjectKeyFrame>
             </ObjectAnimationUsingKeyFrames>
            </Storyboard>
           </Rtc_System_Windows:VisualState>
           <Rtc_System_Windows:VisualState x:Name="SearchNotInUse" />
          </Rtc_System_Windows:VisualStateGroup>
         </Rtc_System_Windows:VisualStateManager.VisualStateGroups>
         <Grid Margin="{TemplateBinding Padding}">
          <Grid.RowDefinitions>
           <RowDefinition />
           <RowDefinition />
          </Grid.RowDefinitions>                
          <Border BorderThickness="1" CornerRadius="3" BorderBrush="White">
           <Microsoft_Lync_Controls_Internal:WatermarkedTextBox x:Name="PART_TextSearch" AutomationProperties.AutomationId="ContactSearchInputTextBox" AutomationProperties.Name="Contact search input text box" MaxLength="256" Watermark="{Binding IsSkillSearchEnabled, Converter={StaticResource SearchInputWatermarkConveter}, RelativeSource={RelativeSource TemplatedParent}}" IsEnabled="{TemplateBinding IsSignedIn}" Height="26" BorderThickness="1" BorderBrush="{Binding ContactSearchBorderBrush, Source={StaticResource ControlColors}}" Background="{Binding ContactSearchBackgroundBrush, Source={StaticResource ControlColors}}" Padding="8,0,31,0" Style="{StaticResource GlobalTextBoxSizeStyle.Standard}" Foreground="{Binding GlobalTextColor_Dark, Source={StaticResource ControlColors}}">
            <ToolTipService.ToolTip>
             <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.SearchInputNameTooltip, Source={StaticResource ResourcesWrapper}}" />
            </ToolTipService.ToolTip>
           </Microsoft_Lync_Controls_Internal:WatermarkedTextBox>
          </Border>
          <Microsoft_Lync_Controls_Internal:HelpTextButton x:Name="PART_ClearButton" Style="{StaticResource SearchCancelButtonStyle}" HorizontalAlignment="Right" VerticalAlignment="Center" Height="24" Width="23" Margin="2" IsEnabled="{TemplateBinding IsSignedIn}" Visibility="Collapsed">
           <ToolTipService.ToolTip>
            <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.SearchInputCloseButtonTooltip, Source={StaticResource ResourcesWrapper}}" />
           </ToolTipService.ToolTip>
           <ContentControl HorizontalAlignment="Left" IsHitTestVisible="False" Style="{StaticResource IconStyle.CloseSearch}" />
          </Microsoft_Lync_Controls_Internal:HelpTextButton>
          <ContentControl x:Name="PART_SearchHint" Margin="0,0,4,0" HorizontalAlignment="Right" IsHitTestVisible="False" Style="{StaticResource IconStyle.Search}" />
          <StackPanel Grid.Row="1" Orientation="Horizontal" Height="26">
           <Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton Style="{StaticResource ListFilterRadioButtonStyle}" Content="{Binding Resources.SearchInputFilterName, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}" AutomationProperties.AutomationId="NameSearchButton" IsEnabled="{TemplateBinding IsSignedIn}" IsChecked="{Binding SearchType, ConverterParameter=Name, Converter={StaticResource EnumToBoolConverter}, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" Margin="0,4,0,4">
            <ToolTipService.ToolTip>
             <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.SearchInputNameButtonTooltip, Source={StaticResource ResourcesWrapper}}" />
            </ToolTipService.ToolTip>
           </Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton>
           <Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton Style="{StaticResource ListFilterRadioButtonStyle}" Content="{Binding Resources.SearchInputFilterSkill, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}" AutomationProperties.AutomationId="KeywordSearchButton" IsEnabled="{TemplateBinding IsSignedIn}" IsChecked="{Binding SearchType, ConverterParameter=Skill, Converter={StaticResource EnumToBoolConverter}, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" Visibility="{Binding IsSkillSearchEnabled, Converter={StaticResource BooleanToVisibilityConverter}, RelativeSource={RelativeSource TemplatedParent}}">
            <ToolTipService.ToolTip>
             <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.SearchInputSkillButtonTooltip, Source={StaticResource ResourcesWrapper}}" />
            </ToolTipService.ToolTip>
           </Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton>
          </StackPanel>
         </Grid>
        </Border>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

