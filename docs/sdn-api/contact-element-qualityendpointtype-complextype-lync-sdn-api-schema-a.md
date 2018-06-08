---
title: Contact element (QualityEndPointType complexType) (Lync SDN API Schema A)
TOCTitle: Contact element (QualityEndPointType complexType)
ms:assetid: 46444871-edf3-f92c-a96a-adfd4a3e6813
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775114(v=office.15)
ms:contentKeyID: 62626085
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Contact element (QualityEndPointType complexType) 

(Lync SDN API Schema A)

SIP URI of the user as extracted from the Contact header of the underlying SIP message. This field is obfuscated unless hidepii is set to false in the LDL configuration file.


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
<td><p>xs:anyURI</p></td>
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
<xs:element name="Contact" type="xs:anyURI" minOccurs="0"></xs:element>
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
<td><p><a href="from-element-qualityupdate-element-sdn-api-schema-a.md">From</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>The source of the reported media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-qualityupdate-element-sdn-api-schema-a.md">To</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-api-schema-a.md">QualityEndPointType</a></p></td>
<td><p>Destination of the media stream.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

