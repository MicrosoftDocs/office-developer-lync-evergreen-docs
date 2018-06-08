---
title: MyStatusArea control
TOCTitle: MyStatusArea control
ms:assetid: bed55d63-05a6-42d0-8627-00aa2b05b7e6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945575(v=office.15)
ms:contentKeyID: 51541391
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# MyStatusArea control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 MyStatusArea control.

**Last modified:** February 12, 2013

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

Use the [MyStatusArea](https://msdn.microsoft.com/en-us/library/hh363503\(v=office.15\)) control in Microsoft Lync Control applications to display the note string, an availability icon/photo, a textblock with the user’s name, and a textblock with the user’s location. It also displays the MyNoteBox and MyPresenceChooser controls together. To display these in separate locations, use MyNoteBox and MyPresenceChooser as separate controls. Clicking the presence status box displays a list of presence options, for example "Be Right Back." Users can change their presence by selecting one of these. Users can also change their note string by typing in new text and pressing the **Enter** key.

![MyStatusArea Control](images/JJ945575.MyStatusAreaControl(Office.15).png "MyStatusArea Control")

## Members

Notable MyStatusArea control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

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
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh378959(v=office.15)">Location</a> property</p></td>
<td><p>Gets a string that shows the location of the currently signed-in user.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363904(v=office.15)">Model</a> property</p></td>
<td><p>Reserved for internal use. This property might appear in XAML text when editing templates. To preserve control functionality, it should remain unchanged.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363918(v=office.15)">AvailabilityState</a> property</p></td>
<td><p>Gets an enumeration value that represents the contact’s availability. The type is a ContactAvailability enumeration. Possible values:</p>
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
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345761(v=office.15)">PersonalNote</a> property</p></td>
<td><p>Gets a string that shows the content of the note box for the signed-in user.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345959(v=office.15)">PhotoDisplayMode</a> property</p></td>
<td><p>Gets or sets an enumeration value that determines the presence photo display mode. The type is a PhotoDisplayMode enumeration. Possible values include:</p>
<ul>
<li><p>Hidden</p></li>
<li><p>Large</p></li>
<li><p>Small</p></li>
</ul></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<StackPanel>
  <controls:MyStatusArea PhotoDisplayMode="Small"/>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

