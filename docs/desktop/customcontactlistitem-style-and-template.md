---
title: CustomContactListItem style and template
TOCTitle: CustomContactListItem style and template
ms:assetid: e89d6346-2f27-42ab-9423-a3c9b5cc91e3
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933216(v=office.15)
ms:contentKeyID: 50877360
ms.date: 07/24/2014
mtps_version: v=office.15
---

# CustomContactListItem style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [CustomContactListItem](https://msdn.microsoft.com/library/hh346017\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.



**Applies to**: Lync 2013 | Lync Server 2013

 

There are no states or [Style](http://msdn.microsoft.com/library/system.windows.style\(vs.95\).aspx) properties for the CustomContactListItem control.

![CustomContactListItem Control](images/JJ945570.CustomContactListItemControl_(Office.15).png "CustomContactListItem Control")

## CustomContactListItem parts

The following table lists the named parts for the CustomContactListItem control.

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
<td><p>ContactItem</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh379432(v=office.15)">ContactItem</a></p></td>
<td><p>A listed contact.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the CustomContactListItem control.

    <Style x:Key="CustomContactListItemStyle1" TargetType="{x:Type controls:CustomContactListItem}" BasedOn="{StaticResource FocusVisualStyleToNullStyle}">
      <Setter Property="Padding" Value="3" />
      <Setter Property="HorizontalContentAlignment" Value="Stretch" />
      <Setter Property="VerticalContentAlignment" Value="Stretch" />
      <Setter Property="Background" Value="Transparent" />
      <Setter Property="BorderThickness" Value="1" />       
      <Setter Property="PersonContentTemplate" Value="{StaticResource PersonContactItemDataTemplateOneLine}" />
      <Setter Property="TelephoneContentTemplate" Value="{StaticResource TelephoneContactItemDataTemplateOneLine}" />
      <Setter Property="BotContentTemplate" Value="{StaticResource BotContactItemDataTemplateOneLine}" />
      <Setter Property="GroupContentTemplate" Value="{StaticResource DistributionListContactItemDataTemplateOneLine}" />        
      <Setter Property="PersonTwoLineContentTemplate" Value="{StaticResource PersonContactItemDataTemplateTwoLines}" />
      <Setter Property="TelephoneTwoLineContentTemplate" Value="{StaticResource TelephoneContactItemDataTemplateTwoLines}" />
      <Setter Property="BotTwoLineContentTemplate" Value="{StaticResource BotContactItemDataTemplateTwoLines}" />
      <Setter Property="GroupTwoLineContentTemplate" Value="{StaticResource DistributionListContactItemDataTemplateTwoLines}" />        
      <Setter Property="Template">
       <Setter.Value>
        <ControlTemplate TargetType="{x:Type controls:CustomContactListItem}">                    
         <Microsoft_Lync_Controls_Internal:PopupContactCardHost x:Name="PART_PopupContactCardHost">
          <Microsoft_Lync_Controls_Internal:PopupContactCardHost.PopupContactCard>
           <Microsoft_Lync_Controls_Internal:PopupContactCard Placement="LeftAndVerticallyCentered" ClickTarget="{Binding RelativeSource={RelativeSource TemplatedParent}}" />
          </Microsoft_Lync_Controls_Internal:PopupContactCardHost.PopupContactCard>
          <Rtc_System_Windows:VisualStateManager.VisualStateGroups>
           <Rtc_System_Windows:VisualStateGroup x:Name="CommonStates">
            <Rtc_System_Windows:VisualState x:Name="Normal" />
            <Rtc_System_Windows:VisualState x:Name="MouseOver">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetName="HoverBorder" Storyboard.TargetProperty="Visibility">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Disabled" />
           </Rtc_System_Windows:VisualStateGroup>
           <Rtc_System_Windows:VisualStateGroup x:Name="PressedStates">
            <Rtc_System_Windows:VisualState x:Name="NotPressed" />
            <Rtc_System_Windows:VisualState x:Name="Pressed">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetName="PressedRectangle" Storyboard.TargetProperty="Visibility">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
           </Rtc_System_Windows:VisualStateGroup>
           <Rtc_System_Windows:VisualStateGroup x:Name="SelectionStates">
            <Rtc_System_Windows:VisualState x:Name="Unselected" />
            <Rtc_System_Windows:VisualState x:Name="Selected">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetName="SelectionBorder" Storyboard.TargetProperty="Visibility">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
           </Rtc_System_Windows:VisualStateGroup>
           <Rtc_System_Windows:VisualStateGroup x:Name="FocusStates">
            <Rtc_System_Windows:VisualState x:Name="Focused">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Duration="0" Storyboard.TargetName="FocusRectangle" Storyboard.TargetProperty="Visibility">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Unfocused" />
           </Rtc_System_Windows:VisualStateGroup>
          </Rtc_System_Windows:VisualStateManager.VisualStateGroups>
          <Grid Background="{TemplateBinding Background}" Microsoft_Lync_Controls_Internal:PopupContactCardHost.IsPlacementTarget="True" Microsoft_Lync_Controls_Internal:PopupContactCardHost.IsHoverOffTarget="True">
           <Border x:Name="SelectionBorder" Visibility="Collapsed" Background="{Binding GlobalListSelectionBackground_Selected, Source={StaticResource ControlColors}}" BorderBrush="{Binding GlobalListSelectionBorder_Selected, Source={StaticResource ControlColors}}" BorderThickness="2" CornerRadius="1" />
           <Border x:Name="HoverBorder" Visibility="Collapsed" BorderBrush="{Binding GlobalListSelectionBorder_Hover, Source={StaticResource ControlColors}}" BorderThickness="1" CornerRadius="1">
            <Rectangle StrokeThickness="1" Stroke="{Binding GlobalListSelectionInnerBorder_Hover, Source={StaticResource ControlColors}}" Fill="{Binding GlobalListSelectionBackground_Hover, Source={StaticResource ControlColors}}" />
           </Border>
           <Rectangle x:Name="PressedRectangle" Visibility="Collapsed" Fill="{Binding GlobalListSelectionBackground_Pressed, Source={StaticResource ControlColors}}" StrokeThickness="1" RadiusX="1" RadiusY="1" />
           <Rectangle x:Name="FocusRectangle" Stroke="{Binding GlobalListSelection_Focus, Source={StaticResource ControlColors}}" StrokeThickness="1" RadiusX="1" RadiusY="1" Visibility="Collapsed" />
           <controls:ContactItem x:Name="PART_ContactItem" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" Source="{TemplateBinding Source}" IsSelected="{TemplateBinding IsSelected}" ContextualInformation="{TemplateBinding ContextualInformation}" ContactLayoutView="{TemplateBinding ContactLayoutView}" ShowFriendlyName="{TemplateBinding ShowFriendlyName}" CallButtonVisibility="{TemplateBinding CallButtonVisibility}" PersonContentTemplate="{TemplateBinding PersonContentTemplate}" TelephoneContentTemplate="{TemplateBinding TelephoneContentTemplate}" BotContentTemplate="{TemplateBinding BotContentTemplate}" GroupContentTemplate="{TemplateBinding GroupContentTemplate}" PersonTwoLineContentTemplate="{TemplateBinding PersonTwoLineContentTemplate}" TelephoneTwoLineContentTemplate="{TemplateBinding TelephoneTwoLineContentTemplate}" BotTwoLineContentTemplate="{TemplateBinding BotTwoLineContentTemplate}" GroupTwoLineContentTemplate="{TemplateBinding GroupTwoLineContentTemplate}" Microsoft_Lync_Controls_Internal:PopupContactCardHost.IsModelTarget="True" />
          </Grid>
         </Microsoft_Lync_Controls_Internal:PopupContactCardHost>
        </ControlTemplate>
       </Setter.Value>
      </Setter>
     </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

