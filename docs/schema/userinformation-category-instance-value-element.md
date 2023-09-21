---
title: userInformation category instance value element
TOCTitle: userInformation category instance value element
ms:assetid: 45bdddee-1d80-49b7-b3a3-0535b3e9f261
ms:mtpsurl: https://msdn.microsoft.com/library/Dn438978(v=office.15)
ms:contentKeyID: 57094025
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userInformation category instance value element


**Applies to**: Lync Server 2013

Specifies the list of optional phone lines made available to reach the user. These options are specified in the Microsoft Lync 2013 **Lync Options** dialog box.

```xml
<ui:userInformation xmlns:ui="http://schemas.microsoft.com/2006/09/sip/options/userInformation" 
       majorVersion="xs:unsignedInt" 
       minorVersion="xs:unsignedInt"
       [anyAttri]="anyAttribute">
   <ui:phones>Zero or more phone elements</ui:phones>
   <ui:callHandlingList>Zero or more targets to handle the listed phones</ui:callHandlingList>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <[any]>any element</[any]>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...<ct:extension>
</ui:userInformation>
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
<td><p>Optional attribute of the xs:unsignedInt type to specify the major version number of this category instance value element.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute of the xs:unsignedInt type to specify minor version number.</p></td>
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
<td><p>ct:delimiter</p></td>
<td><p>0 or more</p></td>
<td><p>An empty element, of the CommonTypes (ct) namespace, to mark the start of a schema extension to its parent element. Elements describing the extension are enclosed between a ct:delimiter and ct:end elements or between two ct:delimiter elements.</p></td>
</tr>
<tr class="even">
<td><p>ct:end</p></td>
<td><p>0 or 1</p></td>
<td><p>An empty element, of the CommonTypes (ct) namespace, to mark the end of all the schema extensions to its parent element.</p></td>
</tr>
<tr class="odd">
<td><p>ct:extension</p></td>
<td><p>0 or more</p></td>
<td><p>An element, of the CommonTypes (ct) namespace, to hold any elements of any namespace as an application-defined custom extension to the parent element.</p></td>
</tr>
<tr class="even">
<td><p>[any]</p></td>
<td><p>0 or more</p></td>
<td><p>A custom element describing an extension to its parent element. When enclosed between a ct:delimiter element and a ct:end element or between two ct:delimiter elements, this element serves to describe a schema extension and can have any name in the namespace of its parent element. When contained in an ct:extension element, this element describes the application-defined custom extension and can have any name in any namespace.</p></td>
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
<td><p>This is a top-level element as a user-information options category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

The userInformation category instance represents the options that can be set by a user to share his or her phone numbers and to configure how calls may be handled. Lync 2013 publishes this type of category instances to the [Self container](self-container.md) only.

## Example

The following XML snippet shows a userInformation category instance value containing two types (work and mobile) of phone numbers

```xml
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

#### Concepts

[Self container](self-container.md)

