---
title: Determine message origin in federated networks (FederationEdge sample)
TOCTitle: Determine message origin in federated networks (FederationEdge sample)
ms:assetid: cfd903a5-bed1-4458-bb51-76b28faeb4ef
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439093(v=office.15)
ms:contentKeyID: 57096247
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Determine message origin in federated networks (FederationEdge sample)

Learn about the Microsoft Lync Server 2013 SDK FederationEdge sample application.


**Applies to:** Lync 2013 | Lync Server 2013


> [!NOTE]
> <P>By default, the FederationEdge application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\FederationEdge folder. FederationEdge and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-determine-ae41d27b">MSDN Code Gallery</A>.</P>



The FederationEdge application that is distributed with the Lync Server 2013 SDK shows how to use a script-only SIP application to determine the origin of a message by using the **MessageOrigin** enumeration against the **Origin** property on an incoming message. After displaying the original source of the message in the ApiLogger utility, it routes the message back to the server without any updates.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\FederationEdge folder to a Microsoft Lync Server 2013 computer on which the application runs.

### To run the application

1.  Log on to the Lync Server 2013 RTC Server Applications local security group account.

2.  Copy the application manifest (.am) and the configuration files to the %progfile%\\Microsoft Lync Server 2013\\Server\\Core folder.

3.  Register the application by running the following commands in a Lync Server Management Shell window.
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server. You may have to change the priority value so that it is larger than the <STRONG>UserServices</STRONG> application value.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/FederationEdge" -identity "service:registrar:<lync.Server.Fdqn>/FederationEdge" -critical $false -priority 6 -scriptname FederationEdge.am -enabled $true

4.  Send IM messages from a SIP client to another user from various user accounts in different networks.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

