---
title: 'How to: Add logging to a Lync Controls application'
TOCTitle: 'How to: Add logging to a Lync Controls application'
ms:assetid: 6a7054ab-4de6-4e20-b9d6-e84fce14ee32
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933056(v=office.15)
ms:contentKeyID: 50877186
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
- csharp
---

# How to: Add logging to a Lync Controls application

Learn how to add logging to a Microsoft Windows Presentation Foundation (WPF) application that contains Microsoft Lync Controls. The application writes log entries to a file on the local computer when the Initialized event on the [PresenceIndicator](https://msdn.microsoft.com/en-us/library/hh345947\(v=office.15\)) control occurs.



**Applies to**: Lync 2013 | Lync Server 2013

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
Debug the application<br />
Sample logging output<br />
Additional resources</p></td>
<td></td>
</tr>
</tbody>
</table>

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
<td><p>When logging is used in WPF or Microsoft Silverlight applications, personal information such as telephone numbers can appear in logs. To protect confidential information, ensure logs are written to secure locations.<br />
<br />
In Silverlight applications, I/O operations typically are restricted to isolated storage and do not use the file system of the operating system. It is possible to work around this restriction by logging to a Web service or by using COM to access the local file system. For more information, see the MSDN articles <a href="http://go.microsoft.com/fwlink/?linkid=168185">Isolated Storage</a> and <a href="http://go.microsoft.com/fwlink/?linkid=168183">Isolated Storage In Silverlight 2</a>.</p></td>
</tr>
</tbody>
</table>

## Prerequisites

For a list of prerequisites, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

## Create a WPF application

### To create the WPF application

1.  Create a Lync WPF application.
    
    For more information, see [How to: Create a Silverlight page that displays a Lync presence control](how-to-create-a-silverlight-page-that-displays-a-lync-presence-control.md).

2.  In Window1.xaml, add a declaration for the Initialized event to the PresenceIndicator control.
    
    ```xaml
    <controls:PresenceIndicator Initialized="PresenceEventHandler" Source="sip:elise@contoso.com"/>
    ```

In the following procedures, add code to the Initialized event previously registered in the XAML text, implement a class derived from the **LogListener** class, implement the Write method of that class, and then add code to write entries to a file on the local computer.

### To implement a LogListener class

1.  In Window1.xaml.cs, add the following two using directives.
    
    ```csharp
    using Microsoft.Lync.Utilities.Logging;
    using System.IO;
    ```

2.  Implement a class derived from LogListener.
    
    ```csharp
    // Implementation of the LogListener class
    class MyListener : LogListener
    {
      FileStream fs;
      StreamWriter w;
    
      public MyListener()
      {
        // Change the file path to a valid value
        fs = new FileStream(@"C:\Temp\log.txt", FileMode.Create);
        w = new StreamWriter(fs, Encoding.UTF8);
     }
    
      public MyListener(LogLevel myLevel, string[] categories)
      { }
    
      public override void Write(LogEntry logEntry)
      {
        w.WriteLine("");
        w.WriteLine(logEntry.Message);
        w.Flush();
      }
    }
    ```

### To add LogListener to the logging framework

  - In the Window1 constructor, add the following statements to instantiate a LogListener object, and then add it to the Listeners collection.
    
    ```csharp
    MyListener defaultListener = new MyListener();   //Instantiate a LogListener object.
    Logger.AddListener(defaultListener);   //Add it to the Listeners collection.
    Logger.Level = LogLevel.Verbose;   //Set a value indicating the event types to be logged.
    ```

### To implement the Initialized event

1.  In Window1.xaml, right-click the Initialized event declaration, and then click **Navigate to Event Handler**.

2.  In the event handler, add code to create a LogEntry object, and then call the Write method on the Logger object.
    
    ```csharp
    private void PresenceEventHandler(object sender, EventArgs e)
    {
      LogEntry myEntry = new LogEntry(LogLevel.Verbose, null, null, "log text");
      myEntry.Level = LogLevel.Verbose;
      myEntry.Message = "A test log entry.";
      Logger.Write(myEntry);
    }
    ```

## Debug the application

Run the application and then browse to the text file on the local computer and review the log entry.

### To see logging in action

1.  Press **F5** to build and run the application.

2.  Browse to the text file to view the log entry.

## Sample logging output

    Created CollectionViewSource
    Populated ContactList Hash: 21551780
    Got groups from internal model
    Loaded ContactList Hash: 21551780
    Control 'ContactItem' entering 'OnLoaded'
    =================> CreateContact ContactItem, john@contoso.com
    Entering GetContactOrGroupByUri<String>:john@contoso.com
    Populated ContactItem Hash: 11207750
    Loaded ContactItem Hash: 11207750
    Control 'ContactItem' entering 'OnLoaded'
    =================> CreateContact ContactItem, jane@contoso.com
    Entering GetContactOrGroupByUri<String>:jane@contoso.com
    Populated ContactItem Hash: 56864589
    Loaded ContactItem Hash: 56864589
    Control 'ContactSearchInputBox' entering 'OnLoaded'

## See also

  - [What you can do in Lync SDK](what-you-can-do-in-lync-sdk.md)

  - [How to: Use log data to debug a Lync Controls applications](how-to-use-log-data-to-debug-a-lync-controls-applications.md)

