---
title: Automation.EndMeetNow method  (Microsoft.Lync.Model.Extensibility)
TOCTitle: 'EndMeetNow method '
ms:assetid: M:Microsoft.Lync.Model.Extensibility.Automation.EndMeetNow(System.IAsyncResult)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.automation.endmeetnow(v=office.15)
ms:contentKeyID: 48599908
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.Automation.EndMeetNow
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Automation.EndMeetNow method

Ends the MeetNow operation, unblocks program execution on the calling thread, and returns a new conversation window.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function EndMeetNow ( _
    asyncResult As IAsyncResult _
) As ConversationWindow
'Usage
Dim instance As Automation
Dim asyncResult As IAsyncResult
Dim returnValue As ConversationWindow

returnValue = instance.EndMeetNow(asyncResult)
```

``` csharp
public ConversationWindow EndMeetNow(
    IAsyncResult asyncResult
)
```

#### Parameters

  - asyncResult  
    Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

#### Return value

Type: [Microsoft.Lync.Model.Extensibility.ConversationWindow](conversationwindow-class-microsoft-lync-model-extensibility_2.md)  

## See also

#### Reference

[Automation class](automation-class-microsoft-lync-model-extensibility_2.md)

[Automation members](automation-members-microsoft-lync-model-extensibility_2.md)

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

