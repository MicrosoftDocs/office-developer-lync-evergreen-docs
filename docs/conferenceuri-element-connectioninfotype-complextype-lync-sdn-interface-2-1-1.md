---
title: ConferenceURI element (ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: ConferenceURI element
ms:assetid: db7305b8-f27f-ad24-c1fa-3596bdd73375
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912692(v=office.15)
ms:contentKeyID: 64126862
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# ConferenceURI element (ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)

(Deprecated - use ConferenceId instead) Sip URI used for the conference. This field is obfuscated unless hidepii is set to false in configuration.


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
<td><p>LyncSDNInterface.Schema.C.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml

    <xs:element name="ConferenceURI"  type="xs:anyURI" minOccurs="0">
    
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
<td><p><a href="connectioninfo-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">ConnectionInfo</a></p></td>
<td><p><a href="connectioninfotype-complextype-lync-sdn-interface-2-1-1.md">ConnectionInfoType</a></p></td>
<td><p>Connection-related properties regardless of the media stream and end points.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

