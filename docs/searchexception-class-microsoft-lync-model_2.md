---
title: SearchException class (Microsoft.Lync.Model)
TOCTitle: SearchException class
ms:assetid: T:Microsoft.Lync.Model.SearchException_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.searchexception_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601753
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SearchException
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchException class

Exception thrown when search operation ended with an error.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Exception](http://msdn2.microsoft.com/en-us/library/c18k6c59)  
    [Microsoft.Lync.Model.LyncClientException](lyncclientexception-class-microsoft-lync-model_2.md)  
      [Microsoft.Lync.Model.OperationException](operationexception-class-microsoft-lync-model_2.md)  
        Microsoft.Lync.Model.SearchException  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<SerializableAttribute> _
Public Class SearchException _
    Inherits OperationException
'Usage
Dim instance As SearchException
```

``` csharp
[SerializableAttribute]
public class SearchException : OperationException
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[SearchException members](searchexception-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

