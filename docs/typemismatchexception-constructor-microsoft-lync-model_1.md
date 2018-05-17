---
title: TypeMismatchException constructor  (Microsoft.Lync.Model)
TOCTitle: 'TypeMismatchException constructor '
ms:assetid: M:Microsoft.Lync.Model.TypeMismatchException.#ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.typemismatchexception.typemismatchexception(v=office.15)
ms:contentKeyID: 48596395
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.TypeMismatchException.TypeMismatchException
dev_langs:
- CSharp
- JScript
- VB
- other
---

# TypeMismatchException constructor

Initializes a new instance of the TypeMismatchException class with serialized data.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Protected Sub New ( _
    info As SerializationInfo, _
    context As StreamingContext _
)
'Usage
Dim info As SerializationInfo
Dim context As StreamingContext

Dim instance As New TypeMismatchException(info, context)
```

``` csharp
protected TypeMismatchException(
    SerializationInfo info,
    StreamingContext context
)
```

#### Parameters

  - info  
    Type: [System.Runtime.Serialization.SerializationInfo](http://msdn2.microsoft.com/en-us/library/a9b6042e)  
    
    SerializationInfo object that holds the serialized object data about the exception being thrown.

<!-- end list -->

  - context  
    Type: [System.Runtime.Serialization.StreamingContext](http://msdn2.microsoft.com/en-us/library/t16abws5)  
    
    StreamingContext object that contains contextual information about the source or destination.

## See also

#### Reference

[TypeMismatchException class](typemismatchexception-class-microsoft-lync-model_2.md)

[TypeMismatchException members](typemismatchexception-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

