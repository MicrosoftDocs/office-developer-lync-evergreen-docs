---
title: QualityType complexType (Lync SDN Interface 2.1.1)
TOCTitle: QualityType complexType
ms:assetid: 9d9ac2b4-6513-a116-464f-629e33e0fb33
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912863(v=office.15)
ms:contentKeyID: 64127032
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# QualityType complexType (Lync SDN Interface 2.1.1)

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
      <xs:complexType name="QualityType">
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
<td><p><a href="from-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">From</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">QualityEndPointType</a></p></td>
<td><p>The source of the reported media stream.</p></td>
</tr>
<tr class="even">
<td><p><a href="properties-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">Properties</a></p></td>
<td><p><a href="qualitypropertiestype-complextype-lync-sdn-interface-2-1-1.md">QualityPropertiesType</a></p></td>
<td><p>Properties of the media stream, including a selected set of quality metrics reported and thresholds that are used to determine a bad call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="route-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">Route</a></p></td>
<td><p><a href="routetype-complextype-lync-sdn-interface-2-1-1.md">RouteType</a></p></td>
<td><p>Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">To</a></p></td>
<td><p><a href="qualityendpointtype-complextype-lync-sdn-interface-2-1-1.md">QualityEndPointType</a></p></td>
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
<td><p>Modality or media type for which the quality metrics are reported. The supported options are audio, video and applicationsharing.</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

