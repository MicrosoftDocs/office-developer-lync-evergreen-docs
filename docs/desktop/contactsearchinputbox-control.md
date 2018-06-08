---
title: ContactSearchInputBox control
TOCTitle: ContactSearchInputBox control
ms:assetid: 7d8a263a-d04d-4b59-8960-9b11dc7de009
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945549(v=office.15)
ms:contentKeyID: 51541362
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# ContactSearchInputBox control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 ContactSearchInputBox control.

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
<td><p></p></td>
</tr>
</tbody>
</table>

## Control overview

Use the [ContactSearchInputBox](https://msdn.microsoft.com/en-us/library/hh379719\(v=office.15\)) control to enable users to search their organization for people based on name, phone number, or skill. The ContactSearchInputBox control displays a text box where users enter a search string. The search is executed automatically, one second after the search text is changed, or explicitly when the user presses **Enter** in the ContactSearchInputBox. When a search is complete, the results appear in a ContactSearchResultList control.

The ContactSearchInputBox and ContactSearchResultList controls, while related, are designed as separate controls to allow the developer to display search results and search input in separate locations on a page. Use the ContactSearch control in Microsoft Lync Control applications to display the ContactSearchInputBox and ContactSearchResultList controls together in the same location on a page.

![ContactSearchInputBox Control](images/JJ945549.ContactSearchInputBoxControl(Office.15).png "ContactSearchInputBox Control")

## Members

Notable ContactSearchInputBox control public properties and events relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The <a href="https://msdn.microsoft.com/en-us/library/hh363796(v=office.15)">Results</a> property can contain Lync 2013 API objects. The ContactSearchInputBox control maintains these Lync 2013 API objects and discards them when a new search is started or a search is cleared. If an application stores the Results property, it must manage the existing references to the discarded Lync 2013 API objects.</p></td>
</tr>
</tbody>
</table>

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
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363796(v=office.15)">Results</a> property</p></td>
<td><p>Gets a <a href="https://msdn.microsoft.com/en-us/library/hh345953(v=office.15)">SearchResultCollection</a> containing the results of the last completed search.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345991(v=office.15)">IsClearEnabled</a> property</p></td>
<td><p>Gets a bool value that specifies the visibility of the clear search button. This button is enabled whenever there is a value in the search text input box.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363628(v=office.15)">IsSkillSearchEnabled</a> property</p></td>
<td><p>Gets a bool value that indicates whether the skill search feature is enabled.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346468(v=office.15)">SearchState</a> property</p></td>
<td><p>Gets an enumeration value that indicates the current state of the search operation. Valid values are Cleared, Searching, Finished, and Error.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh378960(v=office.15)">SearchTextInput</a> property</p></td>
<td><p>Gets or sets a value that sets the current search criteria. When this property is set, any pending search operation is canceled, the search results are reset, and a new search operation is invoked with the given criteria. If this value is set to null, the pending search operation is canceled, the search results are reset, and the control returns to an idle Cleared state.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh364234(v=office.15)">SearchType</a> property</p></td>
<td><p>Gets or sets an enumerated value that represents the search type. The type is a SearchType enumeration. Possible values include:</p>
<ul>
<li><p>Name</p></li>
<li><p>Skill</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346592(v=office.15)">MaxResults</a> property</p></td>
<td><p>Gets or sets the maximum number of results to return.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) application development.

```xaml
<StackPanel>
  <controls:ContactSearchInputBox x:Name="searchInput"/>
  <controls:ContactSearchResultList
    ItemsSource="{Binding Results, ElementName=searchInput, Mode=OneWay}"
    ResultsState="{Binding SearchState, ElementName=searchInput, Mode=OneWay}"/>
</StackPanel>
```

## See also

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

