---
title: rccOptions/forwarding/mode element
TOCTitle: rccOptions/forwarding/mode element
ms:assetid: 248f56f9-4681-4e22-9752-317ebeb2d6ea
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454789(v=office.15)
ms:contentKeyID: 57093698
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# rccOptions/forwarding/mode element


_**Applies to:** Lync 2013 | Lync Server 2013_

Specifies the mode to forward calls from the PBX phone.

``` xml
<mode xmlns="http://schemas.microsoft.com/2006/09/sip/options/rccOptions">
a forwardingModeTypeEnumEx value
</mode>
```

forwardingModeTypeEnumEx

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

A token of the forwardingModeTypeEnumEx type. The default value is disabled.

## Remarks

Microsoft Lync 2013 recognizes the following forwarding mode tokens:

  - disabled  
    Forwarding of calls from a PBX phone is disabled.

  - static  
    Forwarding of calls from a PBX phone is persistent.

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

