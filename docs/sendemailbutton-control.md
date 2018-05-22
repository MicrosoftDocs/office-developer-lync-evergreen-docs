---
title: SendEmailButton control
TOCTitle: SendEmailButton control
ms:assetid: 41b7ed45-b204-488e-8074-e3085a312560
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945543(v=office.15)
ms:contentKeyID: 51541349
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# SendEmailButton control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 SendEmailButton control.

**Last modified:** February 14, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

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

Use the [SendEmailButton](https://msdn.microsoft.com/en-us/library/hh379649\(v=office.15\)) control in Microsoft Lync Control applications to start Microsoft Outlook and compose an email to a selected contact. The selected contact must have an email address exposed for this feature to work. Optionally, you can specify a subject for the email as well.

The control is designed to mimic the functionality provided by the corresponding button on the Quick Connect toolbar of the ContactCard. As such, it must be bound to a contact using the Source property before it can be used. When clicked, it starts Outlook and initiates the desired action with that contact. This button is not a general-purpose Outlook Integration tool. It is intended to be used with other Lync Controls to provide a full set of collaboration options for interacting with a specific contact or distribution group. Despite the fact that no Microsoft Lync 2013 functionality is actually used here, this control leverages the binding model of the other Lync Controls to provide the full scope of features accessible on the ContactCard Quick Connect toolbar.

![SendEmailButton Control](images/JJ945543.SendEmailButtonControl(Office.15).png "SendEmailButton Control")

## Members

Notable SendEmailButton control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

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
<td><p>Gets or sets the contact to use. Valid types include the <a href="https://msdn.microsoft.com/en-us/library/jj266463(v=office.15)">Contact</a> object, <a href="https://msdn.microsoft.com/en-us/library/jj293432(v=office.15)">DistributionGroup</a> object, and <a href="http://go.microsoft.com/fwlink/?linkid=131086%26clcid=0x409">String</a>.</p>
<ul>
<li><p>If the value is a string that does not contain the sip: or tel: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: or tel: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a Contact or DistributionGroup object, it is used as-is. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346067(v=office.15)">Subject</a> property</p></td>
<td><p>Gets or sets the subject string for the message.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363342(v=office.15)">ContextualInformation</a> property</p></td>
<td><p>This property is ignored. Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about the use of contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Model property</p></td>
<td><p>Reserved for internal use. This property may appear in XAML text when editing templates. To preserve control functionality, it should remain unchanged.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

``` xaml
<StackPanel>
  <controls:SendEmailButton Source="sip:elise@contoso.com"/>
</StackPanel>
```

## Additional resources

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

