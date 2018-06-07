---
title: device/capabilities/breakthrough element
TOCTitle: device/capabilities/breakthrough element
ms:assetid: 2d37f77a-d54a-48c9-bad1-4b945ec9953f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454742(v=office.15)
ms:contentKeyID: 57093629
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# device/capabilities/breakthrough element


**Applies to**: Lync Server 2013

Specifies the device capability to forward calls automatically, also known as breakthrough.

``` xml
<capabilities uri="uri" preferred="boolean" [anyAttr]="anyattr" 
              xmlns="http://schemas.microsoft.com/2006/09/sip/device">
     <breakThrough 
          preferred="boolean" 
          preferredEndpointId="endpointId"
          uri="uri" 
          render="boolean" 
          capture="boolean" 
          publish="boolean"
          version="uint" 
          deviceAvailability="uint" 
          anyAttr="anyattr" />
</capabilities>
```

capabilityType

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
<td><p>Inherited from the preferredType, this optional attribute serves as a Boolean flag to indicate if the specified capability of a given modality is preferred (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="even">
<td><p>preferredEndpointId</p></td>
<td><p>Inherited from the preferredEndpointType type, the optional attribute describes the endpoint Id of the preferred device for display this capability.</p></td>
</tr>
<tr class="odd">
<td><p>uri</p></td>
<td><p>Optional attribute to specify the SIP URI of the user logged in to Microsoft Lync Server 2013 on the device for which the capability is described by this element.</p></td>
</tr>
<tr class="even">
<td><p>render</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the device has a rendering ability for this modality (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="odd">
<td><p>capture</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the device has a capturing ability for this modality (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="even">
<td><p>publish</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the device has a rendering ability for this modality (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="odd">
<td><p>version</p></td>
<td><p>Optional attribute to specify the version number of this publication. The default value is 0.</p></td>
</tr>
<tr class="even">
<td><p>deviceAvailability</p></td>
<td><p>Optional attribute to show the device availability number.</p></td>
</tr>
<tr class="odd">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace</p></td>
</tr>
</tbody>
</table>


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
<td><p><a href="device-capabilities-element.md">device/capabilities element</a></p></td>
<td><p>This is a top-level element as an enhanced presence category instance</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

This element is introduced in the Microsoft Office Communications Server 2007 R2 release.

When a user (such as an administrative assistant) has set his or her VoIP calls to be forwarded to another number, then a breakthrough capability allows calls from people in the user's contact list to go directly to the user's phone without being explicitly forwarded.

## Example

The following XML code snippet describes a presence capability for automatic call forwarding on a device named "BOB\_client".

    <?xml version="1.0" encoding="utf-8" ?>
    <de:device xmlns:de="http://schemas.microsoft.com/2006/09/sip/device" 
               endpointId="3CC22CF7-1BEA-5A5E-B256-E662173CD273">
      <de:capabilities preferred="false" uri="sip:bob@contoso.com">
         <de:breakthrough capture="false" render="true" publish="false" />
      </de:capabilities>
      <de:timezone>00:00:00-07:00</de:timezone>
      <de:machineName>BOB_client</de:machineName>
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

