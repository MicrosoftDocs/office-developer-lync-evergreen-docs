---
title: Bandwidth element (CodecType complexType) (Lync SDN API Schema A)
TOCTitle: Bandwidth element
ms:assetid: ad870978-98bb-481d-8e89-6fe512f95865
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775105(v=office.15)
ms:contentKeyID: 62626080
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Bandwidth element (CodecType complexType) (Lync SDN API Schema A)

Lower limit of the estimated bandwidth.


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
<xs:element name="Bandwidth" type="xs:string" minOccurs="0"></xs:element>
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
<td><p><a href="codec-element-properties-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-api-schema-a.md">CodecType</a></p></td>
<td><p>Codec and estimates for the bandwidth that the codecs will use. This list contains all codecs that are agreed upon by the two endpoints. Both end-points may decide to switch amoung these codecs at any time (without additional signalling).</p></td>
</tr>
<tr class="even">
<td><p><a href="codec-element-properties-element-qualityupdate-element-lyncdiagnostics-element-lync-sdn-api-schema-a.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-api-schema-a.md">CodecType</a></p></td>
<td><p>Describes the last codec used for the media.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

