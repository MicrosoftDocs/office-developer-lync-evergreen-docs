---
title: userInformation/phones element
TOCTitle: userInformation/phones element
ms:assetid: 9adc496c-835c-45ae-81b2-d8738fd4b3ab
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438971(v=office.15)
ms:contentKeyID: 57094016
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userInformation/phones element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the list of optional phone lines made available to reach the user. The options are set in the Microsoft Lync 2013 **Lync Options** dialog box.

``` xml
<ui:phones xmlns:ui="http://schemas.microsoft.com/2006/09/sip/options/userInformation" >
   <ui:phones>Zero or more phone elements</ui:phones>
   <ui:callHandlingList>Zero or more targets to handle the listed phones</ui:callHandlingList>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <[any]>any element</[any]>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...<ct:extension>
</ui:phones>
```

userInformationType

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
<td><p>majorVersion</p></td>
<td><p>Optional attribute to specify major version information. The default value is unspecified.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify minor version information. The default value is unspecified.</p></td>
</tr>
<tr class="odd">
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
<td><p><a href="userinformation-phones-element.md">userInformation/phones element</a></p></td>
<td><p>1</p></td>
<td><p>A list of phone numbers a user can choose to make available to others.</p></td>
</tr>
<tr class="even">
<td><p><a href="userinformation-callhandlinglist-element.md">userInformation/callHandlingList element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>A list of handlers for listed phone lines.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker of a schema extension to this element.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Schema extension</p></td>
</tr>
<tr class="odd">
<td><p><a href="end-element.md">end element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>The ending marker of all the schema extensions to this element.</p></td>
</tr>
<tr class="even">
<td><p><a href="extension-element.md">extension element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Application-specific custom extension.</p></td>
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

## Remarks

The userInformation category instance represents the options that can be set by a user to share his or her phone numbers and to configure how calls may be handled. Lync 2013 publishes this type of category instances to the [Self container](self-container.md) only.

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

