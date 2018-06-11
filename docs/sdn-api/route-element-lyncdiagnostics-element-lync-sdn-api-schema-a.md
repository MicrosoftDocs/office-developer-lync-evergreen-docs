---
title: Route element (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: Route element
ms:assetid: f0c19a1e-f4cb-a8c9-9a2c-169f2e6ca9fd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439271(v=office.15)
ms:contentKeyID: 57261007
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Route element 

(LyncDiagnostics element) (Lync SDN API Schema A)

Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.


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

```xml
<xs:element name="Route" minOccurs="0">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="Hop" type="xs:string" maxOccurs="unbounded"></xs:element>
        </xs:sequence>
    </xs:complexType>
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
<td><p><a href="lyncdiagnostics-element-lync-sdn-api-schema-a.md">LyncDiagnostics</a></p></td>
<td><p>Not defined</p></td>
<td><p>The root element for output from the Lync SDN Manager.</p></td>
</tr>
</tbody>
</table>


### Child elements

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
<td><p><a href="hop-element-route-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Hop</a></p></td>
<td><p>xs:string</p></td>
<td><p>IP address of one hop (router, gateway, switch, etc) on the path from the source to the destination of the media stream.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

