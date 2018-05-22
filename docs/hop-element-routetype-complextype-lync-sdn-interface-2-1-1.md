---
title: Hop element (RouteType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Hop element
ms:assetid: aecbf57a-9223-77e7-84c2-f0af417de118
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912741(v=office.15)
ms:contentKeyID: 64126911
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Hop element (RouteType complexType) (Lync SDN Interface 2.1.1)

IP address of one hop (router, gateway, switch, etc) on the path from the source to the destination of the media stream.


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
<td><p>xs:string</p></td>
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

    <xs:element name="Hop"  type="xs:string" maxOccurs="unbounded">
    
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
<td><p><a href="route-element-qualitytype-complextype-lync-sdn-interface-2-1-1.md">Route</a></p></td>
<td><p><a href="routetype-complextype-lync-sdn-interface-2-1-1.md">RouteType</a></p></td>
<td><p>Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.</p></td>
</tr>
<tr class="even">
<td><p><a href="route-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Route</a></p></td>
<td><p><a href="routetype-complextype-lync-sdn-interface-2-1-1.md">RouteType</a></p></td>
<td><p>Network path of the media stream only provided in Lync 2013 and when the traceRoute feature is activated in Lync.</p></td>
</tr>
</tbody>
</table>


### Child elements

None.

### Attributes

None.

