---
title: Filter messages for load balance using file-based policy (PublicIM sample)
TOCTitle: Filter messages for load balance using file-based policy (PublicIM sample)
ms:assetid: ab60b030-070c-4cd4-9848-39e280fc51fe
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439098(v=office.15)
ms:contentKeyID: 57096250
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Filter messages for load balance using file-based policy (PublicIM sample)

Learn about the Microsoft Lync Server 2013 SDK PublicIM sample application and how to load balance in a Microsoft Lync 2013 topology.


_**Applies to:** Lync 2013 | Lync Server 2013_


> [!NOTE]
> <P>By default, the PublicIM application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\PublicIM folder. PublicIM and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-filter-e187ff8c">MSDN Code Gallery</A>.</P>



The PublicIM application that is distributed with the Lync Server 2013 SDK shows how to use a script-only SIP application to route incoming SIP messages from external networks to an internal Microsoft Lync Server 2013 computer.

As a routing application, the strictRoute attribute must be set to false on the [requestFilter](https://msdn.microsoft.com/en-us/library/hh364675\(v=office.15\)) in the application manifest.

The following logic is implemented by the Microsoft SIP Processing Language (MSPL) script:

1.  Verify that a SIP request originates from an external network by comparing the sipRequest.Origin against Messageorigin.NetworkExternal.

2.  Selects a fully qualified domain name (FQDN) of a computer that is running Lync Server 2013. In this topic, the selection is based on a hash string of the SIP URI of the requester.

3.  Forward the incoming request to the selected server by calling the [ProxyRequest](https://msdn.microsoft.com/en-us/library/hh364778\(v=office.15\)) function with a new SIP URI that is constructed by using the following format: "\<original request Uri\>;maddr=\<selected server address\>;transport=tls".

4.  For other messages, forward the message as is, by calling ProxyRequest("") or ProxyResponse().

Additional PublicIM features:

  - Accesses the config.txt file through the declaration of the [\<file\>](https://msdn.microsoft.com/en-us/library/hh364639\(v=office.15\)) element in the application manifest.

  - Parses the contained data by column names.

You may need to change occurrences of Log("Debug", …); in the application manifest to Log("Debugr", …);, if they are not already updated.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\PublicIM folder to a Lync Server 2013 computer on which the application runs.

### To run the application

1.  Log on to the Lync Server 2013 RTC Server Applications local security group account.

2.  Update the list of server addresses in the configuration (config.txt) file. Copy the application manifest (.am) and configuration files to the %progfile%\\Microsoft Lync Server 2013\\Server\\Core folder.

3.  Register the application by running the following commands in a Lync Server Management Shell window:
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server. You may have to change the priority value so that it is larger than the <STRONG>UserServices</STRONG> application value.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/PublicIM" -identity "service:registrar:<lync.Server.Fdqn>/PublicIM" -critical $false -priority 6 -scriptname Public.am -enabled $true

4.  Send IM messages from a SIP client to another user.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

