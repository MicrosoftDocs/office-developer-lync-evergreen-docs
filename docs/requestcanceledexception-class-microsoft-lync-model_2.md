---
title: RequestCanceledException class (Microsoft.Lync.Model)
TOCTitle: RequestCanceledException class
ms:assetid: T:Microsoft.Lync.Model.RequestCanceledException_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.requestcanceledexception_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597262
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.RequestCanceledException
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RequestCanceledException class

Exception thrown when the request is already cancelled.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Exception](http://msdn2.microsoft.com/en-us/library/c18k6c59)  
    [Microsoft.Lync.Model.LyncClientException](lyncclientexception-class-microsoft-lync-model_2.md)  
      Microsoft.Lync.Model.RequestCanceledException  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<SerializableAttribute> _
Public Class RequestCanceledException _
    Inherits LyncClientException
'Usage
Dim instance As RequestCanceledException
```

``` csharp
[SerializableAttribute]
public class RequestCanceledException : LyncClientException
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[RequestCanceledException members](requestcanceledexception-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

