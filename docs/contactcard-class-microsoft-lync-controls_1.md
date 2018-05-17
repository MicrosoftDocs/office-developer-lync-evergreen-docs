---
title: ContactCard class (Microsoft.Lync.Controls)
TOCTitle: ContactCard class
ms:assetid: T:Microsoft.Lync.Controls.ContactCard_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactcard_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591184
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactCard
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactCard class

The ContactCard control shows basic or detailed contact and organization information for contacts.

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
                  Microsoft.Lync.Controls.ContactCard  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_NoteContainer", Type := GetType(FrameworkElement))> _
<TemplatePartAttribute(Name := "PART_ExpandDetailsToggleButton", Type := GetType(ToggleButton))> _
<TemplatePartAttribute(Name := "PART_DetailsContainer", Type := GetType(FrameworkElement))> _
Public Class ContactCard _
    Inherits ContactBase
'Usage
Dim instance As ContactCard
```

``` csharp
[TemplatePartAttribute(Name = "PART_NoteContainer", Type = typeof(FrameworkElement))]
[TemplatePartAttribute(Name = "PART_ExpandDetailsToggleButton", Type = typeof(ToggleButton))]
[TemplatePartAttribute(Name = "PART_DetailsContainer", Type = typeof(FrameworkElement))]
public class ContactCard : ContactBase
```

## Remarks

This control displays a contact card for a person or distribution group, specified by the property. The card can optionally be [IsExpanded](contactcard-isexpanded-property-microsoft-lync-controls_1.md), to reveal a set of [SelectedTabIndex](contactcard-selectedtabindex-property-microsoft-lync-controls_1.md) which show detailed information about the contact. This control displays presence and availability of colleagues, and gives users the ability to start instant message sessions, voice calls, file transfers, application sharing sessions, or conference calls.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactCard members](contactcard-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

