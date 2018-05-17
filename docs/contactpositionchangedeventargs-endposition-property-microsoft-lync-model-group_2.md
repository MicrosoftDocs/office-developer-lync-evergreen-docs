---
title: ContactPositionChangedEventArgs.EndPosition property  (Microsoft.Lync.Model.Group)
TOCTitle: 'EndPosition property '
ms:assetid: P:Microsoft.Lync.Model.Group.ContactPositionChangedEventArgs.EndPosition_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.contactpositionchangedeventargs.endposition_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592294
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.ContactPositionChangedEventArgs.EndPosition
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactPositionChangedEventArgs.EndPosition property

Returns the end position of the contacts that have their positions changed. A value greater than the contact count means that all contacts from the start position have their positions changed.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property EndPosition As Integer
    Get
'Usage
Dim instance As ContactPositionChangedEventArgs
Dim value As Integer

value = instance.EndPosition
```

``` csharp
public int EndPosition { get; }
```

#### Property value

Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

## See also

#### Reference

[ContactPositionChangedEventArgs class](contactpositionchangedeventargs-class-microsoft-lync-model-group_2.md)

[ContactPositionChangedEventArgs members](contactpositionchangedeventargs-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

