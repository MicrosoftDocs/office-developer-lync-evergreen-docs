---
title: MessageProperties complexType (Lync SDN Interface 2.1.1)
TOCTitle: MessageProperties complexType
ms:assetid: ce2e4c5b-837e-2ec3-b608-f35fb60a1bc1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912856(v=office.15)
ms:contentKeyID: 64127025
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# MessageProperties complexType (Lync SDN Interface 2.1.1)


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
<td><p>None</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml
      <xs:complexType name="MessageProperties">
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
<td><p><a href="msdiagnostics-element-messageproperties-sdn-interface-2-1-1.md">MSDiagnostics</a></p></td>
<td><p>xs:string</p></td>
<td><p>Lync-specific diagnostics message.</p></td>
</tr>
<tr class="even">
<td><p><a href="msdiagnosticsclient-element-messageproperties-sdn-interface-2-1-1.md">MSDiagnosticsClient</a></p></td>
<td><p>Not defined</p></td>
<td><p>Lync-specific diagnostics message from the client.</p></td>
</tr>
<tr class="odd">
<td><p><a href="msdiagnosticspublic-element-messageproperties-sdn-interface-2-1-1.md">MSDiagnosticsPublic</a></p></td>
<td><p>Not defined</p></td>
<td><p>Lync-specific public diagnostics message.</p></td>
</tr>
<tr class="even">
<td><p><a href="responsecode-element-messageproperties-sdn-interface-2-1-1.md">ResponseCode</a></p></td>
<td><p><a href="responsecodetype-complextype-lync-sdn-interface-2-1-1.md">ResponseCodeType</a></p></td>
<td><p>Message describing the error.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

