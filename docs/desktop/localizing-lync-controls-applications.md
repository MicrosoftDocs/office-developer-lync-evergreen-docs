---
title: Localizing Lync Controls applications
TOCTitle: Localizing Lync Controls applications
ms:assetid: 46d3185a-b8d6-4cae-b259-bab5748edcfc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937328(v=office.15)
ms:contentKeyID: 50877161
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Localizing Lync Controls applications

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about localizing the strings displayed on the Microsoft Lync 2013 Controls that are in Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Localizing overview<br />
Localizing Microsoft Silverlight applications<br />
Localizing Microsoft WPF applications<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Localizing overview

To localize a Lync Controls application, create a separate set of resources (such as strings and images) that are appropriate for the users of each targeted culture or locale and that can be retrieved dynamically depending on the culture and locale.

## Localizing Microsoft Silverlight applications

For localization information, see the MSDN Library article [Localizing Silverlight-based Applications](http://go.microsoft.com/fwlink/?linkid=204377%26clcid=0x409). To correctly display the private use area (PUA) and double-byte characters in a Lync Controls Silverlight application, explicitly set the font, as shown in the following example.

```xaml
  <controls:MyStatusArea Name="mystatusarea1" Height="24" FontFamily="Tahoma, Segoe UI, Lucida Sans Unicode, Lucida Grande, SimSun, SimSun-18030"/>
```

## Localizing Microsoft WPF applications

For localization information, see the MSDN Library article [Localizing a WPF Application](http://go.microsoft.com/fwlink/?linkid=204378%26clcid=0x409).

## See also

  - [Beyond the basics: Lync Controls](beyond-the-basics-lync-controls.md)

