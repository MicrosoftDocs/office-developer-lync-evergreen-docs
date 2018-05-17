---
title: SearchResults.AllResults property  (Microsoft.Lync.Model)
TOCTitle: 'AllResults property '
ms:assetid: P:Microsoft.Lync.Model.SearchResults.AllResults_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.searchresults.allresults_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597512
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SearchResults.AllResults
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchResults.AllResults property

Returns all search results (contacts, groups or expert search results)

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property AllResults As IList(Of SearchResult)
    Get
'Usage
Dim instance As SearchResults
Dim value As IList(Of SearchResult)

value = instance.AllResults
```

``` csharp
public IList<SearchResult> AllResults { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[SearchResult](searchresult-class-microsoft-lync-model_2.md)\>  

## See also

#### Reference

[SearchResults class](searchresults-class-microsoft-lync-model_2.md)

[SearchResults members](searchresults-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

