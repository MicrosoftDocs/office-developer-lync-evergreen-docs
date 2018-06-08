---
title: Properties element (MessageType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Properties element (MessageType complexType)
ms:assetid: 5da0daf6-1235-b779-4a67-074bed2c527f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912784(v=office.15)
ms:contentKeyID: 64126953
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (MessageType complexType) (Lync SDN Interface 2.1.1)

Details of the Error or reason for ending the streams.


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
<td><p><a href="messageproperties-complextype-lync-sdn-interface-2-1-1.md">MessageProperties</a></p></td>
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

    <xs:element name="Properties"  type="MessageProperties" minOccurs="0">
    
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
<td><p><a href="lyncdiagnostics-element-lync-sdn-interface-2-1-1.md">LyncDiagnostics</a></p></td>
<td><p><a href="messagetype-complextype-lync-sdn-interface-2-1-1.md">MessageType</a></p></td>
<td><p>The root element for output from the Lync SDN Manager.</p></td>
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

