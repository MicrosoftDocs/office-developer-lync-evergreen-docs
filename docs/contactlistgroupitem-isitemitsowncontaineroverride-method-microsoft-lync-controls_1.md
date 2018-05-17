---
title: ContactListGroupItem.IsItemItsOwnContainerOverride method  (Microsoft.Lync.Controls)
TOCTitle: 'IsItemItsOwnContainerOverride method '
ms:assetid: M:Microsoft.Lync.Controls.ContactListGroupItem.IsItemItsOwnContainerOverride(System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactlistgroupitem.isitemitsowncontaineroverride(v=office.15)
ms:contentKeyID: 48596353
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactListGroupItem.IsItemItsOwnContainerOverride
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactListGroupItem.IsItemItsOwnContainerOverride method

Determines whether an object is a [ContactListGroupItem](contactlistgroupitem-class-microsoft-lync-controls_1.md).

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overrides Function IsItemItsOwnContainerOverride ( _
    item As Object _
) As Boolean
'Usage
Dim item As Object
Dim returnValue As Boolean

returnValue = Me.IsItemItsOwnContainerOverride(item)
```

``` csharp
protected override bool IsItemItsOwnContainerOverride(
    Object item
)
```

#### Parameters

  - item  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
    
    The object to evaluate.

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
true if item is a [ContactListGroupItem](contactlistgroupitem-class-microsoft-lync-controls_1.md); otherwise, false.  

## See also

#### Reference

[ContactListGroupItem class](contactlistgroupitem-class-microsoft-lync-controls_1.md)

[ContactListGroupItem members](contactlistgroupitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

