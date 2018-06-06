---
title: userProperties category instance value element
TOCTitle: userProperties category instance value element
ms:assetid: 119f5981-8205-43a4-8cbd-d6df439fba8d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438963(v=office.15)
ms:contentKeyID: 57094001
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# userProperties category instance value element


_**Applies to:** Lync Server 2013_

Contains user properties that are received by using in-band provisioning from the server.

``` xml
<up:userProperties xmlns:up="http://schemas.microsoft.com/2006/09/sip/categories" 
       majorVersion="xs:unsignedInt" 
       minorVersion="xs:unsignedInt"
       [anyAttri]="anyAttribute">
   <up:lines>List of <up:line> elements </up:phones>
   <up:telephonyMode>telephonyMode token or string </up:telephonyMode>
   <up:fascimileTelephoneNumber>xs:token</up:fascimileTelephoneNumber>
   <up:streetAdress>xs:token</up:streetAddress>
   <up:l>xs:token<up:l>
   <up:st>xs:token</up:st>
   <up:countryCode>xs:token</up:countryCode>
   <up:postalCode>xs:token</up:postalCode>
   <up:wWWHomePage>xs:token</up:wWWHomePage>
   <up:exumEnabled>xs:unsignedLong</up:exumEnabled>
   <up:exumURL>xs:token</upexumURL>
   <up:forwardingUrls>List of any elements</up:forwardingUrls>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <up:acpInformation>up:acpProvisionType</up:acpInformation>
   <ct:delimiter xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <[any]>any element</[any]>
   <ct:end xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" />
   <ct:extension xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" >...<ct:extension>
</up:userProperties>
```

userPropertiesType

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
<td><p>Optional attribute to specify schema-dependent major version information. The default value is unspecified.</p></td>
</tr>
<tr class="even">
<td><p>minorVersion</p></td>
<td><p>Optional attribute to specify schema-dependent minor version information. The default value is unspecified.</p></td>
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
<td><p><a href="userproperties-lines-element.md">userProperties/lines element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>An element of the xs:element type containing a list of the <a href="userproperties-lines-line-element.md">userProperties/lines/line element</a> elements specifying the list of phone lines controlled by the user.</p></td>
</tr>
<tr class="even">
<td><p>up:telephonyMode</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the up:telephonyModeEnumEx type to specify the telephony mode of the user. Microsoft Lync 2013 recognizes the following telephony modes:</p>
<dl>
<dt>None</dt>
<dd><p>Telephony is not enabled.</p>
</dd>
<dt>Uc</dt>
<dd><p>The user has a VoIP phone.</p>
</dd>
<dt>Rcc</dt>
<dd><p>The user has a RCC phone.</p>
</dd>
<dt>Dual</dt>
<dd><p>The user can make VoIP and RCC calls.</p>
</dd>
</dl></td>
</tr>
<tr class="odd">
<td><p>up:facsimileTelphoneNumber</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the fax number of the user.</p></td>
</tr>
<tr class="even">
<td><p>up:streetAddress</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the street address of the user.</p></td>
</tr>
<tr class="odd">
<td><p>up:l</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the city name of the user.</p></td>
</tr>
<tr class="even">
<td><p>up:st</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the name of state or province of the user.</p></td>
</tr>
<tr class="odd">
<td><p>up:countryCode</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the country code of the user.</p></td>
</tr>
<tr class="even">
<td><p>up:postalCode</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the zip code or postal code of the user.</p></td>
</tr>
<tr class="odd">
<td><p>up:wWWHomePage</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the website of the user.</p></td>
</tr>
<tr class="even">
<td><p>up:exumEnabled</p></td>
<td><p>0 or 1</p></td>
<td><p>A bit flag of the xs:unsignedLong type to indicate whether voicemail is enabled for the user (0x0001) or not (otherwise).</p></td>
</tr>
<tr class="odd">
<td><p>up:exumURL</p></td>
<td><p>0 or 1</p></td>
<td><p>A token of the xs:token type to specify the Exchange Unified Messaging URL for the user.</p></td>
</tr>
<tr class="even">
<td><p>up:forwardingUrls</p></td>
<td><p>0 or more</p></td>
<td><p>A sequence of any elements in the same namespace specifying the URLs to which incoming calls are forwarded.</p></td>
</tr>
<tr class="odd">
<td><p><a href="userproperties-acpinformation-element.md">userProperties/acpInformation element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>An element of the acpProvisionType type specifying the audio conference provider (ACP) information for the user.</p></td>
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
<td><p>None</p></td>
<td><p>This is a top-level element as a userProperties category instance value.</p></td>
</tr>
</tbody>
</table>


## Text value

None

## Remarks

Lync 2013 publishes the userProperties category instance to the Self container only.

## Example

The following XML snippet shows a userProperties category instance value.

``` xml
<userProperties xmlns="http://schemas.microsoft.com/2006/09/sip/categories">
   <lines>
      <line lineType="Uc">tel:+1421112222;ext=12222</line>
   </lines>
   <telephonyMode>Uc</telephonyMode>
   <exumEnabled>1</exumEnabled>
   <exumURL>EUM:john@contoso.com;phone-context=EX-OCS-SIPSec.exchange.contoso.com</exumURL>
</userProperties>
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

#### Concepts

[Self container](self-container.md)

