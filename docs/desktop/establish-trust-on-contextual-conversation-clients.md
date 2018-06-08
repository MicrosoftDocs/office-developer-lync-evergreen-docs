---
title: Establish trust on contextual conversation clients
TOCTitle: Establish trust on contextual conversation clients
ms:assetid: a96b244e-d4e0-4710-9527-a85fad9213da
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945572(v=office.15)
ms:contentKeyID: 51541387
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Establish trust on contextual conversation clients

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Trust in a Microsoft Lync Control application is determined by the source of the contextual information offered to the user. If context comes from an installed application, an offer of trust is present. If context comes from a URL, there is less trust.

**Last modified:** February 14, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Not trusted - context provided by contextual link<br />
Trusted - context provided by package registration<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Not trusted - context provided by contextual link

Contextual link is the simplest form of context for Lync 2013 applications. The developer uses the [HyperLink](https://msdn.microsoft.com/en-us/library/gg267182\(v=office.15\)) enumerated value to add a URL to the message. The message recipient sees the following message along with the URL and should evaluate the circumstances and decide whether to trust the URL: A contextual link has been provided with this conversation. If the link below looks suspicious, do not click it.

For an example of an application that sends a contextual link message, see [How to: Start a contextual conversation with an IM call](how-to-start-a-contextual-conversation-with-an-im-call.md).

## Trusted - context provided by package registration

Alternatively, provide context by installing a package or application on the sending and receiving client computers. Trust for the application’s context is managed by registering a client-side application. This type of registration resembles a simple plug-in model. In this case, when the user starts a conversation, the application providing context is already verified. The user can trust the installed application.

There are two package registration methods. Both methods allow the developer to deploy a trusted application to client computers without involvement or management by a system administrator. For information about package registration data, see [Register contextual conversation packages](register-contextual-conversation-packages.md).

### Install Registration

In this method, the package registration data is typically added to the Lync 2013 registry hive by an installing application. Install Registration is also possible using Group Policy object (GPO) deployment or by the system administrator editing the registry. Use Install Registration for Lync 2013 applications that use a default application to provide message context. For an example that shows how to perform install registration, see [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md).

### Runtime Registration

In this method, the application registration data is added to the Lync 2013 registration pool at runtime by the Lync 2013 application. By using Runtime Registration, the developer can decide to manage the contextual experience by selecting one of several alternative packages to install. For an example that shows how to perform Runtime Registration, see [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md).

## See also

  - [Contextual Lync conversations](contextual-lync-conversations.md)

