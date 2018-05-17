---
title: ContactManager.EndLookup method  (Microsoft.Lync.Model)
TOCTitle: 'EndLookup method '
ms:assetid: M:Microsoft.Lync.Model.ContactManager.EndLookup(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.endlookup(v=office.15)
ms:contentKeyID: 48598182
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.EndLookup
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.EndLookup method

Looks up a contact or a distribution group by entryid, sip address, email address, display name, etc..

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndLookup ( _
    asyncResult As IAsyncResult _
) As Object
'Usage
Dim instance As ContactManager
Dim asyncResult As IAsyncResult
Dim returnValue As Object

returnValue = instance.EndLookup(asyncResult)
```

``` csharp
public Object EndLookup(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

