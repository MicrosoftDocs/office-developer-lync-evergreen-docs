---
title: userInformation/callHandlingLIst/lastPhone element
TOCTitle: userInformation/callHandlingLIst/lastPhone element
ms:assetid: e88a737b-7f7f-4a01-ad33-3896154a2d47
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438955(v=office.15)
ms:contentKeyID: 57093973
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userInformation/callHandlingLIst/lastPhone element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the phone that handled the last call.

``` xml
<ui:lastPhone xmlns:ui="http://schemas.microsoft.com/2006/09/sip/options/userInformation" >
   <ui:displayString>xs:token</ui:displayString>
   <ui:uri>xs:anyURI</ui:uri>
</ui:lastPhone>
```

callHandlingTargetType

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
<td><p>displayString</p></td>
<td><p>0 or more</p></td>
<td><p>A token as the display string of the phone.</p></td>
</tr>
<tr class="even">
<td><p>uri</p></td>
<td><p>0 or 1</p></td>
<td><p>TEL URI of the phone.</p></td>
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
<td><p><a href="userinformation-callhandlinglist-element.md">userInformation/callHandlingList element</a></p></td>
<td><p>The phone list containing this phone.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Example

The following XML snippet shows a userInformation category instance value containing two types (work and mobile) of phone numbers

``` xml
<userInformation xmlns="http://schemas.microsoft.com/2006/09/sip/options/userInformation">
    <callHandlingList>
       <lastPhone>
           <displayString>+12063334444</displayString>
           <uri>tel:+12063334444</uri>
       </lastPhone>
   </callHandlingList>
   <phones>
       <phone type="work">
           <readOnly>true</readOnly>
           <displayString>+1 (425) 1113872 X13872</displayString>
           <uri>tel:+14251113872;ext=13872</uri>
       </phone>
       <phone type="mobile">
           <displayString>+12062221115</displayString>
           <uri>tel:+12062221115</uri>
       </phone>
       <phone type="home"></phone>
       <phone type="other"></phone>
   </phones>
</userInformation>
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
<td><p>http://schemas.microsoft.com/2006/09/sip/options/userInformation</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>Options-UserInformation</p></td>
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

