---
title: CustomContactListItem control
TOCTitle: CustomContactListItem control
ms:assetid: 92fddd82-0f04-4162-846f-09d9a250dd34
ms:mtpsurl: https://msdn.microsoft.com/library/JJ945570(v=office.15)
ms:contentKeyID: 51541385
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# CustomContactListItem control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 CustomContactListItem control.



***Applies to:** Lync 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Control overview<br />
Members<br />
Code example<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Control overview

Use the [CustomContactListItem](https://msdn.microsoft.com/library/hh346017\(v=office.15\)) control with the CustomContactList control to show basic or detailed contact and organization information for contacts.

CustomContactListItem is an item control, created for use with the [CustomContactList](https://msdn.microsoft.com/library/hh346321\(v=office.15\)) control. CustomContactListItem supports a Source property, similar to that used by other Microsoft Lync 2013 SDK objects that operate on a single contact.

![CustomContactListItem Control](images/JJ945570.CustomContactListItemControl_(Office.15).png "CustomContactListItem Control")

## Members

Notable CustomContactListItem control public properties relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/library/jj933088\(v=office.15\)).

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh379350(v=office.15)">PersonTwoLineContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh346307(v=office.15)">TelephoneTwoLineContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a telephone-only contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh345386(v=office.15)">GroupTwoLineContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a DistributionGroup-type contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh346184(v=office.15)">BotTwoLineContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a bot-type contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh345387(v=office.15)">PersonContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh364209(v=office.15)">TelephoneContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a telephone-only contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh379570(v=office.15)">GroupContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a DistributionGroup-type contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh363460(v=office.15)">BotContentTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render bot-type contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh363533(v=office.15)">ContactLayoutView</a> property</p></td>
<td><p>Gets or sets an enumerated value that toggles the display between Show Photos and Show Status Only. The default is Show Photos.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh363537(v=office.15)">ShowFriendlyName</a> property</p></td>
<td><p>Gets or sets whether contacts in the list are shown using their display names or their SIP URIs.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh363565(v=office.15)">Source</a> property</p></td>
<td><p>Gets or sets the contact to display. Valid types include the <a href="https://msdn.microsoft.com/library/jj266463(v=office.15)">Contact</a> object, <a href="https://msdn.microsoft.com/library/jj293432(v=office.15)">DistributionGroup</a> object, and <a href="http://go.microsoft.com/fwlink/?linkid=131086%26clcid=0x409">String</a>.</p>
<ul>
<li><p>If the value is a string that does not contain the sip: or tel: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: or tel: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a Contact or DistributionGroup object, it is used without changes. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<controls:CustomContactList>
  <controls:CustomContactListItem Source="sip:mary@contoso.com"/>
</controls:CustomContactList>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

