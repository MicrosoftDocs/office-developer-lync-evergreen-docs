---
title: device/capabilities element
TOCTitle: device/capabilities element
ms:assetid: 005f51a2-2f64-4c3d-abe5-d32927c9d66a
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454741(v=office.15)
ms:contentKeyID: 57093628
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# device/capabilities element


**Applies to**: Lync Server 2013

Describes the presence capabilities of the device.

```xml
<capabilities uri="uri" preferred="boolean" [anyAttr]="anyattr" 
              xmlns="http://schemas.microsoft.com/2006/09/sip/device">
    <CCCP preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean " capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
    <calendar preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
    <remoteCallControll preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
    <voice preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
    <video preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
    <text preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
    <gifInk preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <isfInk preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <breakthrough preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <applicationSharing preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <ucs preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <containerIntegrity preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <contentWhiteboard preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <contentPowerPoint preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <contentNativeFile preferred="boolean" preferredEndpointId="endpointId"
          uri="uri" render="boolean" capture="boolean" publish="boolean"
          version="number" deviceAvailability="number" anyAttr="anyattr" />
     <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
     <any >any</any>
     <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
     <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
         <any >any</any>
     </extension>
</capabilities>
```

capabilitiesType

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
<td><p>preferred</p></td>
<td><p>Optional attribute as a Boolean flag to indicate if the specified capability of a given modality is preferred (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="even">
<td><p>uri</p></td>
<td><p>Required attribute to specify the SIP URI of the user logged in to Microsoft Lync Server 2013 on the device for which the capabilities are described by this element.</p></td>
</tr>
<tr class="odd">
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
<td><p>calendar</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the presence capability for the user’s calendar data on this device.</p></td>
</tr>
<tr class="even">
<td><p>remoteCallControl</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for remote call control on this device.</p></td>
</tr>
<tr class="odd">
<td><p>voice</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for voice calls on this device.</p></td>
</tr>
<tr class="even">
<td><p>video</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for video calls on this device.</p></td>
</tr>
<tr class="odd">
<td><p>CCCP</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for CCCP on this device.</p></td>
</tr>
<tr class="even">
<td><p>text</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for instant messaging on this device.</p></td>
</tr>
<tr class="odd">
<td><p>gifInk</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for GIF images on this device.</p></td>
</tr>
<tr class="even">
<td><p>isfInk</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for ISF images on this device.</p></td>
</tr>
<tr class="odd">
<td><p>breakthrough</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for breakthrough on this device. It is introduced in the Microsoft Office Communications Server 2007 R2 release.</p>
<p>When a user (such as an administrative assistant) has set his or her VoIP calls to be forwarded to another number, then a breakthrough capability allows calls from people in the user's contact list to go directly to the user's phone without being explicitly forwarded.</p></td>
</tr>
<tr class="even">
<td><p>ApplicationSharing</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for application sharing on this device. This is introduced in the Office Communications Server 2007 R2 release.</p></td>
</tr>
<tr class="odd">
<td><p>ucs</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for UCS on this device. This is introduced in the Microsoft Lync Server 2010 release.</p></td>
</tr>
<tr class="even">
<td><p>containerIntegrity</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for container integrity on this device. This is introduced in the Lync Server 2010 release.</p></td>
</tr>
<tr class="odd">
<td><p>contentWhiteboard</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for content sharing with whiteboard on this device. This is introduced in the Lync Server 2010 release.</p></td>
</tr>
<tr class="even">
<td><p>contentNativeFile</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for content sharing using native files on this device. This is introduced in the Lync Server 2010 release.</p></td>
</tr>
<tr class="odd">
<td><p>contentPowerPoint</p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the capability for content sharing with PowerPoint on this device. This is introduced in the Lync Server 2010 release.</p></td>
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
<td><p><a href="device-category-instance-value-element.md">device category instance value element</a></p></td>
<td><p>The device for which the presence capabilities are described by this element.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Example

The following XML code snippet describes a device named "BOB\_client", that is enabled for displaying texts and images, but disabled for capturing or publishing the media.

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

[device category instance value element](device-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

