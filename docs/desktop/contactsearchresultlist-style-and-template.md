---
title: ContactSearchResultList style and template
TOCTitle: ContactSearchResultList style and template
ms:assetid: bbb5a6e8-a3b6-4f14-96a3-d336d876d40b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933177(v=office.15)
ms:contentKeyID: 50877317
ms.date: 07/24/2014
mtps_version: v=office.15
---

# ContactSearchResultList style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [ContactSearchResultList](https://msdn.microsoft.com/en-us/library/hh379201\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.

**Last modified:** November 27, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

**In this article**  
ContactSearchResultList parts  
ContactSearchResultList properties  
Default style and template  
Additional resources  

There are no states for the ContactSearchResultList control.

![ContactSearchResultList](images/JJ945538.ContactSearchResultList_RTW_bugfix(Office.15).png "ContactSearchResultList")

## ContactSearchResultList parts

The following table lists the named parts for the ContactSearchResultList control.

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
<td><p>ScrollViewer</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.frameworkelement.aspx">FrameworkElement</a></p></td>
<td><p>Represents a scrollable area.</p></td>
</tr>
<tr class="even">
<td><p>TrySkillSearchButton</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.primitives.buttonbase.aspx">ButtonBase</a></p></td>
<td><p>A button that launches a search for a skill or area of expertise.</p></td>
</tr>
</tbody>
</table>

## ContactSearchResultList properties

