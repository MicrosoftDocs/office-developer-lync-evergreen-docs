---
title: UCBase.OnSelfModelPropertyChanged method  (Microsoft.Lync.Controls)
TOCTitle: 'OnSelfModelPropertyChanged method '
ms:assetid: M:Microsoft.Lync.Controls.UCBase.OnSelfModelPropertyChanged(Microsoft.Lync.Controls.Internal.Model.ISelfModel,Microsoft.Lync.Controls.Internal.Model.ISelfModel)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.ucbase.onselfmodelpropertychanged(v=office.15)
ms:contentKeyID: 48600997
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.UCBase.OnSelfModelPropertyChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# UCBase.OnSelfModelPropertyChanged method

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overridable Sub OnSelfModelPropertyChanged ( _
    oldSelfModel As ISelfModel, _
    newSelfModel As ISelfModel _
)
'Usage
Dim oldSelfModel As ISelfModel
Dim newSelfModel As ISelfModel

Me.OnSelfModelPropertyChanged(oldSelfModel, _
    newSelfModel)
```

``` csharp
protected virtual void OnSelfModelPropertyChanged(
    ISelfModel oldSelfModel,
    ISelfModel newSelfModel
)
```

#### Parameters

  - oldSelfModel  
    Type: **ISelfModel**  

<!-- end list -->

  - newSelfModel  
    Type: **ISelfModel**  

## See also

#### Reference

[UCBase class](ucbase-class-microsoft-lync-controls_1.md)

[UCBase members](ucbase-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

