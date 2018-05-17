---
title: ContactItem.PersonContentTemplate property  (Microsoft.Lync.Controls)
TOCTitle: 'PersonContentTemplate property '
ms:assetid: P:Microsoft.Lync.Controls.ContactItem.PersonContentTemplate_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactitem.personcontenttemplate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600906
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactItem.PersonContentTemplate
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactItem.PersonContentTemplate property

Gets or sets the [DataTemplate](http://msdn2.microsoft.com/en-us/library/ms589297) used for Person-type contacts in [OneLine](contactlayoutoption-enumeration-microsoft-lync-controls_1.md) mode. (See [ContactLayoutView](contactitem-contactlayoutview-property-microsoft-lync-controls_1.md)).

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property PersonContentTemplate As DataTemplate
    Get
    Set
'Usage
Dim instance As ContactItem
Dim value As DataTemplate

value = instance.PersonContentTemplate

instance.PersonContentTemplate = value
```

``` csharp
public DataTemplate PersonContentTemplate { get; set; }
```

#### Property value

Type: [System.Windows.DataTemplate](http://msdn2.microsoft.com/en-us/library/ms589297)  

## See also

#### Reference

[ContactItem class](contactitem-class-microsoft-lync-controls_1.md)

[ContactItem members](contactitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

