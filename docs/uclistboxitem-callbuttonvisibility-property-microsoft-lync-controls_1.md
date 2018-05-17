---
title: UCListBoxItem.CallButtonVisibility property  (Microsoft.Lync.Controls)
TOCTitle: 'CallButtonVisibility property '
ms:assetid: P:Microsoft.Lync.Controls.UCListBoxItem.CallButtonVisibility_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.uclistboxitem.callbuttonvisibility_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591136
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.UCListBoxItem.CallButtonVisibility
dev_langs:
- CSharp
- JScript
- VB
- other
---

# UCListBoxItem.CallButtonVisibility property

Gets or sets an enumerated value which indicates whether or not the call button on this contact item's template is visible. This property is updated based on **\[MouseEnter\]** and **\[MouseLeave\]** events.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property CallButtonVisibility As Visibility
    Get
    Set
'Usage
Dim instance As UCListBoxItem
Dim value As Visibility

value = instance.CallButtonVisibility

instance.CallButtonVisibility = value
```

``` csharp
public Visibility CallButtonVisibility { get; set; }
```

#### Property value

Type: [System.Windows.Visibility](http://msdn2.microsoft.com/en-us/library/ms590101)  

## See also

#### Reference

[UCListBoxItem class](uclistboxitem-class-microsoft-lync-controls_1.md)

[UCListBoxItem members](uclistboxitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

