---
title: InviteType complexType (Lync SDN API Schema A)
TOCTitle: InviteType complexType
ms:assetid: a36e217b-af08-97a2-28e4-17fc290d096f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775148(v=office.15)
ms:contentKeyID: 62626122
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# InviteType complexType 

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
<xs:complexType name="InviteType">
    <xs:sequence>
        <xs:element name="Caller" type="EndPointType"></xs:element>
        <xs:element name="Callee" type="EndPointType"></xs:element>
    </xs:sequence>
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
<td><p><a href="callee-element-invitetype-complextype-lync-sdn-api-schema-a.md">Callee</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Properties of the callee.</p></td>
</tr>
<tr class="even">
<td><p><a href="caller-element-invitetype-complextype-lync-sdn-api-schema-a.md">Caller</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-api-schema-a.md">EndPointType</a></p></td>
<td><p>Properties of the caller.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

