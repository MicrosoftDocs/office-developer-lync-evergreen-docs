---
title: services/service/capabilities/contentPowerPoint element
TOCTitle: services/service/capabilities/contentPowerPoint element
ms:assetid: d46e1cdb-342d-4f62-a9a6-5e4ed143b1f5
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454803(v=office.15)
ms:contentKeyID: 57093892
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# services/service/capabilities/contentPowerPoint element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the capability of a presentity to share content using PowerPoint. This is introduced in the Microsoft Lync Server 2010 release.

``` xml
<capabilities uri="uri" preferred="boolean" [anyAttr]="anyattr" 
              xmlns="http://schemas.microsoft.com/2006/09/sip/service">     <contentPowerPoint 
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
<td><p>Optional attribute to specify the SIP URI of the user logged in to Microsoft Lync Server 2013 for which the capability is described by this element.</p></td>
</tr>
<tr class="even">
<td><p>render</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the presentity has a rendering ability for this modality (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="odd">
<td><p>capture</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the presentity has a capturing ability for this modality (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="even">
<td><p>publish</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the presentity has a rendering ability for this modality (true) or not (false). The default value is false.</p></td>
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

## Example

The following XML code snippet describes a presence capability for a presentity to share content in PowerPoint

    <?xml version="1.0" encoding="utf-8" ?>
    <se:service xmlns:se="http://schemas.microsoft.com/2006/09/sip/service" >
      <se:capabilities preferred="false" uri="sip:bob@contoso.com">
         <se:contentPowerPoint capture="false" render="true" publish="false" />
      </se:capabilities>
    </se:service>

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/service</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>service</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>service.xsd, servicetypes.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[services/service element](services-service-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

