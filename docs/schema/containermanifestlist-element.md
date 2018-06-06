---
title: containerManifestList element
TOCTitle: containerManifestList element
ms:assetid: bfe32929-7791-47f3-9032-e367a9867068
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438980(v=office.15)
ms:contentKeyID: 57094024
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# containerManifestList element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies a container manifest that prescribes container semantics for grammar-based publication.

``` xml
<containerManifestList xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
     xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
     minSupportedClientVersion="2.0.0.0" 
     xmlns="http://schemas.microsoft.com/2008/09/sip/ContainerManifest">
   <containerManifest>...</ containerManifest >
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...</ct:extension>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
   <[any>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
</containerManifestList>
```

containerManifestListType

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
<td><p>minSupportedClientVersion</p></td>
<td><p>A token of the xs:token type specifying the earliest version of Microsoft Lync 2013 that supports this feature. Different versions indicate that the container manifest format is not compatible.</p></td>
</tr>
<tr class="even">
<td><p>majorVersion</p></td>
<td><p>An unsigned integer of the (xs:unsignedInt) type to specify the major version of the schema defining this element.</p></td>
</tr>
<tr class="odd">
<td><p>minorVersion</p></td>
<td><p>An unsigned integer of the (xs:unsignedInt) type to specify the minor version of the schema defining this element.</p></td>
</tr>
<tr class="even">
<td><p>[anyAttribute]</p></td>
<td><p>Any attribute</p></td>
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
<td><p><a href="containermanifest-element.md">containerManifest element</a></p></td>
<td><p>1</p></td>
<td><p>A manifest specifying prescribed container semantics.</p></td>
</tr>
<tr class="even">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A marker to begin a version-dependent schema extension.</p></td>
</tr>
<tr class="odd">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Any element in the namespace of the parent element, specifying the extension to the parent element introduced in a particular version of the schema.</p></td>
</tr>
<tr class="even">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The marker to end all the schema extensions.</p></td>
</tr>
<tr class="odd">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-specified extension to the parent element.</p></td>
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
<td><p>This is the top-level element that holds the container manifests as part of the prescribed publication grammar.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

A container manifest specifies which containers can be used in a grammar-based publication. It also specifies the meaning of each of the containers. Container manifest is obtainable via in-band provisioning. In UCMA, this involves reading the LocalEndpoint.ContainerManifest property. For more information about publication grammar, see the [Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md) topic.

## Example

The following is the container manifest prescribed by Lync 2013 and provisioned from Lync Server 2013.

``` xml
  <containerManifestList xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
       xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
       minSupportedClientVersion="2.0.0.0" 
       xmlns="http://schemas.microsoft.com/2008/09/sip/ContainerManifest">
    <containerManifest>
      <containers>
        <container id="0">
          <visible>false</visible> 
          <avoidRedundantMembers>false</avoidRedundantMembers> 
        </container>
        <container id="100">
          <visible>true</visible> 
          <avoidRedundantMembers>true</avoidRedundantMembers> 
        </container>
        <container id="200">
          <visible>true</visible> 
          <avoidRedundantMembers>true</avoidRedundantMembers> 
        </container>
        <container id="300">
          <visible>true</visible> 
          <avoidRedundantMembers>true</avoidRedundantMembers> 
        </container>
        <container id="400">
          <visible>true</visible> 
          <avoidRedundantMembers>true</avoidRedundantMembers> 
        </container>
        <container id="32000">
          <visible>true</visible> 
          <avoidRedundantMembers>false</avoidRedundantMembers> 
          <blocked>true</blocked> 
        </container>
      </containers>
      <members>
        <member role="buddy">
          <allowedContainers type="visibleContainers" /> 
          <defaultContainer id="100" /> 
          <occurrenceConstraint type="one" /> 
          <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
          <sourceNetworks>
            <sourceNetwork type="publicCloud" /> 
            <sourceNetwork type="federated" /> 
          </sourceNetworks>
          <resolutionRules>
            <resolutionRule type="moveToDefaultContainer" /> 
          </resolutionRules>
          <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
        </member>
        <member role="buddy">
          <allowedContainers type="visibleContainers" /> 
          <defaultContainer id="200" /> 
          <occurrenceConstraint type="one" /> 
          <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
          <sourceNetworks>
            <sourceNetwork type="sameEnterprise" /> 
          </sourceNetworks>
          <resolutionRules>
            <resolutionRule type="moveToDefaultContainer" /> 
          </resolutionRules>
          <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
        </member>
        <member type="sameEnterprise">
          <allowedContainers type="visibleContainers" /> 
          <defaultContainer id="200" /> 
          <occurrenceConstraint type="one" /> 
        </member>
        <member type="federated">
          <allowedContainers type="visibleContainers" /> 
          <defaultContainer id="100" /> 
          <occurrenceConstraint type="one" /> 
        </member>
        <member type="publicCloud">
          <allowedContainers type="visibleContainers" /> 
          <occurrenceConstraint type="zeroOrOne" /> 
        </member>
        <member role="delegate">
          <allowedContainers type="custom">
            <container id="300" /> 
          </allowedContainers>
          <defaultContainer id="300" /> 
          <occurrenceConstraint type="one" /> 
          <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
          <resolutionRules>
            <resolutionRule type="moveToDefaultContainer" /> 
          </resolutionRules>
          <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
        </member>
      </members>
      <delimiter xmlns="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
      <blockRules>
        <blockRule type="invites">
          <containers type="custom">
            <container id="0" /> 
          </containers>
          <sourceNetworks>
            <sourceNetwork type="publicCloud" /> 
          </sourceNetworks>
        </blockRule>
        <blockRule type="invites">
          <maxAvailability>11999</maxAvailability> 
          <minAvailability>9000</minAvailability> 
        </blockRule>
        <blockRule type="invites">
          <containers type="custom">
            <container id="32000" /> 
          </containers>
        </blockRule>
        <blockRule type="subscriberPrompt">
          <containers type="custom">
            <container id="32000" /> 
          </containers>
        </blockRule>
      </blockRules>
      <rolePrecedence>
        <rolePrecedenceEntry type="delegate" /> 
        <rolePrecedenceEntry type="buddy" /> 
      </rolePrecedence>
      <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" /> 
    </containerManifest>
  </containerManifestList>
```

In this example, six containers are used in grammar-based publication. These are specified in the [containers element](containers-element.md) element. The Ids of these containers are 0, 100, 200, 300, 400, and 32000. Container 0 is not visible and can have redundant membership specifications. Container 32000 is visible and blocked. It can also have redundant membership specification. The other containers are all visible.

Members of various types and roles are specified in the [members element](members-element.md) element. The membership type includes sameEnterprise, federated, and publicCloud. The membership role includes buddy and delegate. A member can be assigned to a list of allowed containers and a default container.

Also, a set of block rules are applied to Container 0 and 32000. They are used to block incoming calls (invites) and disable subscriber alerts.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2008/09/sip/ContainerManifest</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>ContainerManifest</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>ContainerManifestSchema.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[Category instance elements for publication grammar](category-instance-elements-for-publication-grammar.md)

#### Concepts

[Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)

