---
title: ConversationWindow.FlashExtensibilityWindow method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'FlashExtensibilityWindow method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.ConversationWindow.FlashExtensibilityWindow(System.String,System.Boolean)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.conversationwindow.flashextensibilitywindow(v=office.15)
ms:contentKeyID: 48599426
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.ConversationWindow.FlashExtensibilityWindow
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ConversationWindow.FlashExtensibilityWindow method

Start or stop flashing the extensibility window of the given application GUID.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub FlashExtensibilityWindow ( _
    applicationId As String, _
    flash As Boolean _
)
'Usage
Dim instance As ConversationWindow
Dim applicationId As String
Dim flash As Boolean

instance.FlashExtensibilityWindow(applicationId, _
    flash)
```

``` csharp
public void FlashExtensibilityWindow(
    string applicationId,
    bool flash
)
```

#### Parameters

  - applicationId  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - flash  
    Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## See also

#### Reference

[ConversationWindow class](conversationwindow-class-microsoft-lync-model-extensibility_2.md)

[ConversationWindow members](conversationwindow-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

