---
title: Modality.ActionAvailabilityChanged event (Microsoft.Lync.Model.Conversation)
TOCTitle: ActionAvailabilityChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Modality.ActionAvailabilityChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.modality.actionavailabilitychanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600602
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Modality.ActionAvailabilityChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Modality.ActionAvailabilityChanged event

Raised when an action availability changes.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ActionAvailabilityChanged As EventHandler(Of ModalityActionAvailabilityChangedEventArgs)
'Usage
Dim instance As Modality
Dim handler As EventHandler(Of ModalityActionAvailabilityChangedEventArgs)

AddHandler instance.ActionAvailabilityChanged, handler
```

``` csharp
public event EventHandler<ModalityActionAvailabilityChangedEventArgs> ActionAvailabilityChanged
```

## Remarks

When you want to be advised that an action to be taken is on a single participant modality instead of the conversation modality, register for this event on Participant.Modalities\[ModalityType\]. For example, if the availability of a controller action changes on a conversation participant's ApplicationSharingModality, you get the event if you have registered for it on the modality at Participant.Modalities\[ModalityType.ApplicationSharing\]. Note: You must always register for this event on the conversation Modality in addition to event registration on any participant's modalty.

## See also

#### Reference

[Modality class](modality-class-microsoft-lync-model-conversation_2.md)

[Modality members](modality-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

