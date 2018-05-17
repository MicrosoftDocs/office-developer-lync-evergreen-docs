---
title: UCListBox.PrepareContainerForItemOverride method  (Microsoft.Lync.Controls)
TOCTitle: 'PrepareContainerForItemOverride method '
ms:assetid: M:Microsoft.Lync.Controls.UCListBox.PrepareContainerForItemOverride(System.Windows.DependencyObject,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.uclistbox.preparecontainerforitemoverride(v=office.15)
ms:contentKeyID: 48594405
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.UCListBox.PrepareContainerForItemOverride
dev_langs:
- CSharp
- JScript
- VB
- other
---

# UCListBox.PrepareContainerForItemOverride method

Prepares the specified element to display the specified item.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overrides Sub PrepareContainerForItemOverride ( _
    element As DependencyObject, _
    item As Object _
)
'Usage
Dim element As DependencyObject
Dim item As Object

Me.PrepareContainerForItemOverride(element, _
    item)
```

``` csharp
protected override void PrepareContainerForItemOverride(
    DependencyObject element,
    Object item
)
```

#### Parameters

  - element  
    Type: [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
    
    The element used to display the specified item.

<!-- end list -->

  - item  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
    
    The item to display

## See also

#### Reference

[UCListBox class](uclistbox-class-microsoft-lync-controls_1.md)

[UCListBox members](uclistbox-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

