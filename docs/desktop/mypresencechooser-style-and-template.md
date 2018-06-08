---
title: MyPresenceChooser style and template
TOCTitle: MyPresenceChooser style and template
ms:assetid: 8f514079-60dd-4ca9-baf2-7cc9ed792c0a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933130(v=office.15)
ms:contentKeyID: 50877267
ms.date: 07/24/2014
mtps_version: v=office.15
---

# MyPresenceChooser style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [MyPresenceChooser](https://msdn.microsoft.com/en-us/library/hh379434\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013

There are no states or parts or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the MyPresenceChooser control.

![MyPresenceChooser Control](images/JJ933130.MyPresenceChooserControl(Office.15).png "MyPresenceChooser Control")

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the MyPresenceChooser control.

    <Style x:Key="MyPresenceChooserStyle1" TargetType="controls:MyPresenceChooser">
     <Setter Property="Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper.PropertyBindingCollection">
      <Setter.Value>
       <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Binding="{Binding GlobalTextColor_Black, Source={StaticResource ControlColors}}" Property="Foreground"/>
       </Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
      </Setter.Value>
     </Setter>
     <Setter Property="Height" Value="16"/>
     <Setter Property="FontSize" Value="10.6"/>
     <Setter Property="Padding" Value="2,0,0,0"/>
     <Setter Property="Width" Value="Auto"/>
     <Setter Property="HorizontalAlignment" Value="Left"/>
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="controls:MyPresenceChooser">
        <Border BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Background="{TemplateBinding Background}">
         <Microsoft_Lync_Controls_Internal:SplitButton AutomationProperties.AutomationId="MyPresenceChooserSplitButton" Content="{Binding Model.Contact.PresenceItems.ActivityString, RelativeSource={RelativeSource TemplatedParent}}" HorizontalContentAlignment="{TemplateBinding HorizontalContentAlignment}" IsEnabled="{TemplateBinding IsSignedIn}" Padding="{TemplateBinding Padding}" Style="{StaticResource SplitButtonWithoutDefaultStyle}" VerticalContentAlignment="{TemplateBinding VerticalContentAlignment}" Width="Auto">
          <Microsoft_Lync_Controls_Internal:SplitButton.DropDown>
           <Microsoft_Lync_Controls_Internal:ContextMenu AutomationProperties.AutomationId="AvailabilityDropDownMenu" FontSize="10.6" ItemContainerStyle="{StaticResource CustomPresenceMenuItemStyle}" Style="{StaticResource ContextMenuDefaultStyle}">
            <Microsoft_Lync_Controls_Internal:ContextMenu.ItemsSource>
             <Microsoft_Lync_Controls_Internal_Common:CompoundCollection>
              <Microsoft_Lync_Controls_Internal:MenuItem Command="{Binding Model.SetAvailabilityCommand, RelativeSource={RelativeSource TemplatedParent}}" Header="{Binding Resources.MyPresenceChooserAvailable, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}">
               <Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
                <Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>Free</Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>
               </Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
               <Microsoft_Lync_Controls_Internal:MenuItem.Icon>
                <ContentControl Height="10" Template="{StaticResource ContactAvailability.Solitary.Available}" Width="10"/>
               </Microsoft_Lync_Controls_Internal:MenuItem.Icon>
              </Microsoft_Lync_Controls_Internal:MenuItem>
              <Microsoft_Lync_Controls_Internal:MenuItem Command="{Binding Model.SetAvailabilityCommand, RelativeSource={RelativeSource TemplatedParent}}" Header="{Binding Resources.MyPresenceChooserBusy, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}">
               <Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
                <Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>Busy</Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>
               </Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
               <Microsoft_Lync_Controls_Internal:MenuItem.Icon>
                <ContentControl Height="10" Template="{StaticResource ContactAvailability.Solitary.Busy}" Width="10"/>
               </Microsoft_Lync_Controls_Internal:MenuItem.Icon>
              </Microsoft_Lync_Controls_Internal:MenuItem>
              <Microsoft_Lync_Controls_Internal:MenuItem Command="{Binding Model.SetAvailabilityCommand, RelativeSource={RelativeSource TemplatedParent}}" Header="{Binding Resources.MyPresenceChooserDoNotDisturb, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}">
               <Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
                <Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>DoNotDisturb</Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>
               </Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
               <Microsoft_Lync_Controls_Internal:MenuItem.Icon>
                <ContentControl Height="10" Template="{StaticResource ContactAvailability.Solitary.DoNotDisturb}" Width="10"/>
               </Microsoft_Lync_Controls_Internal:MenuItem.Icon>
              </Microsoft_Lync_Controls_Internal:MenuItem>
              <Microsoft_Lync_Controls_Internal:MenuItem Command="{Binding Model.SetAvailabilityCommand, RelativeSource={RelativeSource TemplatedParent}}" Header="{Binding Resources.MyPresenceChooserBeRightBack, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}">
               <Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
                <Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>TemporaryUnalertable</Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>
               </Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
               <Microsoft_Lync_Controls_Internal:MenuItem.Icon>
                <ContentControl Height="10" Template="{StaticResource ContactAvailability.Solitary.Away}" Width="10"/>
               </Microsoft_Lync_Controls_Internal:MenuItem.Icon>
              </Microsoft_Lync_Controls_Internal:MenuItem>
              <Microsoft_Lync_Controls_Internal:MenuItem Command="{Binding Model.SetActivityIdCommand, RelativeSource={RelativeSource TemplatedParent}}" Header="{Binding Resources.MyPresenceChooserOffWork, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}">
               <Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
                <Microsoft_Lync_Controls_Internal_Model:PublishableActivityId>OffWork</Microsoft_Lync_Controls_Internal_Model:PublishableActivityId>
               </Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
               <Microsoft_Lync_Controls_Internal:MenuItem.Icon>
                <ContentControl Height="10" Template="{StaticResource ContactAvailability.Solitary.Away}" Width="10"/>
               </Microsoft_Lync_Controls_Internal:MenuItem.Icon>
              </Microsoft_Lync_Controls_Internal:MenuItem>
              <Microsoft_Lync_Controls_Internal:MenuItem Command="{Binding Model.SetAvailabilityCommand, RelativeSource={RelativeSource TemplatedParent}}" Header="{Binding Resources.MyPresenceChooserAppearAway, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}">
               <Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
                <Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>Unalertable</Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>
               </Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
               <Microsoft_Lync_Controls_Internal:MenuItem.Icon>
                <ContentControl Height="10" Template="{StaticResource ContactAvailability.Solitary.Away}" Width="10"/>
               </Microsoft_Lync_Controls_Internal:MenuItem.Icon>
              </Microsoft_Lync_Controls_Internal:MenuItem>
              <Microsoft_Lync_Controls_Internal:MenuItem Command="{Binding Model.SetAvailabilityCommand, RelativeSource={RelativeSource TemplatedParent}}" Header="{Binding Resources.MyPresenceChooserResetStatus, Converter={StaticResource StringToAcceleratorConverter}, Source={StaticResource ResourcesWrapper}}">
               <Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
                <Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>None</Microsoft_Lync_Controls_Internal_Model:PresenceAvailability>
               </Microsoft_Lync_Controls_Internal:MenuItem.CommandParameter>
              </Microsoft_Lync_Controls_Internal:MenuItem>
              <Microsoft_Lync_Controls_Internal:MenuItem Height="3" IsTabStop="False" Style="{StaticResource MenuItemSeparatorStyle}" Template="{StaticResource MenuItemSeparatorTemplate}" Visibility="{Binding Model.CustomPresenceList, ConverterParameter=1, Converter={StaticResource EnumberableContainsGreaterThanEqualToVisibilityConverter}, RelativeSource={RelativeSource TemplatedParent}}"/>
              <Microsoft_Lync_Controls_Internal_Common:CompoundCollectionPart Collection="{Binding Model.CustomPresenceList, RelativeSource={RelativeSource TemplatedParent}}"/>
             </Microsoft_Lync_Controls_Internal_Common:CompoundCollection>
            </Microsoft_Lync_Controls_Internal:ContextMenu.ItemsSource>
           </Microsoft_Lync_Controls_Internal:ContextMenu>
          </Microsoft_Lync_Controls_Internal:SplitButton.DropDown>
          <Microsoft_Lync_Controls_Internal:SplitButton.RightToolTip>
           <ToolTip Content="{Binding Resources.ToolTipSetAvailability, Source={StaticResource ResourcesWrapper}}" Style="{StaticResource DefaultToolTipStyle}"/>
          </Microsoft_Lync_Controls_Internal:SplitButton.RightToolTip>
         </Microsoft_Lync_Controls_Internal:SplitButton>
        </Border>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

