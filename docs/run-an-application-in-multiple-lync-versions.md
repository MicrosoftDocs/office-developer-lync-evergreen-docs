---
title: Run an application in multiple Lync versions
TOCTitle: Run an application in multiple Lync versions
ms:assetid: 507d0239-5c49-4ddf-bbb0-8d82d5a4febb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937316(v=office.15)
ms:contentKeyID: 50877146
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Run an application in multiple Lync versions

![What's new topic](images/JJ937254.mod_icon_whatsnew_long(Office.15).png "What's new topic")

Learn how to run a Microsoft Lync 2013 API-enabled application on a computer where multiple versions of the Lync client is installed.

**Last modified:** February 22, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Lync client compatibility<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Lync client compatibility

Microsoft Lync 2013 client supports all applications that reference the Lync 2013 API or any previous version of the Lync client API. However, older versions of the Lync client do not support applications built with later versions of the Lync API. In this case, attempting to get the API entry point by calling the static [LyncClient.GetClient](https://msdn.microsoft.com/en-us/library/jj278213\(v=office.15\)) or [LyncClient.GetAutomation](https://msdn.microsoft.com/en-us/library/jj266970\(v=office.15\)) method fails with the [Microsoft.Lync.Model.ClientNotFoundException](https://msdn.microsoft.com/en-us/library/jj293274\(v=office.15\)) exception. If multiple versions of the Lync client are installed on a computer, be sure to start the highest version of the client before starting your application.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A side-by-side installation of Microsoft Lync 2010 SDK and Microsoft Lync 2013 SDK is not supported by Microsoft. You should uninstall any older versions of Lync SDK before installing Microsoft Lync 2013 SDK.</p></td>
</tr>
</tbody>
</table>

### UI suppression

If multiple versions of the Lync client are installed on a computer, the most recent version of the client process starts when your application initializes the process by calling the [LyncClient.GetClient](https://msdn.microsoft.com/en-us/library/jj278213\(v=office.15\)) method. If the starting process is not configured for UI suppression, the client UI is shown on the desktop. To avoid this, be sure to set UI suppression for all version of the client that you install on a computer.

## Additional resources

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

