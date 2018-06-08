---
title: SourcePool element (ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)
TOCTitle: SourcePool element
ms:assetid: 3e85ad2e-50ed-98ff-2348-25bd51e4d5ba
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn912818(v=office.15)
ms:contentKeyID: 64126987
ms.date: 02/16/2015
mtps_version: v=office.15
dev_langs:
- xml
---

# SourcePool element 

(ConnectionInfoType complexType) (Lync SDN Interface 2.1.1)

Name of the Lync/Skype pool this message originated. If a QualityUpdate message is merged and originated from two pools only one is included here. Currently, the FQDN of one sourcepool is provided, expect a comma delimited list in future releases.

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

```xml

    <xs:element name="SourcePool"  type="xs:string" minOccurs="0">
    
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

