---
title: Codec element (StartOrUpdateType complexType) (Lync SDN API Schema A)
TOCTitle: Codec element (Properties element) (StartOrUpdateType complexType)
ms:assetid: 410acce4-c1d2-5be8-8af4-b97ed958588f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775110(v=office.15)
ms:contentKeyID: 62626087
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Codec element (StartOrUpdateType complexType)

(Properties element) (StartOrUpdateType complexType) (Lync SDN API Schema A)

Codec and estimates for the bandwidth that the codecs will use. This list contains all codecs that are agreed upon by the two endpoints. Both end-points may decide to switch amoung these codecs at any time (without additional signalling).


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
<td><p><a href="codectype-complextype-lync-sdn-api-schema-a.md">CodecType</a></p></td>
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
<xs:element name="Codec" type="CodecType" maxOccurs="unbounded"></xs:element>
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
<td><p><a href="properties-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">Properties</a></p></td>
<td><p>Not defined</p></td>
<td><p>Properties of the started or updated media stream.</p></td>
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

