---
title: Application strategies in Lync Controls applications
TOCTitle: Application strategies in Lync Controls applications
ms:assetid: e5ca6227-cda8-486e-a770-8595a9cb9189
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933241(v=office.15)
ms:contentKeyID: 50877387
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# Application strategies in Lync Controls applications

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the application strategies used in developing Microsoft Lync 2013 Controls applications.

**Last modified:** February 22, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Application strategy overview<br />
Add presence to an existing WPF application<br />
Add presence to an existing Silverlight application<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Application strategy overview

Use Microsoft Lync Controls to add presence and availability information about Lync users and PIC users to your new or existing applications. Lync Controls such as the StartInstantMessagingButton control provide a one-click way to start a conversation with Lync user or PIC user

Lync Control applications require the user to sign in to Microsoft Lync 2013. A Lync Controls application connects to Lync Server 2013 through a single out-of-process connection to Lync 2013. The out-of-process connection to the Lync client endpoint logic enables the custom window to have a lightweight memory and process footprint.

The application is a WPF or Silverlight window that contains Lync Controls and may also have custom logic. For Windows Forms and WPF applications, it is common to use one thread for the UI and a separate thread for tasks such as database access or other asynchronous operations. However, in Silverlight Lync Controls applications, keep all application logic in the UI thread. For event handling in Silverlight Lync Controls applications, you must marshal relevant event data to your UI thread using something like Dispatcher.Invoke. To do otherwise raises a cross-thread exception.

## Add presence to an existing WPF application

To add Lync Controls to an existing WPF application, add project references for the Lync Control DLLs and add XAML code to create the Lync Controls.

### To add presence to an existing WPF application

1.  Sign in to Microsoft Lync 2013.

2.  In Microsoft Visual Studio, add project references to the WPF versions of the following libraries:
    
      - Microsoft.Lync.Controls.dll
    
      - Microsoft.Lync.Controls.Framework.dll
    
      - Microsoft.Lync.Model.dll
    
      - Microsoft.Lync.Utilities.dll

3.  On the appropriate XAML page, add the following XAML text to declare the Lync Controls namespace.
    
    ```xaml
    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
    ```

4.  Author the appropriate XAML code to add the Lync Controls. For example, the following XAML adds a [MyStatusArea](https://msdn.microsoft.com/en-us/library/hh363503\(v=office.15\)) control.
    
    For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).
    
    ```xaml
    <StackPanel>
      <controls:MyStatusArea PhotoDisplayMode="Small"/>
    </StackPanel>
    ```

5.  Build and run the application.

## Add presence to an existing Silverlight application

To add Lync Controls to an existing Silverlight application, add project references for the Lync Control DLLs and add XAML code to create the Lync Controls.

### To add presence to an existing Silverlight application

1.  Sign in to Lync 2013.

2.  Add project references to the Silverlight versions of the following libraries:
    
      - Microsoft.Lync.Controls.dll
    
      - Microsoft.Lync.Controls.Framework.dll
    
      - Microsoft.Lync.Model.dll
    
      - Microsoft.Lync.Utilities.dll

3.  On the appropriate XAML page, add the following XAML text to declare the Lync 2013 namespace.
    
    ```xaml
    xmlns:controls="clr-namespace:Microsoft.Lync.Controls;assembly=Microsoft.Lync.Controls"
    ```

4.  Author the appropriate XAML code to add the Lync Controls. For example, the following XAML adds a [MyStatusArea](https://msdn.microsoft.com/en-us/library/hh363503\(v=office.15\)) control.
    
    For more information, see [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md).
    
    ```xaml
    <StackPanel>
      <controls:MyStatusArea PhotoDisplayMode="Small"/>
    </StackPanel>
    ```

5.  Build and run the application.

## See also

  - [Core concepts in Lync 2013 SDK](core-concepts-in-lync-2013-sdk.md)

  - [Lync Controls reference](lync-controls-reference.md)

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

