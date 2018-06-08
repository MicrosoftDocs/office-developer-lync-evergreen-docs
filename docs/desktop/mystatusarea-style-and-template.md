---
title: MyStatusArea style and template
TOCTitle: MyStatusArea style and template
ms:assetid: 62a51658-9598-4405-83b6-5904baba0d4f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933064(v=office.15)
ms:contentKeyID: 50877194
ms.date: 07/24/2014
mtps_version: v=office.15
---

# MyStatusArea style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [MyStatusArea](https://msdn.microsoft.com/en-us/library/hh363503\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013

There are no states or parts or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the MyStatusArea control.

![MyStatusArea Control](images/JJ945575.MyStatusAreaControl(Office.15).png "MyStatusArea Control")

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the MyStatusArea control.

    <Style x:Key="MyStatusAreaStyle1" TargetType="{x:Type controls:MyStatusArea}">
     <Setter Property="Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper.PropertyBindingCollection">
      <Setter.Value>
       <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Property="Foreground" Binding="{Binding GlobalTextColor_Black, Source={StaticResource ControlColors}}" />
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Property="Background" Binding="{Binding DefaultControlBackgroundBrush, Source={StaticResource ControlColors}}" />
       </Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
      </Setter.Value>
     </Setter>
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:MyStatusArea}">
        <Border BorderBrush="{TemplateBinding BorderBrush}" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}">
         <Rtc_System_Windows:VisualStateManager.VisualStateGroups>
          <Rtc_System_Windows:VisualStateGroup x:Name="PhotoModeStates">
           <Rtc_System_Windows:VisualState x:Name="PhotoHidden">
            <Storyboard>
             <DoubleAnimation Duration="0" From="0" To="16" Storyboard.TargetProperty="(FrameworkElement.Width)" Storyboard.TargetName="PART_AvailabilityIcon" />
             <DoubleAnimation Duration="0" From="0" To="16" Storyboard.TargetProperty="(FrameworkElement.Height)" Storyboard.TargetName="PART_AvailabilityIcon" />
             <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(FrameworkElement.Margin)" Storyboard.TargetName="PART_AvailabilityIconContentControl">
              <DiscreteObjectKeyFrame KeyTime="0">
               <DiscreteObjectKeyFrame.Value>
                <Thickness>6,2,6,0</Thickness>
               </DiscreteObjectKeyFrame.Value>
              </DiscreteObjectKeyFrame>
             </ObjectAnimationUsingKeyFrames>
             <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="PhotoDisplayMode" Storyboard.TargetName="PART_AvailabilityIcon">
              <DiscreteObjectKeyFrame KeyTime="0">
               <DiscreteObjectKeyFrame.Value>
                <controls:PhotoDisplayMode>Hidden</controls:PhotoDisplayMode>
               </DiscreteObjectKeyFrame.Value>
              </DiscreteObjectKeyFrame>
             </ObjectAnimationUsingKeyFrames>
            </Storyboard>
           </Rtc_System_Windows:VisualState>
           <Rtc_System_Windows:VisualState x:Name="PhotoSmall">
            <Storyboard>
             <DoubleAnimation Duration="0" From="0" To="45" Storyboard.TargetProperty="(FrameworkElement.Width)" Storyboard.TargetName="PART_AvailabilityIcon" />
             <DoubleAnimation Duration="0" From="0" To="36" Storyboard.TargetProperty="(FrameworkElement.Height)" Storyboard.TargetName="PART_AvailabilityIcon" />
             <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="PhotoDisplayMode" Storyboard.TargetName="PART_AvailabilityIcon">
              <DiscreteObjectKeyFrame KeyTime="0">
               <DiscreteObjectKeyFrame.Value>
                <controls:PhotoDisplayMode>Small</controls:PhotoDisplayMode>
               </DiscreteObjectKeyFrame.Value>
              </DiscreteObjectKeyFrame>
             </ObjectAnimationUsingKeyFrames>
            </Storyboard>
           </Rtc_System_Windows:VisualState>
           <Rtc_System_Windows:VisualState x:Name="PhotoLarge">
            <Storyboard>
             <DoubleAnimation Duration="0" From="0" To="61" Storyboard.TargetProperty="(FrameworkElement.Width)" Storyboard.TargetName="PART_AvailabilityIcon" />
             <DoubleAnimation Duration="0" From="0" To="52" Storyboard.TargetProperty="(FrameworkElement.Height)" Storyboard.TargetName="PART_AvailabilityIcon" />
             <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="PhotoDisplayMode" Storyboard.TargetName="PART_AvailabilityIcon">
              <DiscreteObjectKeyFrame KeyTime="0">
               <DiscreteObjectKeyFrame.Value>
                <controls:PhotoDisplayMode>Large</controls:PhotoDisplayMode>
               </DiscreteObjectKeyFrame.Value>
              </DiscreteObjectKeyFrame>
             </ObjectAnimationUsingKeyFrames>
            </Storyboard>
           </Rtc_System_Windows:VisualState>
          </Rtc_System_Windows:VisualStateGroup>
         </Rtc_System_Windows:VisualStateManager.VisualStateGroups>
         <StackPanel Margin="{TemplateBinding Padding}">                            
          <controls:MyNoteBox Foreground="{TemplateBinding Foreground}" />
          <Grid Height="Auto" Width="Auto" Margin="0,-1,0,0">                                
           <Grid.RowDefinitions>
            <RowDefinition Height="6" />
            <RowDefinition Height="20" />
            <RowDefinition Height="16" />
            <RowDefinition Height="16" />
           </Grid.RowDefinitions>
           <Grid.ColumnDefinitions>                                    
            <ColumnDefinition Width="Auto" />                                   
            <ColumnDefinition Width="*" />
           </Grid.ColumnDefinitions>
           <Canvas Grid.Column="1" Margin="2,-2,0,0" Width="10.034" Height="10.723" HorizontalAlignment="Left" VerticalAlignment="Top">
            <Path Stretch="Fill" Width="8.744" Height="8.462" Data="M201.71561,184.84197 L201.65289,195.37144 212.28231,184.79956" Fill="{Binding MyNoteBoxBackgroundBrush, Source={StaticResource ControlColors}}" Stroke="{Binding MyNoteBoxBorderBrush, Source={StaticResource ControlColors}}" StrokeLineJoin="Round" Canvas.Left="0.993" />
            <Path Stretch="Fill" Width="10.034" Height="9.55" Data="M201.69698,185.08987 L201.65289,197.04248 214.05387,184.92965" Stroke="#7FFFFFFF" StrokeLineJoin="Round" Canvas.Top="1.173" />
           </Canvas>
           <ContentControl x:Name="PART_AvailabilityIconContentControl" Grid.Column="0" Grid.Row="1" Grid.RowSpan="3" Margin="0,0,6,0" Style="{StaticResource FocusVisualStyleToNullStyle}" HorizontalAlignment="Left" VerticalAlignment="Top">
            <ContentControl.Template>
             <ControlTemplate TargetType="{x:Type ContentControl}">
              <ContentPresenter Content="{TemplateBinding Content}" />
             </ControlTemplate>
            </ContentControl.Template>
            <controls:AvailabilityIcon x:Name="PART_AvailabilityIcon" AutomationProperties.AutomationId="AvailabilityIcon" Source="{Binding Model.Contact, RelativeSource={RelativeSource TemplatedParent}}" IsTabStop="False" />
           </ContentControl>
           <Microsoft_Lync_Controls_Internal:TruncatedTextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Model.Contact.PresenceItems.Name, RelativeSource={RelativeSource TemplatedParent}}" Foreground="{TemplateBinding Foreground}" Style="{StaticResource GlobalTruncatedTextSizeStyle.Medium}" VerticalAlignment="Bottom" Margin="2,0,0,0" AutomationProperties.AutomationId="Name">
            <ToolTipService.ToolTip>
             <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Model.Contact.PresenceItems.Name, RelativeSource={RelativeSource TemplatedParent}}" />
            </ToolTipService.ToolTip>
            </Microsoft_Lync_Controls_Internal:TruncatedTextBlock>
           <controls:MyPresenceChooser Grid.Row="2" Grid.Column="1" HorizontalAlignment="Left" />
           <Microsoft_Lync_Controls_Internal:TruncatedTextBlock Grid.Row="3" Grid.Column="1" Text="{Binding Model.Contact.PresenceItems.Location, RelativeSource={RelativeSource TemplatedParent}}" Foreground="{TemplateBinding Foreground}" Style="{StaticResource GlobalTruncatedTextSizeStyle.Standard}" HorizontalAlignment="Left" Margin="2,0,0,0" AutomationProperties.AutomationId="Location" />
          </Grid>
         </StackPanel>
        </Border>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

