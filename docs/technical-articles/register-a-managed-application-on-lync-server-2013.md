---
title: Register a managed application on Lync Server 2013
TOCTitle: Register a managed application on Lync Server 2013
ms:assetid: b69d571e-eacc-494a-9a74-047468265b20
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn600167(v=office.15)
ms:contentKeyID: 61055790
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Register a managed application on Lync Server 2013

**Applies to:** Lync 2013 | Lync Server 2013

There are several required steps when you install a managed application on Microsoft Lync Server 2013. This article describes those steps and the errors Lync Server 2013 may return when the installation is not done correctly.

## Videos and samples

- [Lync Server 2013: Register a managed code application](http://channel9.msdn.com/posts/lync-server-2013-register-a-managed-code-application)

- [Lync Developer Roundtable: Introduction to the Lync Server SDK and MSPL](http://channel9.msdn.com/posts/lync-developer-roundtable-introduction-to-lync-server-2013-sdk-and-mspl)

- [Lync Server 2013: Modify SIP message content](http://code.msdn.microsoft.com/lync-server-2013-modify-37847bc4)

- [Lync Server 2013: Filter messages based on file-based policy](http://code.msdn.microsoft.com/lync-server-2013-filter-2bd7aae7)


## Prerequisites for registering a managed application

- Lync Server 2013

- A managed code application that references the Lync Server API.

- Membership in the local computer RTC Server Applications group on the computer where the application is installed.

### Core concepts to know for registering a managed application

Registering an application requires use of the management shell, and PowerShell cmdlets. Also, it is useful to be familiar with the Lync Server API, and the tools for managing Lync Server.

Table 1. Core concepts for registering a managed application

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Article title</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="../server-sdk/get-started-with-lync-server-2013-sdk.md">Get started with Lync Server 2013 SDK</a></p></td>
<td><p>Familiarity with the Lync Server API.</p></td>
</tr>
<tr class="even">
<td><p><a href="http://technet.microsoft.com/en-us/library/gg195756.aspx">Lync Server Administrative Tools</a></p></td>
<td><p>Familiarity with Lync Server administrative tools.</p></td>
</tr>
<tr class="odd">
<td><p><a href="http://technet.microsoft.com/en-us/library/gg398474.aspx">Lync Server Management Shell</a></p></td>
<td><p>Use of the Lync Server Management Shell.</p></td>
</tr>
</tbody>
</table>


## Introduction

Use the Lync Server SDK to create server applications that extend and customize Lync Server features. For example, features to add might include forwarding messages to different targets, managing message content, or modifying message headers.

There are two types of server applications created with the Lync Server SDK: script applications and managed code applications. Server applications are often deployed on an application server. In simple topologies server applications can be deployed to the Lync Front End server. To run a managed or script application on Lync Server you must register it, which includes configuring and deploying the application on a computer in the Lync Server domain.

For typical coding patterns in Lync Server applications, see the samples listed in [Lync developer sample applications](lync-developer-sample-applications.md).

## Register a managed code server application

The tasks listed here are required to register a managed server application.

### To register a managed code server application

1.  Compile the application and the application manifest, configured as a 64-bit application.

2.  Copy the application executable and manifest files to the server.

3.  Log in to the server as a member of the local computer RTC Server Applications group.

4.  Use the cmdlet [New-CsServerApplication](http://technet.microsoft.com/en-us/library/gg398096.aspx) to create the server application.

5.  Ensure that the URI in the manifest file is identical to the URI used in the New-CsServerApplication cmdlet.

6.  Start the application executable. Using administrator privileges to start the executable is recommended.

## Troubleshoot application registration

The following list contains some common errors seen when registering an application and the steps commonly used to fix the error.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Error text</p></th>
<th><p>Try this</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Is not a valid Win32 application</p></td>
<td><p>Rebuild the application, and ensure the build is configured for a 64-bit application.</p></td>
</tr>
<tr class="even">
<td><p>Registration time-out</p></td>
<td><p>Use the cmdlet <a href="http://technet.microsoft.com/en-us/library/gg425948.aspx">Get-CsServerApplication</a> to verify that the application exists on the server. Verify that the URI listed on the server application is identical to the URI in the manifest.</p></td>
</tr>
<tr class="odd">
<td><p>Queue could not be opened</p></td>
<td><p>Make sure you are logged on as a member of the local computer RTC Server Applications group. Then, log off, log back in, and try again.</p></td>
</tr>
<tr class="even">
<td><p>Server application failed to start</p></td>
<td><p>Make sure that the URI listed on the server application is identical to the URI in the manifest.</p></td>
</tr>
</tbody>
</table>


## See also

- [Lync 2013 technical articles](lync-2013-technical-articles.md)
- [Video demo: Register a managed code application](http://channel9.msdn.com/posts/lync-server-2013-register-a-managed-code-application)
- [NextHop](http://blogs.technet.com/b/nexthop/)
- [Lync Server SDK forum](http://social.msdn.microsoft.com/forums/lync/en-us/home?forum=communicationsserversdk%26filter=alltypes%26sort=lastpostdesc)

