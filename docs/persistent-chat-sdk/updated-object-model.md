---
title: Updated object model
TOCTitle: Updated object model
ms:assetid: 20f5d304-2e81-4eaa-a134-00b0951383a6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439201(v=office.15)
ms:contentKeyID: 57101301
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Updated object model

Learn about new Microsoft Lync Server 2013 Persistent Chat API components.


**Applies to:** Lync 2013 | Lync Server 2013

## Object model

The following table lists the updates to the Lync Server 2013 Persistent Chat API components in the current release.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Update</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Persistent chat room management services</p></td>
<td><p>Persistent chat room management services are available for non-administrative users. Administrators use the Windows PowerShell cmdlets to provide the chat room management services.</p></td>
</tr>
<tr class="even">
<td><p>Persistent chat room category management</p></td>
<td><p>Persistent chat room category management services support read-only category operations for end users only. Category creation and management are no longer exposed by the Lync Server 2013 Persistent Chat API. Administrators can access the services through the Windows PowerShell or the Lync Server Control Panel interface.</p></td>
</tr>
<tr class="odd">
<td><p>User administration services</p></td>
<td><p>User administration services is no longer managed by or replicated to persistent chat. Instead, user administration is now role-based in a manner consistent with the rest of the Lync system. Federation is no longer supported in Persistent Chat. Management of user groups and federated user groups is no longer exposed by the Lync Server 2013 Persistent Chat API, although user permissions are still accessible through the Lync Server 2013 Persistent Chat API.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[What's new in Lync Server 2013 Persistent Chat SDK](what-s-new-in-lync-server-2013-persistent-chat-sdk.md)

[Class library changes](class-library-changes.md)

