---
title: ContactSearchResultList class (Microsoft.Lync.Controls)
TOCTitle: ContactSearchResultList class
ms:assetid: T:Microsoft.Lync.Controls.ContactSearchResultList_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactsearchresultlist_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591199
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactSearchResultList
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSearchResultList class

Use the ContactSearchResultList control to display the result of a search performed by the [ContactSearchInputBox](contactsearchinputbox-class-microsoft-lync-controls_1.md) control.

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
                      Microsoft.Lync.Controls.ContactSearchResultList  
                        

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_TrySkillSearchButton", Type := GetType(ButtonBase))> _
<TemplatePartAttribute(Name := "ScrollViewer", Type := GetType(FrameworkElement))> _
Public Class ContactSearchResultList _
    Inherits UCListBox
'Usage
Dim instance As ContactSearchResultList
```

``` csharp
[TemplatePartAttribute(Name = "PART_TrySkillSearchButton", Type = typeof(ButtonBase))]
[TemplatePartAttribute(Name = "ScrollViewer", Type = typeof(FrameworkElement))]
public class ContactSearchResultList : UCListBox
```

## Remarks

This control provides an result list for a contact search. To initiate a search, this control must be paired with a [ContactSearchInputBox](contactsearchinputbox-class-microsoft-lync-controls_1.md).

The [ContactSearchInputBox](contactsearchinputbox-class-microsoft-lync-controls_1.md) and ContactSearchResultList controls, while related, are designed as separate controls to allow the developer to display search results and search input in separate locations on a page.

Alternatively, use the [ContactSearch](contactsearch-class-microsoft-lync-controls_1.md) control, which encapsulates both features in a single, self contained control.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactSearchResultList members](contactsearchresultlist-members-microsoft-lync-controls_1.md)

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
                      Microsoft.Lync.Controls.ContactSearchResultList

