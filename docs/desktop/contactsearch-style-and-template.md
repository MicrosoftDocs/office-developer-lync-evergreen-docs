---
title: ContactSearch style and template
TOCTitle: ContactSearch style and template
ms:assetid: 476ecb88-92b0-411b-96dd-1c917520dc76
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937311(v=office.15)
ms:contentKeyID: 50877142
ms.date: 07/24/2014
mtps_version: v=office.15
---

# ContactSearch style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the styles and templates for the [ContactSearch](https://msdn.microsoft.com/library/hh379436\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013



There are no states or [Style](http://msdn.microsoft.com/library/system.windows.style\(vs.95\).aspx) properties for the ContactSearch control.

![ContactSearch](images/JJ945544.ContactSearch_RTW_bugfix(Office.15).png "ContactSearch")

## ContactSearch parts

The following table lists the named parts for the ContactSearch control.

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
<td><p>ContactSearchInputBox</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh379719(v=office.15)">ContactSearchInputBox</a></p></td>
<td><p>Enables users to search their organization for people based on name, phone number, or skill.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the ContactSearch control.

    <Style x:Key="ContactSearchStyle1" TargetType="{x:Type controls:ContactSearch}">
     <Setter Property="ScrollViewer.HorizontalScrollBarVisibility" Value="Disabled" />
     <Setter Property="ScrollViewer.VerticalScrollBarVisibility" Value="Auto" />
     <Setter Property="Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper.PropertyBindingCollection">
      <Setter.Value>
       <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
        <Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelper Property="Background" Binding="{Binding DefaultControlBackgroundBrush, Source={StaticResource ControlColors}}" />
       </Microsoft_Lync_Internal_Utilities_Helpers:SetterValueBindingHelperCollection>
      </Setter.Value>
     </Setter>
     <Setter Property="Template">
      <Setter.Value>                
       <ControlTemplate TargetType="{x:Type controls:ContactSearch}">
        <Border Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}">
         <Grid>
          <Grid.RowDefinitions>
           <RowDefinition Height="Auto" />
           <RowDefinition Height="*" />
          </Grid.RowDefinitions>
          <controls:ContactSearchInputBox x:Name="ContactSearchInputBox" Grid.Row="0" MaxResults="{Binding MaxResults, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" SearchType="{Binding SearchType, Mode=TwoWay, RelativeSource={RelativeSource TemplatedParent}}" Background="{TemplateBinding Background}" />
          <controls:ContactSearchResultList Grid.Row="1" ItemsSource="{Binding Results, ElementName=ContactSearchInputBox}" ResultsState="{Binding SearchState, ElementName=ContactSearchInputBox}" SearchType="{Binding SearchType, ElementName=ContactSearchInputBox, Mode=TwoWay}" Visibility="{Binding SearchState, ConverterParameter=Cleared, Converter={StaticResource EnumToNotVisibleConverter}, ElementName=ContactSearchInputBox}" ContextualInformation="{TemplateBinding ContextualInformation}" ScrollViewer.HorizontalScrollBarVisibility="{TemplateBinding ScrollViewer.HorizontalScrollBarVisibility}" ScrollViewer.VerticalScrollBarVisibility="{TemplateBinding ScrollViewer.VerticalScrollBarVisibility}" Background="{TemplateBinding Background}" />
         </Grid>
        </Border>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

