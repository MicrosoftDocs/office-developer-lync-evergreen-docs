---
title: SearchResultCollection class (Microsoft.Lync.Controls)
TOCTitle: SearchResultCollection class
ms:assetid: T:Microsoft.Lync.Controls.SearchResultCollection_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.searchresultcollection_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596312
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.SearchResultCollection
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchResultCollection class

A data structure which holds the result set and metadata which describes a search operation that has been executed by the [ContactSearch](contactsearch-class-microsoft-lync-controls_1.md) control.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.Collections.ObjectModel.ReadOnlyCollection](http://msdn2.microsoft.com/en-us/library/ms132474)\<[SearchResult](searchresult-class-microsoft-lync-controls_1.md)\>  
    Microsoft.Lync.Controls.SearchResultCollection  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class SearchResultCollection _
    Inherits ReadOnlyCollection(Of SearchResult)
'Usage
Dim instance As SearchResultCollection
```

``` csharp
public class SearchResultCollection : ReadOnlyCollection<SearchResult>
```

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[SearchResultCollection members](searchresultcollection-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

