---
title: ContactManager.SearchProviderStateChanged event (Microsoft.Lync.Model)
TOCTitle: SearchProviderStateChanged event
ms:assetid: E:Microsoft.Lync.Model.ContactManager.SearchProviderStateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactmanager.searchproviderstatechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592957
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactManager.SearchProviderStateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactManager.SearchProviderStateChanged event

Occurs when the status of a search provider changes.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event SearchProviderStateChanged As EventHandler(Of SearchProviderStateChangedEventArgs)
'Usage
Dim instance As ContactManager
Dim handler As EventHandler(Of SearchProviderStateChangedEventArgs)

AddHandler instance.SearchProviderStateChanged, handler
```

``` csharp
public event EventHandler<SearchProviderStateChangedEventArgs> SearchProviderStateChanged
```

## See also

#### Reference

[ContactManager class](contactmanager-class-microsoft-lync-model_2.md)

[ContactManager members](contactmanager-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

