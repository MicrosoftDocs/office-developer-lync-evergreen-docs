---
title: ContactListGroupItem class (Microsoft.Lync.Controls)
TOCTitle: ContactListGroupItem class
ms:assetid: T:Microsoft.Lync.Controls.ContactListGroupItem_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactlistgroupitem_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592307
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactListGroupItem
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactListGroupItem class

Reserved for internal use. This control is used to display the group nodes in a [ContactList](contactlist-class-microsoft-lync-controls_1.md) control.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [System.Windows.Controls.ItemsControl](http://msdn2.microsoft.com/en-us/library/ms611045)  
                [System.Windows.Controls.HeaderedItemsControl](http://msdn2.microsoft.com/en-us/library/ms616578)  
                  [System.Windows.Controls.TreeViewItem](http://msdn2.microsoft.com/en-us/library/ms595701)  
                    [Microsoft.Lync.Controls.UCTreeViewItem](uctreeviewitem-class-microsoft-lync-controls_1.md)  
                      Microsoft.Lync.Controls.ContactListGroupItem  
                        

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_GroupRenameTextbox", Type := GetType(TextBox))> _
Public Class ContactListGroupItem _
    Inherits UCTreeViewItem
'Usage
Dim instance As ContactListGroupItem
```

``` csharp
[TemplatePartAttribute(Name = "PART_GroupRenameTextbox", Type = typeof(TextBox))]
public class ContactListGroupItem : UCTreeViewItem
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactListGroupItem members](contactlistgroupitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [System.Windows.Controls.ItemsControl](http://msdn2.microsoft.com/en-us/library/ms611045)  
                [System.Windows.Controls.HeaderedItemsControl](http://msdn2.microsoft.com/en-us/library/ms616578)  
                  [System.Windows.Controls.TreeViewItem](http://msdn2.microsoft.com/en-us/library/ms595701)  
                    [Microsoft.Lync.Controls.UCTreeViewItem](uctreeviewitem-class-microsoft-lync-controls_1.md)  
                      Microsoft.Lync.Controls.ContactListGroupItem

