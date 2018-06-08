---
title: MyNoteBox control
TOCTitle: MyNoteBox control
ms:assetid: 9635f546-2c32-4204-9081-dc51dd2e21ca
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945564(v=office.15)
ms:contentKeyID: 51541377
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# MyNoteBox control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 MyNoteBox control.

**Last modified:** April 09, 2013

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

Use the [MyNoteBox](https://msdn.microsoft.com/en-us/library/hh346137\(v=office.15\)) control in Microsoft Lync Control applications to display and change the current user’s personal note. Users can change their personal note by typing in new text and pressing the **Enter** key.

![MyNoteBox Control](images/JJ937324.MyNoteBoxControl(Office.15).png "MyNoteBox Control")

## Members

Notable MyNoteBox control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property or event</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363484(v=office.15)">DisplayName</a> property</p></td>
<td><p>Gets the display name of the currently logged-in user.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363904(v=office.15)">Model</a> property</p></td>
<td><p>Reserved for internal use. This property may appear in XAML text when editing templates. To preserve control functionality, it should remain unchanged.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363725(v=office.15)">PersonalNote</a> property</p></td>
<td><p>Gets a string that shows the content of the note box for the signed-in user.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<StackPanel>
  <controls:MyNoteBox/>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

