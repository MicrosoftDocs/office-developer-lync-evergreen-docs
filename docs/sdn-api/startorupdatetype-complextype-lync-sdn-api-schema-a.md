---
title: StartOrUpdateType complexType (Lync SDN API Schema A)
TOCTitle: StartOrUpdateType complexType
ms:assetid: b6b11311-693e-e822-1686-d805ef035b22
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775150(v=office.15)
ms:contentKeyID: 62626124
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# StartOrUpdateType complexType 

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

``` xml
<xs:complexType name="StartOrUpdateType">
    <xs:sequence>
        <xs:element name="EndPoint" type="EndPointType" minOccurs="0" maxOccurs="2"></xs:element>
        <xs:element name="From" type="EndPointType" minOccurs="0"></xs:element>
        <xs:element name="To" type="EndPointType" minOccurs="0"></xs:element>
        <xs:element name="Properties" minOccurs="0">
            <xs:complexType>
                <xs:sequence>
                    <xs:element name="Protocol" type="xs:string"></xs:element>
                    <xs:element name="Codec" type="CodecType" maxOccurs="unbounded"></xs:element>
                </xs:sequence>
            </xs:complexType>
        </xs:element>
    </xs:sequence>
    <xs:attribute name="Type" type="xs:string" use="required" />
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
<td><p><a href="endpoint-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Endpoint while the call is on-hold.</p></td>
</tr>
<tr class="even">
<td><p><a href="from-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">From</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Source of the media stream.</p></td>
</tr>
<tr class="odd">
<td><p><a href="properties-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">Properties</a></p></td>
<td><p>Not defined</p></td>
<td><p>Properties of the started or updated media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-startorupdatetype-complextype-lync-sdn-api-schema-a.md">To</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
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
<td><p>Type</p></td>
<td><p>xs:string</p></td>
<td><p>required</p></td>
<td><p>Modelity or media type for which the quality metrics are reported. The valid options are audio, video and applicationsharing</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

