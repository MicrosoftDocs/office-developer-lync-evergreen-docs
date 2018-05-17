---
title: RoomMessageFilteringAction enumeration (Microsoft.Lync.Model.Room)
TOCTitle: RoomMessageFilteringAction enumeration
ms:assetid: T:Microsoft.Lync.Model.Room.RoomMessageFilteringAction_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.room.roommessagefilteringaction_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48594498
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Room.RoomMessageFilteringAction
- Microsoft.Lync.Model.Room.RoomMessageFilteringAction.Canceled
- Microsoft.Lync.Model.Room.RoomMessageFilteringAction.Invalid
- Microsoft.Lync.Model.Room.RoomMessageFilteringAction.Passed
- Microsoft.Lync.Model.Room.RoomMessageFilteringAction.Replaced
dev_langs:
- CSharp
- JScript
- VB
- other
---

# RoomMessageFilteringAction enumeration

Enumerates the action taken by message filtering logic for a room message when Room.SendFilteredMessge is called.

**Namespace:**  [Microsoft.Lync.Model.Room](microsoft-lync-model-room-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration RoomMessageFilteringAction
'Usage
Dim instance As RoomMessageFilteringAction
```

``` csharp
public enum RoomMessageFilteringAction
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
<td>Canceled</td>
<td>The message send operation is canceled.</td>
</tr>
<tr class="even">
<td></td>
<td>Replaced</td>
<td>The original message text is replaced with new text and then sent.</td>
</tr>
<tr class="odd">
<td></td>
<td>Passed</td>
<td>The original message text is sent without change.</td>
</tr>
<tr class="even">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## Remarks

Choose RoomMessageFilteringAction.Canceled when you want to prevent the user's pending message post from completing. Use RoomMessageFilteringAction.Replaced when you have reformatted or replaced text in the user's original pending message text. Use RoomMessageFilteringAction.Passed when you are sending the user's original message text unchanged.

## See also

#### Reference

[Microsoft.Lync.Model.Room namespace](microsoft-lync-model-room-namespace_2.md)

