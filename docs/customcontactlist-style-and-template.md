---
title: CustomContactList style and template
TOCTitle: CustomContactList style and template
ms:assetid: 567316a6-45f6-4b0a-9f1b-c74af5ceffd5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933050(v=office.15)
ms:contentKeyID: 50877179
ms.date: 07/24/2014
mtps_version: v=office.15
---

# CustomContactList style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [CustomContactList](https://msdn.microsoft.com/en-us/library/hh346321\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.

**Last modified:** November 27, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

There are no states or parts or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the CustomContactList control.

![CustomContactList Control](images/JJ945533.CustomContactList_rtm(Office.15).png "CustomContactList Control")

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the CustomContactList control.

    <Style x:Key="CustomContactListStyle1" TargetType="{x:Type controls:CustomContactList}">            
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
       <ControlTemplate TargetType="{x:Type controls:CustomContactList}">
        <Grid>                            
         <Microsoft_Lync_Controls_Internal:ContactListMenu x:Name="PART_ContactListMenu" />                            
         <Border SnapsToDevicePixels="true" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="1">
          <ScrollViewer Padding="{TemplateBinding Padding}" Focusable="false" Template="{StaticResource ScrollViewerDefaultTemplate}" HorizontalScrollBarVisibility="{TemplateBinding ScrollViewer.HorizontalScrollBarVisibility}" VerticalScrollBarVisibility="{TemplateBinding ScrollViewer.VerticalScrollBarVisibility}">
           <ItemsPresenter SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" />
          </ScrollViewer>
         </Border>
        </Grid>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

