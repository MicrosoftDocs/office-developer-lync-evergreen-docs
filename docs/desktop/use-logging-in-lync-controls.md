---
title: Use logging in Lync Controls
TOCTitle: Use logging in Lync Controls
ms:assetid: 03ba79e2-edfb-4a01-835a-92c3f6486c3d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ937248(v=office.15)
ms:contentKeyID: 50877061
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Use logging in Lync Controls

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn how to use the **LogListener** object to record logging information in Microsoft Lync Controls applications, for both Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF).

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
Logging overview<br />
Adding logging<br />
Filtering logging output<br />
Writing log entries<br />
Logging in WPF applications<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Logging overview

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
<td><p>When logging is used in WPF or Silverlight applications, personal information such as telephone numbers can appear in logs. To protect confidential information, ensure that logs are saved to a secure location.</p>
<p>In Silverlight applications, I/O operations typically are restricted to isolated storage and do not use the file system of the operating system. It is possible to work around this restriction by logging to a Web service or by using COM to access the local file system.</p></td>
</tr>
</tbody>
</table>

## Adding logging

To add logging in a Lync Controls application, create one or more listener objects derived from the LogListener class. Then, use the AddListener method on the Logger object to add each listener to the Listeners collection.

Use the LogListener.Categories property to filter log entries. Individual listeners can be filtered by different categories. Categories are defined by the developer.

### LogListener object

LogListener has a default constructor and a constructor with parameters. The Write method on each LogListener object added to the Listeners collection is called when an event is processed. Developers should add code to the Write method to write to a Web service, the Event Viewer, or another type of storage.

``` csharp
// Sample implementation of the LogListener class
class MyListener : LogListener 
{
  // Constructor
  public MyListener()
  {}

  // Constructor
  public MyListener(LogLevel myLevel, string[] categories)
  {}

  // Write method
  public override void Write(LogEntry myEntry)
  {}
}
```

#### LogListener parameters

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Categories</p></td>
<td><p>An array of strings that specify the categories for a log entry, or a null reference. In Microsoft Visual Basic, the parameter value is Nothing.</p></td>
</tr>
<tr class="even">
<td><p>Level</p></td>
<td><p>Gets an enumerated value that represents the severity of the event. The type is a <strong>LogLevel</strong> enumeration.</p></td>
</tr>
</tbody>
</table>

### AddListener method

Use the AddListener method to add a LogListener to the Listeners collection as shown in the following example. Listeners is a read-only collection derived from [ReadOnlyCollection](http://go.microsoft.com/fwlink/?linkid=155357%26clcid=0x409).

``` csharp
Logger.AddListener(MyListener);
```

## Filtering logging output

Use the Level property to limit the log entries that appear in logging output. Log entries that do not match the setting of the Level property are ignored. Level is a property on the Logger, LogEntry, and LogListener objects. Level signifies the severity of the event. Filtering is performed on the basis of severity, first by the Logger, then by the LogListener, and finally by the LogEntry object. For example, if Logger.Level is set to Error, LogListener and LogEntry receive error messages and all settings for LogListener and LogEntry are ignored. There are five available levels, in order of perceived severity:

  - Off

  - Verbose

  - Info

  - Warning

  - Error

To change the log level, set the Level property on the Logger, LogListener, and LogEntry objects.

``` csharp
// Set the level on the Logger object
Logger.Level = LogLevel.Info;

// Set the level on the LogEntry object
myEntry.Level = LogLevel.Error;

// Set the level on the LogListener object
MyListener.Level = LogLevel.Warning;
```

## Writing log entries

To write log entries, first override the Write and WriteExtended methods. In the event handlers, call the Write or WriteExtended methods on the Logger object. These methods use the Write method on the LogListener objects to write logging data.

## Logging in WPF applications

Use the TraceLogListener object to provide trace output in Lync Controls WPF applications.

## See also

  - [Beyond the basics: Lync Controls](beyond-the-basics-lync-controls.md)

