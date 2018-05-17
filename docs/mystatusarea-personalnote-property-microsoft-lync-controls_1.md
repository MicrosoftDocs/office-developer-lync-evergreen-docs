---
title: MyStatusArea.PersonalNote property  (Microsoft.Lync.Controls)
TOCTitle: 'PersonalNote property '
ms:assetid: P:Microsoft.Lync.Controls.MyStatusArea.PersonalNote_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.mystatusarea.personalnote_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592782
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.MyStatusArea.PersonalNote
dev_langs:
- CSharp
- JScript
- VB
- other
---

# MyStatusArea.PersonalNote property

Gets a string that shows the content of the note box for the signed-in user.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property PersonalNote As String
    Get
    Private Set
'Usage
Dim instance As MyStatusArea
Dim value As String

value = instance.PersonalNote
```

``` csharp
public string PersonalNote { get; private set; }
```

#### Property value

Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

## Remarks

This will be the OOF note if the user is OOF and no personal note is set.

## See also

#### Reference

[MyStatusArea class](mystatusarea-class-microsoft-lync-controls_1.md)

[MyStatusArea members](mystatusarea-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

