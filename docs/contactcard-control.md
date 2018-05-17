---
title: ContactCard control
TOCTitle: ContactCard control
ms:assetid: e314511f-01b0-4c23-9c39-b61f4a530eb1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945582(v=office.15)
ms:contentKeyID: 51541407
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# ContactCard control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 ContactCard control.


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

Use the [ContactCard](contactcard-class-microsoft-lync-controls_1.md) control to show basic or detailed contact and organization information for contacts. This control displays presence and availability of colleagues and gives users the ability to start instant messaging sessions, voice calls, file transfers, application sharing sessions, or conference calls.

![ContactCard expanded](images/JJ945582.ContactCard_Expanded_rtm(Office.15).png "ContactCard expanded")

![ContactCard](images/JJ945582.ContactCard_rtm(Office.15).png "ContactCard")

## Members

Notable ContactCard control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](lync-2013-class-libraries-reference.md).

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
<td><p><a href="contactbase-displayname-property-microsoft-lync-controls_1.md">DisplayName</a> property</p></td>
<td><p>Gets the display name of the currently logged-in user.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-selectedtabindex-property-microsoft-lync-controls_1.md">SelectedTabIndex</a> property</p></td>
<td><p>Gets or sets the index of the tab item to display when the Contact Card is expanded.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactcard-expandervisibility-property-microsoft-lync-controls_1.md">ExpanderVisibility</a> property</p></td>
<td><p>Gets the Expander Button visibility state.</p></td>
</tr>
<tr class="even">
<td><p><a href="contactbase-contextualinformation-property-microsoft-lync-controls_1.md">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about using contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactbase-source-property-microsoft-lync-controls_1.md">Source</a> property</p></td>
<td><p>Gets or sets the contact to display. Valid types include the <a href="contact-class-microsoft-lync-model_2.md">Contact</a> object, <a href="distributiongroup-class-microsoft-lync-model-group_2.md">DistributionGroup</a> object, and <a href="http://go.microsoft.com/fwlink/?linkid=131086%26clcid=0x409">String</a>.</p>
<ul>
<li><p>If the value is a string that does not contain the sip: or tel: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: or tel: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a Contact or DistributionGroup object, it is used as-is. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="contactcard-isexpanded-property-microsoft-lync-controls_1.md">IsExpanded</a> property</p></td>
<td><p>Gets or sets a bool value, which indicates whether or not the details section of the ContactCard control is expanded.</p></td>
</tr>
</tbody>
</table>


## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

``` xaml
<StackPanel>
  <controls:ContactCard Source="sip:elise@contoso.com" />
</StackPanel>
```

## Additional resources

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

