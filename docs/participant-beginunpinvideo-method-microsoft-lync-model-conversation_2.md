---
title: Participant.BeginUnPinVideo method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginUnPinVideo method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Participant.BeginUnPinVideo(System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.participant.beginunpinvideo(v=office.15)
ms:contentKeyID: 48591797
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Participant.BeginUnPinVideo
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Participant.BeginUnPinVideo method

Asynchronously unpins the participant video

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginUnPinVideo ( _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Participant
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginUnPinVideo(callback, _
    state)
```

``` csharp
public IAsyncResult BeginUnPinVideo(
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - callback  
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

