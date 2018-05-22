---
title: 'How to: Debug a Lync Server SIP application'
TOCTitle: 'How to: Debug a Lync Server SIP application'
ms:assetid: 35964c9d-eae7-444e-aae1-c326f80e1ad1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439089(v=office.15)
ms:contentKeyID: 57096262
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Debug a Lync Server SIP application

Learn how to debug a SIP application in a Microsoft Lync Server 2013 deployment.


_**Applies to:** Lync Server 2013_

To debug a SIP application that is loaded into a Lync Server 2013 deployment, trace the execution of the Microsoft SIP Processing Language (MSPL) script that is embedded in the application manifest in addition to the managed application components.

## Debugging MSPL script

MSPL supports tracing functionality through the built-in [Log](https://msdn.microsoft.com/en-us/library/hh364642\(v=office.15\)) function that can be called throughout the script block to log run-time data in the Windows Event Viewer log on the server or the ApiLogger utility that is distributed with Microsoft Lync Server 2013 SDK. The following example shows the C\# syntax for the **Log** function.

``` csharp
void Log(string name, bool detail, params string[] messages);
```

The name parameter specifies the name of the log. It can be "Event, Error, or Debugr. The first two correspond to the Windows Event Viewer log. Debugr is the application-specific ApiLogger debug utility. The messages parameters contain zero or more messages that appear in the specified log. For the "Event" log, the supplied messages are logged as a warning in Windows Event Viewer. For the "Error" log, the supplied messages appear as an error in Windows Event Viewer.

The level of detail for each message in the log is set with the second parameter. If it is false, only the "Method", "To", "From", and "Request-Uri" headers are logged, together with the date/time and the application URI. If it is true, the whole SIP message is logged.

## Using ApiLogger

By default, the ApiLogger.exe utility is installed in the %progfile%\\Microsoft Lync Server 2013\\SDK\\Bin directory. To run this utility, start the executable by double-clicking the ApiLogger.Exe file or issue the following command from a Command window.

``` 
 "c:\program files\Microsoft Lync Server 2013\SDK\Bin" ApiLogger.exe
```

The utility prompts you to restart the Lync Server Front End role. To do so, issue the following command from another Command window.

    Net stop rtcsrv
    Net start rtcsrv

You can also restart this service by using the Services utility. Right-click the **Lync Server Front-End** entry, and then selecting **Restart**.

When the RtcSrv service is restarted, ApiLogger is connected to the server and the debug messages from all the loaded MSPL scripts appear in the ApiLogger window.

The following table describes the ApiLogger error messages.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Application error message</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&quot;Branched requests must be sent on new client transactions.&quot;</p></td>
<td><p>The application is trying to call <a href="https://msdn.microsoft.com/en-us/library/jj266211(v=office.15)">SendRequest(Request)</a> two times on a <a href="https://msdn.microsoft.com/en-us/library/jj265716(v=office.15)">ClientTransaction</a> instance. Only one request may be sent for each <strong>ClientTransaction</strong>instance.</p></td>
</tr>
<tr class="even">
<td><p>&quot;Cannot proxy more than once if ServerTransaction.EnableForking is set to false.&quot;</p></td>
<td><p>The application is trying to call <a href="https://msdn.microsoft.com/en-us/library/jj265503(v=office.15)">CreateBranch()</a> on the same <a href="https://msdn.microsoft.com/en-us/library/jj265462(v=office.15)">ServerTransaction</a> again, but <a href="https://msdn.microsoft.com/en-us/library/jj266759(v=office.15)">EnableForking</a> is set to false. By default, <strong>EnableForking</strong> is set to true.</p></td>
</tr>
<tr class="odd">
<td><p>&quot;Failed to proxy message. Are you trying to proxy the same response twice?&quot;</p></td>
<td><p>Your application attempted to proxy the same response for the same <a href="https://msdn.microsoft.com/en-us/library/jj265462(v=office.15)">ServerTransaction</a> instance at least two times.</p></td>
</tr>
<tr class="even">
<td><p>&quot;Invalid status code.&quot;</p></td>
<td><p>The application supplied an invalid status code in the <a href="https://msdn.microsoft.com/en-us/library/jj266735(v=office.15)">StatusCode</a> property of the <a href="https://msdn.microsoft.com/en-us/library/jj266760(v=office.15)">Response</a> object that is passed to the <a href="https://msdn.microsoft.com/en-us/library/jj265718(v=office.15)">SendResponse(Response)</a> method.</p></td>
</tr>
<tr class="odd">
<td><p>&quot;Cannot send two requests on the same transaction.&quot;</p></td>
<td><p>The application is trying to send two different requests through the same <a href="https://msdn.microsoft.com/en-us/library/jj265716(v=office.15)">ClientTransaction</a> object. Check your code and ensure that you are not passing more than one <a href="https://msdn.microsoft.com/en-us/library/jj266237(v=office.15)">Request</a> object for the same <a href="https://msdn.microsoft.com/en-us/library/jj265716(v=office.15)">ClientTransaction</a> instance by calling the <a href="https://msdn.microsoft.com/en-us/library/jj266211(v=office.15)">SendRequest(Request)</a> method multiple times on it.</p></td>
</tr>
<tr class="even">
<td><p>&quot;Cannot proxy multiple final responses.&quot;</p></td>
<td><p>Your application has tried to proxy two different final responses for the same <a href="https://msdn.microsoft.com/en-us/library/jj265462(v=office.15)">ServerTransaction</a> instance.</p></td>
</tr>
<tr class="odd">
<td><p>&quot;Cannot proxy. Transaction is in canceled / timed out state.&quot;</p></td>
<td><p>The <a href="https://msdn.microsoft.com/en-us/library/jj265742(v=office.15)">Transaction</a> object, (<a href="https://msdn.microsoft.com/en-us/library/jj265462(v=office.15)">ServerTransaction</a> or <a href="https://msdn.microsoft.com/en-us/library/jj265716(v=office.15)">ClientTransaction</a>), timed out when it tried to service a request or response. Examine the message log for the specific message that might have caused the time-out or unexpected cancellation.</p></td>
</tr>
<tr class="even">
<td><p>&quot;Only sip: URIs are supported.&quot;</p></td>
<td><p>The application tried to proxy a message that uses a &quot;tel:&quot;, &quot;sips:&quot; or another URI scheme that is not specifically &quot;sip:&quot;. Consider filtering all messages with URIs that do not use the sip: scheme if they are encountered frequently.</p></td>
</tr>
<tr class="odd">
<td><p>&quot;Internal errors&quot;</p></td>
<td><p>Internal error messages represent internal Lync Server 2013 failures, such as unavailable memory for specific operations. Internal error messages are prefixed with &quot;Internal error:&quot;.</p></td>
</tr>
</tbody>
</table>


## See also

#### Concepts

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

