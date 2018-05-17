---
title: Conversation.BeginSendInitialContext method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'BeginSendInitialContext method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.BeginSendInitialContext(System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{Microsoft.Lync.Model.Conversation.ContextType,System.Object}},System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.beginsendinitialcontext(v=office.15)
ms:contentKeyID: 48595734
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.BeginSendInitialContext
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.BeginSendInitialContext method

Sends an application hyperlink and application Id as initial conversation context.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginSendInitialContext ( _
    contextData As IEnumerable(Of KeyValuePair(Of ContextType, Object)), _
    callback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Conversation
Dim contextData As IEnumerable(Of KeyValuePair(Of ContextType, Object))
Dim callback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginSendInitialContext(contextData, _
    callback, state)
```

``` csharp
public IAsyncResult BeginSendInitialContext(
    IEnumerable<KeyValuePair<ContextType, Object>> contextData,
    AsyncCallback callback,
    Object state
)
```

#### Parameters

  - contextData  
    Type: [System.Collections.Generic.IEnumerable](http://msdn2.microsoft.com/en-us/library/9eekhta0)\<[KeyValuePair](http://msdn2.microsoft.com/en-us/library/5tbh8a42)\<[ContextType](contexttype-enumeration-microsoft-lync-model-conversation_2.md), [Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)\>\>  

<!-- end list -->

  - callback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

