---
title: Enhanced features of Lync SDN Interface 2.1.1
TOCTitle: Enhanced features of Lync SDN Interface 2.1.1
ms:assetid: a0ef6ad8-c0a2-425f-b236-dc4907efa22b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785195(v=office.15)
ms:contentKeyID: 62952679
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Enhanced features of Lync SDN Interface 2.1.1


**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

**In this article**  
New and updated setting-specific behaviors  
New and updated behaviors for version 2.1.1  
Additional resources  

The Lync SDN Interface 2.1.1 updates features that are specific to certain configuration settings. These updates:

  - Enable the network to identify the media streams.

  - Communicate updates of the call state and quality data of the media streams as well as endpoints.

  - Provide information about correlations among calls and external users.

  - Optionally, add more insight about SDP content provision, early forewarning with Invites, and errors at the SIP signaling level.


> [!NOTE]
> <P>For clarity, the "new" features discussed in this article reflect from version 2.0 and 2.1 and 2.1.1; they are not new in the interval between versions 2.1 and 2.1.1.</P>



## New and updated setting-specific behaviors

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Feature Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Bandwidth</p></td>
<td><p>The Bandwidth block provides a rough upper and average estimate on the bandwidth this stream might use. This is a weighted calculation from the codecs used. Most importantly, Bandwidth is set to 0 if the stream is on hold. Furthermore, an attribute in this tag will indicate whether this stream (in this case rather a channel) contains in fact several multiplexed streams showing multiple participants in a video conference scenario.</p></td>
</tr>
<tr class="even">
<td><p>IncallEnabled</p></td>
<td><p>This field indicates whether the Lync client should be sending In-call QoE reports. This field is derived from the UserAgent and currently the Lync Server as well as the Lync SDN components have no way to find out whether a Lync client actually has it activated.</p></td>
</tr>
<tr class="odd">
<td><p>StreamQuality</p></td>
<td><p>Summarizes the quality of the stream based on other factors than MOS. This field can have three values, which describe the quality level: Good, Poor, and Bad. The particular level of a stream is determined from various sources:</p>
<ul>
<li><p>The Media Stack on the Lync client. The Lync client uses a sophisticated algorithm taking particular metrics, thresholds, and the healer component (which attempts to overcome issues introduced by the network) into account and reports this quality level in most InCallQuality reports.</p></li>
<li><p>The LSM uses thresholds defined by the QoE determination and maintained in the QoEMetrics Lync Back-end database to calculate the StreamQuality. These thresholds are configuration settings for the LSM (see <a href="configuring-lsm-using-the-configuration-file.md">Configuring LSM using the configuration file</a>) and might be updated from a QoEMetrics database by using the SDNManager.exe command line options (see <a href="configuring-lsm-using-command-prompt.md">Configuring LSM using command prompt</a>).</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>EPType (Endpoint Type)</p></td>
<td><p>If set to &quot;LRS&quot;, it indicates that an end-point is a Lync Room System. As video conference rooms are usually considered higher priority this flag enables a special characterization of such stream. (This information is determined from the UserAgent.)</p></td>
</tr>
<tr class="odd">
<td><p>SourcePool</p></td>
<td><p>As connection information this field describes the Lync/Skype pool on which the call is handled and originated these messages. This info should enable network controllers to locate the Lync pool as well as identify a back-end and access the Lync Server QoEMetrics database for additional details.</p></td>
</tr>
<tr class="even">
<td><p>DSCPInbound/DSCPOutbound</p></td>
<td><p>These fields describe for an endpoint the DSCP (WMM) value used for outgoing streams as well as the DSCP value received on inbound streams.</p></td>
</tr>
<tr class="odd">
<td><p>Other</p></td>
<td><p>Miscellaneous fields related to the end points to describe the capturing device (usually a microphone), rendering device (usually a speaker), Wifi device, OS and CPU as well as additional network related info such as the MAC address.</p></td>
</tr>
</tbody>
</table>


## New and updated behaviors for version 2.1.1

Following are features and behaviors that have been added or updated in the Lync SDN Interface between versions 2.1 and 2.1.1

  - Disaster failover configuration for LSM pools

  - Reporting on mediabypass PSTN calls that were ignored before

  - Support for Skype for Business vNext and automatic activation of IncallQuality messages in vNext

  - For additional updates, please see the Release Notes.

## See also

  - [Understanding Lync SDN Interface 2.1.1](understanding-lync-sdn-interface-2-1-1.md)

  - [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

