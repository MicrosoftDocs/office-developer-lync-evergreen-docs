---
title: Restyle the ContactList control
TOCTitle: Restyle the ContactList control
ms:assetid: 335829ed-da14-43ec-b765-b27438cd2c57
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945542(v=office.15)
ms:contentKeyID: 51541344
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Restyle the ContactList control

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn how to restyle the [ContactList](contactlist-class-microsoft-lync-controls_1.md) control by changing property values to alter the appearance of the control.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Restyling a Lync Control<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Restyling a Lync Control

Use the following procedure to change the appearance of the control.

### To restyle a ContactList control

1.  Create a Microsoft Lync Controls application using the Microsoft Silverlight or Microsoft WPF template.
    
    For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

2.  In the XAML pane, add the XAML text to create a ContactList control.

3.  Add a style to set the [Background](contactcontentpresenter-background-property-microsoft-lync-controls_1.md) and [FontFamily](http://msdn2.microsoft.com/en-us/library/ms592513) properties on the control.
    
    ``` xaml
    <Grid>
            <Grid.Resources>
                <Style x:Key="MyContactListStyle" TargetType="Controls:ContactList">
                    <Setter Property="Background" Value="AliceBlue"/>
                    <Setter Property="FontFamily" Value="Courier New"/>
                </Style>
            </Grid.Resources>
            <Controls:ContactList Style="{StaticResource MyContactListStyle}"/>
    </Grid>
    ```

4.  Run the project.
    
    If the property values described in the previous step are used, the control background color is now blue and the font family is now Courier New.

## Additional resources

[Customizing Lync Controls](customizing-lync-controls.md)

