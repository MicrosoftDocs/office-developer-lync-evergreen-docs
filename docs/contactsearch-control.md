---
title: ContactSearch control
TOCTitle: ContactSearch control
ms:assetid: 3196935c-0328-478d-a794-b297cb3d2725
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945544(v=office.15)
ms:contentKeyID: 51541352
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# ContactSearch control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 ContactSearch control.


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
<td></td>
</tr>
</tbody>
</table>


## Control overview

Use the [ContactSearch](contactsearch-class-microsoft-lync-controls_1.md) control in Microsoft Lync Control applications to display the ContactSearchInputBox and ContactSearchResultList controls in the same location on a page. To display search results and search input in separate locations on a page, use the ContactSearchInputBox and ContactSearchResultList controls as separate controls.

![ContactSearch](images/JJ945544.ContactSearch_RTW_bugfix(Office.15).png "ContactSearch")

## Members

Notable ContactSearch control public properties relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](lync-2013-class-libraries-reference.md).

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
<td><p><a href="contactsearch-searchtype-property-microsoft-lync-controls_1.md">SearchType</a> property</p></td>
<td><p>Gets or sets the currently selected search type. The type is a SearchType enumeration. Possible values include:</p>
<ul>
<li><p>Skill</p></li>
<li><p>Name</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="contactsearch-contextualinformation-property-microsoft-lync-controls_1.md">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about using contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="odd">
<td><p><a href="contactsearch-maxresults-property-microsoft-lync-controls_1.md">MaxResults</a> property</p></td>
<td><p>The maximum number of results to return.</p></td>
</tr>
</tbody>
</table>


## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

``` xaml
<StackPanel>
  <controls:ContactSearch/>
</StackPanel>
```

## Additional resources

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

