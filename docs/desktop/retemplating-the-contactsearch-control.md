---
title: Retemplating the ContactSearch control
TOCTitle: Retemplating the ContactSearch control
ms:assetid: 6f76e878-38bc-4f1b-9d1b-da2566d11018
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945563(v=office.15)
ms:contentKeyID: 51541375
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Retemplating the ContactSearch control

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about visual template editing for individual parts of the ContactSearch control by using a step-by-step procedure to generate a visual template for a control part and adding elements to the template.

**Last modified:** February 14, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
ContactSearch control overview<br />
Edit the ContactSearchResultlistitem templates<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## ContactSearch control overview

The template for the [ContactSearch](https://msdn.microsoft.com/en-us/library/hh379436\(v=office.15\)) control includes two parts:

  - [ContactSearchInputBox](https://msdn.microsoft.com/en-us/library/hh379719\(v=office.15\)) control

  - [ContactSearchResultList](https://msdn.microsoft.com/en-us/library/hh379201\(v=office.15\)) control

To change the appearance of either control, embed them in your project individually and then retemplate the control.

## Edit the ContactSearchResultlistitem templates

To modify the templates used to display search results within the ContactSearchResultList control, use a technique similar to the one used to edit contact list items in [Retemplating the ContactList control](retemplating-the-contactlist-control.md).

ContactSearchResultList uses a variety of [DataTemplate](http://msdn2.microsoft.com/en-us/library/ms589297) resources to control the appearance of people, telephone numbers, bots, and distribution lists. To customize the DataTemplate for one or more of these contact types, complete the following procedure.

### To edit the ContactSearchResultListItem templates

1.  Before you begin, temporarily add a reference to the following namespace in your form.
    
    ``` xaml
    xmlns:internal=
    "clr-namespace:Microsoft.Lync.Controls.Internal;assembly=Microsoft.Lync.Controls"
    ```

2.  The template for a contact search result is applied to an internal control type called ContactSearchResultListItem. This control is not directly accessible from the ContactSearchResultList template. To get a copy of the templates used by ContactSearchResultListItem, you must temporarily add an instance of ContactSearchResultListItem to your form, and then edit a copy of its template.
    
    ``` xaml
    <internal:ContactSearchResultListItem/> <!-- For temporary use -->
    ```
    
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
    <td><p>Before moving to step 3, ensure that you reference the internal namespace defined earlier.</p></td>
    </tr>
    </tbody>
    </table>

3.  After you save a copy of the template, delete ContactSearchResultListItem and the internal namespace definition from your form.

4.  In the resulting set of resources, styles and templates used by the ContactSearchResultListItem control appear. The DataTemplate objects can be used to customize the appearance of contacts in the ContactSearchResultList control. For example, you can modify the template used to display person-type contacts by customizing the data template that is identified by the key PersonSearchResultItemDataTemplate template. After you make your changes, apply the new template by setting the following property on the ContactSearchResultList control.
    
    ``` xaml
    <controls:ContactSearchResultList 
            PersonItemTemplate="{StaticResource PersonSearchResultItemDataTemplate}"/>
    ```

The following table identifies the templates that can be used to customize the appearance of contacts in the ContactSearchResultList control.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Contact type</p></th>
<th><p>ContactSearchResultList property name</p></th>
<th><p>Name of corresponding DataTemplate</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Person</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363472(v=office.15)">PersonItemTemplate</a></p></td>
<td><p>PersonSearchResultItemDataTemplate</p></td>
</tr>
<tr class="even">
<td><p>Telephone</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363420(v=office.15)">TelephoneItemTemplate</a></p></td>
<td><p>TelephoneSearchResultItemDataTemplate</p></td>
</tr>
<tr class="odd">
<td><p>Bot</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh363732(v=office.15)">BotItemTemplate</a></p></td>
<td><p>BotSearchResultItemDataTemplate</p></td>
</tr>
<tr class="even">
<td><p>Group</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh379035(v=office.15)">GroupItemTemplate</a></p></td>
<td><p>DistributionListSearchResultItemDataTemplate</p></td>
</tr>
</tbody>
</table>

## See also

[Visual template editing for Lync Controls that use contentPresenters](visual-template-editing-for-lync-controls-that-use-contentpresenters.md)

