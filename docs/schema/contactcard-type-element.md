---
title: contactCard/type element
TOCTitle: contactCard/type element
ms:assetid: e9a06cde-54ff-45cd-bbea-7668e291d846
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454712(v=office.15)
ms:contentKeyID: 57093399
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# contactCard/type element


**Applies to:** Lync 2013 | Lync Server 2013

The type of the contact.

``` xml
<type>Extended presentityTypeToken</type>
```

presentityTypeEnumEx

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
<td><p><a href="contactcard-category-instance-value-element.md">contactCard category instance value element</a></p></td>
<td><p>A contactCard category instance</p></td>
</tr>
</tbody>
</table>


## Text value

An extended presentityTypeToken value.

## Remarks

This element is introduced in the Office Communications Server 2007 release. Microsoft Lync 2013 recognizes the following contact type tokens:

  - *person*  
    The contact is an end user.

  - *huntgroup*  
    The contact is a Bot that does not ever directly interact with the caller, but will pass a call through to specified persons immediately, much as in a team call.

  - *autoattendant*  
    The contact is a Bot that connects the user to another person after first interacting with the user directly.

  - *automaton*  
    The contact is a Bot that can interact with the user directly, but does not necessarily connect the caller to another person.

## Example

The following XML code snippet shows a contactCard category instance for a person entity.

    <contactCard xmlns="http://schemas.microsoft.com/2006/09/sip/contactcard" isUCEnabled="true">
       <type>person</type>
    </contactCard>

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Namespace</p></td>
<td><p>http://schemas.microsoft.com/2006/09/sip/contactcard</p></td>
</tr>
<tr class="even">
<td><p>Schema Name</p></td>
<td><p>contactCard</p></td>
</tr>
<tr class="odd">
<td><p>Validation File</p></td>
<td><p>contactCard.xsd, contactCardTypes.xsd</p></td>
</tr>
<tr class="even">
<td><p>Can be Empty</p></td>
<td><p>True</p></td>
</tr>
</tbody>
</table>


## See also

#### Reference

[contactCard category instance value element](contactcard-category-instance-value-element.md)

[Category instance elements for presence](category-instance-elements-for-presence.md)