The following table lists the Style properties of the ContactSearchResultList control. You must set the TargetType property when you create a Style.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property Name</p></th>
<th><p>Target Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ItemContainerStyle</p></td>
<td><p>ListBoxItem</p></td>
<td><p>The style applied to the items that contain results.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the ContactSearchResultList control.

    <Style x:Key="ContactSearchResultListStyle1" TargetType="{x:Type controls:ContactSearchResultList}">            
     <Setter Property="SelectionMode" Value="Extended" />           
     <Setter Property="ItemsPanel">
      <Setter.Value>
       <ItemsPanelTemplate>
        <StackPanel />
       </ItemsPanelTemplate>
      </Setter.Value>
     </Setter>
     <Setter Property="ScrollViewer.HorizontalScrollBarVisibility" Value="Disabled" />
     <Setter Property="ScrollViewer.VerticalScrollBarVisibility" Value="Auto" />
     <Setter Property="Background" Value="{Binding DefaultControlBackgroundBrush, Source={StaticResource ControlColors}}" />
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="{x:Type controls:ContactSearchResultList}">
        <Border Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}">
         <Grid VerticalAlignment="Stretch" Margin="{TemplateBinding Padding}">
          <Grid.RowDefinitions>                                   
           <RowDefinition Height="Auto" />                                    
           <RowDefinition Height="*" />                                    
           <RowDefinition Height="Auto" />
          </Grid.RowDefinitions>
          <Microsoft_Lync_Controls_Internal:ContactListMenu x:Name="PART_ContactListMenu" />
          <StackPanel Grid.Row="0">                                    
           <TextBlock AutomationProperties.AutomationId="SearchErrorTextBlock" Text="{Binding Resources.SearchResultsError, Source={StaticResource ResourcesWrapper}}" Visibility="{Binding ResultsState, ConverterParameter=Error, Converter={StaticResource EnumToVisibilityConverter}, RelativeSource={RelativeSource TemplatedParent}}" Foreground="{Binding GlobalTextColor_Black, Source={StaticResource ControlColors}}" />                                    
           <TextBlock AutomationProperties.AutomationId="SearchStateTextBlock" Text="{Binding Resources.SearchResultsInProgress, Source={StaticResource ResourcesWrapper}}" Visibility="{Binding ResultsState, ConverterParameter=Searching, Converter={StaticResource EnumToVisibilityConverter}, RelativeSource={RelativeSource TemplatedParent}}" Foreground="{Binding GlobalTextColor_Black, Source={StaticResource ControlColors}}" />                                    
           <TextBlock AutomationProperties.AutomationId="GalSyncStateTextBlock" Text="{Binding ItemsSource.ProviderSyncState, Converter={StaticResource ControlsEnumToString}, RelativeSource={RelativeSource TemplatedParent}}" Visibility="{Binding ItemsSource.ProviderSyncState, ConverterParameter=Succeeded, Converter={StaticResource EnumToNotVisibleConverter}, RelativeSource={RelativeSource TemplatedParent}}" TextWrapping="Wrap" />
          </StackPanel>                                
          <Border Grid.Row="1" x:Name="Bd" SnapsToDevicePixels="true" Background="Transparent" BorderBrush="Transparent" BorderThickness="0" Padding="1">
           <ScrollViewer x:Name="ScrollViewer" Padding="{TemplateBinding Padding}" Focusable="false" Template="{StaticResource ScrollViewerDefaultTemplate}" HorizontalScrollBarVisibility="{TemplateBinding ScrollViewer.HorizontalScrollBarVisibility}" VerticalScrollBarVisibility="{TemplateBinding ScrollViewer.VerticalScrollBarVisibility}">
            <ItemsPresenter SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" />
           </ScrollViewer>
          </Border>                               
          <StackPanel Grid.Row="1" Visibility="{Binding ItemsSource.Count, ConverterParameter={StaticResource ZeroInt32}, Converter={StaticResource EqualToVisibilityConverter}, FallbackValue=Collapsed, RelativeSource={RelativeSource TemplatedParent}}">                                    
           <TextBlock AutomationProperties.AutomationId="SearchErrorInformationTextBlock" Text="{Binding ItemsSource.SearchError, Converter={StaticResource SearchErrorToLabelConverter}, RelativeSource={RelativeSource TemplatedParent}}" HorizontalAlignment="Center" Margin="5,5,5,0" Style="{StaticResource GlobalTextSizeStyle.Standard}" Foreground="{Binding GlobalTextColor_Black, Source={StaticResource ControlColors}}" Visibility="{Binding}" TextWrapping="Wrap" />                                    
           <Button x:Name="PART_TrySkillSearchButton" Style="{StaticResource ButtonWrapTextlinkStyle}" Content="{Binding Resources.TryKeywordSearch, Source={StaticResource ResourcesWrapper}}" HorizontalAlignment="Center" Margin="5" Visibility="{Binding ItemsSource.IsSkillSearchPossible, Converter={StaticResource BooleanToVisibilityConverter}, FallbackValue=Collapsed, RelativeSource={RelativeSource TemplatedParent}}" />
          </StackPanel>
          <Border Grid.Row="2" BorderThickness="0,1,0,0" BorderBrush="#ffb1c1e7" Visibility="Visible">
           <StackPanel>
            <TextBlock AutomationProperties.AutomationId="NameSearchLabel" Text="{Binding ItemsSource, Converter={StaticResource SearchResultsToLabelConverter}, RelativeSource={RelativeSource TemplatedParent}}" Visibility="{Binding ItemsSource.SearchType, ConverterParameter=Name, Converter={StaticResource EnumToVisibilityConverter}, RelativeSource={RelativeSource TemplatedParent}}" Margin="5,5,5,0" Style="{StaticResource GlobalTextSizeStyle.Standard}" />                                        
            <Microsoft_Lync_Controls_Internal:HyperlinkButton AutomationProperties.AutomationId="SkillSearchHyperlink" Content="{Binding Resources.ViewResultsInSharePoint, Source={StaticResource ResourcesWrapper}}" TargetName="_blank" NavigateUri="{Binding ItemsSource.SkillSearchQueryUri, RelativeSource={RelativeSource TemplatedParent}}" Visibility="{Binding ItemsSource.SearchType, ConverterParameter=Skill, Converter={StaticResource EnumToVisibilityConverter}, FallbackValue=Collapsed, RelativeSource={RelativeSource TemplatedParent}}" />
           </StackPanel>
          </Border>
         </Grid>
        </Border>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

