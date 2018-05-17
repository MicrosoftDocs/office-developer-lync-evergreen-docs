---
title: ControlRequestReceivedEventArgs.Requester property  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'Requester property '
ms:assetid: P:Microsoft.Lync.Model.Conversation.Sharing.ControlRequestReceivedEventArgs.Requester_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.controlrequestreceivedeventargs.requester_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591762
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ControlRequestReceivedEventArgs.Requester
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ControlRequestReceivedEventArgs.Requester property

Gets the participant who requested to take control.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property Requester As Participant
    Get
'Usage
Dim instance As ControlRequestReceivedEventArgs
Dim value As Participant

value = instance.Requester
```

``` csharp
public Participant Requester { get; }
```

#### Property value

Type: [Microsoft.Lync.Model.Conversation.Participant](participant-class-microsoft-lync-model-conversation_2.md)  

## Remarks

To accept the control request, call BeginAcceptControlRequest on the Participant.Modalities\[ModalityType.ApplicationSharing\] modality after casting the Modality returned from this property to ApplicationSharingModality.

## See also

#### Reference

[ControlRequestReceivedEventArgs class](controlrequestreceivedeventargs-class-microsoft-lync-model-conversation-sharing_2.md)

[ControlRequestReceivedEventArgs members](controlrequestreceivedeventargs-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

