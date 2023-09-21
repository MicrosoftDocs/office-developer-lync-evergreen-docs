---
title: 'How to: Install a CWE application in Lync SDK'
TOCTitle: 'How to: Install a CWE application'
ms:assetid: 8a524495-776b-461e-a6e4-03cdad90c239
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933101(v=office.15)
ms:contentKeyID: 50877233
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Install a CWE application in Lync SDK

Learn how to create a registry (.reg) file that registers a Microsoft Lync 2013 Conversation Window Extension (CWE) on a computer so that the CWE can be opened in a Lync 2013 conversation window.



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
Add registry entries<br />
Code example: CWE registry file<br />
Next steps<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

For a list of prerequisites, see [How to: Create a Conversation Window Extension application in Lync SDK](how-to-create-a-conversation-window-extension-application-in-lync-sdk.md).

## Add registry entries

The following procedure shows how to use registry entries to register the context application with Microsoft Lync 2013. In a production environment, use a setup application or Group Policy to create these registry entries.

### To register the application

1.  In Microsoft Visual Studio, create a GUID for the context application.
    
    For more information, see [Create GUID (guidgen.exe)](http://go.microsoft.com/fwlink/?linkid=192728%26clcid=0x409).

2.  If the **HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\Lync\\Security\\Trusted Sites** key does not exist in the registry, create the key.

3.  In the registry at **HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\Lync\\Security\\Trusted Sites**, create a key whose name is the domain of the server that hosts the CWU.
    
    For example:
    
        [HKEY_CURRENT_USER\Software\Microsoft\Office\Lync\Security\Trusted Sites\contoso]

4.  Add a subkey ″https″ to hold a dword value that flags the protocol as https.
    
    The value is 1 if https and 0 if the value is not https.

5.  Add a subkey ″http″ to hold a dword value that flags the protocol as http.
    
    The value is 1 if https and 0 if the value is not https.

6.  If the **HKEY\_CURRENT\_USER\\Software\\Microsoft\\Communicator\\ContextPackages** key does not exist in the registry, create the key.

7.  In the registry at **HKEY\_CURRENT\_USER\\Software\\Microsoft\\Communicator\\ContextPackages**, create a key that contains the GUID that is created in step 6.
    
    For example:
    
        {40499119-4860-45a6-9A7A-DC7A384D5670}

8.  Add the following subkey/value pairs under the GUID that is added in step 7. The values in the bottom four rows are examples. Modify these values to make them appropriate for your scenario.
    
    <table>
    <colgroup>
    <col style="width: 33%" />
    <col style="width: 33%" />
    <col style="width: 33%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>Subkey</p></th>
    <th><p>Type</p></th>
    <th><p>Value</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>DefaultContextPackage</p></td>
    <td><p>REG_DWORD</p></td>
    <td><p>0</p></td>
    </tr>
    <tr class="even">
    <td><p>ExtensibilityWindowSize</p></td>
    <td><p>REG_DWORD</p></td>
    <td><p>1</p></td>
    </tr>
    <tr class="odd">
    <td><p>ExternalURL</p></td>
    <td><p>REG_SZ</p></td>
    <td><p>http://contoso.com/Test/sample.html</p></td>
    </tr>
    <tr class="even">
    <td><p>InternalURL</p></td>
    <td><p>REG_SZ</p></td>
    <td><p>http://localhost/Test/sample.html</p></td>
    </tr>
    <tr class="odd">
    <td><p>Name</p></td>
    <td><p>REG_SZ</p></td>
    <td><p>myContextApplication</p></td>
    </tr>
    </tbody>
    </table>

## Code example: CWE registry file

The following example registers a CWE application called "GenericCWEApp" by adding the location of the HTML page that hosts the Silverlight CWE application to the Lync 2013 trusted sites list and context packages list.

    Windows Registry Editor Version 5.00
    
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Lync\Security\Trusted Sites]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Lync\Security\Trusted Sites\contoso]
    "https"=dword:00000001
    "http"=dword:00000000
    
    [HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages]
    
    [HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Internet Settings\ZoneMap\Domains\ServerName]
    "file"=dword:00000002
    
    [HKEY_CURRENT_USER\Software\Microsoft\Communicator\ContextPackages\{FA44026B-CC48-42DA-AAA8-B849BCB43A21}]
    "Name"="Generic CWE App"
    "InternalURL"="https://contoso/GenericCWEAppTestPage.html"
    "ExternalURL"="https://contoso/GenericCWEAppTestPage.html"
    "InstallLink"="https://contoso/GenericCWEApp.reg"
    "ExtensibilityWindowSize"=dword:00000001

## Next steps

  - [How to: Start an extension application in a Lync conversation window](how-to-start-an-extension-application-in-a-lync-conversation-window.md)

## See also

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

