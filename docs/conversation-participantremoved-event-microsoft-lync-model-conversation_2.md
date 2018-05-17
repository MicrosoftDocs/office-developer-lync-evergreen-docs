---
title: Conversation.ParticipantRemoved event (Microsoft.Lync.Model.Conversation)
TOCTitle: ParticipantRemoved event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Conversation.ParticipantRemoved_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.participantremoved_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592384
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.ParticipantRemoved
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.ParticipantRemoved event

Raised when a participant remove operation completes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ParticipantRemoved As EventHandler(Of ParticipantCollectionChangedEventArgs)
'Usage
Dim instance As Conversation
Dim handler As EventHandler(Of ParticipantCollectionChangedEventArgs)

AddHandler instance.ParticipantRemoved, handler
```

``` csharp
public event EventHandler<ParticipantCollectionChangedEventArgs> ParticipantRemoved
```

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

