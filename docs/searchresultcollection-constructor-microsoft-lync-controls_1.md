---
title: SearchResultCollection constructor  (Microsoft.Lync.Controls)
TOCTitle: 'SearchResultCollection constructor '
ms:assetid: M:Microsoft.Lync.Controls.SearchResultCollection.#ctor(System.Collections.Generic.IList{Microsoft.Lync.Controls.SearchResult},System.Boolean,Microsoft.Lync.Controls.SearchType,System.Uri,Microsoft.Lync.Controls.SearchError,Microsoft.Lync.Controls.SyncState)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.searchresultcollection.searchresultcollection(v=office.15)
ms:contentKeyID: 48592420
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.SearchResultCollection.SearchResultCollection
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchResultCollection constructor

Constructor.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Sub New ( _
    results As IList(Of SearchResult), _
    isMoreAvailable As Boolean, _
    searchType As SearchType, _
    skillSearchQueryUri As Uri, _
    searchError As SearchError, _
    providerSyncState As SyncState _
)
'Usage
Dim results As IList(Of SearchResult)
Dim isMoreAvailable As Boolean
Dim searchType As SearchType
Dim skillSearchQueryUri As Uri
Dim searchError As SearchError
Dim providerSyncState As SyncState

Dim instance As New SearchResultCollection(results, _
    isMoreAvailable, searchType, skillSearchQueryUri, _
    searchError, providerSyncState)
```

``` csharp
public SearchResultCollection(
    IList<SearchResult> results,
    bool isMoreAvailable,
    SearchType searchType,
    Uri skillSearchQueryUri,
    SearchError searchError,
    SyncState providerSyncState
)
```

#### Parameters

  - results  
    Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[SearchResult](searchresult-class-microsoft-lync-controls_1.md)\>  

<!-- end list -->

  - isMoreAvailable  
    Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

<!-- end list -->

  - searchType  
    Type: [Microsoft.Lync.Controls.SearchType](searchtype-enumeration-microsoft-lync-controls_1.md)  

<!-- end list -->

  - skillSearchQueryUri  
    Type: [System.Uri](http://msdn2.microsoft.com/en-us/library/txt7706a)  

<!-- end list -->

  - searchError  
    Type: [Microsoft.Lync.Controls.SearchError](searcherror-enumeration-microsoft-lync-controls_1.md)  

<!-- end list -->

  - providerSyncState  
    Type: [Microsoft.Lync.Controls.SyncState](syncstate-enumeration-microsoft-lync-controls_1.md)  

## See also

#### Reference

[SearchResultCollection class](searchresultcollection-class-microsoft-lync-controls_1.md)

[SearchResultCollection members](searchresultcollection-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

