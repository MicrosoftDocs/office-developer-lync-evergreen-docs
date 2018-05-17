---
title: ContactBase.OnContactPropertyChanged method  (Microsoft.Lync.Controls)
TOCTitle: 'OnContactPropertyChanged method '
ms:assetid: M:Microsoft.Lync.Controls.ContactBase.OnContactPropertyChanged(Microsoft.Lync.Controls.Internal.Model.IContactModel,System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactbase.oncontactpropertychanged(v=office.15)
ms:contentKeyID: 48593912
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactBase.OnContactPropertyChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactBase.OnContactPropertyChanged method

Reserved for internal use.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overridable Sub OnContactPropertyChanged ( _
    contactModel As IContactModel, _
    propertyName As String _
)
'Usage
Dim contactModel As IContactModel
Dim propertyName As String

Me.OnContactPropertyChanged(contactModel, _
    propertyName)
```

``` csharp
protected virtual void OnContactPropertyChanged(
    IContactModel contactModel,
    string propertyName
)
```

#### Parameters

  - contactModel  
    Type: **IContactModel**  

<!-- end list -->

  - propertyName  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

## See also

#### Reference

[ContactBase class](contactbase-class-microsoft-lync-controls_1.md)

[ContactBase members](contactbase-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

