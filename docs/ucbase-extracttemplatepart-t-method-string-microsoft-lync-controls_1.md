---
title: UCBase.ExtractTemplatePart(T) method (String) (Microsoft.Lync.Controls)
TOCTitle: ExtractTemplatePart(T) method (String)
ms:assetid: M:Microsoft.Lync.Controls.UCBase.ExtractTemplatePart``1(System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Hh364282(v=office.15)
ms:contentKeyID: 48602045
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# UCBase.ExtractTemplatePart\<T\> method (String)

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Function ExtractTemplatePart(Of T As DependencyObject) ( _
    partName As String _
) As T
'Usage
Dim partName As String
Dim returnValue As T

returnValue = Me.ExtractTemplatePart(partName)
```

``` csharp
protected T ExtractTemplatePart<T>(
    string partName
)
where T : DependencyObject
```

#### Type parameters

  - T

#### Parameters

  - partName  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

#### Return value

Type: T  

## See also

#### Reference

[UCBase class](ucbase-class-microsoft-lync-controls_1.md)

[UCBase members](ucbase-members-microsoft-lync-controls_1.md)

[ExtractTemplatePart overload](ucbase-extracttemplatepart-method-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

