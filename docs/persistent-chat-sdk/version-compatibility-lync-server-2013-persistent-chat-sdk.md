---
title: Version compatibility (Lync Server 2013 Persistent Chat SDK)
TOCTitle: Version compatibility
ms:assetid: 35a29ae8-a667-4215-a487-0f530bfc34a8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465897(v=office.15)
ms:contentKeyID: 57101345
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Version compatibility (Lync Server 2013 Persistent Chat SDK)

Learn how to set up Microsoft Lync Server 2013 Persistent Chat API and Lync Server deployments.


_**Applies to:** Lync 2013 | Lync Server 2013_

Microsoft Lync Server 2013 Persistent Chat API applications should be used in a Microsoft Lync Server 2013 deployment. Similarly, Microsoft Lync Server 2010 Group Chat API applications should be targeted against Microsoft Lync Server 2010, and Microsoft Office Communications Server 2007 R2 Group Chat API applications should be targeted against Microsoft Office Communications Server 2007 R2. In a mixed deployment environment where Lync Server 2013 coexists with Lync Server 2010 or Office Communications Server 2007 R2, and a Lync Server 2013 Persistent Chat API or Group Chat API application interoperates with different versions of the servers, compatibility issues might appear. The following table lists the potential application compatibility issues.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Application authored using an API version</p></th>
<th><p>Target server version: Lync Server 2013</p></th>
<th><p>Target server version: Lync Server 2010</p></th>
<th><p>Target server version: Office Communications Server 2007 R2</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 Persistent Chat API</p></td>
<td><p>Compatible by design.</p></td>
<td><p>Incompatible. The Lync Server 2013 Persistent Chat API application should not be deployed against Lync Server 2010.</p></td>
<td><p>Incompatible. The Lync Server 2013 Persistent Chat API application should not be deployed against Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010 Group Chat API</p></td>
<td><p>May be compatible, without support of category or user management.</p></td>
<td><p>Compatible by design.</p></td>
<td><p>Compatible.</p></td>
</tr>
<tr class="odd">
<td><p>Office Communications Server 2007 R2 API</p></td>
<td><p>May be compatible, without support of category or user management.</p></td>
<td><p>Compatible.</p></td>
<td><p>Compatible by design.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[What's new in Lync Server 2013 Persistent Chat SDK](what-s-new-in-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK documentation](lync-server-2013-persistent-chat-sdk-documentation.md)

