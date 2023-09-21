---
title: Log and display processed messages (SipSnoop sample)
TOCTitle: Log and display processed messages (SipSnoop sample)
ms:assetid: d195c5b7-0cdd-4135-9e15-82641dbf08ea
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439099(v=office.15)
ms:contentKeyID: 57096252
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- powershell
---

# Log and display processed messages (SipSnoop sample)

Learn about the Microsoft Lync Server 2013 SDK SipSnoop sample application.


**Applies to:** Lync 2013 | Lync Server 2013


> [!NOTE]
> <P>By default, the SipSnoop application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\SipSnoop folder. SipSnoop and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-log-and-6cbaa872">MSDN Code Gallery</A>.</P>



The SipSnoop sample application that is distributed with the Lync Server 2013 SDK shows how to receive all messages that the Microsoft Lync Server 2013 computer processes. The application displays the messages in a UI and maintains statistics about various SIP messages such as number of requests and processed responses.

The application uses two application manifests, SipSnoop.am and SipSnoop2.am, to handle the following tasks.

  - SipSnoop.am is the basic manifest that handles the following application features:
    
      - Uses the \<allowRegistrationBeforeUserServices/\> element to configure the **UserServices** application run time.
    
      - Configures server run time through \<serverFilter roles="ALL"/\>.
    
      - Uses the \<requestFilter methodNames="ALL"/\> and \<responseFilter reasonCodes="ALL"/\> elements to configure how the application receives each request, response, and the corresponding proxy.

  - SipSnoop2.am uses the [DispatchNotification](https://msdn.microsoft.com/library/hh364727\(v=office.15\)) function instead of the [Dispatch](https://msdn.microsoft.com/library/hh364714\(v=office.15\)) function.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\SipSnoop folder to a Lync Server 2013 computer on which the application runs.

### To build the application

1.  Open a command console in a user account that has elevated permission.

2.  Open the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\ folder.

3.  Use the following command to build the application.
    
    ```MS-DOS

        Compile SipSnoop
        
    ```
### To run the application

1.  Log on to a Lync Server 2013 RTC Server Applications local security group account.

2.  Register the application by running the following commands in a Lync Server Management Shell window.
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server.</P>

    
    ```Windows-PowerShell

    new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/SipSnoop" -identity "service:registrar:<lync.Server.Fdqn>/SipSnoop" -critical $false -priority 6 -enabled $true

    ```
    

    > [!NOTE]
    > <P>The application must be registered before the managed code is invoked.</P>



3.  Start the application by using the SipSnoop.exe program.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

