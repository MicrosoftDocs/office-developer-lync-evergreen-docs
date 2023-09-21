---
title: CustomContactList control
TOCTitle: CustomContactList control
ms:assetid: 02aa4ef9-a867-4e05-9aa0-d4e0101fad4d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ945533(v=office.15)
ms:contentKeyID: 51541328
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# CustomContactList control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about using the Microsoft Lync 2013 [CustomContactList](https://msdn.microsoft.com/library/hh346321\(v=office.15\)) control to provide an arbitrary and non-hierarchical display of contacts and groups for specific contexts.



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
<td></td>
</tr>
</tbody>
</table>

## Control overview

CustomContactList is a subclass of ListBox, which is optimized for use in the display of contact information. The CustomContactList control can be used to specify a user-specified collection of contacts. Contacts are displayed using a UI template matching that which is used on the ContactList control. Unlike ContactList, this control permits the user to programmatically specify a list of contacts to display and modify the display settings.

![CustomContactList Control](images/JJ945533.CustomContactList_rtm(Office.15).png "CustomContactList Control")

## Members

Notable CustomContactList control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/library/jj933088\(v=office.15\)).

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property or event</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh363576(v=office.15)">ContactLayoutView</a> property</p></td>
<td><p>Gets or sets an enumerated value that toggles the display between OneLine and TwoLines. OneLine is an abbreviated presentation, while TwoLines is a larger layout that includes a photo. The default is TwoLine.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh363405(v=office.15)">BotTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render an Automaton, AutoAttendant, or Huntgroup contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh379585(v=office.15)">GroupTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a DistributionGroup-type contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh379568(v=office.15)">PersonTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh363486(v=office.15)">TelephoneTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a telephone-only contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh363732(v=office.15)">BotItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a bot item contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh379035(v=office.15)">GroupItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a group item contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh363472(v=office.15)">PersonItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a person item contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh363420(v=office.15)">TelephoneItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a telephone item contact when the ContactLayoutView property is set to OneLine mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh346167(v=office.15)">ShowFriendlyName</a> property</p></td>
<td><p>Gets or sets a bool value that controls the display of friendly name strings in the list. When true, contacts are displayed using their friendly names, such as John Smith. When false, contacts are displayed by URI, such as joe@contoso.com. Gets or sets a Boolean value that specifies whether friendly names are displayed. The default is true.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh346324(v=office.15)">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about the use of contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<StackPanel>
  <controls:CustomContactList Height="300" x:Name="_xamlCustomContactsList" ContactLayoutView="TwoLines">
   <controls:CustomContactListItem Source="sip:elise@contoso.com"/>
   <controls:CustomContactListItem Source="sip:bob@contoso.com"/>
   <controls:CustomContactListItem Source="sip:mary@contoso.com"/>
  </controls:CustomContactList>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

