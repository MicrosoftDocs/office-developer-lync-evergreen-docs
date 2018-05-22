---
title: Troubleshooting Lync Controls applications
TOCTitle: Troubleshooting Lync Controls applications
ms:assetid: 8c6213e2-e820-43c3-9e21-7e5c52bb3bba
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933104(v=office.15)
ms:contentKeyID: 50877239
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Troubleshooting Lync Controls applications

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about troubleshooting Microsoft Lync 2013 Controls application by using [UCBase](https://msdn.microsoft.com/en-us/library/hh364242\(v=office.15\)) class read-only properties to display Microsoft Lync Control initialization errors at runtime.

**Last modified:** December 26, 2012

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Troubleshooting overview<br />
Code example: Display initialization errors<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Troubleshooting overview

Use read-only properties inherited from the [UCBase](https://msdn.microsoft.com/en-us/library/hh364242\(v=office.15\)) class to display Microsoft Lync Control initialization errors at runtime. Lync Controls automatically establish a connection to Microsoft Lync 2013 when they load. The first control to load establishes the connection, which is shared by all subsequently loaded controls.

When a Lync Control fails to initialize the connection to Lync 2013, the initialization state and error are stored in the following properties on the control.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh379166(v=office.15)">InitializationError</a></p></td>
<td><p>Provides an enumeration value of type <a href="https://msdn.microsoft.com/en-us/library/hh363873(v=office.15)">LyncControlInitializationError</a> to indicate the reason for the initialization failure.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh345993(v=office.15)">InitializationFailed</a></p></td>
<td><p>Returns a Boolean value indicating whether initialization failed.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/en-us/library/hh379615(v=office.15)">InitializationErrorMessage</a></p></td>
<td><p>Provides a string message describing the error.</p></td>
</tr>
</tbody>
</table>

## Code example: Display initialization errors

Use the following XAML code to display Lync Control initialization errors at runtime.

``` xaml
<StackPanel>
  <TextBlock HorizontalAlignment="Left" Text="Application Initialization Failed:" />
  <TextBox Text="{Binding InitializationFailed, ElementName=presence, Mode=OneWay}" />
  <TextBlock HorizontalAlignment="Left" Text="Application Initialization Error:" />
  <TextBox Text="{Binding InitializationErrorMessage, ElementName=presence, Mode=OneWay}" />
  <controls:PresenceIndicator Source="sip:elise@contoso.com" />
</StackPanel>
```

## Additional resources

  - [Beyond the basics: Lync Controls](beyond-the-basics-lync-controls.md)

