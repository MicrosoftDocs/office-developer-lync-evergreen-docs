---
title: ContactSearchResultList control
TOCTitle: ContactSearchResultList control
ms:assetid: 1d454543-46e0-483a-915a-6b5cd188796b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945538(v=office.15)
ms:contentKeyID: 51541339
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# ContactSearchResultList control

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the properties of the Microsoft Lync 2013 ContactSearchResultList control.

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
Control overview<br />
Members<br />
Code example<br />
Additional resources</p></td>
<td></td>
</tr>
</tbody>
</table>

## Control overview

Use the [ContactSearchResultList](https://msdn.microsoft.com/en-us/library/hh379201\(v=office.15\)) control to display the result of a search performed by the ContactSearchInputBox control.

The ContactSearchResultList control is intended to be used with and bound to a ContactSearchInputBox control. To bind a ContactSearchResultList control to a ContactSearchInputBox control, bind the properties as shown in the code sample later in this topic. The ContactSearchResultList control gets its results collection from the ContactSearchInputBox control.

The ContactSearchInputBox and ContactSearchResultList controls, while related, are designed as separate controls to allow the developer to display search results and search input in separate locations on a page.

![ContactSearchResultList](images/JJ945538.ContactSearchResultList_RTW_bugfix(Office.15).png "ContactSearchResultList")

## Members

Notable ContactSearchResultList control public properties relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](https://msdn.microsoft.com/en-us/library/jj933088\(v=office.15\)).

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
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh364112(v=office.15)">ResultsState</a> property</p></td>
<td><p>Gets or sets a SearchState enumeration representing the search status. Possible values include:</p>
<ul>
<li><p>Cleared</p></li>
<li><p>Searching</p></li>
<li><p>Finished</p></li>
<li><p>Error</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh379543(v=office.15)">SearchType</a> property</p></td>
<td><p>Gets or sets a SearchType enumeration representing the search type. Possible values include:</p>
<ul>
<li><p>Name</p></li>
<li><p>Skill</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346324(v=office.15)">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about the use of contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh346167(v=office.15)">ShowFriendlyName</a> property</p></td>
<td><p>Gets or sets a bool value that determines whether contacts in the list display as friendly names or URIs.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363732(v=office.15)">BotItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a bot item.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh379035(v=office.15)">GroupItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a group item.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363472(v=office.15)">PersonItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a person item.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363420(v=office.15)">TelephoneItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a telephone item.</p></td>
</tr>
<tr class="odd">
<td><p>ItemsSource property</p></td>
<td><p>This property specifies a collection that is used to generate the content of the ContactSearchResultList control. In typical applications, ContactSearchResultList is intended to display the results of a search that is performed using a ContactSearchInputBox control that appears elsewhere on the page. As shown in the following code example, to establish the connection between these controls, you should bind ItemsSource to the Results property of the ContactSearchInputBox control.</p></td>
</tr>
</tbody>
</table>

## Code example

The following example can be used for Silverlight and WPF application development.

``` xaml
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

