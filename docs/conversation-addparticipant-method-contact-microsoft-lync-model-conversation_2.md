---
title: Conversation.AddParticipant method (Contact) (Microsoft.Lync.Model.Conversation)
TOCTitle: AddParticipant method (Contact)
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.AddParticipant(Microsoft.Lync.Model.Contact)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.addparticipant(v=office.15)
ms:contentKeyID: 48598030
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Conversation.AddParticipant method (Contact)

Adds a contact to a conversation and returns the contact as a participant.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function AddParticipant ( _
    contact As Contact _
) As Participant
'Usage
Dim instance As Conversation
Dim contact As Contact
Dim returnValue As Participant

returnValue = instance.AddParticipant(contact)
```

``` csharp
public Participant AddParticipant(
    Contact contact
)
```

#### Parameters

  - contact  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

#### Return value

Type: [Microsoft.Lync.Model.Conversation.Participant](participant-class-microsoft-lync-model-conversation_2.md)  

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[AddParticipant overload](conversation-addparticipant-method-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

