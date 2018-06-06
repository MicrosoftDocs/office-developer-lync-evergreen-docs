---
title: userInformation/phones/phone element
TOCTitle: userInformation/phones/phone element
ms:assetid: 1cc5d9f4-4e6e-4629-a723-7d2aec4a2400
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438976(v=office.15)
ms:contentKeyID: 57094021
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userInformation/phones/phone element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies a phone line made available to reach the user.

``` xml
<ui:phone xmlns:ui="http://schemas.microsoft.com/2006/09/sip/options/userInformation" 
       type="ui:phoneTypeEnumEx" 
       [anyAttri]="anyAttribute">
   <ui:publish>xs:boolean</ui:publish>
   <ui:readOnly>xs:boolean</ui:readOnly>
   <ui:displayString 
       LCID="xs:unsignedInt" 
       updated="xs:dateTime"
       [anyAttribute]="any_Attribute">xs:string </ui:displayString>
   <ui:uri updated="xs:dateTime"
       [anyAttribute]="any_Attribute">xs:anyURI</ui:uri>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <[any]>any element</[any]>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...<ct:extension>
</ui:phone>
```

phoneInformationType

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
<td><p>type</p></td>
<td><p>Required attribute to specify the type of a phone. The attribute value is a token or string of the phoneTypeEnumEx type. Microsoft Lync 2013 recognizes the following phone type tokens: work, home, mobile, other, and custom1.</p></td>
</tr>
<tr class="even">
<td><p>[anyAttribute]</p></td>
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
<td><p>publish</p></td>
<td><p>1</p></td>
<td><p>A Boolean flag to specify whether to publish the phone information (true) or not (false). The default is true.</p></td>
</tr>
<tr class="even">
<td><p>readOnly</p></td>
<td><p>0 or 1</p></td>
<td><p>A Boolean flag to specify whether the phone number is derived from the underlying Active Directory and thus cannot be modified in the <strong>Lync - Options</strong> dialog box. Select (true) or (false). The default is false.</p></td>
</tr>
<tr class="odd">
<td><p><a href="userinformation-phones-phone-displaystring-element.md">userInformation/phones/phone/displayString element</a></p></td>
<td><p>0 or more</p></td>
<td><p>The display string of the phone.</p></td>
</tr>
<tr class="even">
<td><p><a href="userinformation-phones-phone-uri-element.md">userInformation/phones/phone/uri element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>TEL URI of the phone.</p></td>
</tr>
<tr class="odd">
<td><p><a href="delimiter-element.md">delimiter element</a></p></td>
<td><p>0 or more</p></td>
<td><p>A beginning marker of a schema extension to this element.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>Any element of the same namespace as a schema extension.</p></td>
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
<td><p><a href="userinformation-phones-element.md">userInformation/phones element</a></p></td>
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

