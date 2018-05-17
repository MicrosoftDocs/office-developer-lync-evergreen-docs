---
title: Retemplating the ContactCard control
TOCTitle: Retemplating the ContactCard control
ms:assetid: bd545e3b-6ebe-420e-a0a2-c7a7003de68c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945577(v=office.15)
ms:contentKeyID: 51541396
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Retemplating the ContactCard control

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about advanced visual template editing for Microsoft Lync 2013 Controls that inherit the ContactContactPresenter control.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
ContactCard control overview<br />
Understanding the ContactContentPresenter control<br />
Editing the ContactCardDetailsPersonDataTemplate<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## ContactCard control overview

If you follow the steps in [Editing the template of a Lync Control](editing-the-template-of-a-lync-control.md) to retemplate a PresenceIndicator control, but perform the operation on a [ContactCard](contactcard-class-microsoft-lync-controls_1.md) control, the operation generates new styles, templates, and other resources in your resource dictionary. The template for the ContactCard control can be found by searching for the following string.

``` xaml
    <ControlTemplate TargetType="{x:Type controls:ContactCard}">
```

This template includes four parts, arranged in a simple vertical StackPanel:

  - The ContactNote instance, which appears at the top of the Microsoft Lync 2013 Contact Card.

  - A [ContactContentPresenter](contactcontentpresenter-class-microsoft-lync-controls_1.md) instance that handles the primary contact information area of the Contact Card. This area is the part of the Contact Card that shows the contact’s name, photo, and basic information.

  - A small Grid that defines the toolbar appearing at the bottom of the Contact Card.

  - A second ContactContentPresenter instance that handles the details section of the Contact Card. This area is the part of the Contact Card appearing only after clicking the toggle button in the lower-right corner. When ContactContentPresenter is displayed, a set of tabs appear that, depending on the type of contact, provide more detailed information.

You can easily add another section to the Contact Card by inserting it into this StackPanel in the desired location. However, if you want to make changes to one of the existing sections, a closer examination of the XAML is required.

## Understanding the ContactContentPresenter control

Review the ContactCard template appearing in the resource dictionary that you previously created. You can find this template by searching for the following string.

``` xaml
    <ControlTemplate TargetType="{x:Type controls:ContactCard}">
```

Near the bottom of this template is a ContactContentPresenter control appears in a Grid called PART\_DetailsContainer. This control is responsible for displaying the set of tabs that show details about the contact when the user clicks the toggle button in the lower-right corner of the Contact Card. It uses a variety of different templates to accomplish this task. The next few paragraphs discuss how ContactContentPresenter controls work. In the last section of this topic, you add a custom tab option to a Contact Card by editing a data template.

Like the [ContentPresenter](http://msdn2.microsoft.com/en-us/library/ms609804) control from which ContactContentPresenter is derived, ContactContentPresenter includes a Content property that is bound to an arbitrary data model. In this case, the data model is an internal structure that encapsulates the contact that was selected by the parent control’s Source property.

A ContentPresenter instance uses the template referenced by its ContentTemplate property to render the Content data. When using ContactContentPresenter, directly setting the Content property is not necessary. Instead, the ContactContentPresenter control supports automatic selection of this template, based on the type of contact that is provided.

The ContactContentPresenter control includes four dependency properties that identify the specific data template used for different contact types.

``` xaml
  PersonContentTemplate="{StaticResource ContactCardDetailsPersonDataTemplate}" 
  GroupContentTemplate="{StaticResource ContactCardDetailsDistributionListDataTemplate}" 
  BotContentTemplate="{StaticResource ContactCardDetailsBotDataTemplate}" 
  TelephoneContentTemplate="{StaticResource ContactCardDetailsTelephoneDataTemplate}" 
```

These properties refer to data templates that are defined elsewhere in the resource dictionary for your Contact Card.

The summary portion of the Contact Card, which displays the photo, name, and availability information, also uses a ContentPresenter control to render its content. The process of identifying the data templates for this control is identical to the process described for the details section of the Contact Card.

The following table summarizes the data templates that you can modify.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Contact type</p></th>
<th><p>ContactCard section</p></th>
<th><p>Name of corresponding data template</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Person</p></td>
<td><p>Brief</p></td>
<td><p>ContactCardBriefPersonDataTemplate</p></td>
</tr>
<tr class="even">
<td><p>Person</p></td>
<td><p>Details</p></td>
<td><p>ContactCardDetailsPersonDataTemplate</p></td>
</tr>
<tr class="odd">
<td><p>Telephone</p></td>
<td><p>Brief</p></td>
<td><p>ContactCardBriefTelephoneDataTemplate</p></td>
</tr>
<tr class="even">
<td><p>Telephone</p></td>
<td><p>Details</p></td>
<td><p>ContactCardDetailsTelephoneDataTemplate</p></td>
</tr>
<tr class="odd">
<td><p>Bot</p></td>
<td><p>Brief</p></td>
<td><p>ContactCardBriefBotDataTemplate</p></td>
</tr>
<tr class="even">
<td><p>Bot</p></td>
<td><p>Details</p></td>
<td><p>ContactCardDetailsBotDataTemplate</p></td>
</tr>
<tr class="odd">
<td><p>Group</p></td>
<td><p>Brief</p></td>
<td><p>ContactCardBriefDistributionListDataTemplate</p></td>
</tr>
<tr class="even">
<td><p>Group</p></td>
<td><p>Details</p></td>
<td><p>ContactCardDetailsDistributionListDataTemplate</p></td>
</tr>
</tbody>
</table>


In the next section of this topic, a new tab option is added to the details section of a Contact Card data template. You can customize the appearance of any section of the Contact Card by editing the appropriate data templates.

## Editing the ContactCardDetailsPersonDataTemplate

When bound to a person’s SIP URI, the ContactCard control expands to display a set of tabs. The first tab lists detailed contact information, and the second shows organizational information for the selected person. To add a third tab, retemplate the ContactCard control and then edit the ContactCardDetailsPersonDataTemplate data template.

To retemplate the ContactCard control, follow the standard retemplating procedure described earlier. When you complete this procedure, copies of the styles, templates, and other resources used by the ContactCard control appear in the resource dictionary. Search for the ContactCardDetailsPersonDataTemplate template in your resource dictionary.

``` xaml
    <DataTemplate x:Key="ContactCardDetailsPersonDataTemplate">
```

Within ContactCardDetailsPersonDataTemplate, insert the following XAML into the list of existing tab options.

``` xaml
    <TabItem Header="My Custom Tab" MinWidth="90"
         Style="{StaticResource EntityCardDetailsTabItemStyle}" 
         Background="{Binding Background, RelativeSource={RelativeSource TemplatedParent}}">
         <StackPanel>
             <TextBlock Text="This tab contains"/>
             <TextBlock Text="my customized"/>
             <TextBlock Text="functionality"/>
             <TextBlock Text="for ContactCard"/>
         </StackPanel>
    </TabItem>
```

When you run the application and expand the Contact Card, **My Custom Tab** appears in the details section.

## Additional resources

[Visual template editing for Lync Controls that use contentPresenters](visual-template-editing-for-lync-controls-that-use-contentpresenters.md)

