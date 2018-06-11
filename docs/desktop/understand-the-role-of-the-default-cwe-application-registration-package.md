---
title: Understand the role of the default CWE application registration package
TOCTitle: Understand the role of the default CWE application registration package
ms:assetid: 8e594256-6d06-44a4-80ee-07fe41969f9a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945568(v=office.15)
ms:contentKeyID: 51541383
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Understand the role of the default CWE application registration package

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Use the default CWE application registration package in custom Lync 2013 automation applications to specify an extensibility tab application on the receiver side of a conversation.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Where to use a default package<br />
Specify a default package<br />
Understand when a default package starts<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Where to use a default package

If an incoming conversation has no context, you can specify a default package that starts when the conversation is accepted. For example, you might want to start a customer relationship management application with every incoming call, as in the following scenario.

John receives a telephone call on Lync 2013 from an important customer. When he answers, the most important data about the customer appears in his conversation window, including that his company just opened a high-priority support case. He answers the customer by name and immediately acknowledges the issue.

## Specify a default package

You must use Install Registration to register context packages on a computer. To use a context package, register it with Lync 2013. For more information about installing and registering packages, see [Register contextual conversation packages](register-contextual-conversation-packages.md). Although multiple context packages can be installed on a computer, there is only one default package. To specify that a context package is the default, set the **DefaultContextPackage** registry key to 1.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A default package cannot be overridden at runtime by using an <a href="https://msdn.microsoft.com/en-us/library/jj293820(v=office.15)">Microsoft.Lync.Model.Extensibility.ApplicationRegistration</a> object. The default package CWE application starts with every new conversation, even when application logic specifies another install-time or runtime override application for a different extensibility tab in the conversation window.</p></td>
</tr>
</tbody>
</table>

## Understand when a default package starts

On the sender side, the default CWE application starts when the conversation window opens. On the receiving side, if a default context package is registered on the receiving computer, it starts. If another CWE application ID is specified by the sending computer and a matching application ID is found on the local computer, both CWE applications start.

## See also

  - [Contextual Lync conversations](contextual-lync-conversations.md)

  - [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md)

  - [How to: Start an extension application in a Lync conversation window](how-to-start-an-extension-application-in-a-lync-conversation-window.md)

