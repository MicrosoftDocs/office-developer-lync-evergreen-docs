---
title: ApplicationSharingModality.ParticipationStateChanged event (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ParticipationStateChanged event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.ParticipationStateChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality.participationstatechanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600983
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.ParticipationStateChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationSharingModality.ParticipationStateChanged event

Raised when the participation state has changed.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ParticipationStateChanged As EventHandler(Of ParticipationStateChangedEventArgs)
'Usage
Dim instance As ApplicationSharingModality
Dim handler As EventHandler(Of ParticipationStateChangedEventArgs)

AddHandler instance.ParticipationStateChanged, handler
```

``` csharp
public event EventHandler<ParticipationStateChangedEventArgs> ParticipationStateChanged
```

## Remarks

The participation state change event is raised multiple times when a participant attempts to take a control action on a shared resource. For example, if a user requests control of a shared resource and the control request is granted, the event is rased when the ParticipationState goes from Viewing to RequestingControl. When the request is granted, the event is raised again when the ParticipationState changes to Controlling.

## See also

#### Reference

[ApplicationSharingModality class](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

