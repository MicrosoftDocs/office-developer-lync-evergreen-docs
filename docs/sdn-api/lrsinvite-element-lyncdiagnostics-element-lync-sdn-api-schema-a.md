---
title: LRSInvite element (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: LRSInvite element
ms:assetid: ee22b77d-02e2-70a6-3274-37ddc347067a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439217(v=office.15)
ms:contentKeyID: 57260953
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# LRSInvite element 

(LyncDiagnostics element) (Lync SDN API Schema A)

Event that a Lync Room System (LRS) endpoint (i.e., a Lync meeting room) attempts to establish a call. LDL sends LRSInvite messages depending on how the LDL configuration is set. If the sendmeetingroominfo entry is set to True (activated) and the sendcallinvites entry is set to false (deactivated), LDL send LRSInvite when the call is made from a Lync meeting room. If the sendcallinvites and sendmeetingroominfo entries are both activated, LDL will not send LRSInvite because the Inivte element will already contain the necessary information about which endpoints are of meeting rooms.


**Applies to**: Lync 2013

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p>Not defined</p></td>
</tr>
<tr class="even">
<td><p><strong>Namespace</strong></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Schema file</strong></p></td>
<td><p>LyncSdnApi.Schema.A.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml
<xs:element name="LRSInvite"></xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as sequence, minOccurs, maxOccurs, and choice, see the definition section.

### Parent elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lyncdiagnostics-element-lync-sdn-api-schema-a.md">LyncDiagnostics</a></p></td>
<td><p>Not defined</p></td>
<td><p>The root element for output from the Lync SDN Manager.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

