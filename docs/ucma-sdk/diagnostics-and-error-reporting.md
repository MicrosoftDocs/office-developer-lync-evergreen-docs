---
title: Diagnostics and error reporting
TOCTitle: Diagnostics and error reporting
ms:assetid: 6c2b33a0-a4f3-444f-a5fb-fb905bdd2f37
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466074(v=office.15)
ms:contentKeyID: 57103068
ms.date: 07/25/2014
mtps_version: v=office.15
description: Improve diagnostics & error reporting with Microsoft Lync, UCMA SDK, and Lync Server 2013. Efficiently discover, diagnose, and resolve failures.
---

# Diagnostics and error reporting


**Applies to:** Lync 2013 | Lync Server 2013

Significant improvements in diagnostics and debugging for the administrator and application developer were added in Microsoft Lync Server 2010. Developers who are working with Microsoft Unified Communications Managed API 4.0 can take advantage of a number of improvements that were introduced in Microsoft Unified Communications Managed API (UCMA) 3.0, to quickly and efficiently discover, diagnose, and resolve any failures that occur within the platform or application, and that can result in failure or call termination.

As part of the manageability and alerting capabilities that are currently present in Microsoft Lync Server 2013, errors are placed on the wire by UCMA 4.0 applications, Lync, and Lync Server 2013. These errors provide a first hint to an administrator tracking a failure in the Lync Server 2013 system. Errors are categorized and surfaced to the administrator of a Lync Server 2013 deployment according to severity and frequency of occurrence. Based on these factors, alerts are raised to the administrator to indicate failures or recurring issues within the Lync Server 2013 deployment or the application pool.

If the UCMA 4.0 platform causes the termination of an existing session or declines an incoming session, the platform automatically sends the appropriate error code on the wire in a header with the following form, shown in Backus-Naur form.

**ms-diagnostics** HCOLON  **ErrorId** SEMI **source-param**  SEMI **reason-param** \*(SEMI **generic-param**)

**ErrorId** = unsigned-integer

Required. Value MUST be within unsigned integer range. **ErrorId** represents a specific error condition, and SHOULD be used by the SIP client to determine appropriate error handling behavior.

**source-param** = "source=" **source-valuesource-value** = quoted-string

Optional. Value SHOULD be the FQDN or the IP address of SIP server generating the header.

**reason-param** = "reason=" **reason-value**

**reason-value** = quoted-stringOptional. Reason should indicate a specific reason for an explanation of the error. The SIP client SHOULD NOT use this parameter value for defining error handling behavior. This parameter value can be used for SIP server troubleshooting purposes.

\*(SEMI **generic-param**) Optional. **generic-param** can be used to define custom attribute-value pairs to convey additional information to the SIP client on how to troubleshoot or fix the problem.

The following are three example headers. An "ms-diagnostics" header is sent for application endpoints; an "ms-client-diagnostics" header is sent for user endpoints.

**ms-diagnostics**: 24081;Component="RTCC/4.0.0.0\_ContosoApplication";Reason="Endpoint termination";Source= applicationserver.contoso.com

**ms-client-diagnostics**: 24083;Component="RTCC/4.0.0.0\_ContosoApplication";Reason="Message was received out of dialog.";request=BENOTIFY;Source=applicationserver.contoso.com

**ms-client-diagnostics**: 24067;Component="RTCC/4.0.0.0\_ContosoApplication";Reason="Mcu is rolling over";Source= applicationserver.contoso.com

"ms-diagnostics" and "ms-client-diagnostics" do not cross federation boundaries. To provide diagnostic information to an administrator across a federation boundary, use an "ms-diagnostics-public" header.

For the full error code descriptions for UCMA 4.0, UCCP, and Lync Server 2013, see [\[MS-OCER\]: Client Error Reporting Protocol Specification](http://msdn.microsoft.com/library/cc431503.aspx).

It's strongly advised that an application add its own diagnostic header if the API call to send failure or rejection is caused by the application, either directly or as a reaction to changing server/platform conditions. Applications can use the members on the [DiagnosticsInformation](https://msdn.microsoft.com/library/hh161812\(v=office.15\)) class to supply diagnostics code.

The UCMA 4.0 platform has reserved a set of diagnostic ranges solely for use by developers so that errors raised from the application will be captured and logged within the Lync Server 2013 reporting infrastructure.

The following table lists the reserved ranges.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Range and range name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>60000 - 60999</p></td>
<td><p>These codes should be used to indicate ‘success’: terminations or responses that are expected in the normal functioning of the application. An example is an application hanging up due to the user completing an Interactive Voice Response (IVR) application.</p></td>
</tr>
<tr class="even">
<td><p>61000 - 61999</p></td>
<td><p>These codes should be used to indicate expected failures: terminations or responses that are expected in common error cases. An example is an application hang-up due to a user not providing any input to an IVR, and the application timing out.</p></td>
</tr>
<tr class="odd">
<td><p>62000 - 62999</p></td>
<td><p>These codes should be used to indicate unexpected failures: terminations or responses due to the application entering some unexpected state or corner case. An example is an AVFlow changing its state to Idle in the middle of a speech recognition attempt, and the application choosing to terminate at that time.</p></td>
</tr>
</tbody>
</table>

