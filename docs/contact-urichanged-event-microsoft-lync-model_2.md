---
title: Contact.UriChanged event (Microsoft.Lync.Model)
TOCTitle: UriChanged event
ms:assetid: E:Microsoft.Lync.Model.Contact.UriChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contact.urichanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600660
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Contact.UriChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Contact.UriChanged event

Occurs when the contact URI is changed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event UriChanged As EventHandler(Of UriChangedEventArgs)
'Usage
Dim instance As Contact
Dim handler As EventHandler(Of UriChangedEventArgs)

AddHandler instance.UriChanged, handler
```

``` csharp
public event EventHandler<UriChangedEventArgs> UriChanged
```

## See also

#### Reference

[Contact class](contact-class-microsoft-lync-model_2.md)

[Contact members](contact-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

