---
title: MyPresenceChooser control
TOCTitle: MyPresenceChooser control
ms:assetid: d19cd08f-4dd0-4de3-8a2a-05d462de6cff
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945580(v=office.15)
ms:contentKeyID: 51541404
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# MyPresenceChooser control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 MyPresenceChooser control.



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

Use the [MyPresenceChooser](https://msdn.microsoft.com/en-us/library/hh379434\(v=office.15\)) control in Microsoft Lync Control applications to display and change the user’s current presence status selection. Clicking the control displays a list of presence status options, for example "Be Right Back." The user can change their presence status by selecting one of these options. The MyPresenceChooser control includes the ability to show and select custom presence states. This control can only be applied to the currently signed-in user and therefore does not have a Source property.

![MyPresenceChooser Control](images/JJ933130.MyPresenceChooserControl(Office.15).png "MyPresenceChooser Control")

## Members

Notable MyPresenceChooser control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

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
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363484(v=office.15)">DisplayName</a> property</p></td>
<td><p>Gets the display name of the currently logged-in user.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363408(v=office.15)">AvailabilityState</a> property</p></td>
<td><p>Gets an enumerated value that represents the currently signed-in user’s availability. The type is a ContactAvailability enumeration. Possible values:</p>
<ul>
<li><p>Invalid</p></li>
<li><p>None</p></li>
<li><p>Free</p></li>
<li><p>FreeIdle</p></li>
<li><p>Busy</p></li>
<li><p>BusyIdle</p></li>
<li><p>DoNotDisturb</p></li>
<li><p>TemporarilyAway</p></li>
<li><p>Away</p></li>
<li><p>Offline</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Model property</p></td>
<td><p>Reserved for internal use. This property may appear in XAML text when editing templates. To preserve control functionality, it should remain unchanged.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<StackPanel>
  <controls:MyPresenceChooser/>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

