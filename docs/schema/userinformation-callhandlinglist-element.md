---
title: userInformation/callHandlingList element
TOCTitle: userInformation/callHandlingList element
ms:assetid: 39b98666-1fe1-4824-aaba-cadfddf2e635
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454810(v=office.15)
ms:contentKeyID: 57093954
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userInformation/callHandlingList element


**Applies to**: Lync Server 2013

Specifies a list of call-handling targets. These options are set in the Microsoft Lync 2013 **Lync Options** dialog box.

```xml
<ui:callHandlingList xmlns:ui="http://schemas.microsoft.com/2006/09/sip/options/userInformation" >
   <ui:lastPhone>Zero or more phone elements</ui:displayString>
   <ui:lastContact>Zero or more contacts handling the listed phones</ui:uri>
</ui:callHandlingList>
```

callHandlingListType

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

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
<td><p><a href="userinformation-callhandlinglist-lastphone-element.md">userInformation/callHandlingLIst/lastPhone element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The phone that handled the last call.</p></td>
</tr>
<tr class="even">
<td><p><a href="userinformation-callhandlinglist-lastcontact-element.md">userInformation/callHandlingList/lastContact element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The contact that handled the last call.</p></td>
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
<td><p><a href="userinformation-category-instance-value-element.md">userInformation category instance value element</a></p></td>
<td><p>The userInformation category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/options/userInformation</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>Options-userInformation</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>Options-UserInformation.xsd, Options-UserInformationtypes.xsd</p></td>
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

[userInformation category instance value element](userinformation-category-instance-value-element.md)

#### Concepts

[Self container](self-container.md)

