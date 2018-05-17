---
title: AlertLevel class (Microsoft.Lync.Model)
TOCTitle: AlertLevel class
ms:assetid: T:Microsoft.Lync.Model.AlertLevel_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.alertlevel_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600892
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.AlertLevel
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AlertLevel class

Presence-based alert policy.

## Inheritance hierarchy

[System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  
  [System.MarshalByRefObject](http://msdn2.microsoft.com/en-us/library/w4302s1f)  
    **UCWBase**  
      **UCWLite**  
        Microsoft.Lync.Model.AlertLevel  

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Class AlertLevel _
    Inherits UCWLite
'Usage
Dim instance As AlertLevel
```

``` csharp
public class AlertLevel : UCWLite
```

## Remarks

The AlertLevel.NotificationEnabled property tells you whether notification for new group chat messages, conversation invitations, or meeting reminders should be displayed. You do not display such notifications if a user is presenting in a meeting and is sharing a display or presenting a PowerPoint slide deck. In those cases, NotificationEnabled returns false and you must honor the policy.

## Thread safety

Any public static (Shared in Visual Basic) members of this type are thread safe. Any instance members are not guaranteed to be thread safe.

## See also

#### Reference

[AlertLevel members](alertlevel-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

