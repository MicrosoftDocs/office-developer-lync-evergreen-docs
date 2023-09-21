---
title: CodecType complexType (Lync SDN API Schema A)
TOCTitle: CodecType complexType
ms:assetid: 4cfab2e0-9910-d64c-1682-a92322be5a13
ms:mtpsurl: https://msdn.microsoft.com/library/Dn775146(v=office.15)
ms:contentKeyID: 62626120
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# CodecType complexType 

(Lync SDN API Schema A)

**Applies to**: Lync 2013

 

## Type information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Namespace</strong></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Schema file</strong></p></td>
<td><p>LyncSdnApi.Schema.A.xsd</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension base</strong></p></td>
<td><p>None</p></td>
</tr>
</tbody>
</table>


## Definition

```xml
<xs:complexType name="CodecType">
    <xs:sequence>
        <xs:element name="Bandwidth" type="xs:string" minOccurs="0"></xs:element>
        <xs:element name="MaxBandwidth" type="xs:string" minOccurs="0"></xs:element>
    </xs:sequence>
    <xs:attribute name="Name" type="xs:string" use="required" />
</xs:complexType>
```

## Elements and attributes

If the schema defines specific requirements, such as sequence, minOccurs, maxOccurs, and choice, see the definition section.

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
<td><p><a href="bandwidth-element-codectype-complextype-lync-sdn-api-schema-a.md">Bandwidth</a></p></td>
<td><p>xs:string</p></td>
<td><p>Lower limit of the estimated bandwidth.</p></td>
</tr>
<tr class="even">
<td><p><a href="maxbandwidth-element-codectype-complextype-lync-sdn-api-schema-a.md">MaxBandwidth</a></p></td>
<td><p>xs:string</p></td>
<td><p>Upper limit of the estimated bandwidth.</p></td>
</tr>
</tbody>
</table>


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
<td><p>Name</p></td>
<td><p>xs:string</p></td>
<td><p>required</p></td>
<td><p>Name of the standard SIP codec used for the media stream.</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

