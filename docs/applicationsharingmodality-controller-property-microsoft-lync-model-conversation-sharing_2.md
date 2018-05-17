---
title: ApplicationSharingModality.Controller property  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'Controller property '
ms:assetid: P:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.Controller_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality.controller_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48588605
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.Controller
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationSharingModality.Controller property

Gets the conversation participant that is in control of the shared resource.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Controller As Participant
    Get
'Usage
Dim instance As ApplicationSharingModality
Dim value As Participant

value = instance.Controller
```

``` csharp
public Participant Controller { get; }
```

#### Property value

Type: [Microsoft.Lync.Model.Conversation.Participant](participant-class-microsoft-lync-model-conversation_2.md)  

## Remarks

The Controller property returns null when the resource owner is in control of the resource.

## See also

#### Reference

[ApplicationSharingModality class](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

