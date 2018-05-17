---
title: SearchResult.HitHighlightSummary property  (Microsoft.Lync.Controls)
TOCTitle: 'HitHighlightSummary property '
ms:assetid: P:Microsoft.Lync.Controls.SearchResult.HitHighlightSummary_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.searchresult.hithighlightsummary_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599841
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.SearchResult.HitHighlightSummary
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchResult.HitHighlightSummary property

An XML string which describes the matches in a Skill search summary.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property HitHighlightSummary As String
    Get
    Friend Set
'Usage
Dim instance As SearchResult
Dim value As String

value = instance.HitHighlightSummary
```

``` csharp
public string HitHighlightSummary { get; internal set; }
```

#### Property value

Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

## Remarks

This string contains a sequence of skills which describe the contact found in the [Result](searchresult-result-property-microsoft-lync-controls_1.md). The skill descriptions are separated by delimiters, and within each delimited sstring, there is additional XML markup which identifies the specific word or words which matched the search.

## See also

#### Reference

[SearchResult class](searchresult-class-microsoft-lync-controls_1.md)

[SearchResult members](searchresult-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

