---
title: SearchResult.Result property  (Microsoft.Lync.Controls)
TOCTitle: 'Result property '
ms:assetid: P:Microsoft.Lync.Controls.SearchResult.Result_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.searchresult.result_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600989
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.SearchResult.Result
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchResult.Result property

The contact or distribution group which was returned for this search result.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property Result As Object
    Get
    Friend Set
'Usage
Dim instance As SearchResult
Dim value As Object

value = instance.Result
```

``` csharp
public Object Result { get; internal set; }
```

#### Property value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

## Remarks

This value references either a [Contact](contact-class-microsoft-lync-model_2.md) or a [DistributionGroup](distributiongroup-class-microsoft-lync-model-group_2.md).

## See also

#### Reference

[SearchResult class](searchresult-class-microsoft-lync-controls_1.md)

[SearchResult members](searchresult-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

