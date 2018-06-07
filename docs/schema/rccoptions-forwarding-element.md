---
title: rccOptions/forwarding element
TOCTitle: rccOptions/forwarding element
ms:assetid: 86b77dc3-f0c2-49a9-84cb-37213bc42ca8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454787(v=office.15)
ms:contentKeyID: 57093676
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# rccOptions/forwarding element


**Applies to:** Lync 2013 | Lync Server 2013

Specifies where and how to forward calls from the PBX phone.

``` xml
<forwarding xmlns="http://schemas.microsoft.com/2006/09/sip/options/rccOptions">
   <mode>...</mode>
   <toPhoneType>...</toPhoneType>
</forwarding>
```

forwarding

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
<td><p><a href="rccoptions-forwarding-mode-element.md">rccOptions/forwarding/mode element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies a mode to forward a call from a PBX phone.</p></td>
</tr>
<tr class="even">
<td><p><a href="rccoptions-forwarding-tophonetype-element.md">rccOptions/forwarding/toPhoneType element</a></p></td>
<td><p>0 or 1</p></td>
<td><p>Specifies the type of the target phone to forward call from a PBX phone.</p></td>
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
<td><p><a href="rccoptions-category-instance-value-element.md">rccOptions category instance value element</a></p></td>
<td><p>This is a top-level element as an enhanced presence category instance.</p></td>
</tr>
</tbody>
</table>


## Text value

None

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

