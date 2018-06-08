---
title: Maintain topology-aware message logs (Archiver sample)
TOCTitle: Maintain topology-aware message logs (Archiver sample)
ms:assetid: 287720f8-95ce-4e67-b404-53ef2b82d0f3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439091(v=office.15)
ms:contentKeyID: 57096245
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Maintain topology-aware message logs (Archiver sample)

Learn about the Microsoft Lync Server 2013 SDK Archiver sample application.


**Applies to:** Lync 2013 | Lync Server 2013


> [!NOTE]
> <P>By default, the Archiver application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\Archiver folder. Archiver and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-maintain-11e5d354">MSDN Code Gallery</A>.</P>



The Archiver application that is distributed with the Lync Server 2013 SDK shows how to use a managed SIP application to build a topology-aware SIP application that uses message stamping for multi-homed application communications. Each **Archiver** instance logs messages that are not yet stored by any instance on another server. The logged requests and responses are stamped to notify downstream **Archiver** instances that additional logging is not necessary.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\Archiver folder to a Microsoft Lync Server 2013 computer on which the application runs.

### To build the application assembly

1.  Open a command console in a user account that has elevated permission.

2.  Open the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples folder.

3.  Use the following command to build the application.
    
        Compile Archiver

### To run the application

1.  Log on to the two Lync Server 2013 computers by using an RTC Server Applications local security group account.

2.  Register the application by running the following commands in a Lync Server Management Shell window.
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server. You may have to change the priority value so that it is larger than the <STRONG>UserServices</STRONG> application value.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/Archiver" -identity "service:registrar:<lync.Server.Fdqn>/Archiver" -critical $false -priority 6 -enabled $true

3.  In a command console, run Archiver.exe to start the application.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

