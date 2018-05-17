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

Use the [ContactSearchResultList](contactsearchresultlist-class-microsoft-lync-controls_1.md) control to display the result of a search performed by the ContactSearchInputBox control.

The ContactSearchResultList control is intended to be used with and bound to a ContactSearchInputBox control. To bind a ContactSearchResultList control to a ContactSearchInputBox control, bind the properties as shown in the code sample later in this topic. The ContactSearchResultList control gets its results collection from the ContactSearchInputBox control.

The ContactSearchInputBox and ContactSearchResultList controls, while related, are designed as separate controls to allow the developer to display search results and search input in separate locations on a page.

![ContactSearchResultList](images/JJ945538.ContactSearchResultList_RTW_bugfix(Office.15).png "ContactSearchResultList")

## Members

Notable ContactSearchResultList control public properties relating to unified communications appear in the following table. For a full list, see [Lync 2013 class libraries reference](lync-2013-class-libraries-reference.md).

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
<td><p><a href="contactsearchresultlist-resultsstate-property-microsoft-lync-controls_1.md">ResultsState</a> property</p></td>
<td><p>Gets or sets a SearchState enumeration representing the search status. Possible values include:</p>
<ul>
<li><p>Cleared</p></li>
<li><p>Searching</p></li>
<li><p>Finished</p></li>
<li><p>Error</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="contactsearchresultlist-searchtype-property-microsoft-lync-controls_1.md">SearchType</a> property</p></td>
<td><p>Gets or sets a SearchType enumeration representing the search type. Possible values include:</p>
<ul>
<li><p>Name</p></li>
<li><p>Skill</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="uclistbox-contextualinformation-property-microsoft-lync-controls_1.md">ContextualInformation</a> property</p></td>
<td><p>Gets or sets a data structure that contains information used to customize the information that accompanies messages. For more information about the use of contextual information, see <a href="contextual-lync-conversations.md">Contextual Lync conversations</a>.</p></td>
</tr>
<tr class="even">
<td><p><a href="uclistbox-showfriendlyname-property-microsoft-lync-controls_1.md">ShowFriendlyName</a> property</p></td>
<td><p>Gets or sets a bool value that determines whether contacts in the list display as friendly names or URIs.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uclistbox-botitemtemplate-property-microsoft-lync-controls_1.md">BotItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a bot item.</p></td>
</tr>
<tr class="even">
<td><p><a href="uclistbox-groupitemtemplate-property-microsoft-lync-controls_1.md">GroupItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a group item.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uclistbox-personitemtemplate-property-microsoft-lync-controls_1.md">PersonItemTemplate</a> property</p></td>
<td><p>Gets or sets the DataTemplate used to render a person item.</p></td>
</tr>
<tr class="even">
<td><p><a href="uclistbox-telephoneitemtemplate-property-microsoft-lync-controls_1.md">TelephoneItemTemplate</a> property</p></td>
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

## Additional resources

  - [Lync Controls reference](lync-controls-reference.md)

  - [Core concepts: Lync Controls](core-concepts-lync-controls.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

