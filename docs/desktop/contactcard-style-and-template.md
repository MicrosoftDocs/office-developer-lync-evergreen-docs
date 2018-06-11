---
title: ContactCard style and template
TOCTitle: ContactCard style and template
ms:assetid: 7214ea80-2c40-4d48-a12b-f2088feca660
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933075(v=office.15)
ms:contentKeyID: 50877205
ms.date: 07/24/2014
mtps_version: v=office.15
---

# ContactCard style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the styles and templates for the [ContactCard](https://msdn.microsoft.com/en-us/library/hh379168\(v=office.15\)) control. You can modify the default [ControlTemplate](http://msdn.microsoft.com/en-us/library/system.windows.controls.controltemplate\(vs.95\).aspx) to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013

 

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the ContactCard control.

![ContactCard](images/JJ945582.ContactCard_rtm(Office.15).png "ContactCard")

## ContactCard parts

The following table lists the named parts for the ContactCard control.

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
<td><p>DetailsContainer</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.frameworkelement.aspx">FrameworkElement</a></p></td>
<td><p>Contains detailed information about the contact.</p></td>
</tr>
<tr class="even">
<td><p>NoteContainer</p></td>
<td><p>FrameworkElement</p></td>
<td><p>Contains the note for the contact card, which can be expanded or not.</p></td>
</tr>
<tr class="odd">
<td><p>ExpandDetailsToggleButton</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.primitives.togglebutton.aspx">ToggleButton</a></p></td>
<td><p>A button that expands or contracts the contact card.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the ContactCard control.

    <Style x:Key="ContactCardStyle1" BasedOn="{StaticResource FocusVisualStyleToNullStyle}" TargetType="controls:ContactCard">
      <Setter Property="Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper PropertyBindingCollection">
        <Setter Value>
          <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
            <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Binding="{Binding ContactCardBorderBrush, Source={StaticResource ControlColors}}" Property="BorderBrush"/>
            <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Binding="{Binding ContactCardBackgroundBrush, Source={StaticResource ControlColors}}" Property="Background"/>
          </Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
        </Setter Value>
      </Setter>
      <Setter Property="BorderThickness" Value="1"/>
      <Setter Property="Template">
        <Setter Value>
          <ControlTemplate TargetType="controls:ContactCard">
            <Border BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Background="{TemplateBinding Background}" CornerRadius="5" VerticalAlignment="Top" Width="300">
              <StackPanel Margin="{TemplateBinding Padding}">
                <Grid x:Name="PART_NoteContainer">
                  <Microsoft_Lync_Controls_Internal:ContactNote Background="{Binding ContactCardBubbleBackgroundBrush, Source={StaticResource ControlColors}}" Grid ColumnSpan="2" IsTabStop="False" Margin="-1,-1,-1,0" Grid Row="0" Source="{TemplateBinding Model}" Visibility="{Binding Source PresenceItems DefaultNote, Converter={StaticResource NullOrEmptyStringToVisibilityConverter}, FallbackValue=Collapsed, RelativeSource={RelativeSource Self}}"/>
                </Grid>
                <controls:ContactContentPresenter BotContentTemplate="{StaticResource ContactCardBriefBotDataTemplate}" ContextualInformation="{TemplateBinding ContextualInformation}" ContentType="{Binding Model ContactType, RelativeSource={RelativeSource TemplatedParent}}" Grid ColumnSpan="2" Content="{TemplateBinding Model}" GroupContentTemplate="{StaticResource ContactCardBriefDistributionListDataTemplate}" Height="52" Margin="0,6,0,0" PersonContentTemplate="{StaticResource ContactCardBriefPersonDataTemplate}" Grid Row="1" Grid RowSpan="1" TelephoneContentTemplate="{StaticResource ContactCardBriefTelephoneDataTemplate}"/>
                <Grid Height="22" Margin="6,8,2,3">
                  <Grid ColumnDefinitions>
                    <ColumnDefinition Width="*"/>
                    <ColumnDefinition Width="22"/>
                  </Grid ColumnDefinitions>
                  <Microsoft_Lync_Controls_Internal:ActionsBar ContextualInformation="{TemplateBinding ContextualInformation}" IsTabStop="False" Source="{TemplateBinding Model}"/>
                  <Rectangle Fill="{Binding ContactCardBorderBrushLight, Source={StaticResource ControlColors}}" HorizontalAlignment="Right" Height="20" Margin="0,0,2,0" Visibility="{TemplateBinding ExpanderVisibility}" Width="1"/>
                  <Microsoft_Lync_Controls_Internal:HelpTextToggleButton x:Name="PART_ExpandDetailsToggleButton" Grid Column="1" Height="22" IsChecked="{Binding IsExpanded, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" IsEnabled="{TemplateBinding IsSignedIn}" Style="{StaticResource FocusVisualStyleToNullStyle}" Template="{StaticResource ExpanderToggleButtonTemplate}" Visibility="{TemplateBinding ExpanderVisibility}" Width="22">
                    <ToolTipService ToolTip>
                      <ToolTip Content="{Binding IsExpanded, Converter={StaticResource BooleanToExpanderButtonToolTipConverter}, RelativeSource={RelativeSource TemplatedParent}}" Style="{StaticResource DefaultToolTipStyle}"/>
                    </ToolTipService ToolTip>
                    <ContentControl Style="{StaticResource IconStyle ExpanderWedge}"/>
                  </Microsoft_Lync_Controls_Internal:HelpTextToggleButton>
                </Grid>
                <Grid x:Name="PART_DetailsContainer">
                  <controls:ContactContentPresenter BotContentTemplate="{StaticResource ContactCardDetailsBotDataTemplate}" Background="{TemplateBinding Background}" ContextualInformation="{TemplateBinding ContextualInformation}" ContentType="{Binding Model ContactType, RelativeSource={RelativeSource TemplatedParent}}" Content="{TemplateBinding Model}" GroupContentTemplate="{StaticResource ContactCardDetailsDistributionListDataTemplate}" Height="Auto" PersonContentTemplate="{StaticResource ContactCardDetailsPersonDataTemplate}" SelectedTabIndex="{Binding SelectedTabIndex, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" TelephoneContentTemplate="{StaticResource ContactCardDetailsTelephoneDataTemplate}" Visibility="{Binding IsChecked, Converter={StaticResource BooleanToVisibilityConverter}, ElementName=PART_ExpandDetailsToggleButton}" VerticalAlignment="Top" Width="Auto"/>
                </Grid>
              </StackPanel>
            </Border>
          </ControlTemplate>
        </Setter Value>
      </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

