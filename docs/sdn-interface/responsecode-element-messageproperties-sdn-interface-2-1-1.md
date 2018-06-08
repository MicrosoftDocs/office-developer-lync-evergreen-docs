---
title: ResponseCode element (MessageProperties complexType) (Lync SDN Interface 2.1.1)
TOCTitle: ResponseCode element (MessageProperties complexType)
ms:assetid: cd0aa12a-ce65-faf2-04d4-3f7e02441338
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912811(v=office.15)
ms:contentKeyID: 64126980
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# ResponseCode element (MessageProperties complexType) (Lync SDN Interface 2.1.1)

Message describing the error.


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
<td><p><a href="responsecodetype-complextype-lync-sdn-interface-2-1-1.md">ResponseCodeType</a></p></td>
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

    <xs:element name="ResponseCode"  type="ResponseCodeType" minOccurs="0">
    
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
<td><p><a href="properties-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Properties</a></p></td>
<td><p><a href="messageproperties-complextype-lync-sdn-interface-2-1-1.md">MessageProperties</a></p></td>
<td><p>Details of the Error or reason for ending the streams.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

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
<td><p>Code</p></td>
<td><p>xs:unsignedShort</p></td>
<td><p>required</p></td>
<td><p>SIP error code for this error.</p></td>
<td><p>Values of the xs:unsignedShort type.</p></td>
</tr>
</tbody>
</table>

