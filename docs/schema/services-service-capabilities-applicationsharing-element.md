---
title: services/service/capabilities/applicationSharing element
TOCTitle: services/service/capabilities/applicationSharing element
ms:assetid: 439a0b42-795d-4fee-bb84-580b5760b08b
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454784(v=office.15)
ms:contentKeyID: 57093671
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# services/service/capabilities/applicationSharing element


**Applies to**: Lync Server 2013

Specifies the presence capability for a presentity to participate in application-sharing.

```xml
<capabilities uri="uri" preferred="boolean" [anyAttr]="anyattr" 
              xmlns="http://schemas.microsoft.com/2006/09/sip/service">
     <applicationSharing 
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
<td><p>Inherited from the preferredType, this optional attribute serves as a Boolean flag to indicate if this capability is preferred (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="even">
<td><p>preferredEndpointId</p></td>
<td><p>Inherited from the preferredEndpointType type, the optional attribute specifies the preferred device that supports this capability.</p></td>
</tr>
<tr class="odd">
<td><p>uri</p></td>
<td><p>Optional attribute to specify the SIP URI used to sign in to Microsoft Lync Server 2013.</p></td>
</tr>
<tr class="even">
<td><p>render</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the specified presentity can render this type of presence data (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="odd">
<td><p>capture</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the specified presentity can capture this type of presence data (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="even">
<td><p>publish</p></td>
<td><p>Optional attribute as a Boolean flag to indicate whether the specified presentity can publish this type of presence data (true) or not (false). The default value is false.</p></td>
</tr>
<tr class="odd">
<td><p>version</p></td>
<td><p>Optional attribute to specify the version number of this publication. The default value is 0.</p></td>
</tr>
<tr class="even">
<td><p>deviceAvailability</p></td>
<td><p>Optional attribute to show the availability number of the reachable device supporting this capability.</p></td>
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
<td><p><a href="services-service-capabilities-element.md">services/service/capabilities element</a></p></td>
<td><p>This is the set of the presence capabilities of the specified presentity.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Example

The following XML code snippet describes a service capability to handle application-sharing for the user, sip:alice@contoso.com.

    <se:service xmlns:se="http://schemas.microsoft.com/2006/09/sip/service">
      <se:capabilities>
        <se:applicationSharing uri="sip:alice@contoso.com" render="true" publish="true" />
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

[device/capabilities element](device-capabilities-element.md)

[services/service element](services-service-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

