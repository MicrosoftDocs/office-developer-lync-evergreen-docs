---
title: Performance Counters provided by LSM and LDL
TOCTitle: Performance Counters provided by LSM and LDL
ms:assetid: 66a0c1f3-32a4-4e59-9646-824f28d332d0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785223(v=office.15)
ms:contentKeyID: 62952706
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Performance Counters provided by LSM and LDL


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

LDL and LSM provide a number of performance counters. They are described in the following table and may be accessed using [Perfmon](https://technet.microsoft.com/en-us/library/bb490957.aspx).

## Performance counters by LSM

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Performance counter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p># Messages received</p></td>
<td><p>Total number of call related messages received</p></td>
</tr>
<tr class="even">
<td><p># call messages sent overall</p></td>
<td><p>Total number of call related messages sent successfully - counting every destination</p></td>
</tr>
<tr class="odd">
<td><p># unique call messages sent</p></td>
<td><p>Total number of unique call related messages attempted to send (regardless of how many destinations)</p></td>
</tr>
<tr class="even">
<td><p># call messages failed</p></td>
<td><p>Total number of send failures (regardless whether resending succeeded)</p></td>
</tr>
<tr class="odd">
<td><p># undelivered messages</p></td>
<td><p>Total number messages that were not received at a destination - even with attempting to resend</p></td>
</tr>
<tr class="even">
<td><p># messages failed processing</p></td>
<td><p>Total number messages that failed during processing</p></td>
</tr>
<tr class="odd">
<td><p># messages / sec</p></td>
<td><p>Number of messages sent per second</p></td>
</tr>
<tr class="even">
<td><p># length of longest queue</p></td>
<td><p>Longest send message queue</p></td>
</tr>
<tr class="odd">
<td><p># incoming messages / sec</p></td>
<td><p>Rate of incoming call related messages</p></td>
</tr>
<tr class="even">
<td><p># messages processing time (ms)</p></td>
<td><p>Processing time per message (ms)</p></td>
</tr>
<tr class="odd">
<td><p># calls tracked in the cache</p></td>
<td><p>Number of messages currently in the state cache</p></td>
</tr>
<tr class="even">
<td><p># collisions in the cache</p></td>
<td><p>Number of colliding concurrent updates in the state cache</p></td>
</tr>
<tr class="odd">
<td><p># of past due calls being processed</p></td>
<td><p>Number of calls being processed for a state update being past due</p></td>
</tr>
<tr class="even">
<td><p># Average message delivery time</p></td>
<td><p>Time in ms from attempting to send a message to actually receive a delivery confirmation (including resending attempts).</p></td>
</tr>
</tbody>
</table>


## Performance counters by LDL

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Performance counter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p># Messages received</p></td>
<td><p>Total number of call related messages received</p></td>
</tr>
<tr class="even">
<td><p># call messages sent overall</p></td>
<td><p>Total number of call related messages sent successfully - counting every destination</p></td>
</tr>
<tr class="odd">
<td><p># unique call messages sent</p></td>
<td><p>Total number of unique call related messages attempted to send (regardless of to how many destinations)</p></td>
</tr>
<tr class="even">
<td><p># call messages failed</p></td>
<td><p>Total number of send failures (regardless whether resending succeeded</p></td>
</tr>
<tr class="odd">
<td><p># undelivered messages</p></td>
<td><p>Total number messages that were not received at a destination - even when there were attempts to resend them.</p></td>
</tr>
<tr class="even">
<td><p># messages failed processing</p></td>
<td><p>Total number messages that failed during processing</p></td>
</tr>
<tr class="odd">
<td><p># messages / sec</p></td>
<td><p>Number of messages sent per second</p></td>
</tr>
<tr class="even">
<td><p># length of longest queue</p></td>
<td><p>Longest send-message queue</p></td>
</tr>
<tr class="odd">
<td><p># messages attempted to send</p></td>
<td><p>Number of messages currently attempted to send.</p></td>
</tr>
<tr class="even">
<td><p># messages attempted to send overall</p></td>
<td><p>Number of messages overall attempted to send.</p></td>
</tr>
<tr class="odd">
<td><p># Average message delivery time</p></td>
<td><p>Time in ms from attempting to send a message to actually receive a delivery confirmation (including resending attempts).</p></td>
</tr>
</tbody>
</table>

