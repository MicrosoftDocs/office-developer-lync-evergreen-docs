---
title: Lync Controls common properties
TOCTitle: Lync Controls common properties
ms:assetid: b28c0d3b-30d9-413f-a746-e9d48ed0299f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945574(v=office.15)
ms:contentKeyID: 51541389
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync Controls common properties

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the common properties of the Microsoft Lync 2013Lync Controls.

**Last modified:** February 14, 2013

***Applies to:** Lync 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Properties common to all Lync Controls<br />
Additional resources</p></td>
<td></td>
</tr>
</tbody>
</table>

## Properties common to all Lync Controls

The properties listed in the following table are common to most Lync Controls in Microsoft Lync 2013 SDK.

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
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363627(v=office.15)">IsInResiliencyMode</a> property</p></td>
<td><p>Gets a bool value. The value true indicates that the server has entered a state of limited functionality and some features, such as presence, might not be available.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346560(v=office.15)">IsSignedIn</a> property</p></td>
<td><p>Gets a bool value indicating whether the application user is signed in to Microsoft Lync 2013.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345993(v=office.15)">InitializationFailed</a> property</p></td>
<td><p>Returns a Boolean value indicating whether initialization failed.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh379615(v=office.15)">InitializationErrorMessage</a> property</p></td>
<td><p>When InitializationFailed is true, this property stores a descriptive message generated during initialization.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh379166(v=office.15)">InitializationError</a> property</p></td>
<td><p>Provides an enumerated value of type <strong>[Microsoft.Lync.Controls.LyncControlInitializationError]</strong> to indicate the reason of the initialization failure.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363994(v=office.15)">InitializationCompleted</a> event</p></td>
<td><p>Indicates that the control completed its initialization.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363342(v=office.15)">ContextualInformation</a> property</p></td>
<td><p>Gets or sets data structure that provides contextual information for use with the contextual conversation feature. For more information about conversation context, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
</tbody>
</table>

## Additional resources

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

