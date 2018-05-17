---
title: SendEmailButton style and template
TOCTitle: SendEmailButton style and template
ms:assetid: 7b5f2fe6-435e-458b-a4d3-46cc0a4ae26f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933090(v=office.15)
ms:contentKeyID: 50877221
ms.date: 07/24/2014
mtps_version: v=office.15
---

# SendEmailButton style and template

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the style and template for the [SendEmailButton](sendemailbutton-class-microsoft-lync-controls_1.md) control. You can modify the default ControlTemplate to give the control a unique appearance. For more information, see the other topics in the [Customizing Lync Controls](customizing-lync-controls.md) section.


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
SendEmailButton parts  
Default style and template  
Additional resources  

There are no states or [Style](http://msdn.microsoft.com/en-us/library/system.windows.style\(vs.95\).aspx) properties for the SendEmailButton control.

![SendEmailButton Control](images/JJ945543.SendEmailButtonControl(Office.15).png "SendEmailButton Control")

## SendEmailButton parts

The following table lists the named parts for the SendEmailButton control.

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
<td><p>CommandControl</p></td>
<td><p><a href="http://msdn.microsoft.com/en-us/library/system.windows.controls.control.aspx">Control</a></p></td>
<td><p>Starts Microsoft Outlook and initiates the desired action with that contact.</p></td>
</tr>
</tbody>
</table>


## Default style and template

The following shows the XML namespace mapping that you have to specify when you work with styles and templates.

    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"

The following sample shows the default Windows Presentation Foundation style and template for the SendEmailButton control.

    <Style x:Key="SendEmailButtonStyle1" TargetType="controls:SendEmailButton">
     <Setter Property="Template">
      <Setter.Value>
       <ControlTemplate TargetType="controls:SendEmailButton">
        <Microsoft_Lync_Controls_Internal:HelpTextButton AutomationProperties.AutomationId="StartEmailButton" Background="{TemplateBinding Background}" Microsoft_Lync_Controls_Internal_Framework_Commands:Command.Click="{Binding Model.SendEmailCommand, RelativeSource={RelativeSource TemplatedParent}}" Microsoft_Lync_Controls_Internal_Framework_Commands:Command.CommandParameter="{TemplateBinding Subject}" Padding="{TemplateBinding Padding}" Style="{StaticResource GlobalIconButtonStyle}">
         <ToolTipService.ToolTip>
          <ToolTip Content="{Binding Model.PresenceItems.PrimaryEmail, Converter={StaticResource EmailAddressToStartEmailTooltipConverter}, RelativeSource={RelativeSource TemplatedParent}}" Style="{StaticResource DefaultToolTipStyle}"/>
         </ToolTipService.ToolTip>
         <Binding Path="Content" RelativeSource="{RelativeSource TemplatedParent}">
          <Binding.TargetNullValue>
           <ContentControl Style="{StaticResource IconStyle.StartEmail}"/>
          </Binding.TargetNullValue>
         </Binding>
        </Microsoft_Lync_Controls_Internal:HelpTextButton>
       </ControlTemplate>
      </Setter.Value>
     </Setter>
    </Style>

## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

