---
title: Enable stateful SIP applications (LoggingNotice sample)
TOCTitle: Enable stateful SIP applications (LoggingNotice sample)
ms:assetid: e37aa355-eed1-445d-9001-ba93ebe019a1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439095(v=office.15)
ms:contentKeyID: 57096248
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- powershell
---

# Enable stateful SIP applications (LoggingNotice sample)

Learn about the Microsoft Lync Server 2013 SDK LoggingNotice sample application.


**Applies to:** Lync 2013 | Lync Server 2013


> [!NOTE]
> <P>By default, the LoggingNotice application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\LoggingNotice folder. LoggingNotice and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-enable-eddaa75c">MSDN Code Gallery</A>.</P>



The LoggingNotice application that is distributed with the Lync Server 2013 SDK shows how to implement stateful application logic and message modification. The application maintains dialog state, and appends text to the first IM in each session.

Session state is maintained in a Hashtable and indexed by call-id. An incoming ACK moves a dialog to the modify-IM state, where incoming IM messages are appended with warning text until all parties in the conversation are notified. A separate session-participant table is used to determine the parties that have already been notified, so that each party is notified one time only. When all parties in a session are notified, the session state is deleted.


> [!NOTE]
> <P>Clients that create a session and never send a message move the LoggingNotice application to the leak state.</P>



## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\LoggingNotice folder to a Microsoft Lync Server 2013 computer on which the application runs.

### To build the application

1.  Open a command console in a user account that has elevated permission.

2.  Open the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples folder.

3.  Use the following command to build the application.
    
        Compile LoggingNotice

### To run the application

1.  Log on to a Lync Server 2013 RTC Server Applications local security group account.

2.  Copy the LoggingNotice.exe, LoggingNotice.exe.config, and LoggingNotice.am files to the %progfile%\\Microsoft Lync Server 2013\\Server\\Core directory.

3.  Register the application by running the following commands in a Lync Server Management Shell window.
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server.</P>

    
    ``` powershell
    new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/LoggingNotice" -identity "service:registrar:<lync.Server.Fdqn>/LoggingNotice" -critical $false -priority 6 -enabled $true
    ```
    

    > [!NOTE]
    > <P>You must register the application before the managed code is invoked.</P>



4.  Start the application by using the LoggingNotice.exe program.

5.  In two active client sessions, add each client to the other client contact list, if not already present. Start a new IM session and then send messages in both directions. The following text appears in the first IM message that is sent to each client:
    
    <pre IsFakePre="true" xmlns="http://www.w3.org/1999/xhtml">(*** This conversation may be logged. ***)</pre>


## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

