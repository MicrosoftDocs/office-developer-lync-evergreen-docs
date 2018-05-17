---
title: Participant.CanBeMuted method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'CanBeMuted method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Participant.CanBeMuted_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.canbemuted_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48593518
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.CanBeMuted
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.CanBeMuted method

Returns true if a participant can be muted.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanBeMuted As Boolean
'Usage
Dim instance As Participant
Dim returnValue As Boolean

returnValue = instance.CanBeMuted()
```

``` csharp
public bool CanBeMuted()
```

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## Remarks

Do not use this method. Use Participant.CanInvoke(ParticipantAction.SetMute) instead.

## See also

#### Reference

[Participant class](participant-class-microsoft-lync-model-conversation_2.md)

[Participant members](participant-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

