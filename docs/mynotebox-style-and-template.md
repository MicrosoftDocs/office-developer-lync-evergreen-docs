---
title: MyNoteBox style and template
TOCTitle: MyNoteBox style and template
ms:assetid: 455d5856-6391-4f42-8b09-542ffcc79633
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937324(v=office.15)
ms:contentKeyID: 50877157
ms.date: 07/24/2014
mtps_version: v=office.15
---

# MyNoteBox style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [MyNoteBox](https://msdn.microsoft.com/en-us/library/hh346137\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.

**Last modified:** November 27, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

**In this article**  
MyNoteBox parts  
Default style and template  
Additional resources  

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the MyNoteBox control.

![MyNoteBox Control](images/JJ937324.MyNoteBoxControl(Office.15).png "MyNoteBox Control")

## MyNoteBox parts

The following table lists the named parts for the MyNoteBox control.

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
<td><p>EditNoteToggleButton</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.primitives.togglebutton.aspx">ToggleButton</a></p></td>
<td><p>A button that switches the note state.</p></td>
</tr>
<tr class="even">
<td><p>NoteEditTextBox</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.textbox.aspx">TextBox</a></p></td>
<td><p>Use this part to display or edit the note.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the MyNoteBox control.

    <Style x:Key="MyNoteBoxStyle1" BasedOn="{StaticResource FocusVisualStyleToNullStyle}" TargetType="controls:MyNoteBox">
     <Setter Property="Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper.PropertyBindingCollection">
      <Setter.Value>
       <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Binding="{Binding GlobalTextColor_MediumDark, Source={StaticResource ControlColors}}" Property="Foreground"/>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Binding="{Binding MyNoteBoxBackgroundBrush, Source={StaticResource ControlColors}}" Property="Background"/>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Binding="{Binding MyNoteBoxBorderBrush, Source={StaticResource ControlColors}}" Property="BorderBrush"/>
       </Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
      </Setter.Value>
     </Setter>
     <Setter Property="HorizontalContentAlignment" Value="Stretch"/>
     <Setter Property="VerticalContentAlignment" Value="Center"/>
     <Setter Property="BorderThickness" Value="1"/>
     <Setter Property="Padding" Value="5,0"/>
     <Setter Property="FontSize" Value="10.6"/>
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="controls:MyNoteBox">
        <Grid HorizontalAlignment="Stretch" VerticalAlignment="Stretch">
         <VisualStateManager.VisualStateGroups>
          <VisualStateGroup x:Name="CommonStates">
           <VisualState x:Name="Normal"/>
           <VisualState x:Name="Focused">
            <Storyboard>
             <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" Duration="00:00:00.0010000" Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="FocusedBorder">
              <DiscreteObjectKeyFrame KeyTime="0">
               <DiscreteObjectKeyFrame.Value>
                <Visibility>Visible</Visibility>
               </DiscreteObjectKeyFrame.Value>
              </DiscreteObjectKeyFrame>
             </ObjectAnimationUsingKeyFrames>
            </Storyboard>
           </VisualState>
          </VisualStateGroup>
         </VisualStateManager.VisualStateGroups>
         <Border BorderBrush="#7FFFFFFF" BorderThickness="1" CornerRadius="4">
          <Grid>
           <Border BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Background="{TemplateBinding Background}" CornerRadius="2"/>
           <Border x:Name="FocusedBorder" BorderThickness="{TemplateBinding BorderThickness}" CornerRadius="2" Visibility="Collapsed">
            <Border.BorderBrush>
             <LinearGradientBrush EndPoint="0.5,1" StartPoint="0.5,0">
              <GradientStop Color="#FF71CAE3"/>
              <GradientStop Color="#FF71CAE3" Offset="1"/>
             </LinearGradientBrush>
            </Border.BorderBrush>
           </Border>
          </Grid>
         </Border>
         <Grid Margin="{TemplateBinding BorderThickness}">
          <ToggleButton x:Name="PART_EditNoteToggleButton" AutomationProperties.AutomationId="DefaultNoteToggleButton" Cursor="IBeam" HorizontalAlignment="Stretch" Height="Auto" IsChecked="False" IsEnabled="{TemplateBinding IsEnabled}" MinHeight="22" AutomationProperties.Name="Default note toggle button" Style="{StaticResource FocusVisualStyleToNullStyle}" VerticalAlignment="Stretch" Width="Auto">
           <ToolTipService.ToolTip>
            <ToolTip MaxWidth="250" Style="{StaticResource DefaultToolTipStyle}" Visibility="{Binding PersonalNote, Converter={StaticResource NullOrEmptyStringToVisibilityConverter}, RelativeSource={RelativeSource TemplatedParent}}">
             <TextBlock TextWrapping="Wrap" Text="{Binding PersonalNote, RelativeSource={RelativeSource TemplatedParent}}"/>
            </ToolTip>
           </ToolTipService.ToolTip>
           <ToggleButton.Template>
            <ControlTemplate TargetType="ContentControl">
             <Border Background="Transparent">
              <ContentPresenter Content="{TemplateBinding Content}"/>
             </Border>
            </ControlTemplate>
           </ToggleButton.Template>
           <Grid AutomationProperties.AutomationId="NonEditModeContainer" Background="Transparent" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Height="Auto" Visibility="{Binding IsChecked, Converter={StaticResource NotBooleanToVisibilityConverter}, ElementName=PART_EditNoteToggleButton}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
            <Microsoft_Lync_Controls_Internal:TruncatedTextBlock x:Name="PART_NonEditModeActualText" AutomationProperties.AutomationId="NonEditModeActualText" Foreground="{TemplateBinding Foreground}" Margin="{TemplateBinding Padding}" Style="{TemplateBinding FontSize}" Text="{Binding PersonalNote, Converter={StaticResource StringToSingleLineStringConverter}, RelativeSource={RelativeSource TemplatedParent}}" UseEllipsis="True" Visibility="{Binding PersonalNote, Converter={StaticResource NullOrEmptyStringToVisibilityConverter}, RelativeSource={RelativeSource TemplatedParent}}"/>
            <Microsoft_Lync_Controls_Internal:TruncatedTextBlock x:Name="NonEditModeWatermark" AutomationProperties.AutomationId="NonEditModeWatermark" Foreground="{TemplateBinding Foreground}" Margin="{TemplateBinding Padding}" Style="{TemplateBinding FontSize}" Text="{Binding Resources.MyNoteBoxWatermark, Source={StaticResource ResourcesWrapper}}" UseEllipsis="True" Visibility="{Binding PersonalNote, Converter={StaticResource NotNullOrEmptyStringToVisibility}, RelativeSource={RelativeSource TemplatedParent}}"/>
           </Grid>
          </ToggleButton>
          <TextBox x:Name="PART_NoteEditTextBox" AutomationProperties.AutomationId="NoteEditTextBox" AcceptsReturn="True" BorderThickness="0" Background="Transparent" Foreground="{TemplateBinding Foreground}" FontSize="{TemplateBinding FontSize}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" IsEnabled="{TemplateBinding IsEnabled}" Margin="{TemplateBinding Padding}" Padding="-2,0,0,0" Style="{StaticResource MyNoteTextBoxStyle}" Text="{Binding PersonalNote, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" Visibility="{Binding IsChecked, Converter={StaticResource BooleanToVisibilityConverter}, ElementName=PART_EditNoteToggleButton, Mode=OneWay}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
         </Grid>
        </Grid>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

