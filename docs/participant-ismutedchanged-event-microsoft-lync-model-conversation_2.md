---
title: Participant.IsMutedChanged event (Microsoft.Lync.Model.Conversation)
TOCTitle: IsMutedChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Participant.IsMutedChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.ismutedchanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48597762
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.IsMutedChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.IsMutedChanged event

Raised when the mute state changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event IsMutedChanged As EventHandler(Of MutedChangedEventArgs)
'Usage
Dim instance As Participant
Dim handler As EventHandler(Of MutedChangedEventArgs)

AddHandler instance.IsMutedChanged, handler
```

``` csharp
public event EventHandler<MutedChangedEventArgs> IsMutedChanged
```

## See also

#### Reference

[Participant class](participant-class-microsoft-lync-model-conversation_2.md)

[Participant members](participant-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

