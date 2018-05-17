---
title: Self.BeginSetPhone method  (Microsoft.Lync.Model)
TOCTitle: 'BeginSetPhone method '
ms:assetid: M:Microsoft.Lync.Model.Self.BeginSetPhone(Microsoft.Lync.Model.ContactEndpointType,System.String,System.Boolean,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.beginsetphone(v=office.15)
ms:contentKeyID: 48601094
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.BeginSetPhone
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.BeginSetPhone method

Add the phone if not exist, update if exist.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSetPhone ( _
    phoneType As ContactEndpointType, _
    phoneUri As String, _
    toBePublished As Boolean, _
    selfCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Self
Dim phoneType As ContactEndpointType
Dim phoneUri As String
Dim toBePublished As Boolean
Dim selfCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSetPhone(phoneType, _
    phoneUri, toBePublished, selfCallback, _
    state)
```

``` csharp
public IAsyncResult BeginSetPhone(
    ContactEndpointType phoneType,
    string phoneUri,
    bool toBePublished,
    AsyncCallback selfCallback,
    Object state
)
```

#### Parameters

  - phoneType  
    Type: [Microsoft.Lync.Model.ContactEndpointType](contactendpointtype-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - phoneUri  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - toBePublished  
    Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

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

