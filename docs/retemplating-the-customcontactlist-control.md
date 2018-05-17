---
title: Retemplating the CustomContactList control
TOCTitle: Retemplating the CustomContactList control
ms:assetid: d8f509aa-7340-45de-8380-39e3df55501b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945581(v=office.15)
ms:contentKeyID: 51541405
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Retemplating the CustomContactList control

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about visual template editing for individual parts of the CustomContactList control by using a step-by-step procedure to generate a visual template for a control part and adding elements to the template.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
CustomContactList control overview<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## CustomContactList control overview

The [CustomContactList](customcontactlist-class-microsoft-lync-controls_1.md) control uses different DataTemplate resources to control the appearance of people, telephone numbers, bots, and distribution lists. There are two data templates for each type of contact:

  - Name View template

  - Picture View template

These views are sometimes referred to as OneLine and TwoLines view, respectively.

### To customize the DataTemplate for one or more view

1.  The template for a contact within the CustomContactList control is applied to a control called [CustomContactListItem](customcontactlistitem-class-microsoft-lync-controls_1.md). CustomContactListItem is not directly accessible from the CustomContactList template. To get a copy of the template for a CustomContactListItem, temporarily add an instance of CustomContactListItem to your form and then edit a copy of its template.
    
        <controls:CustomContactListItem/> <!-- For temporary use -->

2.  After you save a copy of the template, delete CustomContactListItem from your form.

3.  In the resulting set of resources, styles and templates used by the CustomContactListItem control appear. The DataTemplate objects can be used to customize the appearance of contacts in the CustomContactList control.
    
    For example, you can modify the template used to display person-type contacts in TwoLines view by customizing the data template that is identified by the key PersonContactItemDataTemplateTwoLines template. After you make your changes, apply the new template by setting the following property on the CustomContactList control.
    
        <controls:CustomContactList PersonTwoLineItemTemplate=
                "{StaticResource PersonContactItemDataTemplateTwoLines}"/>

The following table lists the templates that can be used to customize the appearance of contacts in the CustomContactList control.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Contact type</p></th>
<th><p>Layout view</p></th>
<th><p>ContactList property name</p></th>
<th><p>Name of corresponding DataTemplate</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Person</p></td>
<td><p>OneLine</p></td>
<td><p><a href="uclistbox-personitemtemplate-property-microsoft-lync-controls_1.md">PersonItemTemplate</a></p></td>
<td><p>PersonContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Person</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="customcontactlist-persontwolineitemtemplate-property-microsoft-lync-controls_1.md">PersonTwoLineItemTemplate</a></p></td>
<td><p>PersonContactItemDataTemplateTwoLines</p></td>
</tr>
<tr class="odd">
<td><p>Telephone</p></td>
<td><p>OneLine</p></td>
<td><p><a href="uclistbox-telephoneitemtemplate-property-microsoft-lync-controls_1.md">TelephoneItemTemplate</a></p></td>
<td><p>TelephoneContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Telephone</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="customcontactlist-telephonetwolineitemtemplate-property-microsoft-lync-controls_1.md">TelephoneTwoLineItemTemplate</a></p></td>
<td><p>TelephoneContactItemDataTemplateTwoLines</p></td>
</tr>
<tr class="odd">
<td><p>Bot</p></td>
<td><p>OneLine</p></td>
<td><p><a href="uclistbox-botitemtemplate-property-microsoft-lync-controls_1.md">BotItemTemplate</a></p></td>
<td><p>BotContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Bot</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="customcontactlist-bottwolineitemtemplate-property-microsoft-lync-controls_1.md">BotTwoLineItemTemplate</a></p></td>
<td><p>BotContactItemDataTemplateTwoLines</p></td>
</tr>
<tr class="odd">
<td><p>Group</p></td>
<td><p>OneLine</p></td>
<td><p><a href="uclistbox-groupitemtemplate-property-microsoft-lync-controls_1.md">GroupItemTemplate</a></p></td>
<td><p>GroupContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Group</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="customcontactlist-grouptwolineitemtemplate-property-microsoft-lync-controls_1.md">GroupTwoLineItemTemplate</a></p></td>
<td><p>GroupContactItemDataTemplateTwoLines</p></td>
</tr>
</tbody>
</table>


## Additional resources

[Visual template editing for Lync Controls that use contentPresenters](visual-template-editing-for-lync-controls-that-use-contentpresenters.md)

