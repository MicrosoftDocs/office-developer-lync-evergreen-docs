---
title: CustomContactList.GetContainerForItemOverride method  (Microsoft.Lync.Controls)
TOCTitle: 'GetContainerForItemOverride method '
ms:assetid: M:Microsoft.Lync.Controls.CustomContactList.GetContainerForItemOverride_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.customcontactlist.getcontainerforitemoverride_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595262
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.CustomContactList.GetContainerForItemOverride
dev_langs:
- CSharp
- JScript
- VB
- other
---

# CustomContactList.GetContainerForItemOverride method

Overrides the GetContainerForItemOverride method to create a **\[CustomContactListItem\]** container and apply a DataTemplate, if there is an explicit one.

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

## See also

#### Reference

[CustomContactList class](customcontactlist-class-microsoft-lync-controls_1.md)

[CustomContactList members](customcontactlist-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

