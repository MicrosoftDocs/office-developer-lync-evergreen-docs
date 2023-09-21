---
title: LowResolutionCallPercent element (QualityPropertiesType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: LowResolutionCallPercent element
ms:assetid: 16ec328c-7910-3838-5de2-2611f7dbab81
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912755(v=office.15)
ms:contentKeyID: 64126925
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# LowResolutionCallPercent element 

(QualityPropertiesType complexType) (Lync SDN Interface 2.1.1)

Percentage of time of the call where resolution is low. Threshold is 120 pixels for smaller dimension. This metric is reported for video streams when available. (percent)

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
<td><p>LyncSDNInterface.Schema.C.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

```xml

    <xs:element name="LowResolutionCallPercent" >
    
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
<td><p><a href="properties-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">Properties</a></p></td>
<td><p><a href="qualitypropertiestype-complextype-lync-sdn-interface-2-1-1.md">QualityPropertiesType</a></p></td>
<td><p>Properties of the media stream, including a selected set of quality metrics reported and thresholds that are used to determine a bad call.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

