---
title: Bandwidth element (CodecType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Bandwidth element (CodecType complexType)
ms:assetid: 0a904fd1-6a8a-0f55-e08a-cc97998a2caa
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912676(v=office.15)
ms:contentKeyID: 64126845
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Bandwidth element (CodecType complexType) 

(Lync SDN Interface 2.1.1)

Average estimated bandwidth.

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

```xml

    <xs:element name="Bandwidth"  type="xs:string" minOccurs="0">
    
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
<td><p><a href="codec-element-startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-interface-2-1-1.md">CodecType</a></p></td>
<td><p>Codec and estimates for the bandwidth that the codecs will use. This list contains all codecs that are agreed upon by the two endpoints. Both end-points may decide to switch among these codecs at any time (without additional signalling).</p></td>
</tr>
<tr class="even">
<td><p><a href="codec-element-qualitypropertiestype-complextype-lync-sdn-interface-2-1-1.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-interface-2-1-1.md">CodecType</a></p></td>
<td><p>Describes the last codec used for the media.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

