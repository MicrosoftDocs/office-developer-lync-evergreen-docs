---
title: ContactSearchResultList.ClearContainerForItemOverride method  (Microsoft.Lync.Controls)
TOCTitle: 'ClearContainerForItemOverride method '
ms:assetid: M:Microsoft.Lync.Controls.ContactSearchResultList.ClearContainerForItemOverride(System.Windows.DependencyObject,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactsearchresultlist.clearcontainerforitemoverride(v=office.15)
ms:contentKeyID: 48593902
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactSearchResultList.ClearContainerForItemOverride
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSearchResultList.ClearContainerForItemOverride method

Removes any bindings and templates applied to the item container for the specified content.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overrides Sub ClearContainerForItemOverride ( _
    element As DependencyObject, _
    item As Object _
)
'Usage
Dim element As DependencyObject
Dim item As Object

Me.ClearContainerForItemOverride(element, _
    item)
```

``` csharp
protected override void ClearContainerForItemOverride(
    DependencyObject element,
    Object item
)
```

#### Parameters

  - element  
    Type: [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
    
    The item used to display the specified content.

<!-- end list -->

  - item  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
    
    The item content.

## See also

#### Reference

[ContactSearchResultList class](contactsearchresultlist-class-microsoft-lync-controls_1.md)

[ContactSearchResultList members](contactsearchresultlist-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

