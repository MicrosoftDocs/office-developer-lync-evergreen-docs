---
title: Route element (MessageType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Route element (MessageType complexType)
ms:assetid: 73a104e6-8bbc-5bf4-c801-32ac573a70f3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912814(v=office.15)
ms:contentKeyID: 64126983
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Route element (MessageType complexType) (Lync SDN Interface 2.1.1)

Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.


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
<td><p><a href="routetype-complextype-lync-sdn-interface-2-1-1.md">RouteType</a></p></td>
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

    <xs:element name="Route"  type="RouteType" minOccurs="0">
    
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
<td><p><a href="hop-element-routetype-complextype-lync-sdn-interface-2-1-1.md">Hop</a></p></td>
<td><p>xs:string</p></td>
<td><p>IP address of one hop (router, gateway, switch, etc) on the path from the source to the destination of the media stream.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

