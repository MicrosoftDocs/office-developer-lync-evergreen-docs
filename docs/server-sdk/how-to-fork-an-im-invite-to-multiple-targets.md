---
title: 'How to: Fork an IM invite to multiple targets'
TOCTitle: 'How to: Fork an IM invite to multiple targets'
ms:assetid: a57ab2af-0484-4421-8a29-06b5aa59649d
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439076(v=office.15)
ms:contentKeyID: 57096237
ms.date: 07/24/2014
mtps_version: v=office.15
---

# How to: Fork an IM invite to multiple targets

Learn how to use a script application to fork a message in a Microsoft Lync Server 2013 deployment.


**Applies to:** Lync 2013 | Lync Server 2013

When you forward a message to multiple endpoints, forking occurs. Ringing multiple devices that belong to a user simultaneously is an example of forking. The process of broadcasting a message is used to fork a message to multiple users. The Microsoft Lync Server 2013 SIP Application API supports this kind of scenario by using either script-only or managed code applications, depending on the complexity of the application logic. In this topic, a script-only application is used to fork a message in a Lync Server 2013 deployment.

The following Microsoft SIP Processing Language (MSPL) script forks an INVITE request to all currently active endpoints that are connected to the targeted user.

    <?xml version="1.0"?>
    <r:applicationManifest
       r:appUri="http://www.contoso.com/ForkInvite"
       xmlns:r="http://schemas.microsoft.com/lcs/2006/05">
       <r:allowRegistrationBeforeUserServices/>
       <r:serverFilter roles="ALL"/>
    
       <!-- handle INVITE requests -->
       <r:requestFilter methodNames="INVITE"
                     strictRoute="false"
                     registrarGenerated="true"
                     domainSupported="true"/>
    
       <!-- handle no response. -->
       <r:responseFilter reasonCodes="NONE"/>
    
       <r:proxyByDefault action=”true”/>
    
       <!-- Script-only application. -->
       <r:scriptOnly/>
    
       <r:splScript><![CDATA[
         if (!sipRequest) {
           return;
         }
    
         foreach( h in GetHeaderValues(StandardHeader.UserAgent)) {
           if (ContainsString(h, "Microsoft Lync", false)) {
             Log("Event", false, "With Lync, forking is not necessary.");
     return;
           }
         }
         
         forked=false;
         toUri = GetUri(sipRequest.To); 
         toUserAtHost = GetUserAtHost(toUri);
         Log("Event", true, "Enter ForkInvite...", "\r\ntoUri: ", toUri, "\r\ntoUserAtHost: ", toUserAtHost);
         BeginFork(false, 0);
         foreach(dbEndpoint in QueryEndpoints(toUserAtHost)) {
           Log("Event", false, "dbEndpoint: ", dbEndpoint.ContactInfo);
           Fork(dbEndpoint.ContactInfo);
           forked=true;
         }
         EndFork();
    
         if (!forked) {
           Log("Event", false, "Invite not forked");
           ProxyRequest("");
         }
         else {
           Log("Event", false, "Invite forked");
         }
       ]]></r:splScript>
    </r:applicationManifest>

Fixed routing resembles message forwarding. It must be disabled in the application manifest. This means that the strictRoute attribute of the [requestFilter](https://msdn.microsoft.com/library/hh347121\(v=office.15\)) element must be set to false in the application manifest for message forking. Also, forking should not be applied to a session-bound message.


> [!NOTE]
> <P>The application should be registered to run at a higher priority than the <STRONG>UserServices</STRONG> application.</P>



## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

[Scenarios for using the Lync Server 2013 API](scenarios-for-using-the-lync-server-2013-api.md)

