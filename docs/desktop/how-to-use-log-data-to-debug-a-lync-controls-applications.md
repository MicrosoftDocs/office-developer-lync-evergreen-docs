---
title: 'How to: Use log data to debug a Lync Controls applications'
TOCTitle: 'How to: Use log data to debug a Lync Controls applications'
ms:assetid: b495ddad-2ff9-4581-a680-24a760209dee
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933145(v=office.15)
ms:contentKeyID: 50877281
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
---

# How to: Use log data to debug a Lync Controls applications

Learn how to use log data to debug a Microsoft Windows Presentation Foundation (WPF) application that contains Microsoft Lync Controls. This topic builds on [How to: Add logging to a Lync Controls application](how-to-add-logging-to-a-lync-controls-application.md), which describes how to enable logging.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Create a WPF application<br />
Debug the Lync Is Not Running error<br />
Debug a malformed URI<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

For a list of prerequisites, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

## Create a WPF application

Create a Lync WPF application with logging enabled and then add XAML code that contains an error.

### To create the application

1.  Create a Lync WPF application with logging enabled.
    
    For more information, see [How to: Add logging to a Lync Controls application](how-to-add-logging-to-a-lync-controls-application.md).

2.  In Page.xaml, add the following XAML, which sets the [Source](https://msdn.microsoft.com/en-us/library/hh363511\(v=office.15\)) property to an invalid URI.
    
    ```xaml
    <controls:StartInstantMessagingButton Source="sip:typo@contoso"/>
    ```

3.  Exit Microsoft Lync 2013.

## Debug the Lync Is Not Running error

To experience how easy it is to use log data, find the message created after exiting Lync 2013.

### To set up and run the Lync Is Not Running scenario

1.  Exit Lync 2013.

2.  Build and run the application created in the previous procedure.
    
    In the log file, output that resembles the following message appears.
    
        2010-07-21T13:16:05.4663269-07:00 : Error : MThreadId=10 : Categories=LyncServiceProvider : Message=UCClientInitializationFailed:Microsoft Lync 4.0.7400.542 or later is not running and it is required for this application. Please start Lync to resolve this issue.

## Debug a malformed URI

Review the message created by a malformed URI after you exited Lync 2013 in the previous procedure.

### To run the Lync Is Not Running scenario

1.  The Lync 2013 session ended in the previous procedure. Restart Lync 2013.

2.  Build and run the application created in the first procedure.
    
    In the log file, output that resembles the following message appears.
    
        Unable to create IContactModel from ContactUri.  Uri='typo@contoso.'
        Unable to create a contact for 'sip:typo@contoso.'. System.ArgumentException: Value does not fall within the expected range.

3.  Fix the malformed URI: sip:typo@contoso.com.

4.  Build and run the application.

## See also

  - [What you can do with Lync Controls](what-you-can-do-with-lync-controls.md)

  - [How to: Add logging to a Lync Controls application](how-to-add-logging-to-a-lync-controls-application.md)

