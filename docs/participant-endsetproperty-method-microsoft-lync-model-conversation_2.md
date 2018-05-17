---
title: Participant.EndSetProperty method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'EndSetProperty method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Participant.EndSetProperty(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.endsetproperty(v=office.15)
ms:contentKeyID: 48597569
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.EndSetProperty
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.EndSetProperty method

Sets a property associated with this participant.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndSetProperty ( _
    asyncResult As IAsyncResult _
) As ParticipantProperty
'Usage
Dim instance As Participant
Dim asyncResult As IAsyncResult
Dim returnValue As ParticipantProperty

returnValue = instance.EndSetProperty(asyncResult)
```

``` csharp
public ParticipantProperty EndSetProperty(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Conversation.ParticipantProperty](participantproperty-enumeration-microsoft-lync-model-conversation_2.md)  

## See also

#### Reference

[Participant class](participant-class-microsoft-lync-model-conversation_2.md)

[Participant members](participant-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

