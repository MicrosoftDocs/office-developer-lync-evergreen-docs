---
title: ContactManager.EndSearch method  (Microsoft.Lync.Model)
TOCTitle: 'EndSearch method '
ms:assetid: M:Microsoft.Lync.Model.ContactManager.EndSearch(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.endsearch(v=office.15)
ms:contentKeyID: 48598260
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.EndSearch
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.EndSearch method

Searches for contacts and distribution groups that match the given search criteria.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndSearch ( _
    asyncResult As IAsyncResult _
) As SearchResults
'Usage
Dim instance As ContactManager
Dim asyncResult As IAsyncResult
Dim returnValue As SearchResults

returnValue = instance.EndSearch(asyncResult)
```

``` csharp
public SearchResults EndSearch(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.SearchResults](searchresults-class-microsoft-lync-model_2.md)  

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

