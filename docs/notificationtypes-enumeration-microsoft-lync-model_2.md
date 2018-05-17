---
title: NotificationTypes enumeration (Microsoft.Lync.Model)
TOCTitle: NotificationTypes enumeration
ms:assetid: T:Microsoft.Lync.Model.NotificationTypes_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.notificationtypes_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48600356
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.NotificationTypes.All
- Microsoft.Lync.Model.NotificationTypes
- Microsoft.Lync.Model.NotificationTypes.FileTransfer
- Microsoft.Lync.Model.NotificationTypes.Audio
- Microsoft.Lync.Model.NotificationTypes.Sharing
- Microsoft.Lync.Model.NotificationTypes.InstantMessage
- Microsoft.Lync.Model.NotificationTypes.Unknown
- Microsoft.Lync.Model.NotificationTypes.Invalid
- Microsoft.Lync.Model.NotificationTypes.Video
dev_langs:
- CSharp
- JScript
- VB
- other
---

# NotificationTypes enumeration

Enumerates the notification types that are related to level of alerts.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration NotificationTypes
'Usage
Dim instance As NotificationTypes
```

``` csharp
[FlagsAttribute]
public enum NotificationTypes
```

## Members

<table>
<thead>
<tr class="header">
<th></th>
<th>Member name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td>Unknown</td>
<td>Unknown or other notification types</td>
</tr>
<tr class="even">
<td></td>
<td>Audio</td>
<td>Type of notification for incoming voice conversation</td>
</tr>
<tr class="odd">
<td></td>
<td>Video</td>
<td>Type of notification for incoming video conversation</td>
</tr>
<tr class="even">
<td></td>
<td>InstantMessage</td>
<td>Type of notification for incoming instant messaging</td>
</tr>
<tr class="odd">
<td></td>
<td>Sharing</td>
<td>Type of notification for incoming app sharing request</td>
</tr>
<tr class="even">
<td></td>
<td>FileTransfer</td>
<td>Type of notification for incoming file transfer request</td>
</tr>
<tr class="odd">
<td></td>
<td>All</td>
<td>All notification types</td>
</tr>
<tr class="even">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

