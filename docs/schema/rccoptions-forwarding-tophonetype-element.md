---
title: rccOptions/forwarding/toPhoneType element
TOCTitle: rccOptions/forwarding/toPhoneType element
ms:assetid: a60849ad-a754-4186-85c4-8030ea073c13
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn438956(v=office.15)
ms:contentKeyID: 57093976
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# rccOptions/forwarding/toPhoneType element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies the type of target to forward calls from the PBX phone.

``` xml
<toPhoneType xmlns="http://schemas.microsoft.com/2006/09/sip/options/rccOptions">
a phoneTypeEnumEx value
</toPhoneType>
```

phoneTypeEnumEx

## Attributes and elements

The following sections describe attributes, child elements, and parent elements.

#### Attributes

None

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
<td><p><a href="rccoptions-forwarding-element.md">rccOptions/forwarding element</a></p></td>
<td><p>The forwarding property of an enhanced presence category instance of rccOptions.</p></td>
</tr>
</tbody>
</table>


## Text value

A token of the phoneTypeEnumEx type. The default value is mobile.

## Remarks

Microsoft Lync 2013 recognizes the following forwarding mode tokens:

  - work  
    The target is a work phone.

  - home  
    The target is a home phone.

  - mobile  
    The target is a mobile phone.

  - other  
    The target is some other phone.

  - custom1  
    The target is a special phone.

## Example

The following XML code snippet specifies that a call from a PBX phone is always forwarded to the user’s mobile phone.

    <ro:rccOptions xmlns="http://schemas.microsoft.com/2006/09/sip/options/rccOptions">
      <ro:forwarding>
        <ro:mode>static</ro:mode>
        <ro:toPhoneType>mobile</ro:toPhoneType>
      </ro:forwarding>
      <ct:extension>false</ct:extension>
    </ro:rccOptions>

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/options/rccOptions</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>options-rccOptions</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>options-rccOptions.xsd</p></td>
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

[rccOptions category instance value element](rccoptions-category-instance-value-element.md)

