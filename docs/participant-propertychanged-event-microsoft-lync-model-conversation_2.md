---
title: Participant.PropertyChanged event (Microsoft.Lync.Model.Conversation)
TOCTitle: PropertyChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Participant.PropertyChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.propertychanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48601813
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.PropertyChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.PropertyChanged event

Raised when a property value changes

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event PropertyChanged As EventHandler(Of ParticipantPropertyChangedEventArgs)
'Usage
Dim instance As Participant
Dim handler As EventHandler(Of ParticipantPropertyChangedEventArgs)

AddHandler instance.PropertyChanged, handler
```

``` csharp
public event EventHandler<ParticipantPropertyChangedEventArgs> PropertyChanged
```

## See also

#### Reference

[Participant class](participant-class-microsoft-lync-model-conversation_2.md)

[Participant members](participant-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

