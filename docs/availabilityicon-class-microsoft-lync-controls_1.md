---
title: AvailabilityIcon class (Microsoft.Lync.Controls)
TOCTitle: AvailabilityIcon class
ms:assetid: T:Microsoft.Lync.Controls.AvailabilityIcon_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.availabilityicon_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597284
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.AvailabilityIcon
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AvailabilityIcon class

Reserved for internal use. (See [PresenceIndicator](presenceindicator-class-microsoft-lync-controls_1.md)).

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [Microsoft.Lync.Controls.UCBase](ucbase-class-microsoft-lync-controls_1.md)  
                [Microsoft.Lync.Controls.ContactBase](contactbase-class-microsoft-lync-controls_1.md)  
                  Microsoft.Lync.Controls.AvailabilityIcon  
                    [Microsoft.Lync.Controls.PresenceIndicator](presenceindicator-class-microsoft-lync-controls_1.md)  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplateVisualStateAttribute(Name := "Telephone", GroupName := "ContactTypeStates")> _
<TemplateVisualStateAttribute(Name := "Person", GroupName := "ContactTypeStates")> _
<TemplateVisualStateAttribute(Name := "LargeSize", GroupName := "PhotoDisplayAutoSizeStates")> _
<TemplateVisualStateAttribute(Name := "Visible", GroupName := "PhotoVisibilityStates")> _
<TemplateVisualStateAttribute(Name := "UnknownContactType", GroupName := "ContactTypeStates")> _
<TemplateVisualStateAttribute(Name := "Away", GroupName := "AvailabilityStates")> _
<TemplateVisualStateAttribute(Name := "Busy", GroupName := "AvailabilityStates")> _
<TemplateVisualStateAttribute(Name := "Unknown", GroupName := "AvailabilityStates")> _
<TemplateVisualStateAttribute(Name := "DoNotDisturb", GroupName := "AvailabilityStates")> _
<TemplateVisualStateAttribute(Name := "Blocked", GroupName := "AvailabilityStates")> _
<TemplateVisualStateAttribute(Name := "Offline", GroupName := "AvailabilityStates")> _
<TemplateVisualStateAttribute(Name := "Hidden", GroupName := "PhotoVisibilityStates")> _
<TemplateVisualStateAttribute(Name := "Available", GroupName := "AvailabilityStates")> _
<TemplateVisualStateAttribute(Name := "HiddenSize", GroupName := "PhotoDisplayAutoSizeStates")> _
<TemplateVisualStateAttribute(Name := "SmallSize", GroupName := "PhotoDisplayAutoSizeStates")> _
<TemplatePartAttribute(Name := "PART_PresenceColorGrid", Type := GetType(Grid))> _
<TemplatePartAttribute(Name := "PART_Viewbox", Type := GetType(Viewbox))> _
<TemplateVisualStateAttribute(Name := "Bot", GroupName := "ContactTypeStates")> _
<TemplateVisualStateAttribute(Name := "DistributionGroup", GroupName := "ContactTypeStates")> _
Public Class AvailabilityIcon _
    Inherits ContactBase
'Usage
Dim instance As AvailabilityIcon
```

``` csharp
[TemplateVisualStateAttribute(Name = "Telephone", GroupName = "ContactTypeStates")]
[TemplateVisualStateAttribute(Name = "Person", GroupName = "ContactTypeStates")]
[TemplateVisualStateAttribute(Name = "LargeSize", GroupName = "PhotoDisplayAutoSizeStates")]
[TemplateVisualStateAttribute(Name = "Visible", GroupName = "PhotoVisibilityStates")]
[TemplateVisualStateAttribute(Name = "UnknownContactType", GroupName = "ContactTypeStates")]
[TemplateVisualStateAttribute(Name = "Away", GroupName = "AvailabilityStates")]
[TemplateVisualStateAttribute(Name = "Busy", GroupName = "AvailabilityStates")]
[TemplateVisualStateAttribute(Name = "Unknown", GroupName = "AvailabilityStates")]
[TemplateVisualStateAttribute(Name = "DoNotDisturb", GroupName = "AvailabilityStates")]
[TemplateVisualStateAttribute(Name = "Blocked", GroupName = "AvailabilityStates")]
[TemplateVisualStateAttribute(Name = "Offline", GroupName = "AvailabilityStates")]
[TemplateVisualStateAttribute(Name = "Hidden", GroupName = "PhotoVisibilityStates")]
[TemplateVisualStateAttribute(Name = "Available", GroupName = "AvailabilityStates")]
[TemplateVisualStateAttribute(Name = "HiddenSize", GroupName = "PhotoDisplayAutoSizeStates")]
[TemplateVisualStateAttribute(Name = "SmallSize", GroupName = "PhotoDisplayAutoSizeStates")]
[TemplatePartAttribute(Name = "PART_PresenceColorGrid", Type = typeof(Grid))]
[TemplatePartAttribute(Name = "PART_Viewbox", Type = typeof(Viewbox))]
[TemplateVisualStateAttribute(Name = "Bot", GroupName = "ContactTypeStates")]
[TemplateVisualStateAttribute(Name = "DistributionGroup", GroupName = "ContactTypeStates")]
public class AvailabilityIcon : ContactBase
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[AvailabilityIcon members](availabilityicon-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

