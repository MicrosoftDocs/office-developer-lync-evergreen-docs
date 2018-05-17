---
title: Self.CanSetPhone method  (Microsoft.Lync.Model)
TOCTitle: 'CanSetPhone method '
ms:assetid: M:Microsoft.Lync.Model.Self.CanSetPhone(Microsoft.Lync.Model.ContactEndpointType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.cansetphone(v=office.15)
ms:contentKeyID: 48592415
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.CanSetPhone
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.CanSetPhone method

Returns true when the specific type can be set.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanSetPhone ( _
    phoneType As ContactEndpointType _
) As Boolean
'Usage
Dim instance As Self
Dim phoneType As ContactEndpointType
Dim returnValue As Boolean

returnValue = instance.CanSetPhone(phoneType)
```

``` csharp
public bool CanSetPhone(
    ContactEndpointType phoneType
)
```

#### Parameters

  - phoneType  
    Type: [Microsoft.Lync.Model.ContactEndpointType](contactendpointtype-enumeration-microsoft-lync-model_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[Self class](self-class-microsoft-lync-model_2.md)

[Self members](self-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

