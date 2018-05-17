---
title: SearchProviderStatusType enumeration (Microsoft.Lync.Model)
TOCTitle: SearchProviderStatusType enumeration
ms:assetid: T:Microsoft.Lync.Model.SearchProviderStatusType_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.searchproviderstatustype_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48599739
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.SearchProviderStatusType.Invalid
- Microsoft.Lync.Model.SearchProviderStatusType.SyncNotStarted
- Microsoft.Lync.Model.SearchProviderStatusType.CredentialsNotEntered
- Microsoft.Lync.Model.SearchProviderStatusType.OtherFailure
- Microsoft.Lync.Model.SearchProviderStatusType
- Microsoft.Lync.Model.SearchProviderStatusType.SyncSucceededForExternalOnly
- Microsoft.Lync.Model.SearchProviderStatusType.FileNotFound
- Microsoft.Lync.Model.SearchProviderStatusType.InitializationFailed
- Microsoft.Lync.Model.SearchProviderStatusType.SyncSucceededForInternalOnly
- Microsoft.Lync.Model.SearchProviderStatusType.FileCorrupted
- Microsoft.Lync.Model.SearchProviderStatusType.LocalDatabaseFailure
- Microsoft.Lync.Model.SearchProviderStatusType.SyncSucceeded
- Microsoft.Lync.Model.SearchProviderStatusType.SyncInProgress
- Microsoft.Lync.Model.SearchProviderStatusType.NotConfigured
dev_langs:
- CSharp
- JScript
- VB
- other
---

# SearchProviderStatusType enumeration

Enumerates search provider statuses.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Enumeration SearchProviderStatusType
'Usage
Dim instance As SearchProviderStatusType
```

``` csharp
public enum SearchProviderStatusType
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
<td>SyncNotStarted</td>
<td>Search provider synchronization has not started.</td>
</tr>
<tr class="even">
<td></td>
<td>SyncInProgress</td>
<td>Search provider synchronization is in progress.</td>
</tr>
<tr class="odd">
<td></td>
<td>SyncSucceeded</td>
<td>Search provider synchronization has completed successfully.</td>
</tr>
<tr class="even">
<td></td>
<td>SyncSucceededForInternalOnly</td>
<td>Search provider service from internal is available.</td>
</tr>
<tr class="odd">
<td></td>
<td>SyncSucceededForExternalOnly</td>
<td>Search provider service from external is available.</td>
</tr>
<tr class="even">
<td></td>
<td>OtherFailure</td>
<td>Search provider synchronization failed for an unknown reason.</td>
</tr>
<tr class="odd">
<td></td>
<td>LocalDatabaseFailure</td>
<td>Search provider synchronization failed due to local database failure.</td>
</tr>
<tr class="even">
<td></td>
<td>FileNotFound</td>
<td>Search provider synchronization failed due to file not found.</td>
</tr>
<tr class="odd">
<td></td>
<td>FileCorrupted</td>
<td>Search provider synchronization failed due to corrupted file.</td>
</tr>
<tr class="even">
<td></td>
<td>CredentialsNotEntered</td>
<td>User has not provided credentials to the challenging search provider.</td>
</tr>
<tr class="odd">
<td></td>
<td>NotConfigured</td>
<td>No search provider has been configured.</td>
</tr>
<tr class="even">
<td></td>
<td>InitializationFailed</td>
<td>Failed to initialize search provider synchronization.</td>
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

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

