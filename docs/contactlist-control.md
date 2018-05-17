---
title: ContactList control
TOCTitle: ContactList control
ms:assetid: fffbb71f-2e43-488d-9bd2-d76904488479
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945579(v=office.15)
ms:contentKeyID: 51541403
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# ContactList control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about using the [ContactList](contactlist-class-microsoft-lync-controls_1.md) control to display the Microsoft Lync 2013 contacts list and give users the ability to launch voice, instant messaging (IM), or email conversations with any of their contacts.


_**Applies to:** Lync 2013_

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

The control supports Group, Relationship, and Status views in the same manner as Microsoft Lync 2013 and includes the option to switch between status only and status with photo display modes. The ContactList control gives users the ability to copy, move, delete, multi-select and sort contacts, set status alerts, and manage privacy settings.

There are two differences in the behavior of this control between the Windows Presentation Foundation (WPF) and Microsoft Silverlight versions:

  - The WPF version of this control launches the default conversation with a contact when double-clicked. Silverlight, on the other hand, does not support double-click.

  - The WPF version of this control includes Clipboard functionality on the context menu to copy the URI of one or more selected contacts, as well as to paste a copied set of contacts into a new custom group. The Silverlight version does not support Clipboard functionality.

![ContactList](images/JJ945579.ContactList_rtm(Office.15).png "ContactList")

## Members

Notable ContactList control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](lync-2013-class-libraries-reference.md).

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
<td><p><a href="contactlist-groupviewbysetting-property-microsoft-lync-controls_1.md">GroupViewBySetting</a> property</p></td>
<td><p>Gets or sets an enumerable that specifies the manner in contacts are aggregated. The default is Groups.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-itemcontainerstyle-property-microsoft-lync-controls_1.md">ItemContainerStyle</a> property</p></td>
<td><p>Gets or sets the style that is used to display the contact item.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-groupitemcontainerstyle-property-microsoft-lync-controls_1.md">GroupItemContainerStyle</a> property</p></td>
<td><p>Gets or sets the style that is used to display the root group.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-persontwolineitemtemplate-property-microsoft-lync-controls_1.md">PersonTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-telephonetwolineitemtemplate-property-microsoft-lync-controls_1.md">TelephoneTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a telephone-only contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-grouptwolineitemtemplate-property-microsoft-lync-controls_1.md">GroupTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a DistributionGroup-type contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-bottwolineitemtemplate-property-microsoft-lync-controls_1.md">BotTwoLineItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render an Automaton, AutoAttendant, or Huntgroup contact when the ContactLayoutView property is set to TwoLines mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-personitemtemplate-property-microsoft-lync-controls_1.md">PersonItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a person item contact when the ContactLayoutView property is set to Status only mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-telephoneitemtemplate-property-microsoft-lync-controls_1.md">TelephoneItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a telephone item contact when the ContactLayoutView property is set to Status only mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-groupitemtemplate-property-microsoft-lync-controls_1.md">GroupItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a group item contact when the ContactLayoutView property is set to Status only mode.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-botitemtemplate-property-microsoft-lync-controls_1.md">BotItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a bot item contact when the ContactLayoutView property is set to Status only mode.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-showpivotbar-property-microsoft-lync-controls_1.md">ShowPivotBar</a> property</p></td>
<td><p>Gets or sets a bool value that determines whether group pivot buttons are displayed. The default is true.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-sortbysetting-property-microsoft-lync-controls_1.md">SortBySetting</a> property</p></td>
<td><p>Gets or sets a value that toggles the sort order. The default is Display Name.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-contactlayoutview-property-microsoft-lync-controls_1.md">ContactLayoutView</a> property</p></td>
<td><p>Gets or sets an enumerated value that toggles the display between Show Photos and Show Status Only. The default is Show Photos.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-showfriendlyname-property-microsoft-lync-controls_1.md">ShowFriendlyName</a> property</p></td>
<td><p>Gets or sets a value toggles the display between the user’s friendly name and his or her SIP URI. The default is true.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactlist-showfrequentcontacts-property-microsoft-lync-controls_1.md">ShowFrequentContacts</a> property</p></td>
<td><p>Gets or sets a bool value that toggles the display of the Frequent Contacts group. This setting only applies to the contact list when the GroupViewBySetting property is set to Group. It does not apply when the setting is Status or Relationship.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactlist-contextualinformation-property-microsoft-lync-controls_1.md">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about using contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="even">
<td><p>Model property</p></td>
<td><p>Reserved for internal use. This property might appear in XAML text when editing templates. To preserve control functionality, it should remain unchanged.</p></td>
</tr>
</tbody>
</table>


## Code example

The following example can be used for Silverlight and WPF application development.

``` xaml
<StackPanel>
  <controls:ContactList Height="180" Width="500"/>
</StackPanel>
```

## Additional resources

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

