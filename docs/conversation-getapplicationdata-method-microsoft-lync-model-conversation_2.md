---
title: Conversation.GetApplicationData method  (Microsoft.Lync.Model.Conversation)
TOCTitle: 'GetApplicationData method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Conversation.GetApplicationData(System.String)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.conversation.getapplicationdata(v=office.15)
ms:contentKeyID: 48601043
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Conversation.GetApplicationData
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Conversation.GetApplicationData method

Gets the contextual conversation application data using the given GUID. Only the registered application with the same GUID may call this.

**Namespace:**  [Microsoft.Lync.Model.Conversation](microsoft-lync-model-conversation-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetApplicationData ( _
    appGuid As String _
) As String
'Usage
Dim instance As Conversation
Dim appGuid As String
Dim returnValue As String

returnValue = instance.GetApplicationData(appGuid)
```

``` csharp
public string GetApplicationData(
    string appGuid
)
```

#### Parameters

  - appGuid  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

#### Return value

Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  
System.String  

## See also

#### Reference

[Conversation class](conversation-class-microsoft-lync-model-conversation_2.md)

[Conversation members](conversation-members-microsoft-lync-model-conversation_2.md)

[Microsoft.Lync.Model.Conversation namespace](microsoft-lync-model-conversation-namespace_2.md)

