---
title: ConversationalMOS element (QualityPropertiesType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: ConversationalMOS element
ms:assetid: 8ffaf084-0f8f-2f08-ea97-57f57170de48
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912698(v=office.15)
ms:contentKeyID: 64126869
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# ConversationalMOS element (QualityPropertiesType complexType) (Lync SDN Interface 2.1.1)

Conversational clarity index for remote party, as described in \[ITUP.562\] section 6.3. This metric is reported for all available modalities and media types. This field is unused and deprecated for Lync clients 2013 and beyond.


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
<td><p>LyncSDNInterface.Schema.C.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml

    <xs:element name="ConversationalMOS"  type="xs:string">
    
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

