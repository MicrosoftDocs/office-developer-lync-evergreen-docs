---
title: NotReadyException class (Microsoft.Lync.Model)
TOCTitle: NotReadyException class
ms:assetid: T:Microsoft.Lync.Model.NotReadyException_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.notreadyexception_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601152
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.NotReadyException
dev_langs:
- CSharp
- JScript
- VB
- other
---

# NotReadyException class

Exception thrown when the operation is pending or Lync client is not ready for the operation.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Exception](http://msdn2.microsoft.com/en-us/library/c18k6c59)  
    [Microsoft.Lync.Model.LyncClientException](lyncclientexception-class-microsoft-lync-model_2.md)  
      Microsoft.Lync.Model.NotReadyException  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<SerializableAttribute> _
Public Class NotReadyException _
    Inherits LyncClientException
'Usage
Dim instance As NotReadyException
```

``` csharp
[SerializableAttribute]
public class NotReadyException : LyncClientException
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[NotReadyException members](notreadyexception-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

