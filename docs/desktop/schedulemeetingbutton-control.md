---
title: ScheduleMeetingButton control
TOCTitle: ScheduleMeetingButton control
ms:assetid: 08dcdec1-6bd7-46a5-9d17-3c1dbe43de0c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945534(v=office.15)
ms:contentKeyID: 51541333
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# ScheduleMeetingButton control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 ScheduleMeetingButton control.



**Applies to**: Lync 2013 | Lync Server 2013

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

Use the [ScheduleMeetingButton](https://msdn.microsoft.com/en-us/library/hh363440\(v=office.15\)) control in Microsoft Lync Control applications to open a Microsoft Outlook meeting invitation dialog box. The control is designed to mimic the functionality provided by the corresponding button on the Quick Connect toolbar of the ContactCard. As such, it must be bound to a contact using the Source property before it can be used. When clicked, it launches the Microsoft Outlook dialog box to initiate the desired action with that contact. This button is not a general-purpose Outlook Integration tool. It is intended to be used with other Lync Controls to provide a full set of collaboration options for interacting with a specific contact or distribution group.

![ScheduleMeetingButton Control](images/JJ945534.ScheduleMeetingButtonControl(Office.15).png "ScheduleMeetingButton Control")

## Members

Notable ScheduleMeetingButton control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

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
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345805(v=office.15)">DisplayName</a> property</p></td>
<td><p>Gets the display name of the currently logged-in user.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363511(v=office.15)">Source</a> property</p></td>
<td><p>Gets or sets the contact to use. Valid types include the <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Contact</a> object, <a href="https://msdn.microsoft.com/en-us/library/jj293432(v=office.15)">DistributionGroup</a> object, and String.</p>
<ul>
<li><p>If the value is a string that does not contain the sip: or tel: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: or tel: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a Contact or DistributionGroup object, it is used as-is. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363342(v=office.15)">ContextualInformation</a> property</p></td>
<td><p>This property is ignored. Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about using contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="even">
<td><p>Model property</p></td>
<td><p>Reserved for internal use. This property may appear in XAML text when editing templates. To preserve control functionality, it should remain unchanged.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<StackPanel>
  <controls:ScheduleMeetingButton Source="sip:mary@contoso.com"/>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

