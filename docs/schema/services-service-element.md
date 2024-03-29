﻿---
title: services/service element
TOCTitle: services/service element
ms:assetid: 3d28aa35-3dc9-417f-a819-4c506d506ab8
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454790(v=office.15)
ms:contentKeyID: 57093706
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# services/service element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies a presence service enabled for a presentity.

```xml
<service 
    xmlns="http://schemas.microsoft.com/2006/09/sip/service"
    uri="xs:anyURI"
    [anyAttr]="any attribute" >
    <service>1 or more</service>
    <extension xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes">
        <[any]>Custom extension</any>
    </extension>
    <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
    <[any]>A schema extension to this element</any>
    <end xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</services>
```

serviceType

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
<td><p>uri</p></td>
<td><p>Required attribute to specify the presentity for which the contained presence capabilities are enabled. For a SIP URI, the presence service is provided by Microsoft Lync Server 2013. For a SMTP address, the presence service is provided by the integrated Exchange Server.</p></td>
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
<td><p>0 or 1</p></td>
<td><p>Contains a specification of a particular presence service.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-dependent custom extension to this element.</p></td>
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
<td><p>The marker to end all the schema extensions.</p></td>
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
<td><p>This is a top-level element as the value of an enhanced presence category instance for presence services.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

A service property of a services category instance describes a list of presence capabilities enabled for the specified user (or presentity) as identified by the uri attribute of the service element. For a Lync Server 2013-based presence store, the uri attribute value is a SIP URI. For an Exchange Server-based presence store, the uri value is a SMTP address.

In contrast, a device category instance describes a list of presence capabilities enabled on the device as identified by the endpointId attribute.

Communicator only publishes the device category instances for local use and publishes services category instance generated by the Aggregation Script for public consumption.

## Example

The following XML snippet shows a services category instance containing a specification of a presence service that is enabled for the administrator at contoso.com (sip:administrator@contoso.com) and supports instant messages rendering and capturing as well as GIF and ISF image rendering.

``` 
  <services xmlns="http://schemas.microsoft.com/2006/09/sip/service">
    <service uri="sip:administrator@contoso.com">
      <capabilities>
        <text render="true" capture="true" deviceAvailability="3500" />
        <gifInk render="true" capture="false" deviceAvailability="3500" />
        <isfInk render="true" capture="false" deviceAvailability="3500" />
      </capabilities>
    </service> 
  </services>
```

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
<td><p>service.xsd</p></td>
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

[device category instance value element](device-category-instance-value-element.md)

