---
title: Impersonating a user
TOCTitle: Impersonating a user
ms:assetid: 5b22dec3-ac5a-4774-95ad-e59c6e66bd50
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn465984(v=office.15)
ms:contentKeyID: 57102789
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Impersonating a user


**Applies to:** Lync 2013 | Lync Server 2013

The local participant address is automatically inferred from the endpoint that is specified. If the application is trusted by Microsoft Lync Server 2013, the application can impersonate another user. This is normally required to offer services on behalf of a specific user who initiated the call to the application. For example, a help-desk application might want to impersonate the user who calls in for help when it directs the call to an agent who can help the user.

Before adding calls to the conversation, the application must first indicate who is being impersonated. The impersonation API can be called for both an outgoing conversation created locally when the conversation state is **Idle**, and for an incoming conversation.

The following code demonstrates impersonating the user specified by the first parameter. The second parameter specifies the phone number of the impersonated user, and the string "Help Desk" is the name that will be displayed for the impersonated user.

``` csharp
conversation.Impersonate("sip:helpdesk@xyz.com", "tel:+2341234678", "Help Desk"); 
```

