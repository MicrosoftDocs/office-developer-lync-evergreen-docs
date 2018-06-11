---
title: Enable version control for client access (ClientVerFilter sample)
TOCTitle: Enable version control for client access (ClientVerFilter sample)
ms:assetid: d835a0d8-c2e5-4f5b-a12d-a0b307136146
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439092(v=office.15)
ms:contentKeyID: 57096246
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Enable version control for client access (ClientVerFilter sample)

Learn about the Microsoft Lync Server 2013 SDK ClientVerFilter sample application.


**Applies to:** Lync 2013 | Lync Server 2013


> [!NOTE]
> <P>By default, the ClientVerFilter application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\ClientVerFilter folder. ClientVerFilter and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-enable-3d5e2b5a">MSDN Code Gallery</A>.</P>



The ClientVerFilter application that is distributed with the Lync Server 2013 SDK shows how to use a script-only SIP application to enforce a simple user-based IM filtering policy. The application includes an application manifest file (ClientFilter.am) and two configuration files (FullMatch\_Config.txt and PartialMatch\_Config.txt). The configuration files are used to specify a list of permissions for various versions of the Microsoft Lync 2013 client.

The following logic is implemented by the Microsoft SIP Processing Language (MSPL) script:

  - Get the **UserAgent** header value for the incoming [Request](https://msdn.microsoft.com/en-us/library/hh364656\(v=office.15\)) instance.

  - Get the permission by using the FullMatch\_Config file setting for the obtained user agent.

  - Do a prefix match by using the partial-match configuration setting for the obtained user agent to determine the final client permission.

  - If the client permission is "allow", then route the message back to the server by calling the [ProxyRequest](https://msdn.microsoft.com/en-us/library/hh364778\(v=office.15\)) function. Otherwise, reject the request with a 403 Response that contains a Forbidden error message.

The sample application accesses the configuration text files through the declaration of the [\<file\>](https://msdn.microsoft.com/en-us/library/hh364639\(v=office.15\)) elements that are listed in the application manifest and the application parses the data by using column names. The file is not declared as static and the application will reread the file when the file content changes.

You may have to change any occurrences of Log("Debug", …); in the application manifest to Log("Debugr", …);, if they are not already updated.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\ClientVerFilter folder to a Microsoft Lync Server 2013 computer on which the application runs.

### To run the application

1.  Log on to the Lync Server 2013 computer by using an RTC Server Applications local security group account.

2.  Update the configuration files, and then copy the application manifest (.am) and configuration files to the %progfile%\\Microsoft Lync Server 2013\\Server\\Core folder.

3.  Register the application by running the following commands in a Lync Server Management Shell window:
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server. You may have to change the priority value so that it is larger than the <STRONG>UserServices</STRONG> application value.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/ClientFilter" -identity "service:registrar:<lync.Server.Fdqn>/ClientFilter" -critical $false -priority 6 -scriptname ClientFilter.am -enabled $true

4.  Send IM messages to another user by using various Lync 2013 clients.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

