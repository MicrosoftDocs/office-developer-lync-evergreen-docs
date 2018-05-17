---
title: AutomationModalitySettings enumeration (Microsoft.Lync.Model.Extensibility)
TOCTitle: AutomationModalitySettings enumeration
ms:assetid: T:Microsoft.Lync.Model.Extensibility.AutomationModalitySettings_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.extensibility.automationmodalitysettings_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48596700
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.SharedDesktop
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.OutlookEntryId
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.ParentWindow
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.FilePathToTransfer
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.FileHistoryLink
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.FileIsShared
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.SendFirstInstantMessageImmediately
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.HyperLink
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.PreviousConversation
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.Invalid
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.DataObjectForFileTransfer
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.FirstInstantMessage
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.ApplicationId
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.ApplicationData
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.Subject
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.SharedProcess
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.SharedWindow
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.StartConferenceByCallingMeAt
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.SharedMonitor
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.Reserved1
- Microsoft.Lync.Model.Extensibility.AutomationModalitySettings.Reserved2
dev_langs:
- CSharp
- JScript
- VB
- other
---

# AutomationModalitySettings enumeration

Enumerates the settings on an automation modality.

This enumeration has a [FlagsAttribute](http://msdn2.microsoft.com/en-us/library/dk06fkbc) attribute that allows a bitwise combination of its member values.

**Namespace:**  [Microsoft.Lync.Model.Extensibility](microsoft-lync-model-extensibility-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
<FlagsAttribute> _
Public Enumeration AutomationModalitySettings
'Usage
Dim instance As AutomationModalitySettings
```

``` csharp
[FlagsAttribute]
public enum AutomationModalitySettings
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
<td>Subject</td>
<td>Conversation subject. Property value type is String.</td>
</tr>
<tr class="even">
<td></td>
<td>PreviousConversation</td>
<td>Previous conversation Id. Property value type is String.</td>
</tr>
<tr class="odd">
<td></td>
<td>OutlookEntryId</td>
<td>Microsoft Outlook entry Id. Property value type is String.</td>
</tr>
<tr class="even">
<td></td>
<td>FilePathToTransfer</td>
<td>The file path of a file to be transferred. Property value type is String.</td>
</tr>
<tr class="odd">
<td></td>
<td>FileIsShared</td>
<td>Returns true if the file is shared. Property value type is Boolean.</td>
</tr>
<tr class="even">
<td></td>
<td>FirstInstantMessage</td>
<td>The first instant message. Text sent with conversation invitation. Property value is of type string.</td>
</tr>
<tr class="odd">
<td></td>
<td>SendFirstInstantMessageImmediately</td>
<td>Set to true if the first instant message text is to be sent immediately upon starting a conversation. Property value is of type boolean.</td>
</tr>
<tr class="even">
<td></td>
<td>FileHistoryLink</td>
<td>File history link. Property value is of type string.</td>
</tr>
<tr class="odd">
<td></td>
<td>StartConferenceByCallingMeAt</td>
<td>Telephone number to call out to conversation participant. Property value is of type string.</td>
</tr>
<tr class="even">
<td></td>
<td>SharedProcess</td>
<td>Share a process running on local computer in conversation. Property value is of type Int.</td>
</tr>
<tr class="odd">
<td></td>
<td>SharedWindow</td>
<td>Share a window open on local computer in conversation. Property value is of type Int.</td>
</tr>
<tr class="even">
<td></td>
<td>SharedDesktop</td>
<td>Share the desktop of the local computer in conversation. No property value needed.</td>
</tr>
<tr class="odd">
<td></td>
<td>SharedMonitor</td>
<td>Shares a monitor attached to local computer in conversation. Property value the monitor Id an is type Int.</td>
</tr>
<tr class="even">
<td></td>
<td>DataObjectForFileTransfer</td>
<td>A data object is to be transferred. Property value is object.</td>
</tr>
<tr class="odd">
<td></td>
<td>ApplicationId</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>ApplicationData</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>HyperLink</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>ParentWindow</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td>Reserved1</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td>Reserved2</td>
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

