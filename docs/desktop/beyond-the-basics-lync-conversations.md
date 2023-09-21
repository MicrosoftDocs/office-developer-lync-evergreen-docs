---
title: 'Beyond the basics: Lync conversations'
TOCTitle: Lync conversations
ms:assetid: b0d9e12e-87ec-4f91-952f-f376630d241b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933166(v=office.15)
ms:contentKeyID: 50877304
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Beyond the basics: Lync conversations

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about extending the functionality of the Lync 2013 conversation window by creating hosted Silverlight browser applications that are powered by the Microsoft Lync 2013 SDK object model to tightly integrate the browser application with the hosting Lync conversation window.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Application development scenarios<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Application development scenarios

If you are familiar with the basic conversation-related components of the Microsoft Lync 2013 API object model, you are ready to learn about what types of solutions you can create using those components. This topic introduces several ways you can use the conversation components of the Lync object model to create solutions. The types of solutions that you can create include the following types:

  - Lync 2013 conversation window docking.

  - Extending the Lync 2013 conversation window by creating hosted Silverlight browser applications.

  - Sending and receiving domain-originated information in a conversation as context.

  - Building a fully featured conversation window replacement as a stand-alone client or module of your application.

Conversation window docking is useful when you want to place a Lync 2013 conversation window within a container control in your own application. When you do this, you provide a user with a seamless experience where the user does not need take focus away from your application to bring the Lync 2013 client to the top of the window order on the desktop. You can programmatically start a conversation window, get the handle of your container control, and then dock the new conversation window in the container.

A Conversation Window Extension (CWE) application is useful when you want to present a rich contextual experience to a user while the user is having a conversation in the context of your application data. The CWE is hosted within the conversation window as a panel to the right of the IM pane. The Lync 2013 API provides the necessary hooks into the hosting conversation and your application logic provides context data in any form that is appropriate for a Silverlight browser application.

A CWE can be packaged in such a way that it is automatically launched in the conversation windows of all participants in a given conversation. That way, the conversation participants can collaborate in the context of your application data. For example, people who work in the accounts payable department of an organization can start a conversation with a person outside of the department in the context of an invoice that will be set up for payment in the department. An appropriate CWE in this scenario would display information from your AP system related to the invoice to be paid.

If you are building an application such as a kiosk application whose purpose is to let users communicate by using the services provided by the Lync 2013 client, but not using the client UI, then you will use the full power of the Lync 2013 API to create your own client that exposes a completely custom set of Lync 2013 features. For example, if your application is designed to let users communicate with a predefined set of other users across the whole range of conversation modalities, you can create a client that presents a prepopulated contact list that cannot be modified. You would exclude the user search feature that is built in to the Lync 2013 client.

## In this section

  - [Conversation window docking](conversation-window-docking.md)

  - [Lync Conversation Window Extension](lync-conversation-window-extension.md)

  - [Contextual Lync conversations](contextual-lync-conversations.md)

  - [Call delegation in Lync](call-delegation-in-lync.md)

## See also

  - [Get started with Lync conversations](get-started-with-lync-conversations.md)

  - [Core concepts: Lync conversations](core-concepts-lync-conversations.md)

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

