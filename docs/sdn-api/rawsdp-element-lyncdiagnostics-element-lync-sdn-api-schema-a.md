---
title: RawSDP element (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: RawSDP element
ms:assetid: bf1a025e-d09e-1794-019e-5fbecf41fd5c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439250(v=office.15)
ms:contentKeyID: 57260986
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# RawSDP element (LyncDiagnostics element) (Lync SDN API Schema A)

Raw Session Description Protocol (SDP) data that is included as the payload of the underlying SIP messages of the Invite, LRSInvite and StartOrUpdate type, if the sendrawsdp entry is set to True in the LDL configuration file.


**Applies to**: Lync 2013

**In this article**  
Element information  
Definition  
Elements and attributes  

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p>xs:string</p></td>
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
<xs:element name="RawSDP" type="xs:string" minOccurs="0"></xs:element>
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

