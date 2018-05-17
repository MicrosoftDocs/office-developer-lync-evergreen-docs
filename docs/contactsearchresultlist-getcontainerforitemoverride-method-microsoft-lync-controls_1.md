---
title: ContactSearchResultList.GetContainerForItemOverride method  (Microsoft.Lync.Controls)
TOCTitle: 'GetContainerForItemOverride method '
ms:assetid: M:Microsoft.Lync.Controls.ContactSearchResultList.GetContainerForItemOverride_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactsearchresultlist.getcontainerforitemoverride_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596314
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactSearchResultList.GetContainerForItemOverride
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSearchResultList.GetContainerForItemOverride method

Creates or identifies the element used to display a specified item.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overrides Function GetContainerForItemOverride As DependencyObject
'Usage
Dim returnValue As DependencyObject

returnValue = Me.GetContainerForItemOverride()
```

``` csharp
protected override DependencyObject GetContainerForItemOverride()
```

#### Return value

Type: [System.Windows.DependencyObject](http://msdn2.microsoft.com/en-us/library/ms589309)  
A **ContactSearchResultListItem** corresponding to a specified item.  

## See also

#### Reference

[ContactSearchResultList class](contactsearchresultlist-class-microsoft-lync-controls_1.md)

[ContactSearchResultList members](contactsearchresultlist-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

