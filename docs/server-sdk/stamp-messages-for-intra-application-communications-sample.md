---
title: Stamp messages for intra-application communications (ApplicationStamping sample)
TOCTitle: Stamp messages for intra-application communications (ApplicationStamping sample)
ms:assetid: 4289fcb6-5208-41d2-bbe7-a75458acaa96
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439090(v=office.15)
ms:contentKeyID: 57096244
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Stamp messages for intra-application communications (ApplicationStamping sample)

Learn about the Microsoft Lync Server 2013 SDK ApplicationStamping sample application.


**Applies to:** Lync 2013 | Lync Server 2013


> [!NOTE]
> <P>By default, the ApplicationStamping application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\ApplicationStamping folder. ApplicationStamping and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-stamp-bd30f0cc">MSDN Code Gallery</A>.</P>



The ApplicationStamping application that is distributed with the Lync Server 2013 SDK shows how to use a script-only SIP application to tag a message with a string that is used to communicate between two identical application instances that run on different Microsoft Lync Server 2013 computers in the same topology. A message stamp is exposed on the **Stamp** property of a [Message](https://msdn.microsoft.com/en-us/library/hh364768\(v=office.15\)) instance and is visible only to the applications of the same URI.

The following logic is implemented by the Microsoft SIP Processing Language (MSPL) script:

1.  Inspect the **Stamp** property on the incoming request (**sipRequest.Stamp**).

2.  If the stamp is unspecified (not null), append the "+" character to the existing stamp. Otherwise, assign a ServerPool value to the message stamp.

3.  Route the newly stamped message to the server by calling the [ProxyRequest](https://msdn.microsoft.com/en-us/library/hh364778\(v=office.15\)) function that uses an empty string as the URI parameter value.

Other features that are implemented include logging the application run time to ApiLogger by using **Log** function.

You may have to change any occurrences of Log("Debug", …); in the application manifest to Log("Debugr", …);, if they are not already updated.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\ApplicationStamping folder to a Lync Server 2013 computer on which the application runs.

### To run the application

1.  Log on to the Lync Server 2013 RTC Server Applications local security group account.

2.  Copy the application manifest (.am) and configuration files to the %progfile%\\Microsoft Lync Server 2013\\Server\\Core folder.

3.  Register the application by running the following commands in a Lync Server Management Shell window:
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server. You may have to change the priority value so that it is larger than the <STRONG>UserServices</STRONG> application value.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/ApplicationStamping" -identity "service:registrar:<lync.Server.Fdqn>/ ApplicationStamping " -critical $false -priority 6 -scriptname ApplicationStamping.am -enabled $true

4.  Send IM messages from a SIP client to another user.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

