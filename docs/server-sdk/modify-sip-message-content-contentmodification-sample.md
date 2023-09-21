---
title: Modify SIP message content (ContentModification sample)
TOCTitle: Modify SIP message content (ContentModification sample)
ms:assetid: 26f05d7c-8665-4d79-9cb4-3f4f4eb4b588
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439094(v=office.15)
ms:contentKeyID: 57096261
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Modify SIP message content (ContentModification sample)

Learn about the Microsoft Lync Server 2013 SDK ContentModification sample application.


**Applies to:** Lync 2013 | Lync Server 2013


> [!NOTE]
> <P>By default, the ContentModification application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\ContentModification folder. ContentModification and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-modify-37847bc4">MSDN Code Gallery</A>.</P>



The ContentModification sample application that is distributed with the Lync Server 2013 SDK shows how to use a script-only SIP application to change the content of a message that is an INVITE or MESSAGE type. SIP responses are not handled.

The following logic is implemented by the Microsoft SIP Processing Language (MSPL) script:

1.  Search for the text of "echo" in the incoming message content by using the [IndexOfString](https://msdn.microsoft.com/library/hh364854\(v=office.15\)) function.

2.  If "echo" is found where the returned index value is greater than -1, change the message content by appending the string of " (echo.)" to the message body.

3.  Route the message, possibly updated, back to the server by calling the [ProxyRequest("")](https://msdn.microsoft.com/library/hh364778\(v=office.15\)) function.


> [!NOTE]
> <P>The previous logic assumes that the message content uses the "text/plain" format. At certain times, some clients might use this format. However, other clients might not use this format. To ensure that all client requests can correctly display the message content, the application must think about the format that is used in the incoming message. To ensure the message content is rendered, you can inspect the Content-Type header value as shown in the next example.</P>



``` 
    contentType = "";
    foreach(ct in GetHeaderValues(StandardHeader.ContentType))
    {
      contentType = ct;
      break;
    }
```

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\ContentModification folder to a Microsoft Lync Server 2013 computer on which the application runs.

### To run the application

1.  Log on to the Lync Server 2013 RTC Server Applications local security group account.

2.  Copy the application manifest (.am) and configuration files to the %progfile%\\Microsoft Lync Server 2013\\Server\\Core folder.

3.  Register the application by running the following commands in a Lync Server Management Shell window.
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name of the testing server. You may have to change the priority value so that it is larger than that of <STRONG>UserServices</STRONG> application installed by the system.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/ContentModification" -identity "service:registrar:<lync.Server.Fdqn>/ContentModification" -critical $false -priority 6 -scriptname ContentModification.am -enabled $true

4.  Send IM messages, with and without the "echo" text, from a SIP client to another user.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

