---
title: userProperties/acpInformation element
TOCTitle: userProperties/acpInformation element
ms:assetid: 5d31a364-930f-4fc0-825e-d13ada23112e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438974(v=office.15)
ms:contentKeyID: 57094019
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userProperties/acpInformation element


_**Applies to:** Lync Server 2013_

Contains the information of the audio conference provider for the user

``` xml
<up:acpInformation xmlns:up="http://schemas.microsoft.com/2006/09/sip/categories" 
       default="xs:boolean" 
       [anyAttri]="anyAttribute">
   <up:tollNumber>xs:token</up:tollNumber>
   <up:tollFreeNumber>xs:token</up:tollFreeNumber>
   <up:participantPassCode>xs:token</up:participantPassCode>
   <up:leaderPassCode>xs:token</up:leaderPassCode>
   <up:domain>xs:token</up:domain>
   <up:name>xs:token</up:name>
   <up:url>xs:anyURI</up:url>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"/>
   <up:[any]>any element of this schema namespace.</up:[any]>
   <ct:end/>
   <ct:extension>any elements of any namespace</ct:extension>
</up:acpInformation>
```

acpProvisionType

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
<td><p>default</p></td>
<td><p>Required attribute of the xs:Boolean type to indicate if this ACP is the default provide for the user (true) or not (false).</p></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace.</p></td>
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
<td><p>Up:tollNumber</p></td>
<td><p>1</p></td>
<td><p>A simple element containing a value of the xs:token type to specify the toll number to connect to this ACP.</p></td>
</tr>
<tr class="even">
<td><p>up:tollFreeNumber</p></td>
<td><p>0 or more</p></td>
<td><p>A simple element containing a value of the xs:token type to specify the toll-free number to connect to this ACP.</p></td>
</tr>
<tr class="odd">
<td><p>Up:participantPassCode</p></td>
<td><p>1</p></td>
<td><p>A simple element containing a value of the xs:token type to specify the participant passcode required to connect to this ACP.</p></td>
</tr>
<tr class="even">
<td><p>up:leaderPassCode</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple element containing a value of the xs:token type to specify the leader passcode required to connect to this ACP.</p></td>
</tr>
<tr class="odd">
<td><p>up:domain</p></td>
<td><p>1</p></td>
<td><p>A simple element containing a value of the xs:token type to specify the domain of this ACP.</p></td>
</tr>
<tr class="even">
<td><p>up:name</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple element containing a value of the xs:token type to specify the name of this ACP.</p></td>
</tr>
<tr class="odd">
<td><p>up:url</p></td>
<td><p>0 or 1</p></td>
<td><p>A simple element containing a value of the xs:anyURI type to specify the URI of this ACP.</p></td>
</tr>
<tr class="even">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker of a schema extension to this element.</p></td>
</tr>
<tr class="odd">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Any element of the same namespace as a schema extension.</p></td>
</tr>
<tr class="even">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The ending marker of all the schema extensions to this element.</p></td>
</tr>
<tr class="odd">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-specific custom extension that contain any elements of any namespace.</p></td>
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
<td><p><a href="userproperties-category-instance-value-element.md">userProperties category instance value element</a></p></td>
<td><p>A userProperties category instance value containing an entry about this ACP.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

When an ACP allows more one set of passcodes or when more than one ACP is configured for a given user, this element occurs multiple times.

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/categories</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>userProperties</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>userProperties.xsd</p></td>
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

[userProperties category instance value element](userproperties-category-instance-value-element.md)

#### Concepts

[Self container](self-container.md)

