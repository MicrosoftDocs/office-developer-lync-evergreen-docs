---
title: Self.AlertLevelChanged event (Microsoft.Lync.Model)
TOCTitle: AlertLevelChanged event
ms:assetid: E:Microsoft.Lync.Model.Self.AlertLevelChanged_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.alertlevelchanged_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595298
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.AlertLevelChanged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.AlertLevelChanged event

Raised when the local user has changed their do-not-disturb level joined a meeting as a presenter and shared a resource such as a primary monitor.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Event AlertLevelChanged As EventHandler(Of AlertLevelChangedEventArgs)
'Usage
Dim instance As Self
Dim handler As EventHandler(Of AlertLevelChangedEventArgs)

AddHandler instance.AlertLevelChanged, handler
```

``` csharp
public event EventHandler<AlertLevelChangedEventArgs> AlertLevelChanged
```

## Remarks

Use this event to determine if your application should show a new conversation invitation to the signed in user when a conversation invitation is received. Conversation invitations should not be displayed when the signed in user is either in do-not-disturb mode or sharing a resource such as a display in a meeting, A meeting presenter's privacy may be violated if conversation invitations are shown on a shared display in a meeting.

## See also

#### Reference

[Self class](self-class-microsoft-lync-model_2.md)

[Self members](self-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

