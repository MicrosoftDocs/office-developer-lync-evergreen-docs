---
title: FrequentContacts.ContactPositionChanged event (Microsoft.Lync.Model.Group)
TOCTitle: ContactPositionChanged event
ms:assetid: E:Microsoft.Lync.Model.Group.FrequentContacts.ContactPositionChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.group.frequentcontacts.contactpositionchanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48590630
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Group.FrequentContacts.ContactPositionChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# FrequentContacts.ContactPositionChanged event

Occurs when one or more contacts in a group are moved to different positions.

**Namespace:**  [Microsoft.Lync.Model.Group](microsoft-lync-model-group-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ContactPositionChanged As EventHandler(Of ContactPositionChangedEventArgs)
'Usage
Dim instance As FrequentContacts
Dim handler As EventHandler(Of ContactPositionChangedEventArgs)

AddHandler instance.ContactPositionChanged, handler
```

``` csharp
public event EventHandler<ContactPositionChangedEventArgs> ContactPositionChanged
```

## See also

#### Reference

[FrequentContacts class](frequentcontacts-class-microsoft-lync-model-group_2.md)

[FrequentContacts members](frequentcontacts-members-microsoft-lync-model-group_2.md)

[Microsoft.Lync.Model.Group namespace](microsoft-lync-model-group-namespace_2.md)

