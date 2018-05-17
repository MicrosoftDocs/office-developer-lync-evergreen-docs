---
title: AutomationModalities enumeration (Microsoft.Lync.Model.Extensibility)
TOCTitle: AutomationModalities enumeration
ms:assetid: T:Microsoft.Lync.Model.Extensibility.AutomationModalities_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.automationmodalities_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48589336
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.AutomationModalities
- Microsoft.Lync.Model.Extensibility.AutomationModalities.ApplicationSharing
- Microsoft.Lync.Model.Extensibility.AutomationModalities.Audio
- Microsoft.Lync.Model.Extensibility.AutomationModalities.FileTransfer
- Microsoft.Lync.Model.Extensibility.AutomationModalities.Video
- Microsoft.Lync.Model.Extensibility.AutomationModalities.Invalid
- Microsoft.Lync.Model.Extensibility.AutomationModalities.InstantMessage
- Microsoft.Lync.Model.Extensibility.AutomationModalities.Reserved1
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AutomationModalities enumeration

Enumerates the types of conversation modality that can be added to a conversation started using the Automation.BeginStartConversation method.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration AutomationModalities
'Usage
Dim instance As AutomationModalities
```

``` csharp
[FlagsAttribute]
public enum AutomationModalities
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
<td>InstantMessage</td>
<td>Instant messaging modality.</td>
</tr>
<tr class="even">
<td></td>
<td>Audio</td>
<td>Audio modality. Used for voice transmission</td>
</tr>
<tr class="odd">
<td></td>
<td>Video</td>
<td>Video modality.</td>
</tr>
<tr class="even">
<td></td>
<td>FileTransfer</td>
<td>File transfer modality.</td>
</tr>
<tr class="odd">
<td></td>
<td>ApplicationSharing</td>
<td>Application sharing modality.</td>
</tr>
<tr class="even">
<td></td>
<td>Reserved1</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Invalid</td>
<td></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Microsoft.Lync.Model.Extensibility namespace](microsoft-lync-model-extensibility-namespace_2.md)

