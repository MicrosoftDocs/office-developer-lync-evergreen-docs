---
title: PresenceIndicator style and template
TOCTitle: PresenceIndicator style and template
ms:assetid: 9ad8b3ca-d397-4e65-b02b-5e3102fe2b92
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933141(v=office.15)
ms:contentKeyID: 50877278
ms.date: 07/24/2014
mtps_version: v=office.15
---

# PresenceIndicator style and template

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [PresenceIndicator](https://msdn.microsoft.com/en-us/library/hh345947\(v=office.15\)) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.

**Last modified:** November 27, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

**In this article**  
PresenceIndicator parts  
PresenceIndicator states  
Default style and template  
Additional resources  

There are no [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the PresenceIndicator control.

![PresenceIndicator Control](images/JJ933141.PresenceIndicatorControl(Office.15).png "PresenceIndicator Control")

![PresenceIndicator Control](images/JJ933141.PresenceIndicator_large_rtm(Office.15).png "PresenceIndicator Control")

## PresenceIndicator parts

The following table lists the named parts for the PresenceIndicator control.

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
<td><p>ViewBox</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.viewbox.aspx">ViewBox</a></p></td>
<td><p>Stretches and scales a single child to fill the available space.</p></td>
</tr>
<tr class="even">
<td><p>PresenceColorGrid</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.grid.aspx">Grid</a></p></td>
<td><p>Hosts the presence color.</p></td>
</tr>
</tbody>
</table>

## PresenceIndicator states

The following table lists the visual states for the PresenceIndicator control.

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
<td><p>Available</p></td>
<td><p>AvailabilityStates</p></td>
<td><p>The contact is available.</p></td>
</tr>
<tr class="even">
<td><p>UnknownContactType</p></td>
<td><p>ContactTypeStates</p></td>
<td><p>The contact type is not known.</p></td>
</tr>
<tr class="odd">
<td><p>Telephone</p></td>
<td><p>ContactTypeStates</p></td>
<td><p>The contact type is telephone.</p></td>
</tr>
<tr class="even">
<td><p>Away</p></td>
<td><p>AvailabilityStates</p></td>
<td><p>The contact is away.</p></td>
</tr>
<tr class="odd">
<td><p>Busy</p></td>
<td><p>AvailabilityStates</p></td>
<td><p>The contact is busy.</p></td>
</tr>
<tr class="even">
<td><p>Unknown</p></td>
<td><p>AvailabilityStates</p></td>
<td><p>The contact availability is not known.</p></td>
</tr>
<tr class="odd">
<td><p>DoNotDisturb</p></td>
<td><p>AvailabilityStates</p></td>
<td><p>The contact availability is do not disturb.</p></td>
</tr>
<tr class="even">
<td><p>Blocked</p></td>
<td><p>AvailabilityStates</p></td>
<td><p>The contact is blocked.</p></td>
</tr>
<tr class="odd">
<td><p>Offline</p></td>
<td><p>AvailabilityStates</p></td>
<td><p>The contact is offline.</p></td>
</tr>
<tr class="even">
<td><p>Hidden</p></td>
<td><p>PhotoVisibilityStates</p></td>
<td><p>The contact photo is hidden.</p></td>
</tr>
<tr class="odd">
<td><p>Visible</p></td>
<td><p>PhotoVisibilityStates</p></td>
<td><p>The contact photo is visible.</p></td>
</tr>
<tr class="even">
<td><p>HiddenSize</p></td>
<td><p>PhotoDisplayAutoSizeStates</p></td>
<td><p>The contact photo size is hidden.</p></td>
</tr>
<tr class="odd">
<td><p>SmallSize</p></td>
<td><p>PhotoDisplayAutoSizeStates</p></td>
<td><p>The contact photo size is small.</p></td>
</tr>
<tr class="even">
<td><p>LargeSize</p></td>
<td><p>PhotoDisplayAutoSizeStates</p></td>
<td><p>The contact photo size is large.</p></td>
</tr>
<tr class="odd">
<td><p>Person</p></td>
<td><p>ContactTypeStates</p></td>
<td><p>The contact type is person.</p></td>
</tr>
<tr class="even">
<td><p>Bot</p></td>
<td><p>ContactTypeStates</p></td>
<td><p>The contact type is bot.</p></td>
</tr>
<tr class="odd">
<td><p>DistributionGroup</p></td>
<td><p>ContactTypeStates</p></td>
<td><p>The contact type is distribution group.</p></td>
</tr>
</tbody>
</table>

## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the PresenceIndicator control.

    <Style x:Key="PresenceIndicatorStyle1" TargetType="{x:Type controls:PresenceIndicator}">
      <Setter Property="HorizontalContentAlignment" Value="Center" />
      <Setter Property="VerticalContentAlignment" Value="Top" />
      <Setter Property="Template">
       <Setter.Value>
        <ControlTemplate TargetType="{x:Type controls:PresenceIndicator}">
         <Grid>
          <Rtc_System_Windows:VisualStateManager.VisualStateGroups>
           <Rtc_System_Windows:VisualStateGroup x:Name="AvailabilityStates">
            <Rtc_System_Windows:VisualState x:Name="Available">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Free">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Away">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Away">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Busy">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Busy">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Unknown">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Unknown">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="DoNotDisturb">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_DoNotDisturb">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Blocked">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Blocked">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Offline">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="Photo_Offline">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
           </Rtc_System_Windows:VisualStateGroup>
           <Rtc_System_Windows:VisualStateGroup x:Name="PhotoVisibilityStates">
            <Rtc_System_Windows:VisualState x:Name="Hidden">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.CornerRadius)" Storyboard.TargetName="AvailabilityBorder_Free">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <CornerRadius>1</CornerRadius>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.CornerRadius)" Storyboard.TargetName="AvailabilityBorder_Away">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <CornerRadius>1</CornerRadius>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.CornerRadius)" Storyboard.TargetName="AvailabilityBorder_Busy">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <CornerRadius>1</CornerRadius>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.CornerRadius)" Storyboard.TargetName="AvailabilityBorder_Unknown">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <CornerRadius>1</CornerRadius>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.CornerRadius)" Storyboard.TargetName="AvailabilityBorder_DoNotDisturb">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <CornerRadius>1</CornerRadius>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.CornerRadius)" Storyboard.TargetName="AvailabilityBorder_Blocked">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <CornerRadius>1</CornerRadius>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.CornerRadius)" Storyboard.TargetName="Photo_Offline">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <CornerRadius>1</CornerRadius>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.BorderThickness)" Storyboard.TargetName="AvailabilityBorder_Away">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>1</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.BorderThickness)" Storyboard.TargetName="AvailabilityBorder_Busy">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>1</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.BorderThickness)" Storyboard.TargetName="AvailabilityBorder_Unknown">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>1</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.BorderThickness)" Storyboard.TargetName="AvailabilityBorder_DoNotDisturb">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>1</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.BorderThickness)" Storyboard.TargetName="AvailabilityBorder_Blocked">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>1</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(Border.BorderThickness)" Storyboard.TargetName="Photo_Offline">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>1</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="Hidden_Free_Internal">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Free_Internal">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Collapsed</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Away_Internal">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Collapsed</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Busy_Internal">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Collapsed</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_Unknown_Internal">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Collapsed</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="AvailabilityBorder_DoNotDisturb_Internal">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Collapsed</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="Photo_Offline_Internal">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Collapsed</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ColorAnimation Duration="0" To="#FFA3AAB2" Storyboard.TargetProperty="(Border.BorderBrush).(SolidColorBrush.Color)" Storyboard.TargetName="Photo_Offline" />
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="OOFIconHidden">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Visible">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="OOFIconPhoto">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="PhotoGrid">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
           </Rtc_System_Windows:VisualStateGroup>
           <Rtc_System_Windows:VisualStateGroup x:Name="PhotoDisplayAutoSizeStates">                                
            <Rtc_System_Windows:VisualState x:Name="HiddenSize" />
            <Rtc_System_Windows:VisualState x:Name="SmallSize">
             <Storyboard>
              <DoubleAnimation Duration="0" From="0" To="36" Storyboard.TargetProperty="(FrameworkElement.Height)" Storyboard.TargetName="PART_PresenceColorGrid" />
              <DoubleAnimation Duration="0" From="0" To="10" Storyboard.TargetProperty="(FrameworkElement.Width)" Storyboard.TargetName="PART_PresenceColorGrid" />                                        
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(FrameworkElement.Margin)" Storyboard.TargetName="PART_PresenceColorGrid">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>0,0,35,0</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="LargeSize">
             <Storyboard>
              <DoubleAnimation Duration="0" From="0" To="52" Storyboard.TargetProperty="(FrameworkElement.Width)" Storyboard.TargetName="PhotoGrid" />
              <DoubleAnimation Duration="0" From="0" To="52" Storyboard.TargetProperty="(FrameworkElement.Height)" Storyboard.TargetName="PhotoGrid" />
              <DoubleAnimation Duration="0" From="0" To="10" Storyboard.TargetProperty="(FrameworkElement.Width)" Storyboard.TargetName="PART_PresenceColorGrid" />
              <DoubleAnimation Duration="0" From="0" To="52" Storyboard.TargetProperty="(FrameworkElement.Height)" Storyboard.TargetName="PART_PresenceColorGrid" />                                        
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(FrameworkElement.Margin)" Storyboard.TargetName="PART_PresenceColorGrid">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Thickness>0,0,51,0</Thickness>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
           </Rtc_System_Windows:VisualStateGroup>
           <Rtc_System_Windows:VisualStateGroup x:Name="ContactTypeStates">
            <Rtc_System_Windows:VisualState x:Name="Person">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="DoughboyPerson">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Bot">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="DoughboyBot">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="DistributionGroup">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="DoughboyDistributionGroup">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="Telephone">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="DoughboyPhone">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
            <Rtc_System_Windows:VisualState x:Name="UnknownContactType">
             <Storyboard>
              <ObjectAnimationUsingKeyFrames Storyboard.TargetProperty="(UIElement.Visibility)" Storyboard.TargetName="DoughboyPerson">
               <DiscreteObjectKeyFrame KeyTime="0">
                <DiscreteObjectKeyFrame.Value>
                 <Visibility>Visible</Visibility>
                </DiscreteObjectKeyFrame.Value>
               </DiscreteObjectKeyFrame>
              </ObjectAnimationUsingKeyFrames>
             </Storyboard>
            </Rtc_System_Windows:VisualState>
           </Rtc_System_Windows:VisualStateGroup>
          </Rtc_System_Windows:VisualStateManager.VisualStateGroups>
          <Microsoft_Lync_Controls_Internal:PopupContactCardHost>
           <Microsoft_Lync_Controls_Internal:PopupContactCardHost.PopupContactCard>
            <Microsoft_Lync_Controls_Internal:PopupContactCard Placement="Top" x:Name="PART_PopupContactCard" ModelTarget="{Binding RelativeSource={RelativeSource TemplatedParent}}" HoverAction="{TemplateBinding HoverAction}" SingleClickAction="{TemplateBinding SingleClickAction}" />
           </Microsoft_Lync_Controls_Internal:PopupContactCardHost.PopupContactCard>
           <Button x:Name="PART_IndicatorButton" AutomationProperties.AutomationId="IndicatorButton" AutomationProperties.Name="Presence indicator button" IsEnabled="{TemplateBinding IsSignedIn}" Style="{StaticResource FocusVisualStyleToNullStyle}" Microsoft_Lync_Controls_Internal:PopupContactCardHost.IsHoverOnTarget="True" Microsoft_Lync_Controls_Internal:PopupContactCardHost.IsHoverOffTarget="True" Microsoft_Lync_Controls_Internal:PopupContactCardHost.IsSingleClickActionTarget="True" Microsoft_Lync_Controls_Internal:PopupContactCardHost.IsPlacementTarget="True" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
            <Button.Template>
             <ControlTemplate TargetType="{x:Type Button}">
              <Grid>
               <Rtc_System_Windows:VisualStateManager.VisualStateGroups>
                <Rtc_System_Windows:VisualStateGroup x:Name="FocusStates">
                 <Rtc_System_Windows:VisualState x:Name="Focused">
                  <Storyboard>
                   <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" Duration="00:00:00.0010000" Storyboard.TargetName="FocusBorder" Storyboard.TargetProperty="(UIElement.Visibility)">
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
               <ContentPresenter Content="{TemplateBinding Content}" />                                            
               <Border x:Name="FocusBorder" BorderBrush="#660A96BE" BorderThickness="1" CornerRadius="1" Visibility="Collapsed" Background="Transparent" />
              </Grid>
             </ControlTemplate>
            </Button.Template>                                
            <Grid x:Name="PART_Grid">
             <Viewbox x:Name="PART_Viewbox" Stretch="None">                                        
              <Grid Background="Transparent" DataContext="{TemplateBinding Model}" Visibility="Visible">                                            
               <Grid x:Name="PhotoGrid" AutomationProperties.AutomationId="PhotoSmall" Margin="9,0,0,0" VerticalAlignment="Top" Width="36" Height="36" Visibility="Collapsed">
                <Image x:Name="PART_PhotoImageSmall" Source="{Binding PresenceItems.Photo, Converter={StaticResource StreamToImageSourceConverter}}" Visibility="{Binding Source, Converter={StaticResource NullObjectToVisibilityConverter}, RelativeSource={RelativeSource Self}}" Stretch="UniformToFill" Margin="2,2,2,2" HorizontalAlignment="Center" VerticalAlignment="Center" />                                                
                <Viewbox Margin="2,2,2,2" Visibility="{Binding Visibility, Converter={StaticResource NotVisibilityConverter}, ElementName=PART_PhotoImageSmall}" Stretch="UniformToFill">
                 <Grid x:Name="Doughboys">
                  <ContentControl x:Name="DoughboyBot" Style="{StaticResource IconStyle.Doughboy.Bot.32}" Visibility="Collapsed" />
                  <ContentControl x:Name="DoughboyPerson" Style="{StaticResource IconStyle.Doughboy.Person.32}" Visibility="Collapsed" />
                  <ContentControl x:Name="DoughboyDistributionGroup" Style="{StaticResource IconStyle.Doughboy.Group.32}" Visibility="Collapsed" />
                  <ContentControl x:Name="DoughboyPhone" Style="{StaticResource IconStyle.Doughboy.Phone.32}" Visibility="Collapsed" />
                 </Grid>
                </Viewbox>
                <Border BorderBrush="#585858" BorderThickness="0,1,1,1" CornerRadius="0,1,1,0">
                 <Rectangle Stroke="#ffffff" />
                </Border>
               </Grid>                                            
               <Grid x:Name="PART_PresenceColorGrid" Margin="0" Width="10" Height="10">
                <Border x:Name="AvailabilityBorder_Free" CornerRadius="1,0,0,1" BorderThickness="1" Visibility="Collapsed">
                 <Border.Background>
                  <LinearGradientBrush EndPoint="1,1" StartPoint="0,0">
                   <GradientStop Color="#FFabe29c" Offset="0" />
                   <GradientStop Color="#FF21ae05" Offset="0.27" />
                   <GradientStop Color="#FF21ae05" Offset="0.56" />
                   <GradientStop Color="#FFa1de90" Offset="1" />
                  </LinearGradientBrush>
                 </Border.Background>
                 <Border.BorderBrush>
                  <LinearGradientBrush EndPoint="0.5,1" StartPoint="0.5,0">
                   <GradientStop Color="#BF64B105" Offset="0" />
                   <GradientStop Color="#BF64B004" Offset="1" />
                  </LinearGradientBrush>
                 </Border.BorderBrush>
                 <Grid>
                  <Border x:Name="AvailabilityBorder_Free_Internal" BorderThickness="2">
                   <Border.BorderBrush>
                    <LinearGradientBrush EndPoint="0.5,1" StartPoint="0.5,0">
                     <GradientStop Color="#BFD5F5A3" />
                     <GradientStop Color="#BFA9EF51" Offset="0.5" />
                     <GradientStop Color="#BFDBF5AF" Offset="1" />
                    </LinearGradientBrush>
                   </Border.BorderBrush>
                  </Border>
                  <Border x:Name="Hidden_Free_Internal" BorderThickness="1.5" BorderBrush="#7FFFFFFF" Visibility="Collapsed" />
                 </Grid>
                </Border>
                <Border x:Name="AvailabilityBorder_Away" CornerRadius="1,0,0,1" BorderThickness="1,1,0,1" BorderBrush="#ffE0B753" Visibility="Collapsed">
                 <Border.Background>
                  <LinearGradientBrush EndPoint="1,1" StartPoint="0,0">
                   <GradientStop Color="#FFffeea5" Offset="0" />
                   <GradientStop Color="#FFffde4e" Offset="0.27" />
                   <GradientStop Color="#FFffde4e" Offset="0.56" />
                   <GradientStop Color="#fffab6" Offset="1" />
                  </LinearGradientBrush>
                 </Border.Background>
                 <Rectangle x:Name="AvailabilityBorder_Away_Internal" Width="1" HorizontalAlignment="Right">
                  <Rectangle.Fill>
                   <LinearGradientBrush EndPoint="0.5,1" StartPoint="0.5,0">
                    <GradientStop Color="#FFFFC71C" Offset="0.527" />
                    <GradientStop Color="#FFFFDE30" Offset="0.747" />
                   </LinearGradientBrush>
                  </Rectangle.Fill>
                 </Rectangle>
                </Border>
                <Border x:Name="AvailabilityBorder_Busy" CornerRadius="1,0,0,1" BorderThickness="1,1,0,1" BorderBrush="#BFB54033" Visibility="Collapsed">
                 <Border.Background>
                  <LinearGradientBrush EndPoint="1,1" StartPoint="0,0">
                   <GradientStop Color="#FFD87F76" Offset="0" />
                   <GradientStop Color="#FFC23A2B" Offset="0.27" />
                   <GradientStop Color="#FFC23A2B" Offset="0.56" />
                   <GradientStop Color="#FFF4B09F" Offset="1" />
                  </LinearGradientBrush>
                 </Border.Background>
                 <Rectangle x:Name="AvailabilityBorder_Busy_Internal" Width="1" HorizontalAlignment="Right">
                  <Rectangle.Fill>
                   <LinearGradientBrush EndPoint="0.5,1" StartPoint="0.5,0">
                    <GradientStop Color="#FFC23A2B" Offset="0.458" />
                    <GradientStop Color="#FFEC7356" Offset="0.83" />
                   </LinearGradientBrush>
                  </Rectangle.Fill>
                 </Rectangle>
                </Border>
                <Border x:Name="AvailabilityBorder_Unknown" CornerRadius="1,0,0,1" BorderThickness="1,1,0,1" BorderBrush="#ff717171" Visibility="Collapsed">
                 <Border.Background>
                  <LinearGradientBrush EndPoint="1,1" StartPoint="0,0">
                   <GradientStop Color="#FFf8f8f8" Offset="0" />
                   <GradientStop Color="#FFf1f1f1" Offset="0.27" />
                   <GradientStop Color="#FFf1f1f1" Offset="0.56" />
                   <GradientStop Color="#ffffffff" Offset="1" />
                  </LinearGradientBrush>
                 </Border.Background>
                 <Border x:Name="AvailabilityBorder_Unknown_Internal" BorderThickness="0,0,1,0" Margin="0,0,-1,0">
                  <Border.BorderBrush>
                   <LinearGradientBrush EndPoint="0.5,1" StartPoint="0.5,0">
                    <GradientStop Color="#FFC8DADE" Offset="0" />
                    <GradientStop Color="#FFC6D8DC" Offset="0.523" />
                    <GradientStop Color="#FFCFDEE2" Offset="1" />
                   </LinearGradientBrush>
                  </Border.BorderBrush>
                 </Border>
                </Border>
                <Border x:Name="AvailabilityBorder_DoNotDisturb" CornerRadius="1,0,0,1" BorderThickness="1,1,0,1" BorderBrush="#F29A1708" Visibility="Collapsed">
                 <Border.Background>
                  <LinearGradientBrush EndPoint="1,1" StartPoint="0,0">
                   <GradientStop Color="#FFAF5858" Offset="0" />
                   <GradientStop Color="#FF850000" Offset="0.27" />
                   <GradientStop Color="#FF850000" Offset="0.56" />
                   <GradientStop Color="#FFAD2D10" Offset="0.794" />
                  </LinearGradientBrush>
                 </Border.Background>
                 <Grid>
                  <Rectangle Fill="White" Stroke="{x:Null}" Height="2" Margin="0" VerticalAlignment="Center" Width="6" HorizontalAlignment="Center" />
                  <Rectangle x:Name="AvailabilityBorder_DoNotDisturb_Internal" Width="1" HorizontalAlignment="Right">
                   <Rectangle.Fill>
                    <LinearGradientBrush EndPoint="0.5,1" StartPoint="0.5,0">
                     <GradientStop Color="#FF850000" Offset="0.46" />
                     <GradientStop Color="#FFAD2D10" Offset="0.832" />
                    </LinearGradientBrush>
                   </Rectangle.Fill>
                  </Rectangle>
                 </Grid>
                </Border>
                <Border x:Name="AvailabilityBorder_Blocked" CornerRadius="1,0,0,1" BorderThickness="1,1,0,1" BorderBrush="#ff717171" Visibility="Collapsed">
                 <Border.Background>
                  <LinearGradientBrush EndPoint="1,1" StartPoint="0,0">
                   <GradientStop Color="#FFf8f8f8" Offset="0" />
                   <GradientStop Color="#FFf1f1f1" Offset="0.27" />
                   <GradientStop Color="#FFf1f1f1" Offset="0.56" />
                   <GradientStop Color="#ffffffff" Offset="1" />
                  </LinearGradientBrush>
                 </Border.Background>
                 <Grid>
                  <Border BorderThickness="1" BorderBrush="{StaticResource ContactAvailability.InternalBorder}" />                                                        
                  <Path Fill="White" Stretch="Fill" Stroke="#FFAC0300" Height="6.293" HorizontalAlignment="Center" Margin="0" VerticalAlignment="Center" Width="6.292" Data="M80.205681, 215.91956 L74.912872221.21237" />
                  <Ellipse Fill="{x:Null}" Stroke="#FFAC0300" Margin="0" HorizontalAlignment="Center" VerticalAlignment="Center" Width="8" Height="8" />
                 </Grid>
                </Border>
                <Border x:Name="Photo_Offline" CornerRadius="1,0,0,1" BorderThickness="1,1,0,1" BorderBrush="#ff717171" Visibility="Collapsed">                                                    
                 <Border.Background>
                  <LinearGradientBrush EndPoint="1,1" StartPoint="0,0">
                   <GradientStop Color="#FFEBF2F3" Offset="0" />
                   <GradientStop Color="#FFD7E4E7" Offset="0.27" />
                   <GradientStop Color="#FFD7E4E7" Offset="0.56" />
                   <GradientStop Color="#FFF7F9FA" Offset="1" />
                  </LinearGradientBrush>
                 </Border.Background>
                 <Border x:Name="Photo_Offline_Internal" BorderThickness="0,0,1,0" BorderBrush="{StaticResource ContactAvailability.Offline.InnerEdgeBorder}" />
                </Border>
               </Grid>                                            
               <Grid AutomationProperties.AutomationId="OutOfOfficeIconOverlayContainer" Visibility="{Binding PresenceItems.IsOutOfOffice, Converter={StaticResource BooleanToVisibilityConverter}, FallbackValue=Collapsed}">
                <Image x:Name="OOFIconHidden" AutomationProperties.AutomationId="HiddenOutOfOfficeIconOverlay" Source="pack://application:,,,/Microsoft.Lync.Controls;component/resources/OOF_overlay_glow.png" Height="7" Width="7" IsHitTestVisible="False" HorizontalAlignment="Right" VerticalAlignment="Bottom" Visibility="Collapsed" Style="{StaticResource BitmapScalingModeStyle}" />
                <Image x:Name="OOFIconPhoto" AutomationProperties.AutomationId="PhotoOutOfOfficeIconOverlay" Source="pack://application:,,,/Microsoft.Lync.Controls;component/resources/OOF_overlay.png" Height="5" Width="5" IsHitTestVisible="False" HorizontalAlignment="Right" VerticalAlignment="Bottom" Visibility="Collapsed" Style="{StaticResource BitmapScalingModeStyle}" />
               </Grid>                                            
              </Grid>
             </Viewbox>
            </Grid>
           </Button>
          </Microsoft_Lync_Controls_Internal:PopupContactCardHost>
         </Grid>
        </ControlTemplate>
       </Setter.Value>
      </Setter>
     </Style>

## See also

[Customizing Lync Controls](customizing-lync-controls.md)

