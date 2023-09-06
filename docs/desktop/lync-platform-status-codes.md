---
title: Lync platform status codes
TOCTitle: Lync platform status codes
ms:assetid: 8ffff73e-b7fc-47d7-9847-b738c6d30470
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933114(v=office.15)
ms:contentKeyID: 50877248
ms.date: 07/24/2014
mtps_version: v=office.15
description: "Learn Lync 2013 API Exception Classes & Error Conditions: Discover how system status codes map to Lync Platform exceptions and their causes."
---

# Lync platform status codes

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn how the system status code hexadecimal values map to a class of Lync 2013 API exceptions and about the condition that causes the error.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
System status code to exception map<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## System status code to exception map

The following table lists the system status codes that are exposed as **StatusCode** properties on event callback method arguments.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Hexadecimal status code</p></th>
<th><p>Exception class</p></th>
<th><p>Error condition</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0x80000001</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/6byb74h9">System.NotImplementedException</a></p></td>
<td><p>The method or property is not implemented.</p></td>
</tr>
<tr class="even">
<td><p>0x80000005</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8w0s4024">System.NullReferenceException</a></p></td>
<td><p>The referenced object is null.</p></td>
</tr>
<tr class="odd">
<td><p>0x8000000A</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293576(v=office.15)">Microsoft.Lync.Model.NotReadyException</a></p></td>
<td><p>An operation is pending.</p></td>
</tr>
<tr class="even">
<td><p>0x80004001</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/6byb74h9">System.NotImplementedException</a></p></td>
<td><p>The method or property is not implemented.</p></td>
</tr>
<tr class="odd">
<td><p>0x80004005</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The operation failed.</p></td>
</tr>
<tr class="even">
<td><p>0x80010105</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The remote procedure call failed due to a COM server fault.</p></td>
</tr>
<tr class="odd">
<td><p>0x80020009</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>An unknown fault.</p></td>
</tr>
<tr class="even">
<td><p>0x8007000E</p></td>
<td><p><strong>[System.OutOfMemoryException]</strong></p></td>
<td><p>Out of memory.</p></td>
</tr>
<tr class="odd">
<td><p>0x80070057</p></td>
<td><p><strong>[System.ArgumentException]</strong></p></td>
<td><p>Invalid argument.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80001</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj268186(v=office.15)">Microsoft.Lync.Model.NotInitializedException</a></p></td>
<td><p>The client is not initialized.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80002</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277975(v=office.15)">Microsoft.Lync.Model.AlreadyInitializedException</a></p></td>
<td><p>The client is already initialized.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80003</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293576(v=office.15)">Microsoft.Lync.Model.NotReadyException</a></p></td>
<td><p>The application is not ready.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80004</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267360(v=office.15)">Microsoft.Lync.Model.ItemNotFoundException</a></p></td>
<td><p>A collection item was not found.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80005</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj268204(v=office.15)">Microsoft.Lync.Model.TypeMismatchException</a></p></td>
<td><p>An item type specified is conflicting with existing item type.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80006</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293812(v=office.15)">Microsoft.Lync.Model.NotSignedInException</a></p></td>
<td><p>The operation cannot be completed because user is not signed in.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80007</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293460(v=office.15)">Microsoft.Lync.Model.ItemAlreadyExistException</a></p></td>
<td><p>The item already exists in the collection.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80008</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276593(v=office.15)">Microsoft.Lync.Model.RequestCanceledException</a></p></td>
<td><p>The requested operation was canceled.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80009</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276593(v=office.15)">Microsoft.Lync.Model.RequestCanceledException</a></p></td>
<td><p>The credential request was canceled or not answered.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8000A</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>The operation is invalid or not supported.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8000B</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The object does not support the operation.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8000C</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj278123(v=office.15)">Microsoft.Lync.Model.ResultOverflowException</a></p></td>
<td><p>There are too many results to be returned.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8000d</p></td>
<td><p></p></td>
<td><p>XCeed library error.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8000e</p></td>
<td><p></p></td>
<td><p>XCeed library error while opening a ZIP file.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8000f</p></td>
<td><p></p></td>
<td><p>XCeed library error while moving a temporary file.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80010</p></td>
<td></td>
<td><p>XCeed library error while processing a file.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80011</p></td>
<td></td>
<td><p>The specified file could not be opened for reading.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80012</p></td>
<td></td>
<td><p>The specified telepointer is not for the local content user.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80013</p></td>
<td></td>
<td><p>The maximum limit for the annotation type has been reached.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80014</p></td>
<td></td>
<td><p>The change has been rejected due to a stale version.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80015</p></td>
<td></td>
<td><p>The slide specified is not in the valid range.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80016</p></td>
<td></td>
<td><p>The click specified is not in the valid range.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80017</p></td>
<td></td>
<td><p>The Preview Thumbnail is not available.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80018</p></td>
<td></td>
<td><p>The DO parts are not connected.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80019</p></td>
<td></td>
<td><p>The full PowerPoint file is not available.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8001a</p></td>
<td></td>
<td><p>There is no information currently available about a local or server resource status.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8001b</p></td>
<td></td>
<td><p>There is no need to upload this resource.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8001c</p></td>
<td></td>
<td><p>There is an outstanding operation initiated for a resource but results are not available yet.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8001d</p></td>
<td></td>
<td><p>The conversion of the resource failed on the uploading client itself.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8001e</p></td>
<td></td>
<td><p>The uploading of the resource failed on the uploading client itself.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8001f</p></td>
<td></td>
<td><p>The uploading client got disconnected before uploading all pending resources.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80020</p></td>
<td></td>
<td><p>The uploading client got demoted before uploading all pending resources.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80021</p></td>
<td></td>
<td><p>The server returned an unknown failure code.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80022</p></td>
<td></td>
<td><p>The partial PowerPoint resource is never going to be available.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80023</p></td>
<td></td>
<td><p>A dependent resource failed, thus the pending resource has failed.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80024</p></td>
<td></td>
<td><p>The supplied file extension is blocked for transfer by a policy.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80025</p></td>
<td></td>
<td><p>The Lync client platform process is in suspended mode.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80026</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293445(v=office.15)">Microsoft.Lync.Model.NotStartedByUserException</a></p></td>
<td><p>The operation was not started by the user.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80027</p></td>
<td></td>
<td><p>A Lync API client requested too many root API objects from one thread.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80028</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277856(v=office.15)">Microsoft.Lync.Model.InvalidStateException</a></p></td>
<td><p>The object is in an invalid state.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80029</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277401(v=office.15)">Microsoft.Lync.Model.PendingOperationException</a></p></td>
<td><p>The pending operation must be completed first.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8002a</p></td>
<td></td>
<td><p>Lync has been suspended.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8002b</p></td>
<td><p>The operation has timed out.</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>0x80C8002C</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj266481(v=office.15)">Microsoft.Lync.Model.JoinRoomFailException</a></p></td>
<td><p>Failure to join a chat room.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8002D</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277941(v=office.15)">Microsoft.Lync.Model.JoinRoomUnauthorizedException</a></p></td>
<td><p>The user is not a member of the chat room that the user is attempting to join.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C8002E</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj294110(v=office.15)">Microsoft.Lync.Model.RoomNotJoinedException</a></p></td>
<td><p>The user attempt to join a chat room did not succeed.</p></td>
</tr>
<tr class="even">
<td><p>0x80C8002f</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275504(v=office.15)">Microsoft.Lync.Model.ContentTitleExistException</a></p></td>
<td><p>The content was not added because other content with the same title has already been uploaded to the conversation.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80030</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj268005(v=office.15)">Microsoft.Lync.Model.MaxContentsExceededException</a></p></td>
<td><p>The conversation content bin is full.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80031</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293584(v=office.15)">Microsoft.Lync.Model.ContentTitleInvalidException</a></p></td>
<td><p>The title of the new content is not valid. Content was not uploaded to the conversation.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80032</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293465(v=office.15)">Microsoft.Lync.Model.ContentNotAuthorizedException</a></p></td>
<td><p>The user is an attendee and cannot upload content to the conversation.</p></td>
</tr>
<tr class="even">
<td><p>0x80C80033</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276531(v=office.15)">Microsoft.Lync.Model.ContentOtherErrorsException</a></p></td>
<td><p>Failed to create a content title.</p></td>
</tr>
<tr class="odd">
<td><p>0x80C80034</p></td>
<td></td>
<td><p>Too many pending searches.</p></td>
</tr>
<tr class="even">
<td><p>0x00EE0009</p></td>
<td><p><strong>NotsupportedException</strong></p></td>
<td><p>An SDP multicast exception.</p></td>
</tr>
<tr class="odd">
<td><p>0x00EE000C</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/cke1faa2">System.TimeoutException</a></p></td>
<td><p>SIP timeout.</p></td>
</tr>
<tr class="even">
<td><p>0x00EE0010</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The SIP authentication type is not supported.</p></td>
</tr>
<tr class="odd">
<td><p>0x00EE0011</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>The SIP authentication failed.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE0012</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/3w1b3114">System.ArgumentException</a></p></td>
<td><p>Invalid URL.</p></td>
</tr>
<tr class="odd">
<td><p>0x00EE001D</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/cke1faa2">System.TimeoutException</a></p></td>
<td><p>SIP SSL negotiation timeout.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE004A</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293460(v=office.15)">Microsoft.Lync.Model.ItemAlreadyExistException</a></p></td>
<td><p>Duplicate contact.</p></td>
</tr>
<tr class="odd">
<td><p>0x80EE004B</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293460(v=office.15)">Microsoft.Lync.Model.ItemAlreadyExistException</a></p></td>
<td><p>Duplicate subscriber.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE0051</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267360(v=office.15)">Microsoft.Lync.Model.ItemNotFoundException</a></p></td>
<td><p>The group does not exist.</p></td>
</tr>
<tr class="odd">
<td><p>0x80EE0052</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293460(v=office.15)">Microsoft.Lync.Model.ItemAlreadyExistException</a></p></td>
<td><p>Duplicate group.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE0053</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>Too many groups.</p></td>
</tr>
<tr class="odd">
<td><p>0x80EE0054</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267360(v=office.15)">Microsoft.Lync.Model.ItemNotFoundException</a></p></td>
<td><p>No contact found.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE0055</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267360(v=office.15)">Microsoft.Lync.Model.ItemNotFoundException</a></p></td>
<td><p>No subscriber found.</p></td>
</tr>
<tr class="odd">
<td><p>0x80EE0058</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267360(v=office.15)">Microsoft.Lync.Model.ItemNotFoundException</a></p></td>
<td><p>RTC: does not exist.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE005A</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>Reached the maximum number of pending operations.</p></td>
</tr>
<tr class="odd">
<td><p>0x80EE005B</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>Too many retries.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE0061</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277856(v=office.15)">Microsoft.Lync.Model.InvalidStateException</a></p></td>
<td><p>An invalid object state.</p></td>
</tr>
<tr class="odd">
<td><p>0x80EE0065</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277856(v=office.15)">Microsoft.Lync.Model.InvalidStateException</a></p></td>
<td><p>SIP invalid certificate.</p></td>
</tr>
<tr class="even">
<td><p>0x80EE0082</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>The operation is not allowed.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10001</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277856(v=office.15)">Microsoft.Lync.Model.InvalidStateException</a></p></td>
<td><p>An invalid state.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10004</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>Not a conference leader.</p></td>
</tr>
<tr class="odd">
<td><p>0x00F10005</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The capability is not supported.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10008</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276593(v=office.15)">Microsoft.Lync.Model.RequestCanceledException</a></p></td>
<td><p>The request was canceled by the platform.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10009</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276593(v=office.15)">Microsoft.Lync.Model.RequestCanceledException</a></p></td>
<td><p>Request is cancelled.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1000F</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276593(v=office.15)">Microsoft.Lync.Model.RequestCanceledException</a></p></td>
<td><p>The request is canceled by another user.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10012</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277401(v=office.15)">Microsoft.Lync.Model.PendingOperationException</a></p></td>
<td><p>The operation is in progress.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10013</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The operation is not supported.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10014</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The user is in DND mode.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10015</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>The device is not available.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10018</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>The audio device is not configured.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10019</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>One or more audio devices are not configured.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1001A</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>A webcam is not configured.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1001B</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>An incoming invitation is automatically rejected.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1001C</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The audio is not accepted.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1001D</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The video is not accepted.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1001E</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The call cannot be held.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1001F</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">NotSupportedException</a></p></td>
<td><p>The mode is not supported.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10020</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The operation or mode is not supported in multi-party conversation.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10025</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The contact is blocked.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10026</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The contact has an unknown capability.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1002A</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The SIP client agent version is not supported.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1002B</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The SIP client version is not supported with supplied URL.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1002C</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The remote client does not support mode.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1002D</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>The session already exists in a conference.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10030</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Too many members in the distribution group.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10031</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>The distribution group is missing a Web service URI.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10032</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>The distribution group expansion is not authorized.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10033</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>An invalid distribution group.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10035</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Too many nested levels in a distribution group.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10037</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Distribution group expansion is disabled.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10038</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>Distribution group file cache error.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10040</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/cke1faa2">System.TimeoutException</a></p></td>
<td><p>SOAP transaction timeout.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10044</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The SOAP port is down.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10054</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>Application is not installed.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10055</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The application is not supported.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10056</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Too many contacts.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10057</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The local contact is not allowed.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10058</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>The call was accepted by another person.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10059</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>The call was accepted by another endpoint.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1005A</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>An anonymous contact is not allowed.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10080</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>Conversation voice mode exists.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10081</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>The operation is not allowed when a call is held.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10082</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The operation is not available when offline.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10083</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The operation is disabled by capability.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10087</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>The transferee rejected transfer.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10088</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Sharing control conflict.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1008A</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The legacy remote client does not support the operation or modality.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1008B</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Control request during escalation to conference.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1008C</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>Invalid normalization rule configured.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1008D</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>Credentials do not match URI.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1008E</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>SharePoint is not configured.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10091</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj277401(v=office.15)">Microsoft.Lync.Model.PendingOperationException</a></p></td>
<td><p>A SharePoint version check is in progress.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10096</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>An application sharing resource is not available.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10098</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/8a7a4e64">System.NotSupportedException</a></p></td>
<td><p>The sharer control request is not supported.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10099</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>Sharing is disabled by role.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1009A</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>Sharing is disabled by permission.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1009B</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>Sharing is disabled in a remote session.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F1009E</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>SharePoint returns all noise.</p></td>
</tr>
<tr class="even">
<td><p>0x80F1009F</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>SharePoint error, no response.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F100A0</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>Bad query.</p></td>
</tr>
<tr class="even">
<td><p>0x80F100A1</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>Bad scope.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F100A2</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>Bad request.</p></td>
</tr>
<tr class="even">
<td><p>0x80F100A3</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>No query.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F100A4</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>Not authorized.</p></td>
</tr>
<tr class="even">
<td><p>0x80F100A5</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>SharePoint server error.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F100A6</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj293959(v=office.15)">Microsoft.Lync.Model.SearchException</a></p></td>
<td><p>An unspecified SharePoint error.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10102</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>A Web search internal error.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10103</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/3w1b3114">System.ArgumentException</a></p></td>
<td><p>A Web search invalid argument.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10106</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj276593(v=office.15)">Microsoft.Lync.Model.RequestCanceledException</a></p></td>
<td><p>A Web search is canceled.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10107</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>A Web search is not authorized.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10108</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>A Web search initialization failed.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10220</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>An AES helper is not initialized.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10300</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>No provider at this location.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10320</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>MAPI email mismatch.</p></td>
</tr>
<tr class="even">
<td><p>0x80F10400</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>Recording WMP is not installed.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F10401</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj275318(v=office.15)">Microsoft.Lync.Model.ConfigurationErrorException</a></p></td>
<td><p>The recording path is not available.</p></td>
</tr>
<tr class="even">
<td><p>0x80F2CB50</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/2asft85a">System.InvalidOperationException</a></p></td>
<td><p>Cannot escalate conversation with pending modes.</p></td>
</tr>
<tr class="odd">
<td><p>0x80f30c2e</p></td>
<td><p><a href="http://msdn2.microsoft.com/en-us/library/f2y9aa54">System.UnauthorizedAccessException</a></p></td>
<td><p>Removed by conference presenter.</p></td>
</tr>
<tr class="even">
<td><p>0x80f30c2f</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Panoramic video is not accepted.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F50103</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Contact list maximum groups exceeded.</p></td>
</tr>
<tr class="even">
<td><p>0x80F50107</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Contact list operation blocked, no provider.</p></td>
</tr>
<tr class="odd">
<td><p>0x80F50108</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/jj267681(v=office.15)">Microsoft.Lync.Model.OperationException</a></p></td>
<td><p>Contact list maximum distribution groups exceeded.</p></td>
</tr>
</tbody>
</table>

## See also

  - [Beyond the basics: Lync 2013 SDK](beyond-the-basics-lync-2013-sdk.md)

