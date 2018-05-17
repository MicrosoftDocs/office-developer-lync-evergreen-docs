---
title: ContactList class (Microsoft.Lync.Controls)
TOCTitle: ContactList class
ms:assetid: T:Microsoft.Lync.Controls.ContactList_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactlist_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599126
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactList
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactList class

Use the ContactList control to display the Lync contacts list, and give users the ability to launch voice, instant messaging (IM), or e-mail conversations with any of their contacts.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [Microsoft.Lync.Controls.UCBase](ucbase-class-microsoft-lync-controls_1.md)  
                Microsoft.Lync.Controls.ContactList  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_TreeControl", Type := GetType(UCTreeView))> _
Public Class ContactList _
    Inherits UCBase
'Usage
Dim instance As ContactList
```

``` csharp
[TemplatePartAttribute(Name = "PART_TreeControl", Type = typeof(UCTreeView))]
public class ContactList : UCBase
```

## Remarks

The control supports Group, Relationship, and Status views, in the same manner as Lync, and includes the option to switch between status only, and status with photo display modes. The ContactList control gives users the ability to copy, move, delete, multi-select and sort contacts, set status alerts, and manage privacy settings.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactList members](contactlist-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

