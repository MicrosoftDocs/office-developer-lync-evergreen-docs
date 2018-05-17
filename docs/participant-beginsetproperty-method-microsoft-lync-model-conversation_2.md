---
title: Participant.BeginSetProperty method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginSetProperty method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Participant.BeginSetProperty(Microsoft.Lync.Model.Conversation.ParticipantProperty,System.Object,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.beginsetproperty(v=office.15)
ms:contentKeyID: 48590507
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.BeginSetProperty
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.BeginSetProperty method

Sets a property associated with this participant.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSetProperty ( _
    propertyType As ParticipantProperty, _
    propertyValue As Object, _
    participantCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Participant
Dim propertyType As ParticipantProperty
Dim propertyValue As Object
Dim participantCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSetProperty(propertyType, _
    propertyValue, participantCallback, _
    state)
```

``` csharp
public IAsyncResult BeginSetProperty(
    ParticipantProperty propertyType,
    Object propertyValue,
    AsyncCallback participantCallback,
    Object state
)
```

#### Parameters

  - propertyType  
    Type: [Microsoft.Lync.Model.Conversation.ParticipantProperty](participantproperty-enumeration-microsoft-lync-model-conversation_2.md)  

<!-- end list -->

  - propertyValue  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

<!-- end list -->

  - participantCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Participant class](participant-class-microsoft-lync-model-conversation_2.md)

[Participant members](participant-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

