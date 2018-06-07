---
title: Hop element (Route element) (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: Hop element
ms:assetid: 58bf7971-c8e6-2dd6-4457-2aa8917f8931
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439221(v=office.15)
ms:contentKeyID: 57260958
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Hop element (Route element) (LyncDiagnostics element) (Lync SDN API Schema A)

IP address of one hop (router, gateway, switch, etc) on the path from the source to the destination of the media stream.


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
<xs:element name="Hop" type="xs:string" maxOccurs="unbounded"></xs:element>
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
<td><p><a href="route-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Route</a></p></td>
<td><p>Not defined</p></td>
<td><p>Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

