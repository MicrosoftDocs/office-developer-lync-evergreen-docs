---
title: Properties element (ErrorType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Properties element (ErrorType complexType)
ms:assetid: 95d69869-e84b-eb40-2e76-5717ada715b3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912782(v=office.15)
ms:contentKeyID: 64126951
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (ErrorType complexType) (Lync SDN Interface 2.1.1)

Properties of the Error.


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
<td><p><a href="errorproperties-complextype-lync-sdn-interface-2-1-1.md">ErrorProperties</a></p></td>
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

    <xs:element name="Properties"  type="ErrorProperties" minOccurs="0">
    
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
<td><p><a href="error-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Error</a></p></td>
<td><p><a href="errortype-complextype-lync-sdn-interface-2-1-1.md">ErrorType</a></p></td>
<td><p>This event is optional. Error event that a SIP dialog has failed. Error events are also sent for SIP calls that are terminated even before a media stream is started or for failed to be updated.</p></td>
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

