---
title: device category instance value element
TOCTitle: device category instance value element
ms:assetid: 3a24bbc7-8a97-4a4f-877f-239c4768b984
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454740(v=office.15)
ms:contentKeyID: 57093627
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# device category instance value element


**Applies to:** Lync 2013 | Lync Server 2013

Contains the information of the device, including the supported presence capabilities, with which the user logs in to Microsoft Lync Server 2013.

``` xml
<device xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns="http://schemas.microsoft.com/2006/09/sip/device"
    endpointId="xs:string"
    majorVersion="xs:unsignedInt"
    minorVersion="xs:unsignedInt"
    anyAttr="any"> 
    <capabilities uri="uri" preferred="boolean" [anyAttr]="anyattr">
       <!-- various child elements of the capabilityType in this namespace--!>
    </capabilities>
    <timezone>xs:time</timezone>
    <machineName>xs:string</machineName>
    <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <any xmlns="any_namespace">any</any>
    </ct:extension>
    <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <any xmlns="http://schemas.microsoft.com/2006/09/sip/device">any element</any>
    <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</device>
```

deviceType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Attribute</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>endpointId</p></td>
<td><p>Required attribute to specify the endpoint Id of the device.</p></td>
</tr>
<tr class="even">
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent major version information.</p></td>
</tr>
<tr class="odd">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent minor version information.</p></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace</p></td>
</tr>
</tbody>
</table>


#### Child elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Occurrence</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>capabilities</p></td>
<td><p>1 ore more</p></td>
<td><p>Presence capabilities of the device.</p></td>
</tr>
<tr class="even">
<td><p>machineName</p></td>
<td><p>1</p></td>
<td><p>Machine name of the device.</p></td>
</tr>
<tr class="odd">
<td><p>timezone</p></td>
<td><p>1</p></td>
<td><p>Time zone time when the device becomes active.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-dependent custom extension.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A marker to begin a version-dependent schema extension.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Custom element of any name in the same namespace describing a schema extension to this element. This element must be enclosed between a delimiter element and an end element or between a two delimiter elements.</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The marker to end all the schema versions.</p></td>
</tr>
</tbody>
</table>


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
<td><p>None</p></td>
<td><p>This is a top-level element as an enhanced presence category instance</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Example

The following XML code snippet describes a device named "BOB\_client", capable of displaying texts and images, disabled for capturing or publishing the said media.

    <?xml version="1.0" encoding="utf-8" ?>
    <de:device xmlns:de="http://schemas.microsoft.com/2006/09/sip/device" 
               endpointId="3CC22CF7-1BEA-5A5E-B256-E662173CD273">
      <de:capabilities preferred="false" uri="sip:bob@contoso.com">
        <de:text capture="false" render="boolean" publish="false" />
        <de:gifInk capture="false" render="boolean" publish="false" />
        <de:isfInk capture="false" render="boolean" publish="false" />
      </de:capabilities>
      <de:timezone>00:00:00-07:00</de:timezone>
      <de:machineName>BOB_client</de:machineName>
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

[Category instance elements for presence](category-instance-elements-for-presence.md)

