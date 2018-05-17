---
title: Participant.CanSetProperty method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'CanSetProperty method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Participant.CanSetProperty(Microsoft.Lync.Model.Conversation.ParticipantProperty)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.cansetproperty(v=office.15)
ms:contentKeyID: 48596307
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.CanSetProperty
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.CanSetProperty method

Test whether the property can be set to the participant.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanSetProperty ( _
    participantProperty As ParticipantProperty _
) As Boolean
'Usage
Dim instance As Participant
Dim participantProperty As ParticipantProperty
Dim returnValue As Boolean

returnValue = instance.CanSetProperty(participantProperty)
```

``` csharp
public bool CanSetProperty(
    ParticipantProperty participantProperty
)
```

#### Parameters

  - participantProperty  
    Type: [Microsoft.Lync.Model.Conversation.ParticipantProperty](participantproperty-enumeration-microsoft-lync-model-conversation_2.md)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## Remarks

Do not use this method. Use CanInvoke(ParticipantAction.SetProperty) instead.

## See also

#### Reference

[Participant class](participant-class-microsoft-lync-model-conversation_2.md)

[Participant members](participant-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

