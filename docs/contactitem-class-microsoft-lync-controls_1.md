---
title: ContactItem class (Microsoft.Lync.Controls)
TOCTitle: ContactItem class
ms:assetid: T:Microsoft.Lync.Controls.ContactItem_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactitem_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594448
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactItem
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactItem class

Reserved for internal use.

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
                  Microsoft.Lync.Controls.ContactItem  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_ContactItemContentPresenter", Type := GetType(ContactItemContentPresenter))> _
Public Class ContactItem _
    Inherits ContactBase
'Usage
Dim instance As ContactItem
```

``` csharp
[TemplatePartAttribute(Name = "PART_ContactItemContentPresenter", Type = typeof(ContactItemContentPresenter))]
public class ContactItem : ContactBase
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactItem members](contactitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

