---
title: Self.GetAlertLevelForNotification method  (Microsoft.Lync.Model)
TOCTitle: 'GetAlertLevelForNotification method '
ms:assetid: M:Microsoft.Lync.Model.Self.GetAlertLevelForNotification(System.String,Microsoft.Lync.Model.NotificationTypes,Microsoft.Lync.Model.NotificationUrgencyType)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.getalertlevelfornotification(v=office.15)
ms:contentKeyID: 48592383
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.GetAlertLevelForNotification
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.GetAlertLevelForNotification method

Get level of alert for notification purpose

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetAlertLevelForNotification ( _
    senderIdentity As String, _
    notificationTypes As NotificationTypes, _
    notificationUrgency As NotificationUrgencyType _
) As AlertLevel
'Usage
Dim instance As Self
Dim senderIdentity As String
Dim notificationTypes As NotificationTypes
Dim notificationUrgency As NotificationUrgencyType
Dim returnValue As AlertLevel

returnValue = instance.GetAlertLevelForNotification(senderIdentity, _
    notificationTypes, notificationUrgency)
```

``` csharp
public AlertLevel GetAlertLevelForNotification(
    string senderIdentity,
    NotificationTypes notificationTypes,
    NotificationUrgencyType notificationUrgency
)
```

#### Parameters

  - senderIdentity  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - notificationTypes  
    Type: [Microsoft.Lync.Model.NotificationTypes](notificationtypes-enumeration-microsoft-lync-model_2.md)  

<!-- end list -->

  - notificationUrgency  
    Type: [Microsoft.Lync.Model.NotificationUrgencyType](notificationurgencytype-enumeration-microsoft-lync-model_2.md)  

#### Return value

Type: [Microsoft.Lync.Model.AlertLevel](alertlevel-class-microsoft-lync-model_2.md)  

## See also

#### Reference

[Self class](self-class-microsoft-lync-model_2.md)

[Self members](self-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

