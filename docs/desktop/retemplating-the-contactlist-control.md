---
title: Retemplating the ContactList control
TOCTitle: Retemplating the ContactList control
ms:assetid: f2ed1b57-4adb-4cf1-a8fc-d04de46fc0c2
ms:mtpsurl: https://msdn.microsoft.com/library/JJ945583(v=office.15)
ms:contentKeyID: 51541408
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Retemplating the ContactList control

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about visual template editing for individual parts of the ContactList control by using a step-by-step procedure to generate a visual template for a control part and adding elements to the template.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
ContactList control overview<br />
Edit the ContactListGroupItem template<br />
Edit the ContactListItem templates<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## ContactList control overview

Similar to the ContactCard control, there are several parts to a [ContactList](https://msdn.microsoft.com/library/hh363781\(v=office.15\)) control that you can customize. The ContactList control includes two parts:

  - The tree view that presents the hierarchical display of groups and contacts.

  - The toolbar that appears at the top of the contact list.

With Microsoft Expression Blend, you can edit a copy of the template for the ContactList control to customize the toolbar or add an additional component to the basic template for a ContactList control. However, to modify the appearance or behavior of the nodes within the tree view control, additional steps are required.

## Edit the ContactListGroupItem template

To customize the template that is used to display top-level group nodes on the ContactList control, complete the following procedure.

### To edit the ContactListGroupItem template

1.  The template for a group-level node is applied to an internal control type called [ContactListGroupItem](https://msdn.microsoft.com/library/hh345694\(v=office.15\)). This control is not directly accessible from the ContactList template. To get a copy of the template for a ContactListGroupItem control, you must temporarily add an instance of ContactListGroupItem to your form, and then edit a copy of its template.
    
    ```xaml
    <controls:ContactListGroupItem/> <!-- For temporary use -->
    ```

2.  In the resulting set of resources, a new style and control template for ContactListGroupItem appears.
    
    If you accepted the suggested name for the new style, output that resembles the following appears.
    
    ```xaml
        <Style x:Key="ContactListGroupItemStyle1" 
            TargetType="{x:Type controls:ContactListGroupItem}">
    ```

3.  Delete the reference to the ContactListGroupItem control that you created in step 1.

4.  Add final changes to the style and the embedded control template.
    
    When complete, you can use the new style and template in your ContactList control by setting the GroupItemContainerStyle property.
    
    ```xaml
        <controls:ContactList 
            GroupItemContainerStyle="{StaticResource ContactListGroupItemStyle1}"/>
    ```

## Edit the ContactListItem templates

The ContactList control uses a variety of DataTemplate resources to control the appearance of people, telephone numbers, bots, and nested distribution groups. There are two data templates for each type of contact:

  - Name View data template

  - Picture View data template

These views are sometimes referred to as OneLine and TwoLines view, respectively.

### To customize the DataTemplate for one or more views

1.  The template for a contact-level node is applied to an internal control type called ContactListItem. This control is not directly accessible from the ContactList template. To get a copy of the template for a ContactListItem, you must temporarily add an instance of ContactListItem to your form, and then edit a copy of its template.
    
    ```xaml
    <controls:ContactListItem/> <!-- For temporary use -->
    ```

2.  After you save a copy of the template, delete ContactListItem from your form.
    
    In the resulting set of resources, styles and templates used by the ContactListItem control appear. The DataTemplate objects can be used to customize the appearance of contacts in the ContactList control.
    
    For example, you can modify the template used to display person-type contacts in TwoLines view by customizing the data template that is identified by the key PersonContactItemDataTemplateTwoLines template. After you make your changes, apply the new template by setting the following property on the ContactList control.
    
    ```xaml
    <controls:ContactList PersonTwoLineItemTemplate=
            "{StaticResource PersonContactItemDataTemplateTwoLines}"/>
    ```

The following table identifies the templates that can be used to customize the appearance of contacts in the ContactList control.

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
<td><p><a href="https://msdn.microsoft.com/library/hh346461(v=office.15)">PersonItemTemplate</a></p></td>
<td><p>PersonContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Person</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh345827(v=office.15)">PersonTwoLineItemTemplate</a></p></td>
<td><p>PersonContactItemDataTemplateTwoLines</p></td>
</tr>
<tr class="odd">
<td><p>Telephone</p></td>
<td><p>OneLine</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh363694(v=office.15)">TelephoneItemTemplate</a></p></td>
<td><p>TelephoneContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Telephone</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh363498(v=office.15)">TelephoneTwoLineItemTemplate</a></p></td>
<td><p>TelephoneContactItemDataTemplateTwoLines</p></td>
</tr>
<tr class="odd">
<td><p>Bot</p></td>
<td><p>OneLine</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh363601(v=office.15)">BotItemTemplate</a></p></td>
<td><p>BotContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Bot</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh345890(v=office.15)">BotTwoLineItemTemplate</a></p></td>
<td><p>BotContactItemDataTemplateTwoLines</p></td>
</tr>
<tr class="odd">
<td><p>Group</p></td>
<td><p>OneLine</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh346626(v=office.15)">GroupItemTemplate</a></p></td>
<td><p>GroupContactItemDataTemplateOneLine</p></td>
</tr>
<tr class="even">
<td><p>Group</p></td>
<td><p>TwoLines</p></td>
<td><p><a href="https://msdn.microsoft.com/library/hh363757(v=office.15)">GroupTwoLineItemTemplate</a></p></td>
<td><p>GroupContactItemDataTemplateTwoLines</p></td>
</tr>
</tbody>
</table>

## See also

[Visual template editing for Lync Controls that use contentPresenters](visual-template-editing-for-lync-controls-that-use-contentpresenters.md)

