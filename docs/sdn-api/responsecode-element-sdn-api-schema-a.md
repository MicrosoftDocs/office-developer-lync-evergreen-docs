---
title: ResponseCode element  (Lync SDN API Schema A)
TOCTitle: ResponseCode element
ms:assetid: 258d235f-f85c-9657-b2d9-ec61e14d0c83
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775138(v=office.15)
ms:contentKeyID: 62626112
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# ResponseCode element 

(Properties element) (LyncDiagnostics element) (Lync SDN API Schema A)

Message describing the error.


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
<xs:element name="ResponseCode">
    <xs:attribute name="Code" type="xs:unsignedShort" use="required" />
</xs:element>
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
<td><p><a href="properties-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Properties</a></p></td>
<td><p>Not defined</p></td>
<td><p>Details of the Error.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Attribute</p></th>
<th><p>Type</p></th>
<th><p>Required</p></th>
<th><p>Description</p></th>
<th><p>Possible values</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Code</p></td>
<td><p>xs:unsignedShort</p></td>
<td><p>required</p></td>
<td><p>SIP error code for this error.</p></td>
<td><p>Values of the xs:unsignedShort type.</p></td>
</tr>
</tbody>
</table>

