---
title: ApplicationSharingModality.LocalSharedResourcesChanged event (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: LocalSharedResourcesChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.LocalSharedResourcesChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality.localsharedresourceschanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597777
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.LocalSharedResourcesChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationSharingModality.LocalSharedResourcesChanged event

Raised when the list of locally shared resources changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event LocalSharedResourcesChanged As EventHandler(Of LocalSharedResourcesChangedEventArgs)
'Usage
Dim instance As ApplicationSharingModality
Dim handler As EventHandler(Of LocalSharedResourcesChangedEventArgs)

AddHandler instance.LocalSharedResourcesChanged, handler
```

``` csharp
public event EventHandler<LocalSharedResourcesChangedEventArgs> LocalSharedResourcesChanged
```

## See also

#### Reference

[ApplicationSharingModality class](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

