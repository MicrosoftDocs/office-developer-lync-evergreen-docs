---
title: Build enhanced access control list (EnhancedAllowList sample)
TOCTitle: Build enhanced access control list (EnhancedAllowList sample)
ms:assetid: 366c56b5-3888-418c-a682-6d1cfdfabb1c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439096(v=office.15)
ms:contentKeyID: 57096249
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Build enhanced access control list (EnhancedAllowList sample)

Learn about the Microsoft Lync Server 2013 SDK EnhancedAllowList sample application.


_**Applies to:** Lync 2013 | Lync Server 2013_


> [!NOTE]
> <P>By default, the EnhancedAllowList application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\EnhancedAllowList folder. EnhancedAllowList and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-build-1b2194e3">MSDN Code Gallery</A>.</P>



The EnhancedAllowList application that is distributed with the Lync Server 2013 SDK shows how to use a managed SIP application to build an allow/block list onto the enhanced federation enabled access proxy to support domain authorization and message filtering. In addition, the application shows how to limit communications with external domains unless the external domains are authorized explicitly by the administrator or internal users send messages to those domains.

Application run-time tasks:

1.  Maintain an application specific allow/block list that is used to contain known external domains that can be allowed or rejected by the Microsoft SIP Processing Language (MSPL) script.

2.  Maintain an application specific unknown domain configuration that is used to control access when the unknown domain is encountered. An unknown domain is one that is not present in the server's default configuration or the application specific list.

3.  Attempt to authorize the source domain for external edge requests by checking it against the internal server list and the application specific list. A message can go through if its source domain is present and marked as allow in the internal server list or in the application specific list. Otherwise, the message is rejected.

4.  Attempt to authorize the target domain for internal edge requests by checking it against the internal server list and the application specific list. A message can go through if its target domain is present and marked as allow. Otherwise, the message is rejected.

5.  Determine the permission for auto-authorization requests from the internal edge of an unknown domain by checking the global configuration in the managed code message handler. If auto authorization is permitted, the domain is added to the application specific list and the request can proceed. Additional requests from this domain are automatically allowed.

6.  Generate log files, one for each edge.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\EnhancedAllowList folder to a Microsoft Lync Server 2013 computer on which the application runs.

### To build the application

1.  Open a command console in a user account that has elevated permission.

2.  Open the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples folder.

3.  Use the following command to build the application.
    
        Compile EnhancedAllowList

### To run the application

1.  Log on to a Lync Server 2013 by using an RTC Server Applications local security group account.

2.  Copy the EnhancedAllowList.exe, EnhancedAllowList.exe.config, EnhancedAllowList.am, UnknownDomainConfig.txt, and EnhancedAllowListConfig.txt files to the Microsoft Lync Server 2013 root folder.

3.  Edit the EnhancedAllowList.exe.config file to match your setup. At a minimum, check and update the following parameters:
    
      - LogPath
    
      - EnhancedAllowListPath
    
      - ActionForUnknownDomainFromInternalEdge

4.  Register the application by running the following commands in a Lync Server Management Shell window.
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name of the testing server.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/EnhancedAllowList" -identity "service:registrar:<lync.Server.Fdqn>/EnhancedAllowList" -critical $false -priority 6 -enabled $true
    

    > [!IMPORTANT]
    > <P>The application should be registered before the managed code is invoked.</P>



5.  Run the following command to install the application as a service. EnhancedAllowList.exe and EnhancedAllowList.exe.config should be saved in the same folder.
    
    ``` 
       %WINDIR%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe /LogToConsole=true EnhancedAllowList.exe
    ```
    

    > [!IMPORTANT]
    > <P>When prompted, type the name and password of an account that is already a member of the RTC Server Applications local group. By default, a user is not part of this local group and you must add the user account before you run InstallUtil.exe.</P>



6.  Use the following commands to start Lync Server 2013.
    
        ```MS-DOS
        Net stop rtcsrv
        Net start rtcsrv
        ```

To uninstall the service, run the following command from the directory that contains the EnhancedAllowList.exe and EnhancedListAllow.exe.config files.

    ```MS-DOS
    %WINDIR%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe /U /LogToConsole=true EnhancedAllowList.exe
    ```

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

