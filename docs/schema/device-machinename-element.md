---
title: device/machineName element
TOCTitle: device/machineName element
ms:assetid: 42fc1333-13a0-4ea6-955c-6b57be9f69b0
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454737(v=office.15)
ms:contentKeyID: 57093591
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# device/machineName element


**Applies to:** Lync 2013 | Lync Server 2013

Holds the name of the device.

```xml
```

xs:string

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

#### Child elements

None

#### Parent elements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="device-category-instance-value-element.md">device category instance value element</a></p></td>
<td><p>The device for which the presence capabilities are described by this element.</p></td>
</tr>
</tbody>
</table>


## Text value

A string of a machine name.

## Example

The following XML code snippet describes a device named "BobClient", that is enabled for displaying texts and images, but disabled for capturing or publishing the media.

    <?xml version="1.0" encoding="utf-8" ?>
    <de:device xmlns:de="http://schemas.microsoft.com/2006/09/sip/device" 
               endpointId="3CC22CF7-1BEA-5A5E-B256-E662173CD273">
      <de:capabilities preferred="false" uri="sip:bob@contoso.com">
        <de:text capture="false" render="true" publish="false" />
        <de:gifInk capture="false" render="true" publish="false" />
        <de:isfInk capture="false" render="true" publish="false" />
      </de:capabilities>
      <de:timezone>00:00:00-07:00</de:timezone>
      <de:machineName>BobClient</de:machineName>
      <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
      <de:any>a version-specific schema extension</de:any>
      <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
      <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >
         <other:any xmlns:other="any-name-space">custom extension</other:any>
      </ct:extension>
    </device>

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/device</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>device</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>device.xsd, devicetypes.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[device category instance value element](device-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

