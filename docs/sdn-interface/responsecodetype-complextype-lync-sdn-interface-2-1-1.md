---
title: ResponseCodeType complexType (Lync SDN Interface 2.1.1)
TOCTitle: ResponseCodeType complexType
ms:assetid: 05b05df9-1ac9-92e2-36d2-cce2bb3cd400
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912861(v=office.15)
ms:contentKeyID: 64127029
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# ResponseCodeType complexType (Lync SDN Interface 2.1.1)


**In this article**  
Type information  
Definition  
Elements and attributes  

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
<td><p>xs:string</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml
      <xs:complexType name="ResponseCodeType">
        <xs:complexContent>
 
        <xs:extension base="xs:string">
      
    <xs:attribute name="Code" type="xs:unsignedShort" use="required"/>
  
        </xs:extension>
 
        </xs:complexContent>
 
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as sequence, minOccurs, maxOccurs, and choice, see the definition section.

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

