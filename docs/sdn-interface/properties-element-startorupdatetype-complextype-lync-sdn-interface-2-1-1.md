---
title: Properties element (StartOrUpdateType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: Properties element (StartOrUpdateType complexType)
ms:assetid: 28542efe-dad5-fe1c-7ba5-7f2b81696efd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912783(v=office.15)
ms:contentKeyID: 64126952
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (StartOrUpdateType complexType) (Lync SDN Interface 2.1.1)

Properties of the started or updated media stream.


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
<td><p><a href="startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">StartPropertiesType</a></p></td>
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

    <xs:element name="Properties"  type="StartPropertiesType" minOccurs="0">
    
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
<td><p><a href="start-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Start</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream is started. Every Start element contains a report about a particular media stream. This event is raised when the call is established, i.e., when the call is picked up and the SIP INVITE is answered with a 200 OK response.</p></td>
</tr>
<tr class="even">
<td><p><a href="update-element-messagetype-complextype-lync-sdn-interface-2-1-1.md">Update</a></p></td>
<td><p><a href="startorupdatetype-complextype-lync-sdn-interface-2-1-1.md">StartOrUpdateType</a></p></td>
<td><p>Event that a media stream previously started has been updated. This event is raised when an update to core parameters of call have changed and the change is established, i.e., when the request is answered with a 200 OK response.</p></td>
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
<td><p><a href="bandwidth-element-startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">Bandwidth</a></p></td>
<td><p><a href="bandwidthtype-complextype-lync-sdn-interface-2-1-1.md">BandwidthType</a></p></td>
<td><p>Describes the maximum and average amount of bandwidth needed by this stream. It takes the possible codecs and stream multiplexing into account.</p></td>
</tr>
<tr class="even">
<td><p><a href="codec-element-startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">Codec</a></p></td>
<td><p><a href="codectype-complextype-lync-sdn-interface-2-1-1.md">CodecType</a></p></td>
<td><p>Codec and estimates for the bandwidth that the codecs will use. This list contains all codecs that are agreed upon by the two endpoints. Both end-points may decide to switch among these codecs at any time (without additional signalling).</p></td>
</tr>
<tr class="odd">
<td><p><a href="protocol-element-startpropertiestype-complextype-lync-sdn-interface-2-1-1.md">Protocol</a></p></td>
<td><p>xs:string</p></td>
<td><p>Transmission protocol of the media stream such as TCP or UDP.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

