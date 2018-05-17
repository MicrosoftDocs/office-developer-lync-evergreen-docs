---
title: ContactListItem.GroupContentTemplate property  (Microsoft.Lync.Controls)
TOCTitle: 'GroupContentTemplate property '
ms:assetid: P:Microsoft.Lync.Controls.ContactListItem.GroupContentTemplate_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactlistitem.groupcontenttemplate_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591202
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactListItem.GroupContentTemplate
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactListItem.GroupContentTemplate property

Gets or sets the [DataTemplate](http://msdn2.microsoft.com/en-us/library/ms589297) used for Group-type contacts in [OneLine](contactlayoutoption-enumeration-microsoft-lync-controls_1.md) mode. (See [ContactLayoutView](contactlistitem-contactlayoutview-property-microsoft-lync-controls_1.md)).

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property GroupContentTemplate As DataTemplate
    Get
    Set
'Usage
Dim instance As ContactListItem
Dim value As DataTemplate

value = instance.GroupContentTemplate

instance.GroupContentTemplate = value
```

``` csharp
public DataTemplate GroupContentTemplate { get; set; }
```

#### Property value

Type: [System.Windows.DataTemplate](http://msdn2.microsoft.com/en-us/library/ms589297)  

## See also

#### Reference

[ContactListItem class](contactlistitem-class-microsoft-lync-controls_1.md)

[ContactListItem members](contactlistitem-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

