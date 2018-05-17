---
title: Participant.CanDeny method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'CanDeny method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Participant.CanDeny_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.candeny_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592211
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.CanDeny
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.CanDeny method

Returns true if a participant waiting in the lobby can be denied access to a conference.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanDeny As Boolean
'Usage
Dim instance As Participant
Dim returnValue As Boolean

returnValue = instance.CanDeny()
```

``` csharp
public bool CanDeny()
```

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## Remarks

Do not use this method. Use Participant.CanInvoke(ParticipantAction.Deny) instead.

## See also

#### Reference

[Participant class](participant-class-microsoft-lync-model-conversation_2.md)

[Participant members](participant-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

