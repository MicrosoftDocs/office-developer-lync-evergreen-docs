---
title: Lync 2013 system registry keys
TOCTitle: Lync 2013 system registry keys
ms:assetid: 82ad3fef-2dfd-47ac-adcc-c8f310bb08ed
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933096(v=office.15)
ms:contentKeyID: 50877228
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Lync 2013 system registry keys

![What's new topic](images/JJ937254.mod_icon_whatsnew_long(Office.15).png "What's new topic")

Learn about the computer registry keys that Microsoft Lync 2013 creates in a computer system registry.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Lync 2013 system registry keys<br />
Lync.exe process is running flag<br />
Conversation window application context packages<br />
Application trusted site list<br />
UI suppression flag<br />
Custom menu commands<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Lync 2013 system registry keys

The behavior of Lync 2013 is dictated by the system registry key values described in this topic. Some of the registry keys are new for Lync 2013 and others have been migrated from prior releases.

## Lync.exe process is running flag

Lync 2013 creates the **HKEY\_CURRENT\_USER\\Software\\IM Providers\\Lync** key and sets the UpAndRunning DWORD value to 2 when the Lync.exe process is running. The DWORD value is 0 when Lync.exe is not running.

The **HKEY\_CURRENT\_USER\\Software\\IM Providers\\Communicator** registry key value stores the flag in all versions before Lync 2013.

## Conversation window application context packages

This registry key value was used in prior versions. For Lync 2013, it's stored in a new location.

The mechanism for setting the location of trusted Silverlight applications that are hosted in a Microsoft Lync 2013 Conversation Window Extension (CWE) has changed. To host your Microsoft Lync 2010 or Lync 2013 CWE application in a Lync 2013 conversation window, create a new key in the registry of the computer that is running the Lync 2013 client. You can host a CWE application on a local computer hard drive, on a network computer referenced by a UNC path, or on a Web site.

Register Lync 2013 CWE applications under HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\Addins\\ as shown in the following example.

    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\Addins\{AFCFD912-E1B7-4CB4-92EE-174D5E7A35DD}]
    "Name"="Mini Proposal Tracker"
    "InternalURL"="http://localhost/MiniProposalTrackerTestPage.html"
    "ExternalURL"="http://localhost/MiniProposalTrackerTestPage.html"
    "InstallLink"="http://localhost/MiniProposalTrackerTestPage.html"
    "DefaultContextPackage"=dword:00000000
    "ExtensibilityWindowSize"=dword:00000000

Lync 2010 used HKEY\_CURRENT\_USER\\Software\\Microsoft\\Communicator\\ContextPackages\\ to find registered CWE applications.

### InternalUrl syntax variations

You can host a CWE application on an internal or external Web site, an internal server, or a local computer hard drive. You must use the syntax demonstrated in the following sections to describe the location of your CWE in these scenarios.

#### Web server

If your application is hosted on a Web server, see the following example.

    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\Addins\{01e48572-1cee-4896-b5d7-f62d19ad145d}]
    "ExternalUrl"="http://www.MySite.com"
    "InternalUrl"="http://MySite/MySite/WhoIsThisTestPage.html"
    "Name"="Who is this?"
    "DefaultContextPackage"=dword:00000000
    "ExtensibilityWindowSize"=dword:00000001

#### Network computer UNC path

If your application is hosted on a server location described by a UNC path, see the following example.

    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\Addins\{01e48572-1cee-4896-b5d7-f62d19ad145d}]
    "ExternalUrl"="http://www.MySite.com"
    "InternalUrl"="\\\\MySite\\test.html"
    "Name"="My Site"
    "DefaultContextPackage"=dword:00000000
    "ExtensibilityWindowSize"=dword:00000001

#### Local computer hard drive

If your application is hosted on a local computer drive path, set the registry as shown in the following example.

    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\Addins\{01e48572-1cee-4896-b5d7-f62d19ad145d}]
    "ExternalUrl"="http://www.MySite.com"
    "InternalUrl"="C:\\MySite\\test.html"
    "Name"="My Site"
    "DefaultContextPackage"=dword:00000000
    "ExtensibilityWindowSize"=dword:00000001

## Application trusted site list

Earlier versions of Lync and Communicator 2007 treated the Internet Explorer trusted site list as the security mechanism that prevented unauthorized Silverlight applications from accessing the running Lync process. With Lync 2013, the mechanism for setting trusted locations that serve Lync-enabled Silverlight applications has changed. Lync 2013 uses a registry key that is dedicated to the Lync 2013 trusted Silverlight application site list.

To host your Microsoft Lync 2010 or Lync 2013 Silverlight application in a Lync 2013 conversation window or browser page, create a new key in the registry of the computer that is running the Lync 2013 client. You can host a Silverlight browser application on a local computer hard drive, on a network computer referenced by a UNC path, or on a Web site.

If your application is hosted on a server configured for SSL/TLS, create a new key like the following key, where MySite.com is the domain that hosts the CWE application.

    HKEY_CURRENT_USER\Software\Microsoft\Office\Lync\Security\Trusted Sites\MySite.com 
    "https"=dword:00000001
    "http"=dword:00000000
    "file"=dword:00000000

Any Silverlight browser application that is hosted on this site is now a trusted application.

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
<td><p>Do not add a trusted site entry for any CWE application hosted on a local path because all local applications are trusted by default.</p></td>
</tr>
</tbody>
</table>

### Trust multiple servers and subdomains with one key

If your network topology includes multiple servers under a domain or subdomains under a domain and you want to add these entities to the trusted site list using a single key, use the wildcard character ″\*″ in the registry key value. To trust all servers under contoso.com, the key value is ″KEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\Lync\\Security\\Trusted Sites\\\*.contoso.com″. This key also creates trust for any subdomains such as ″host1.subdomain.contoso.com″.

## UI suppression flag

This registry key value was used in prior versions. For Lync 2013, it's stored in a new location.

The Microsoft Lync 2013 client uses the following registry key to get the current client UI suppression mode. The new Lync 2013 registry key is:

**HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\UISuppressionMode**

The Microsoft Lync 2010 client uses the following registry key when running under a 64-bit OS:

**HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Communicator\\UISuppressionMode**

When Microsoft Lync 2010 is running under a 32-bit OS:

**HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Communicator\\UISuppressionMode**

## Custom menu commands

To add a custom menu command to the Lync 2013 client menu, add subkeys under the following key: **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\15.0\\Lync\\CustomCommands**. For more information about setting custom commands, see [Add custom commands to Lync menus](add-custom-commands-to-lync-menus.md).

## See also

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

