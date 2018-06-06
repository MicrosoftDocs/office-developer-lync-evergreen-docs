---
title: Media stack performance counters
TOCTitle: Media stack performance counters
ms:assetid: c2476bf2-bb17-4f28-b69b-060fb21924e9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466085(v=office.15)
ms:contentKeyID: 57103176
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Media stack performance counters


_**Applies to:** Lync 2013 | Lync Server 2013_

Media stack performance counters are shipped with A/V Multipoint Control Unit (MCU), Microsoft Lync Server 2010 servers, Application-Sharing MCU, and Microsoft Lync Server 2010 Mediation Server. They are not available on clients (Microsoft Lync 2010, Microsoft Lync 2010 Attendant, and consoles).

The Media stack performance counters are controlled by the following registry subkey:

<pre IsFakePre="true" xmlns="http://www.w3.org/1999/xhtml">
  
    <strong>HKEY_LOCAL_MACHINE</strong>
  \Software\Microsoft\RTC\Performance\EnablePerfCounters\</pre>


The values associated with this registry subkey appear in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>Do not enable performance counters.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Enable Operational, Planning, and Informational performance counters.</p></td>
</tr>
</tbody>
</table>


By default, the value is 0 for clients, and is 1 for A/V MCU, UCMA 3.0, Application-Sharing MCU, and Mediation Server. Values of 2 or larger are reserved for system use.

The following topics discuss each media stack performance counter:

  - [Operations performance counters](operations-performance-counters.md)

  - [Planning performance counters](planning-performance-counters.md)

  - [Informational performance counters](informational-performance-counters.md)

