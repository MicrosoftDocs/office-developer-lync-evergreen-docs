---
title: Bandwidth element (StartPropertiesType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Bandwidth element (StartPropertiesType complexType)
ms:assetid: 17268be6-e3d2-cda2-84ba-5461dd76de65
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912670(v=office.15)
ms:contentKeyID: 64126839
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Bandwidth element (StartPropertiesType complexType) 

(Lync SDN Interface 2.1.1)

Describes the maximum and average amount of bandwidth needed by this stream. It takes the possible codecs and stream multiplexing into account.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="bandwidthtype-complextype-lync-sdn-interface-2-1-1.md">BandwidthType</a></p></td>
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

    <xs:element name="Bandwidth"  type="BandwidthType" minOccurs="0">
    
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
<td><p><a href="properties-element-startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">Properties</a></p></td>
<td><p><a href="startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">StartPropertiesType</a></p></td>
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
<td><p><a href="average-element-bandwidthtype-complextype-lync-sdn-interface-2-1-1.md">Average</a></p></td>
<td><p>xs:long</p></td>
<td><p>Estimated average amount of the bandwidth.</p></td>
</tr>
<tr class="even">
<td><p><a href="maximum-element-bandwidthtype-complextype-lync-sdn-interface-2-1-1.md">Maximum</a></p></td>
<td><p>xs:long</p></td>
<td><p>Estimated upper limit of the bandwidth needed by this stream.</p></td>
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
<td><p>Multiplexed</p></td>
<td><p>xs:int</p></td>
<td><p>optional</p></td>
<td><p>Number of times this stream is multiplexed (if &gt; 1). This might mean the overall bandwidth requirement could be up to as many times.</p></td>
<td><p>Values of the xs:int type.</p></td>
</tr>
</tbody>
</table>

