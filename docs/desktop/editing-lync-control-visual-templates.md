---
title: Editing Lync Control visual templates
TOCTitle: Editing Lync Control visual templates
ms:assetid: a05042f0-7851-4b42-9b68-29be526774a2
ms:mtpsurl: https://msdn.microsoft.com/library/JJ945567(v=office.15)
ms:contentKeyID: 51541381
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Editing Lync Control visual templates

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the concept of customizing the visual template of Microsoft Lync 2013 Controls to provide a customized visual appearance in your application.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Editing overview<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Editing overview

Assigning a new visual template to a Microsoft Lync Control permits fine-grained control over layout and design. With a new template, the Lync Control can be altered to match preexisting corporate or application styles.

To customize the visual template ("retemplate") of a control:

1.  Define a [Style](http://msdn2.microsoft.com/library/ms600899) property targeting the control you'll modify in XAML.

2.  Set the [Template](http://msdn2.microsoft.com/library/ms592524) property on the style to a new [ControlTemplate](http://msdn2.microsoft.com/library/ms609827) instance that incorporates your design.

3.  Apply your new Style to the control.

To create a new ControlTemplate, edit a copy of the existing template for the control you customize. A simple way to get a copy of the existing template for a control is to use Microsoft Expression Blend 4.

## See also

  - [Editing the template of a Lync Control](editing-the-template-of-a-lync-control.md)

  - [Visual template editing for Lync Controls that use contentPresenters](visual-template-editing-for-lync-controls-that-use-contentpresenters.md)

  - [Customizing Lync Controls](customizing-lync-controls.md)

