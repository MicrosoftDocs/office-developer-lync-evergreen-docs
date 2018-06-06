---
title: Filter messages based on file-based policy (FilteringApp sample)
TOCTitle: Filter messages based on file-based policy (FilteringApp sample)
ms:assetid: 5e02ba71-bb3a-4d21-9ccb-a8025b0a47f4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439097(v=office.15)
ms:contentKeyID: 57096251
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Filter messages based on file-based policy (FilteringApp sample)

Learn about the Microsoft Lync Server 2013 SDK FilteringApp sample application.


_**Applies to:** Lync 2013 | Lync Server 2013_


> [!NOTE]
> <P>By default, the FilteringApp application is copied to the %progfile%\Microsoft Lync Server 2013\SDK\Samples\FilteringApp folder. FilteringApp and related code samples can also be downloaded from the <A href="http://code.msdn.microsoft.com/lync-server-2013-filter-2bd7aae7">MSDN Code Gallery</A>.</P>



The FilteringApp application that is distributed with the Lync Server 2013 SDK shows how to use a script-only SIP application to enforce a simple user-based IM filtering policy. The application consists of the application manifest file (Filter.am) and a policy settings file (Policy.txt). The policy settings are specified by a list of whitespace-delimited fields of URI, Policy, and Value. The URI field is a string of the "user@host" format. Use an action verb, for example, allow, filter, or drop, to describe the Policy field. The Value column is optional and specifies forbidden text that causes the IM message to be dropped if the message content contains the forbidden text.

The following logic is implemented by the Microsoft SIP Processing Language (MSPL) script:

  - Parse the **To** header to obtain the targeted SIP URI of an incoming [Request](https://msdn.microsoft.com/en-us/library/hh364656\(v=office.15\)) instance.

  - Parse the policy settings in the policy file to determine the routing behavior for the targeted user.

  - If the policy action verb for the targeted user is allow, the message is routed back to the server for normal processing by calling ProxyRequest("").

  - If the policy action verb for the targeted user is filter and the incoming message content does not contain the specified forbidden text, the message is routed back to the server. Otherwise, the request is rejected with a 403 response that contains a "Forbidden (Message filtered)" message.

  - If the policy action verb is drop or unknown, the request to the targeted user is dropped and a 403 response with an appropriate error message is sent to the sender of the request.

Additional FilteringApp features:

  - Accesses the policy.txt file through the declaration of the [\<file\>](https://msdn.microsoft.com/en-us/library/hh364639\(v=office.15\)) element in the application manifest.

  - Parses the contained data by column names.
    

    > [!NOTE]
    > <P>The file is not declared as static and the application will reread the file when the file content is changed.</P>



You may have to change any occurrences of Log("Debug", …); in the application manifest to Log("Debugr", …);, if they are not already updated.

## Testing the application

If necessary, copy the %progfile%\\Microsoft Lync Server 2013\\SDK\\Samples\\FilteringApp folder to a Microsoft Lync Server 2013 computer on which the application runs.

### To run the application

1.  Log on to the Lync Server 2013 RTC Server Applications local security group account.

2.  Update the access control list in the policy (policy.txt) file. Copy the application manifest (.am) and the policy files to the %progfile%\\Microsoft Lync Server 2013\\Server\\Core folder.

3.  Register the application by running the following commands in a Lync Server Management Shell window:
    

    > [!NOTE]
    > <P>&lt;lync.Server.Fdqn&gt; is the placeholder for the fully qualified domain name for the test server. You may have to change the priority value so that it is larger than the <STRONG>UserServices</STRONG> application value.</P>

    
        new-csServerApplication -uri " http://www.microsoft.com/LC/SDK/Samples/Filter" -identity "service:registrar:<lync.Server.Fdqn>/Filter" -critical $false -priority 6 -scriptname Filter.am -enabled $true

4.  Send IM messages from a SIP client to another user.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

