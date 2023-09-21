---
title: StartAudioCallButton control
TOCTitle: StartAudioCallButton control
ms:assetid: 431dafed-3b79-4b1b-a0fd-d5e464d2ffd4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ945562(v=office.15)
ms:contentKeyID: 51541367
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# StartAudioCallButton control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 StartAudioCallButton control.



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

Use the [StartAudioCallButton](https://msdn.microsoft.com/library/hh378744\(v=office.15\)) control in Microsoft Lync Control applications to enable the user to open a Microsoft Lync 2013 conversation window and start a voice conversation between the user who activated the control and another user. StartAudioCallButton is a split-button control. When clicked, the left side of the split button places a call to the default number that is associated with the contact. The right side of the control exposes a menu of calling options, such as **Lync Call**, **Work**, and **Voice Mail**.

![StartAudioCallButton Control](images/JJ945562.StartAudioCallButtonControl(Office.15).png "StartAudioCallButton Control")![StartAudio expanded](images/JJ945562.startAudioEditedNumber(Office.15).png "StartAudio expanded")

## Members

Notable StartAudioCallButton control public properties and events that are related to unified communications appear in the following table. For information about other properties and events, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/library/jj933088\(v=office.15\)).

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
<td><p><a href="https://msdn.microsoft.com/library/hh345805(v=office.15)">DisplayName</a> property</p></td>
<td><p>Gets the display name of the currently signed-in user.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh363511(v=office.15)">Source</a> property</p></td>
<td><p>Gets or sets the contact to use. Valid types include the <a href="https://msdn.microsoft.com/library/jj266463(v=office.15)">Contact</a> object, <a href="https://msdn.microsoft.com/library/jj293432(v=office.15)">DistributionGroup</a> object, and <a href="http://go.microsoft.com/fwlink/?linkid=131086%26clcid=0x409">String</a>.</p>
<ul>
<li><p>If the value is a string that does not contain the sip: or tel: prefix, the control performs a search, using the string specified as a search criteria, and loads the first contact in the result set matching the specified string. This behavior is not deterministic and yields the slowest performance.</p></li>
<li><p>If the value is a SIP URI string qualified by the sip: or tel: prefix, the contact is loaded using an exact match of the specified URI. This behavior is deterministic and yields better performance.</p></li>
<li><p>If the value is a Contact or DistributionGroup object, it is used without changes. This behavior is deterministic and yields the best performance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/hh363342(v=office.15)">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about using contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/hh346458(v=office.15)">Model</a> property</p></td>
<td><p>Reserved for internal use. This property may appear in XAML text when editing templates. To preserve control functionality, it should remain static.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<StackPanel>
  <controls:StartAudioCallButton Source="sip:elise@contoso.com"/>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

