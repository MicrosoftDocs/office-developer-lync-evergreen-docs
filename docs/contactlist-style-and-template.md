---
title: ContactList style and template
TOCTitle: ContactList style and template
ms:assetid: cdf0e828-6841-4bfd-98a8-39c10b658703
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933196(v=office.15)
ms:contentKeyID: 50877337
ms.date: 07/24/2014
mtps_version: v=office.15
---

# ContactList style and template

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the styles and templates for the [ContactList](contactlist-class-microsoft-lync-controls_1.md) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
ContactList parts  
Default style and template  
Additional resources  

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the ContactList control.

![ContactList](images/JJ945579.ContactList_rtm(Office.15).png "ContactList")

## ContactList parts

The following table lists the named parts for the ContactList control.

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
<td><p>TreeControl</p></td>
<td><p>UCTreeView</p></td>
<td><p>Displays hierarchical data in a tree structure that has items that can expand and collapse.</p></td>
</tr>
</tbody>
</table>


## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the ContactList control.

    <Style x:Key="ContactListStyle1" TargetType="{x:Type controls:ContactList}">
     <Setter Property="ScrollViewer.HorizontalScrollBarVisibility" Value="Disabled" />
     <Setter Property="ScrollViewer.VerticalScrollBarVisibility" Value="Auto" />
     <Setter Property="Background" Value="{Binding DefaultControlBackgroundBrush, Source={StaticResource ControlColors}}" />
     <Setter Property="Template">
      <Setter.Value>               
       <ControlTemplate TargetType="{x:Type controls:ContactList}">
        <ControlTemplate.Resources>                       
         <Style BasedOn="{StaticResource MenuItemDefaultStyle}" TargetType="{x:Type Microsoft_Lync_Controls_Internal:MenuItem}" />
         <Style BasedOn="{StaticResource MenuItemDefaultStyle}" TargetType="{x:Type Microsoft_Lync_Controls_Internal:RadioMenuItem}" />
        </ControlTemplate.Resources>
        <Border Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}">
         <Grid x:Name="PART_ContactListGrid" IsEnabled="{TemplateBinding IsSignedIn}">
          <Grid.RowDefinitions>                               
           <RowDefinition Height="Auto" />                                
           <RowDefinition />
          </Grid.RowDefinitions>                            
          <Grid x:Name="PART_PivotBar" AutomationProperties.AutomationId="PivotBar" Visibility="{Binding ShowPivotBar, Converter={StaticResource BooleanToVisibilityConverter}, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}">
           <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="10" />
           </Grid.RowDefinitions>
           <Grid Visibility="{Binding IsChecked, Converter={StaticResource BooleanToVisibilityConverter}, ElementName=PivotBarDivider}" Height="26">
            <Grid.ColumnDefinitions>                           
             <ColumnDefinition Width="Auto" />
             <ColumnDefinition Width="Auto" />
             <ColumnDefinition Width="Auto" />                            
             <ColumnDefinition Width="*" />
            </Grid.ColumnDefinitions>                        
            <Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton Style="{StaticResource ListFilterRadioButtonStyle}" Grid.Column="0" GroupName="ViewByOptions" Content="{Binding Resources.ContactListFilterGroup, Source={StaticResource ResourcesWrapper}}" AutomationProperties.AutomationId="ViewByGroupButton" IsEnabled="{Binding IsSignedIn, RelativeSource={RelativeSource TemplatedParent}}" IsChecked="{Binding GroupViewBySetting, ConverterParameter=Groups, Converter={StaticResource EnumToBoolConverter}, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}">
             <ToolTipService.ToolTip>
              <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ContactListFilterGroupToolTip, Source={StaticResource ResourcesWrapper}}" />
             </ToolTipService.ToolTip>
            </Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton>
            <Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton Style="{StaticResource ListFilterRadioButtonStyle}" Grid.Column="1" GroupName="ViewByOptions" Content="{Binding Resources.ContactListFilterStatus, Source={StaticResource ResourcesWrapper}}" AutomationProperties.AutomationId="ViewByStatusButton" IsEnabled="{Binding IsSignedIn, RelativeSource={RelativeSource TemplatedParent}}" IsChecked="{Binding GroupViewBySetting, ConverterParameter=Status, Converter={StaticResource EnumToBoolConverter}, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}">
             <ToolTipService.ToolTip>
              <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ContactListFilterStatusToolTip, Source={StaticResource ResourcesWrapper}}" />
             </ToolTipService.ToolTip>
            </Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton>
            <Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton Style="{StaticResource ListFilterRadioButtonStyle}" Grid.Column="2" GroupName="ViewByOptions" Content="{Binding Resources.ContactListFilterRelationship, Source={StaticResource ResourcesWrapper}}" AutomationProperties.AutomationId="ViewByRelationshipButton" IsEnabled="{Binding IsSignedIn, RelativeSource={RelativeSource TemplatedParent}}" IsChecked="{Binding GroupViewBySetting, ConverterParameter=Relationship, Converter={StaticResource EnumToBoolConverter}, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}">
             <ToolTipService.ToolTip>
              <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ContactListFilterRelationshipToolTip, Source={StaticResource ResourcesWrapper}}" />
             </ToolTipService.ToolTip>
            </Microsoft_Lync_Controls_Internal:EnterEnabledRadioButton>                        
            <Microsoft_Lync_Controls_Internal:SplitButton x:Name="PART_ViewLayoutMenu" Grid.Column="3" HorizontalAlignment="Right" VerticalAlignment="Center" IsEnabled="{Binding IsSignedIn, RelativeSource={RelativeSource TemplatedParent}}" AutomationProperties.AutomationId="ViewLayoutMenu" Style="{StaticResource SplitButtonControlTertiaryStyle}" Height="22" Padding="2,0,2,0">
             <Microsoft_Lync_Controls_Internal:SplitButton.LeftToolTip>
              <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ToolTipContactListLayoutMenuLeft, Source={StaticResource ResourcesWrapper}}" />
             </Microsoft_Lync_Controls_Internal:SplitButton.LeftToolTip>
             <Microsoft_Lync_Controls_Internal:SplitButton.RightToolTip>
              <ToolTip Style="{StaticResource DefaultToolTipStyle}" Content="{Binding Resources.ToolTipContactListLayoutMenuRight, Source={StaticResource ResourcesWrapper}}" />
             </Microsoft_Lync_Controls_Internal:SplitButton.RightToolTip>                                       
             <Microsoft_Lync_Controls_Internal:SplitButton.DropDown>
              <Microsoft_Lync_Controls_Internal:ContextMenu Template="{StaticResource ContextMenuDefaultTemplate}">                                               
               <Microsoft_Lync_Controls_Internal:RadioMenuItem x:Name="PART_OneLineMenuItem" GroupName="LineViewGroup" Header="{Binding Resources.ContactListViewOneLine, Source={StaticResource ResourcesWrapper}}">
                <Microsoft_Lync_Controls_Internal:RadioMenuItem.Icon>
                 <ContentControl Style="{StaticResource IconStyle.OneLineView}" />
                </Microsoft_Lync_Controls_Internal:RadioMenuItem.Icon>
               </Microsoft_Lync_Controls_Internal:RadioMenuItem>
               <Microsoft_Lync_Controls_Internal:RadioMenuItem x:Name="PART_TwoLinesMenuItem" GroupName="LineViewGroup" Header="{Binding Resources.ContactListViewTwoLine, Source={StaticResource ResourcesWrapper}}">
                <Microsoft_Lync_Controls_Internal:RadioMenuItem.Icon>
                 <ContentControl Margin="0,1,0,0" Style="{StaticResource IconStyle.TwoLineView}" />
                </Microsoft_Lync_Controls_Internal:RadioMenuItem.Icon>
               </Microsoft_Lync_Controls_Internal:RadioMenuItem>                                                
               <Microsoft_Lync_Controls_Internal:MenuItem Header="{Binding Resources.ContactListViewShowFriendlyName, Source={StaticResource ResourcesWrapper}}" IsCheckable="True" IsChecked="{Binding ShowFriendlyName, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" />
               <Microsoft_Lync_Controls_Internal:MenuItem Style="{StaticResource MenuItemSeparatorStyle}" />                                                
               <Microsoft_Lync_Controls_Internal:RadioMenuItem x:Name="PART_SortByDisplayNameMenuItem" GroupName="SortByGroup" Header="{Binding Resources.ContactListViewDisplayName, Source={StaticResource ResourcesWrapper}}" />
               <Microsoft_Lync_Controls_Internal:RadioMenuItem x:Name="PART_SortByAvailabilityMenuItem" GroupName="SortByGroup" Header="{Binding Resources.ContactListViewAvailability, Source={StaticResource ResourcesWrapper}}" />
               <Microsoft_Lync_Controls_Internal:MenuItem Style="{StaticResource MenuItemSeparatorStyle}" />
               <Microsoft_Lync_Controls_Internal:MenuItem Header="{Binding Resources.ContactListViewShowFrequentContacts, Source={StaticResource ResourcesWrapper}}" IsCheckable="True" IsChecked="{Binding ShowFrequentContacts, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" />
              </Microsoft_Lync_Controls_Internal:ContextMenu>
             </Microsoft_Lync_Controls_Internal:SplitButton.DropDown>                                        
             <Grid>
              <ContentControl Style="{StaticResource IconStyle.OneLineView}" Visibility="{Binding IsChecked, Converter={StaticResource BooleanToVisibilityConverter}, ElementName=PART_OneLineMenuItem, FallbackValue=Collapsed, Mode=OneWay}" />
              <ContentControl Style="{StaticResource IconStyle.TwoLineView}" Visibility="{Binding IsChecked, Converter={StaticResource NotBooleanToVisibilityConverter}, ElementName=PART_OneLineMenuItem, Mode=OneWay}" />
             </Grid>                                        
            </Microsoft_Lync_Controls_Internal:SplitButton>
           </Grid>
           <ToggleButton x:Name="PivotBarDivider" AutomationProperties.AutomationId="PivotBarDivider" AutomationProperties.Name="Pivot bar divider" Grid.Row="1" Style="{StaticResource ToggleButtonPivotDividerStyle}" Height="10" IsChecked="True" />
          </Grid>                            
          <controls:UCTreeView x:Name="PART_TreeControl" Grid.Row="1" ItemsSource="{TemplateBinding Contacts}" HorizontalContentAlignment="Stretch" BorderBrush="{x:Null}" BorderThickness="0" Background="{TemplateBinding Background}" GroupViewBySetting="{TemplateBinding GroupViewBySetting}" ShowFriendlyName="{TemplateBinding ShowFriendlyName}" ContactLayoutView="{TemplateBinding ContactLayoutView}" ContextualInformation="{TemplateBinding ContextualInformation}" ScrollViewer.HorizontalScrollBarVisibility="{TemplateBinding ScrollViewer.HorizontalScrollBarVisibility}" ScrollViewer.VerticalScrollBarVisibility="{TemplateBinding ScrollViewer.VerticalScrollBarVisibility}"/>
         </Grid>
        </Border>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

