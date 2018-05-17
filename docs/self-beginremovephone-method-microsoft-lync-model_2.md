---
title: Self.BeginRemovePhone method  (Microsoft.Lync.Model)
TOCTitle: 'BeginRemovePhone method '
ms:assetid: M:Microsoft.Lync.Model.Self.BeginRemovePhone(Microsoft.Lync.Model.ContactEndpointType,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.beginremovephone(v=office.15)
ms:contentKeyID: 48598428
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.BeginRemovePhone
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.BeginRemovePhone method

Removes the phone.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginRemovePhone ( _
    phoneType As ContactEndpointType, _
    selfCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Self
Dim phoneType As ContactEndpointType
Dim selfCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginRemovePhone(phoneType, _
    selfCallback, state)
```

``` csharp
public IAsyncResult BeginRemovePhone(
    ContactEndpointType phoneType,
    AsyncCallback selfCallback,
    Object state
)
```

#### Parameters

  - phoneType  
    Type: [Microsoft.Lync.Model.ContactEndpointType](contactendpointtype-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - selfCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Self class](self-class-microsoft-lync-model_2.md)

[Self members](self-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

