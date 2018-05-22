---
title: Properties element (EndedType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Properties element (EndedType complexType)
ms:assetid: fe3ffc6f-1ab1-5d92-4084-9d2043b39bdd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912781(v=office.15)
ms:contentKeyID: 64126950
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (EndedType complexType) (Lync SDN Interface 2.1.1)

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
<td><p><a href="endedproperties-complextype-lync-sdn-interface-2-1-1.md">EndedProperties</a></p></td>
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

    <xs:element name="Properties"  type="EndedProperties" minOccurs="0">
    
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
<td><p><a href="ended-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Ended</a></p></td>
<td><p><a href="endedtype-complextype-lync-sdn-interface-2-1-1.md">EndedType</a></p></td>
<td><p>Event that a Sip call has ended and all media stream terminated.</p></td>
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
<td><p><a href="msdiagnostics-element-endedproperties-complextype-lync-sdn-interface-2-1-1.md">MSDiagnostics</a></p></td>
<td><p>xs:string</p></td>
<td><p>More info related to the error.</p></td>
</tr>
<tr class="even">
<td><p><a href="msdiagnosticsclient-element-endedproperties-complextype-lync-sdn-interface-2-1-1.md">MSDiagnosticsClient</a></p></td>
<td><p>xs:string</p></td>
<td><p>Info about the error related to and reported by the client.</p></td>
</tr>
<tr class="odd">
<td><p><a href="msdiagnosticspublic-element-endedproperties-complextype-lync-sdn-interface-2-1-1.md">MSDiagnosticsPublic</a></p></td>
<td><p>xs:string</p></td>
<td><p>Public info about the error.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

