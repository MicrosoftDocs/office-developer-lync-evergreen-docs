---
title: NotInitializedException class (Microsoft.Lync.Model)
TOCTitle: NotInitializedException class
ms:assetid: T:Microsoft.Lync.Model.NotInitializedException_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.notinitializedexception_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592208
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.NotInitializedException
dev_langs:
- CSharp
- JScript
- VB
- other
---

# NotInitializedException class

Exception thrown when the Lync client is not initialized or is already shutdown.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Exception](http://msdn2.microsoft.com/en-us/library/c18k6c59)  
    [Microsoft.Lync.Model.LyncClientException](lyncclientexception-class-microsoft-lync-model_2.md)  
      Microsoft.Lync.Model.NotInitializedException  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<SerializableAttribute> _
Public Class NotInitializedException _
    Inherits LyncClientException
'Usage
Dim instance As NotInitializedException
```

``` csharp
[SerializableAttribute]
public class NotInitializedException : LyncClientException
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[NotInitializedException members](notinitializedexception-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

