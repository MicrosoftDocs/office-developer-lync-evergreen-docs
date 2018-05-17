---
title: ContactSearch class (Microsoft.Lync.Controls)
TOCTitle: ContactSearch class
ms:assetid: T:Microsoft.Lync.Controls.ContactSearch_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactsearch_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594469
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactSearch
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSearch class

ContactSearch combines the functionality of the [ContactSearchInputBox](contactsearchinputbox-class-microsoft-lync-controls_1.md) and [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) controls into a single, self contained control.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              Microsoft.Lync.Controls.ContactSearch  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "ContactSearchInputBox", Type := GetType(ContactSearchInputBox))> _
Public Class ContactSearch _
    Inherits Control
'Usage
Dim instance As ContactSearch
```

``` csharp
[TemplatePartAttribute(Name = "ContactSearchInputBox", Type = typeof(ContactSearchInputBox))]
public class ContactSearch : Control
```

## Remarks

To display search results and search input in separate locations on a page, use the ContactSearchInputBox and ContactSearchResultList controls as separate controls. The ContactSearch control provides an input box for searching for contacts by name or keyword, and a result list for displaying the set of contacts which were found.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactSearch members](contactsearch-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

