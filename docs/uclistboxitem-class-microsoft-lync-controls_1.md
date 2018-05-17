---
title: UCListBoxItem class (Microsoft.Lync.Controls)
TOCTitle: UCListBoxItem class
ms:assetid: T:Microsoft.Lync.Controls.UCListBoxItem_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.uclistboxitem_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592762
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.UCListBoxItem
dev_langs:
- CSharp
- JScript
- VB
- other
---

# UCListBoxItem class

Reserved for internal use.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [System.Windows.Controls.ContentControl](http://msdn2.microsoft.com/en-us/library/ms609797)  
                [System.Windows.Controls.ListBoxItem](http://msdn2.microsoft.com/en-us/library/ms611063)  
                  Microsoft.Lync.Controls.UCListBoxItem  
                    [Microsoft.Lync.Controls.CustomContactListItem](customcontactlistitem-class-microsoft-lync-controls_1.md)  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_ContactItem", Type := GetType(ContactItem))> _
Public MustInherit Class UCListBoxItem _
    Inherits ListBoxItem
'Usage
Dim instance As UCListBoxItem
```

``` csharp
[TemplatePartAttribute(Name = "PART_ContactItem", Type = typeof(ContactItem))]
public abstract class UCListBoxItem : ListBoxItem
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[UCListBoxItem members](uclistboxitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

