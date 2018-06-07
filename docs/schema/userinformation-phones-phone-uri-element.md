---
title: userInformation/phones/phone/uri element
TOCTitle: userInformation/phones/phone/uri element
ms:assetid: 75a48734-b367-42c9-8f51-31fd6ad537bc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438981(v=office.15)
ms:contentKeyID: 57094042
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userInformation/phones/phone/uri element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the TEL URI of a phone in the user’s phone list.

``` xml
<ui:uri xmlns:ui="http://schemas.microsoft.com/2006/09/sip/options/userInformation" 
       updated="xs:dateTime"
       [anyAttri]="anyAttribute">xs:updatedAnyURI</ui: uri >
```

ui:updatedAnyURI

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
<td><p>updated</p></td>
<td><p>Optional attribute as the time and date when the publication was last updated.</p></td>
</tr>
<tr class="even">
<td><p>[anyAttr]</p></td>
<td><p>Optional custom attribute of any name and namespace.</p></td>
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
<td><p><a href="userinformation-phones-phone-element.md">userInformation/phones/phone element</a></p></td>
<td><p>An item of the user’s phone list.</p></td>
</tr>
</tbody>
</table>


## Text value

A string

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

