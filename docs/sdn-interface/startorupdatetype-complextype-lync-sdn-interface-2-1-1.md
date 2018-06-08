---
title: StartOrUpdateType complexType (Lync SDN Interface 2.1.1)
TOCTitle: StartOrUpdateType complexType
ms:assetid: 88001339-2d99-5fba-1b4b-4d6e8d56ea94
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912862(v=office.15)
ms:contentKeyID: 64127031
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# StartOrUpdateType complexType (Lync SDN Interface 2.1.1)

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
<td><p>LyncSDNInterface.Schema.C.xsd</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension base</strong></p></td>
<td><p>None</p></td>
</tr>
</tbody>
</table>


## Definition

```xml
      <xs:complexType name="StartOrUpdateType">
    <xs:attribute name="Type" type="xs:string" use="required"/>
  
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
<td><p><a href="from-element-startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">From</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Source of the media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="properties-element-startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">Properties</a></p></td>
<td><p><a href="startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">StartPropertiesType</a></p></td>
<td><p>Properties of the started or updated media stream.</p></td>
</tr>
<tr class="odd">
<td><p><a href="to-element-startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">To</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
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
<td><p>Modality or media type for which the quality metrics are reported. The valid options are audio, video and applicationsharing</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

