---
title: Automation.GetConversationWindow method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'GetConversationWindow method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.Automation.GetConversationWindow(Microsoft.Lync.Model.Conversation.Conversation)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.automation.getconversationwindow(v=office.15)
ms:contentKeyID: 48591203
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.Automation.GetConversationWindow
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Automation.GetConversationWindow method

Find or create a ConversationWindow for a given conversation.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetConversationWindow ( _
    conversation As Conversation _
) As ConversationWindow
'Usage
Dim instance As Automation
Dim conversation As Conversation
Dim returnValue As ConversationWindow

returnValue = instance.GetConversationWindow(conversation)
```

``` csharp
public ConversationWindow GetConversationWindow(
    Conversation conversation
)
```

#### Parameters

  - conversation  
    Type: [Microsoft.Lync.Model.Conversation.Conversation](conversation-class-microsoft-lync-model-conversation_2.md)  

#### Return value

Type: [Microsoft.Lync.Model.Extensibility.ConversationWindow](conversationwindow-class-microsoft-lync-model-extensibility_2.md)  
IConversationWindow  

## See also

#### Reference

[Automation class](automation-class-microsoft-lync-model-extensibility_2.md)

[Automation members](automation-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

