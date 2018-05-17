---
title: Properties that support restyling
TOCTitle: Properties that support restyling
ms:assetid: 78d6eb40-8872-4569-9632-84d0c9dfcadd
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945548(v=office.15)
ms:contentKeyID: 51541360
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Properties that support restyling

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn how to use the properties on Lync Controls to modify their appearance.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Properties used to change Lync Controls style<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Properties used to change Lync Controls style

### ContactList

The following properties on [ContactList](contactlist-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="contactcontentpresenter-background-property-microsoft-lync-controls_1.md">Background</a></p></td>
<td><p>The background color is painted to the entire area, including buttons and contact items.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592511">BorderBrush</a></p></td>
<td><p>Placed around the entire control. Does not propagate to contact items or any other subcontrol.</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592512">BorderThickness</a></p></td>
<td><p>Placed around the entire control. Does not propagate to contact items or any other subcontrol.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592513">FontFamily</a></p></td>
<td><p>Applies to all visible fonts including filter buttons, headers, contact items, and contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592517">FontWeight</a></p></td>
<td><p>Applies to all visible fonts including filter buttons, headers, contact items, and contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592522">Padding</a></p></td>
<td><p>Applies to the distance between the border controlled by the BorderBrush and BorderThickness properties and the actual content of the ContactList control.</p></td>
</tr>
</tbody>
</table>


### CustomContactList

The following properties on [CustomContactList](customcontactlist-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area, including buttons and contact items.</p></td>
</tr>
<tr class="even">
<td><p>BorderBrush</p></td>
<td><p>Placed around the entire control. Does not propagate to contact items or any other subcontrol.</p></td>
</tr>
<tr class="odd">
<td><p>BorderThickness</p></td>
<td><p>Placed around the entire control. Does not propagate to contact items or any other subcontrol.</p></td>
</tr>
<tr class="even">
<td><p>FontFamily</p></td>
<td><p>Applies to all visible fonts including filter buttons, headers, contact items, and contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="odd">
<td><p>FontWeight</p></td>
<td><p>Applies to all visible fonts including filter buttons, headers, contact items, and contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Applies to the distance between the border controlled by the <strong>BorderBrush</strong> and <strong>BorderThickness</strong> properties and the actual content of the CustomContactList control.</p></td>
</tr>
</tbody>
</table>


### StartInstantMessagingButton

The following properties on [StartInstantMessagingButton](startinstantmessagingbutton-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area shown behind hover/pressed states.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Adds margins to the content of the StartInstantMessagingButton control. In this case, a margin is added to the control’s icon.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Content()</strong></p></td>
<td><p>Enables the developer to assign a string or any other element. The Content property visually replaces the StartInstantMessagingButton control’s icon.</p></td>
</tr>
</tbody>
</table>


### StartAudioCallButton

The following properties on [StartAudioCallButton](startaudiocallbutton-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area shown behind hover/pressed states. Does not apply to the split menu.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Adds margins to the leftmost content of the SplitButton control. In this case, a margin is added to the voice endpoint icon.</p></td>
</tr>
<tr class="odd">
<td><p>Content</p></td>
<td><p>Enables the developer to assign a string or any other element. The Content property visually replaces the StartAudioCallButton control icon.</p></td>
</tr>
</tbody>
</table>


### ContactCard

The following properties on [ContactCard](contactcard-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area including tab content and the tab itself and is placed within the exterior border including rounded corners. The unfocused tab should have a semi-transparent palette that darkens the background color. Does not apply to the note box.</p></td>
</tr>
<tr class="even">
<td><p>BorderBrush</p></td>
<td><p>Placed around the circumference of the contact card, excluding the note border. The note obscures the top border when the contact card is open.</p></td>
</tr>
<tr class="odd">
<td><p>BorderThickness</p></td>
<td><p>Placed around the circumference of the contact card, excluding the note border. The note obscures the top border when it is open.</p></td>
</tr>
<tr class="even">
<td><p>FontFamily</p></td>
<td><p>Applies to all visible fonts. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="odd">
<td><p>FontWeight</p></td>
<td><p>Applies to all visible fonts. Does not apply to menu items and tooltips.</p></td>
</tr>
</tbody>
</table>


### ContactSearchInputBox

The following properties on [ContactSearchInputBox](contactsearchinputbox-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area shown behind the text box. The text box remains white.</p></td>
</tr>
<tr class="even">
<td><p>BorderBrush</p></td>
<td><p>Placed around the entire ContactSearchInputBox control.</p></td>
</tr>
<tr class="odd">
<td><p>BorderThickness</p></td>
<td><p>Placed around the entire ContactSearchInputBox control.</p></td>
</tr>
<tr class="even">
<td><p>FontFamily</p></td>
<td><p>Applies to all visible text.</p></td>
</tr>
<tr class="odd">
<td><p>FontWeight</p></td>
<td><p>Applies to all visible text.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Applies to the distance between the border controlled by the BorderBrush and BorderThickness properties and the actual content of the ContactSearchInputBox control.</p></td>
</tr>
</tbody>
</table>


### ContactSearchResultList

The following properties on [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area, including list items.</p></td>
</tr>
<tr class="even">
<td><p>BorderBrush</p></td>
<td><p>Placed around the entire control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="odd">
<td><p>BorderThickness</p></td>
<td><p>Placed around the entire control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="even">
<td><p>FontFamily</p></td>
<td><p>Applies to all visible fonts, list items, and pop-up contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="odd">
<td><p>FontWeight</p></td>
<td><p>Applies to all visible fonts, list items, and pop-up contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Applies to the distance between the border controlled by the BorderBrush and BorderThickness properties and the actual content of the ContactSearchResultList control.</p></td>
</tr>
</tbody>
</table>


### MyNoteBox

The following properties on [MyNoteBox](mynotebox-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area of the MyNoteBox control.</p></td>
</tr>
<tr class="even">
<td><p>BorderBrush</p></td>
<td><p>Placed around the entire MyNoteBox control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="odd">
<td><p>BorderThickness</p></td>
<td><p>Placed around the entire MyNoteBox control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="even">
<td><p>FontFamily</p></td>
<td><p>Applies to all visible fonts, list items, and pop-up contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="odd">
<td><p>FontWeight</p></td>
<td><p>Applies to all visible fonts, list items, and pop-up contact cards. Does not apply to menu items and tooltips.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Applies to the distance between the border controlled by the BorderBrush and BorderThickness properties and the actual content of the MyNoteBox control.</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592518">Foreground</a></p></td>
<td><p>Applies to the text of the note, during editing or not, with a note already set or not.</p></td>
</tr>
</tbody>
</table>


### MyPresenceChooser

The following properties on [MyPresenceChooser](mypresencechooser-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area behind the split button control.</p></td>
</tr>
<tr class="even">
<td><p>BorderBrush</p></td>
<td><p>Placed around the entire control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="odd">
<td><p>BorderThickness</p></td>
<td><p>Placed around the entire control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="even">
<td><p>FontFamily</p></td>
<td><p>Applies to the presence status text. Does not apply to tooltips.</p></td>
</tr>
<tr class="odd">
<td><p>FontWeight</p></td>
<td><p>Applies to the presence status text. Does not apply to tooltips.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Applies to the distance between the border controlled by the BorderBrush and BorderThickness properties and the actual content of the MyPresenceChooser control.</p></td>
</tr>
<tr class="odd">
<td><p>Foreground</p></td>
<td><p>Applies to the text of the note, during editing or not, with a note set or not.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592520">HorizontalContentAlignment</a></p></td>
<td><p>Applies to the position of the presence text within the MyPresenceChooser control.</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://msdn2.microsoft.com/en-us/library/ms592525">VerticalContentAlignment</a></p></td>
<td><p>Applies to the position of the presence text within the MyPresenceChooser control.</p></td>
</tr>
</tbody>
</table>


### MyStatusArea

The following properties on [MyStatusArea](mystatusarea-class-microsoft-lync-controls_1.md) support restyling the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Action</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Background</p></td>
<td><p>The background color is painted to the entire area.</p></td>
</tr>
<tr class="even">
<td><p>BorderBrush</p></td>
<td><p>Placed around the entire control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="odd">
<td><p>BorderThickness</p></td>
<td><p>Placed around the entire control. Does not propagate to the list control or any other subcontrol.</p></td>
</tr>
<tr class="even">
<td><p>FontFamily</p></td>
<td><p>Applies to all visible fonts, Note control, and PresenceChooser control. Does not apply to tooltips.</p></td>
</tr>
<tr class="odd">
<td><p>FontWeight</p></td>
<td><p>Applies to all visible fonts, MyNoteBox control, and MyPresenceChooser control. Does not apply to tooltips.</p></td>
</tr>
<tr class="even">
<td><p>Padding</p></td>
<td><p>Applies to the distance between the border controlled by the BorderBrush and BorderThickness properties and the actual content of the MyStatusArea control.</p></td>
</tr>
<tr class="odd">
<td><p>Foreground</p></td>
<td><p>Applies to the text of the note, during editing or not, with a note set or not. Does not apply to any other text, for example name, or status.</p></td>
</tr>
</tbody>
</table>


## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

