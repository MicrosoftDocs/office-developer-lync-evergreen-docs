---
title: ContactSearchInputBox class (Microsoft.Lync.Controls)
TOCTitle: ContactSearchInputBox class
ms:assetid: T:Microsoft.Lync.Controls.ContactSearchInputBox_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactsearchinputbox_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598154
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactSearchInputBox
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSearchInputBox class

Use the ContactSearchInputBox control to enable users to search their organization for people based on name, phone number, or skill.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Windows.Threading.DispatcherObject](http://msdn2.microsoft.com/en-us/library/ms615925)  
    [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
      [System.Windows.Media.Visual](http://msdn2.microsoft.com/en-us/library/ms635637)  
        [System.Windows.UIElement](http://msdn2.microsoft.com/en-us/library/ms590078)  
          [System.Windows.FrameworkElement](http://msdn2.microsoft.com/en-us/library/ms602714)  
            [System.Windows.Controls.Control](http://msdn2.microsoft.com/en-us/library/ms609826)  
              [Microsoft.Lync.Controls.UCBase](ucbase-class-microsoft-lync-controls_1.md)  
                Microsoft.Lync.Controls.ContactSearchInputBox  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
<TemplatePartAttribute(Name := "PART_SearchHint", Type := GetType(ContentControl))> _
<TemplatePartAttribute(Name := "PART_ClearButton", Type := GetType(Button))> _
<TemplateVisualStateAttribute(Name := "SearchNotInUse", GroupName := "SearchInUseStates")> _
<TemplateVisualStateAttribute(Name := "SearchInUse", GroupName := "SearchInUseStates")> _
<TemplatePartAttribute(Name := "PART_TextSearch", Type := GetType(TextBox))> _
Public Class ContactSearchInputBox _
    Inherits UCBase
'Usage
Dim instance As ContactSearchInputBox
```

``` csharp
[TemplatePartAttribute(Name = "PART_SearchHint", Type = typeof(ContentControl))]
[TemplatePartAttribute(Name = "PART_ClearButton", Type = typeof(Button))]
[TemplateVisualStateAttribute(Name = "SearchNotInUse", GroupName = "SearchInUseStates")]
[TemplateVisualStateAttribute(Name = "SearchInUse", GroupName = "SearchInUseStates")]
[TemplatePartAttribute(Name = "PART_TextSearch", Type = typeof(TextBox))]
public class ContactSearchInputBox : UCBase
```

## Remarks

The ContactSearchInputBox control displays a text box where users enter a search string. The search is executed automatically, one second after the search text is changed, or explicitly when the user presses Enter in the ContactSearchInputBox. Once a search is complete, the results appear in a [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) control. The [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) control provides an input box for searching for contacts by name or keyword. The ContactSearchInputBox and [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) controls, while related, are designed as separate controls to allow the developer to display search results and search input in separate locations on a page. Use the [ContactSearch](contactsearch-class-microsoft-lync-controls_1.md) control in Lync Control applications to display the ContactSearchInputBox and [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) controls together in the same location on a page.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[ContactSearchInputBox members](contactsearchinputbox-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

