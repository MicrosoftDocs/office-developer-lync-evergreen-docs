---
title: CustomContactList class (Microsoft.Lync.Controls)
TOCTitle: CustomContactList class
ms:assetid: T:Microsoft.Lync.Controls.CustomContactList_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.customcontactlist_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599627
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.CustomContactList
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CustomContactList class

Use the CustomContactsList control to provide an arbitrary and non-hierarchical display of contacts and groups for specific contexts.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [System.Windows.Controls.ItemsControl](http://msdn2.microsoft.com/en-us/library/ms611045)  
                [System.Windows.Controls.Primitives.Selector](http://msdn2.microsoft.com/en-us/library/ms595227)  
                  [System.Windows.Controls.ListBox](http://msdn2.microsoft.com/en-us/library/ms611062)  
                    [Microsoft.Lync.Controls.UCListBox](uclistbox-class-microsoft-lync-controls_1.md)  
                      Microsoft.Lync.Controls.CustomContactList  
                        

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class CustomContactList _
    Inherits UCListBox
'Usage
Dim instance As CustomContactList
```

``` csharp
public class CustomContactList : UCListBox
```

## Remarks

CustomContactsList is a subclass of ListBox which is optimized for use in the display of contact information. The CustomContactsList control can be used to specify a user-specified collection of contacts. Contacts are displayed using a UI template matching that which is used on the ContactList control. Unlike ContactList, this control permits the user to programmatically specify a list of contacts to display, and modify the display settings.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[CustomContactList members](customcontactlist-members-microsoft-lync-controls_1.md)

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
                [System.Windows.Controls.Primitives.Selector](http://msdn2.microsoft.com/en-us/library/ms595227)  
                  [System.Windows.Controls.ListBox](http://msdn2.microsoft.com/en-us/library/ms611062)  
                    [Microsoft.Lync.Controls.UCListBox](uclistbox-class-microsoft-lync-controls_1.md)  
                      Microsoft.Lync.Controls.CustomContactList

