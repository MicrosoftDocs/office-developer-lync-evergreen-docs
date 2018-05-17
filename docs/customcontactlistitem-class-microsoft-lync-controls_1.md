---
title: CustomContactListItem class (Microsoft.Lync.Controls)
TOCTitle: CustomContactListItem class
ms:assetid: T:Microsoft.Lync.Controls.CustomContactListItem_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.customcontactlistitem_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596702
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.CustomContactListItem
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CustomContactListItem class

Use the CustomContactListItem control with the CustomContactsList control to show basic or detailed contact and organization information for contacts.

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
                  [Microsoft.Lync.Controls.UCListBoxItem](uclistboxitem-class-microsoft-lync-controls_1.md)  
                    Microsoft.Lync.Controls.CustomContactListItem  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class CustomContactListItem _
    Inherits UCListBoxItem
'Usage
Dim instance As CustomContactListItem
```

``` csharp
public class CustomContactListItem : UCListBoxItem
```

## Remarks

CustomContactListItem is a child control, created for use with the CustomContactsList control. CustomContactListItem supports a [Source](contactbase-source-property-microsoft-lync-controls_1.md) property, similar to that used by other Microsoft Lync SDK objects which operate on a single contact. CustomContactListItem also supports a ContentPropertyAttribute attribute which permits the Source property to be specified in XAML as a child element.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[CustomContactListItem members](customcontactlistitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

