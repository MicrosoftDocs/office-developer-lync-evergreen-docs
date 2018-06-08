---
title: 'How to: Forward IM invite to a different target'
TOCTitle: 'How to: Forward IM invite to a different target'
ms:assetid: 81d489bf-1e20-41fa-853d-d10541a6b654
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439073(v=office.15)
ms:contentKeyID: 57096233
ms.date: 02/11/2016
mtps_version: v=office.15
dev_langs:
- xml
---

# How to: Forward IM invite to a different target

Learn how to use a script application to configure call forwarding in a Microsoft Lync Server 2013 deployment.


**Applies to:** Lync 2013 | Lync Server 2013

In common SIP application scenarios, incoming calls are forwarded to a different user. For example, in team collaboration, a user (A) might want another user (B) to answer IM calls from another user (C) while A goes on vacation. In customer support situations, a call to anyone in a company can be forwarded to an interactive voice responder (IVR) that can dispatch the call to available support staff. The Microsoft Lync Server 2013 SIP Application API supports this scenario by using either script-only or managed code applications, depending on the complexity of the application logic. In this topic, a script-only application is used to forward a call in a Lync Server 2013 deployment.

## Forward an IM invite from one user to another user

The following Microsoft SIP Processing Language (MSPL) script shows how to forward a call from a specified user to another specified user. The incoming INVITE is originated from the user, Nuria, as identified by the SIP URI of "sip:nuriag@contoso.com". The application uses the [RetargetRequest](https://msdn.microsoft.com/en-us/library/dn439184\(v=office.15\)) function to change the original target, Jenny, as identified by the SIP URI of "sip:jennyl@contoso.com" to a different user, Terry, as identified by the SIP URI of "sip:terrya@contoso.com".


> [!NOTE]
> <P>This script must be registered with a priority higher than that of the <STRONG>UserServices</STRONG> on the deployed Lync Server instance.</P>



```xml
<?xml version="1.0"?>
<r:applicationManifest
   r:appUri="http://www.contoso.com/ForwardInvite"
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

   <!-- Script-only application. -->
   <r:scriptOnly/>

   <r:splScript><![CDATA[
     if (!sipRequest) {
       return;
     }
     toUri = GetUri(sipRequest.To); 
     fromUri = GetUri(sipRequest.From);

     if (toUri == "sip:jennyl@contoso.com" && fromUri == "sip:nuriag@contoso.com")
     {
       RetargetRequest("sip:terrya@contoso.com");
       return;
     }
     ProxyRequest("");
   ]]></r:splScript>
</r:applicationManifest>
```

When enabled, this application forwards the call intended for Jenny (sip:jennyl@contoso.com) from Nuria (sip:nuriag@contoso.com) to Terry (sip:terrya@contoso.com). After accepting the call, Terry communicates with Nuria on behalf of Jenny. To Nuria, the ensuing conversation seems to continue with Jenny, as she intends, even though when she actually converses with Terry. The SIP messages exchanged between Nuria and Terry in this session have the **To** header that contain Jenny’s SIP URI and the **From** header that contains Nuria’s SIP URI. Requests that originate from Terry carry a **P-Asserted-Identity** header that contains Terry’s SIP URI.


> [!NOTE]
> <P>Forwarding should not be applied to any session-bound messages.</P>



Similar to forwarding a call, MSPL supports redirection of a call by using the [Respond](https://msdn.microsoft.com/en-us/library/hh364786\(v=office.15\)) function. This concept appears in the following MSPL example.

``` 
     if (toUri == "sip:jennyl@contoso.com" && fromUri == "sip:nuriag@contoso.com")
     {
       Respond("302", "Forwarded to terrya@contoso.com", "Contact=<sip:terrya@contoso.com>");
       return;
     }
```

In the redirection scenario, the call requester is aware that the call is forwarded to a different target after the call is accepted.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

[Scenarios for using the Lync Server 2013 API](scenarios-for-using-the-lync-server-2013-api.md)

#### Other resources

[Video: Use an MSPL Script to Forward IM Calls](http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.html?cid=ldc%26from=mscomldc%26videoid=d30d1ca4-a6f6-4ca4-9da0-78dda38c335f)

