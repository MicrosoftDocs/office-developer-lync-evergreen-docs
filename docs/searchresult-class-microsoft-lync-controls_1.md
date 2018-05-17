---
title: SearchResult class (Microsoft.Lync.Controls)
TOCTitle: SearchResult class
ms:assetid: T:Microsoft.Lync.Controls.SearchResult_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.searchresult_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597237
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.SearchResult
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchResult class

A data structure which contains a single search result. See [ContactSearchInputBox](contactsearchinputbox-class-microsoft-lync-controls_1.md).

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  Microsoft.Lync.Controls.SearchResult  

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Class SearchResult
'Usage
Dim instance As SearchResult
```

``` csharp
public class SearchResult
```

## Remarks

A search [Result](searchresult-result-property-microsoft-lync-controls_1.md) consists of a single contact or distribution group. For skill searches, the result also contains a [HitHighlightSummary](searchresult-hithighlightsummary-property-microsoft-lync-controls_1.md) which highlights matches for the contact's skill description.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[SearchResult members](searchresult-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

