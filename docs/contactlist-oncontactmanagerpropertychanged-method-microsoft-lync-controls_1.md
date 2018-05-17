---
title: ContactList.OnContactManagerPropertyChanged method  (Microsoft.Lync.Controls)
TOCTitle: 'OnContactManagerPropertyChanged method '
ms:assetid: M:Microsoft.Lync.Controls.ContactList.OnContactManagerPropertyChanged(Microsoft.Lync.Controls.Internal.Model.IContactsAndGroupsManagerModel,Microsoft.Lync.Controls.Internal.Model.IContactsAndGroupsManagerModel)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactlist.oncontactmanagerpropertychanged(v=office.15)
ms:contentKeyID: 48592218
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactList.OnContactManagerPropertyChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactList.OnContactManagerPropertyChanged method

Reserved for internal use.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Protected Overrides NotOverridable Sub OnContactManagerPropertyChanged ( _
    oldContactManager As IContactsAndGroupsManagerModel, _
    newContactManager As IContactsAndGroupsManagerModel _
)
'Usage
Dim oldContactManager As IContactsAndGroupsManagerModel
Dim newContactManager As IContactsAndGroupsManagerModel

Me.OnContactManagerPropertyChanged(oldContactManager, _
    newContactManager)
```

``` csharp
protected override sealed void OnContactManagerPropertyChanged(
    IContactsAndGroupsManagerModel oldContactManager,
    IContactsAndGroupsManagerModel newContactManager
)
```

#### Parameters

  - oldContactManager  
    Type: **IContactsAndGroupsManagerModel**  

<!-- end list -->

  - newContactManager  
    Type: **IContactsAndGroupsManagerModel**  

## See also

#### Reference

[ContactList class](contactlist-class-microsoft-lync-controls_1.md)

[ContactList members](contactlist-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

