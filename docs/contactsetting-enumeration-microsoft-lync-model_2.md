---
title: ContactSetting enumeration (Microsoft.Lync.Model)
TOCTitle: ContactSetting enumeration
ms:assetid: T:Microsoft.Lync.Model.ContactSetting_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactsetting_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48591209
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactSetting
- Microsoft.Lync.Model.ContactSetting.AccessLevel
- Microsoft.Lync.Model.ContactSetting.DefaultContactEndpoint
- Microsoft.Lync.Model.ContactSetting.ExchangeServiceEntryId
- Microsoft.Lync.Model.ContactSetting.Invalid
- Microsoft.Lync.Model.ContactSetting.Source
- Microsoft.Lync.Model.ContactSetting.Tagged
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSetting enumeration

Represents the settings that can be applied locally to a contact.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration ContactSetting
'Usage
Dim instance As ContactSetting
```

``` csharp
public enum ContactSetting
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
<td>Tagged</td>
<td>Returns true if a notification is shown when the presence of a tagged contact is changed.</td>
</tr>
<tr class="even">
<td></td>
<td>AccessLevel</td>
<td>Returns the privacy relationship of a contact expressed as an AccessLevel enumerator.</td>
</tr>
<tr class="odd">
<td></td>
<td>ExchangeServiceEntryId</td>
<td>Read-only, Entry ID of an Exchange contact if the contact is an Exchange contact. String.</td>
</tr>
<tr class="even">
<td></td>
<td>Source</td>
<td>Read-only, Shows the contact source. ContactSourceTypes enum.</td>
</tr>
<tr class="odd">
<td></td>
<td>DefaultContactEndpoint</td>
<td>The default collaboration endpoint (SIP or TEL URI) for this contact.</td>
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

