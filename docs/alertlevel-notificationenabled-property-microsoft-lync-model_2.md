---
title: AlertLevel.NotificationEnabled property  (Microsoft.Lync.Model)
TOCTitle: 'NotificationEnabled property '
ms:assetid: P:Microsoft.Lync.Model.AlertLevel.NotificationEnabled_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.alertlevel.notificationenabled_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591129
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AlertLevel.NotificationEnabled
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AlertLevel.NotificationEnabled property

Returns true when notification is allowed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property NotificationEnabled As Boolean
    Get
'Usage
Dim instance As AlertLevel
Dim value As Boolean

value = instance.NotificationEnabled
```

``` csharp
public bool NotificationEnabled { get; }
```

#### Property value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

## Remarks

The AlertLevel.NotificationEnabled property tells you whether notification for new group chat messages, conversation invitations, or meeting reminders should be displayed. You do not display such notifications if a user is presenting in a meeting and is sharing a display or presenting a PowerPoint slide deck. In those cases, NotificationEnabled returns false and you must honor the policy.

## See also

#### Reference

[AlertLevel class](alertlevel-class-microsoft-lync-model_2.md)

[AlertLevel members](alertlevel-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

