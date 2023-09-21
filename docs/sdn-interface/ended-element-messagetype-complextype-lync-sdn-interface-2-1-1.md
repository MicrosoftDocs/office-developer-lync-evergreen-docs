---
title: Ended element (MessageType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Ended element
ms:assetid: b62db6fd-429d-c840-ac63-e9f2a8fec9b4
ms:mtpsurl: https://msdn.microsoft.com/library/Dn912727(v=office.15)
ms:contentKeyID: 64126900
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Ended element 

(MessageType complexType) (Lync SDN Interface 2.1.1)

Event that a Sip call has ended and all media stream terminated.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p><a href="endedtype-complextype-lync-sdn-interface-2-1-1.md">EndedType</a></p></td>
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

    <xs:element name="Ended"  type="EndedType">
    
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
<td><p><a href="endpoint-element-endedtype-complextype-lync-sdn-interface-2-1-1.md">EndPoint</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="even">
<td><p><a href="from-element-endedtype-complextype-lync-sdn-interface-2-1-1.md">From</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
</tr>
<tr class="odd">
<td><p><a href="properties-element-endedtype-complextype-lync-sdn-interface-2-1-1.md">Properties</a></p></td>
<td><p><a href="endedproperties-complextype-lync-sdn-interface-2-1-1.md">EndedProperties</a></p></td>
<td><p>Properties of the Error.</p></td>
</tr>
<tr class="even">
<td><p><a href="to-element-endedtype-complextype-lync-sdn-interface-2-1-1.md">To</a></p></td>
<td><p><a href="endpointtype-complextype-lync-sdn-interface-2-1-1.md">EndPointType</a></p></td>
<td><p>Endpoint involved in the ended SIP call.</p></td>
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
<td><p>Type</p></td>
<td><p>xs:string</p></td>
<td><p>required</p></td>
<td><p>Modality or media type for which the quality metrics are reported. The supported options are audio, video and applicationsharing.</p></td>
<td><p>Values of the xs:string type.</p></td>
</tr>
</tbody>
</table>

