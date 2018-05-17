---
title: UCBase.OnContactManagerPropertyChanged method  (Microsoft.Lync.Controls)
TOCTitle: 'OnContactManagerPropertyChanged method '
ms:assetid: M:Microsoft.Lync.Controls.UCBase.OnContactManagerPropertyChanged(Microsoft.Lync.Controls.Internal.Model.IContactsAndGroupsManagerModel,Microsoft.Lync.Controls.Internal.Model.IContactsAndGroupsManagerModel)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.ucbase.oncontactmanagerpropertychanged(v=office.15)
ms:contentKeyID: 48592895
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.UCBase.OnContactManagerPropertyChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# UCBase.OnContactManagerPropertyChanged method

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overridable Sub OnContactManagerPropertyChanged ( _
    oldContactManager As IContactsAndGroupsManagerModel, _
    newContactManager As IContactsAndGroupsManagerModel _
)
'Usage
Dim oldContactManager As IContactsAndGroupsManagerModel
Dim newContactManager As IContactsAndGroupsManagerModel

Me.OnContactManagerPropertyChanged(oldContactManager, _
    newContactManager)
```

``` csharp
protected virtual void OnContactManagerPropertyChanged(
    IContactsAndGroupsManagerModel oldContactManager,
    IContactsAndGroupsManagerModel newContactManager
)
```

#### Parameters

  - oldContactManager  
    Type: **IContactsAndGroupsManagerModel**  

<!-- end list -->

  - newContactManager  
    Type: **IContactsAndGroupsManagerModel**  

## See also

#### Reference

[UCBase class](ucbase-class-microsoft-lync-controls_1.md)

[UCBase members](ucbase-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

