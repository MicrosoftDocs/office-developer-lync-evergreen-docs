---
title: ErrorProperties complexType (Lync SDN Interface 2.1.1)
TOCTitle: ErrorProperties complexType
ms:assetid: 57ab3938-2ccb-bb10-88f2-dc83b50644f5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912851(v=office.15)
ms:contentKeyID: 64127019
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# ErrorProperties complexType (Lync SDN Interface 2.1.1)

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
      <xs:complexType name="ErrorProperties">
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
<td><p><a href="msdiagnostics-element-errorproperties-sdn-interface-2-1-1.md">MSDiagnostics</a></p></td>
<td><p>xs:string</p></td>
<td><p>More info related to the error.</p></td>
</tr>
<tr class="even">
<td><p><a href="msdiagnosticsclient-element-errorproperties-sdn-interface-2-1-1.md">MSDiagnosticsClient</a></p></td>
<td><p>xs:string</p></td>
<td><p>Info about the error related to and reported by the client.</p></td>
</tr>
<tr class="odd">
<td><p><a href="msdiagnosticspublic-element-errorproperties-sdn-interface-2-1-1.md">MSDiagnosticsPublic</a></p></td>
<td><p>xs:string</p></td>
<td><p>Public info about the error.</p></td>
</tr>
<tr class="even">
<td><p><a href="responsecode-element-errorproperties-complextype-lync-sdn-interface-2-1-1.md">ResponseCode</a></p></td>
<td><p>xs:int</p></td>
<td><p>SIP Error code.</p></td>
</tr>
<tr class="odd">
<td><p><a href="responsephrase-element-errorproperties-sdn-interface-2-1-1.md">ResponsePhrase</a></p></td>
<td><p>xs:string</p></td>
<td><p>More info related to the error.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

