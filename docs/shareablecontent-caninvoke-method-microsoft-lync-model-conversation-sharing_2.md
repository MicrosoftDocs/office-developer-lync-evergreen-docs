---
title: ShareableContent.CanInvoke method  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'CanInvoke method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.CanInvoke(Microsoft.Lync.Model.Conversation.Sharing.ShareableContentAction,System.Int32@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.shareablecontent.caninvoke(v=office.15)
ms:contentKeyID: 48595373
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ShareableContent.CanInvoke
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ShareableContent.CanInvoke method

Returns true if a specific action is available.

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function CanInvoke ( _
    action As ShareableContentAction, _
    <OutAttribute> ByRef hrReason As Integer _
) As Boolean
'Usage
Dim instance As ShareableContent
Dim action As ShareableContentAction
Dim hrReason As Integer
Dim returnValue As Boolean

returnValue = instance.CanInvoke(action, _
    hrReason)
```

``` csharp
public bool CanInvoke(
    ShareableContentAction action,
    out int hrReason
)
```

#### Parameters

  - action  
    Type: [Microsoft.Lync.Model.Conversation.Sharing.ShareableContentAction](shareablecontentaction-enumeration-microsoft-lync-model-conversation-sharing_2.md)  

<!-- end list -->

  - hrReason  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
System.Boolean  

## See also

#### Reference

[ShareableContent class](shareablecontent-class-microsoft-lync-model-conversation-sharing_2.md)

[ShareableContent members](shareablecontent-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

