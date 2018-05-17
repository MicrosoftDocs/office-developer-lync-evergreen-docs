---
title: ApplicationSharingModality.ControlRequestReceived event (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: ControlRequestReceived event
ms:assetid: E:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.ControlRequestReceived_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingmodality.controlrequestreceived_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598621
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingModality.ControlRequestReceived
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationSharingModality.ControlRequestReceived event

Registered on the Conversation ApplicationSharingModality and raised when someone requests control of a resource.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event ControlRequestReceived As EventHandler(Of ControlRequestReceivedEventArgs)
'Usage
Dim instance As ApplicationSharingModality
Dim handler As EventHandler(Of ControlRequestReceivedEventArgs)

AddHandler instance.ControlRequestReceived, handler
```

``` csharp
public event EventHandler<ControlRequestReceivedEventArgs> ControlRequestReceived
```

## Remarks

To accept a control request, call BeginAcceptControlRequest or BeginGrantControl on the ApplicationSharingResource from the requesting participant modalities collection. Do not call these methods on the ApplicationSharingResource from the Conversation.Modalities collection.

## See also

#### Reference

[ApplicationSharingModality class](applicationsharingmodality-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingModality members](applicationsharingmodality-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

