---
title: Contextual Lync conversations
TOCTitle: Contextual Lync conversations
ms:assetid: e9ecc787-f16a-4244-9eea-6a920a4ec8a3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945578(v=office.15)
ms:contentKeyID: 51541400
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xaml
- csharp
---

# Contextual Lync conversations

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the concept of contextual conversations in Lync 2013 and about application scenarios, application development models, and contextual extension application package registration.

**Last modified:** February 22, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Conversation overview<br />
Application scenarios<br />
Development models<br />
Use Install Registration and Runtime Registration<br />
In this section<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

## Conversation overview

Use contextual conversation with Microsoft Lync 2013 SDK to increase productivity by capturing the message sender’s context, setting up the receiver’s context, or both:

  - Contextual conversation improves productivity by reducing interruptions to the recipient’s workflow.

  - Contextual conversation improves productivity by reducing the time required for call participants to join one unique data environment.

## Application scenarios

Adding context to the data carried by a call makes communication more efficient. The purpose of the context framework is to allow the receiver to quickly step into the same data environment inhabited by the caller.

### Open third-party applications in Conversation Window Extension

Use Microsoft Lync 2013 CWE to display a business application that relates to the call. This application might display information about the caller or allow users to enter information about the call.

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
<td><p>The contextual application must be installed and registered on each client computer where it will be used. For more information, see <a href="register-contextual-conversation-packages.md">Register contextual conversation packages</a>.</p></td>
</tr>
</tbody>
</table>

### Add context to a conversation you are joining

Use contextual conversation features to add information about the sender, the conversation, or other business application uses. For example:

  - Launch an application when the conversation window is opened. For more information, see [Lync Conversation Window Extension](lync-conversation-window-extension.md).

  - Add rich or simple application context. Rich context is automatically starting an application or passing real-time data between business applications. For example, two CAD programs exchanging x, y, z coordinates for a 3D object. For more information, see [Send and update context in an existing conversation](send-and-update-context-in-an-existing-conversation.md). Simple context is sending a URL side that is displayed in the conversation window. It does not require package registration and positions the security responsibility on the user to determine whether he or she wants to click the link.

  - Share a URL. A sales manager can include a supplier's URL in an IM to a member of his or her sales team. For more information, see [How to: Send and receive context information in a Lync conversation](how-to-send-and-receive-context-information-in-a-lync-conversation.md).

  - Customize the message subject. A business analyst can customize the subject line that accompanies his or her audio or IM message.

### Transfer calls with context

Although not necessarily a contextual conversation feature, seamlessly transferring calls without losing context is important to correctly implement the contextual conversation experience. In a previous scenario, Marie opens a conversation with Ken using IM and then transfers the audio call to him.

## Development models

Use Lync SDK at two levels, ranging from easy to complex, to add contextual conversation features to business calls:

  - Use Microsoft Lync Controls to add contextual conversation support to an application by using drag-and-drop XAML controls and code-behind. For more information see [Get started with Lync Controls](get-started-with-lync-controls.md).

  - Use the Microsoft Lync 2013 API to add contextual conversation to an application that uses .NET Framework code. For more information see [How to: Send and receive context information in a Lync conversation](how-to-send-and-receive-context-information-in-a-lync-conversation.md).

### Use contextual conversation with Lync Controls

The Lync 2013 API includes many XAML controls, each available in Microsoft Silverlight and Microsoft Windows Presentation Foundation (WPF) versions. You can add these controls to existing business applications and use either XAML or the code-behind page to add contextual conversation features. The following example adds the sender’s context to an IM conversation. For more information, see [How to: Start a contextual conversation with an IM call](how-to-start-a-contextual-conversation-with-an-im-call.md).

``` xaml
<StackPanel>
  <StackPanel.Resources>
    <controls:ConversationContextualInfo 
      x:Key="contextualInfo" 
      ApplicationId="{}{21224942-AC24-4D0D-B0C7-6107D79448DF}"
      ApplicationData="your application data here"
      Subject="Try out this customized toast!"
    />
  </StackPanel.Resources>
    <controls:StartInstantMessagingButton 
      x:Name="startInstantMessaging"
      Source="sip:barbara@contoso.com"
      ContextualInformation="{StaticResource contextualInfo}"
    />
</StackPanel>
```

### Add context to a conversation with Lync API

The Lync 2013 API includes a managed code API that you can use to add contextual conversation features to conversations with the Lync 2013 UI as an optional element. The following example adds an application ID and application data to a conversation. For more information, see [Send and update context in an existing conversation](send-and-update-context-in-an-existing-conversation.md).

``` csharp
Dictionary<ContextType, object> context = new Dictionary<ContextType, object>();
context.Add(ContextType.ApplicationId, "{d0722164-f660-470f-a933-e4853f215b77}");
context.Add(ContextType.ApplicationData, "Some data string");
IAsyncResult res = conversation.BeginSendInitialContext(context, null, null);
```

### Add simple context or rich context

Developers can add simple context to conversations or install packages to provide rich context.

**Adding simple context**

Developers can add simple context to a conversation by sending an untrusted URL with a message. The message recipient will see the text "A contextual link has been provided with this conversation. If the link below looks suspicious do not click on it." followed by the URL. For more information, see [How to: Send and receive context information in a Lync conversation](how-to-send-and-receive-context-information-in-a-lync-conversation.md).

**Adding rich context**

Developers can add rich context by sending an application ID in the message content. Using rich context requires application package installation on the sending and receiving computers. For more information, see [Register contextual conversation packages](register-contextual-conversation-packages.md). The application ID in the message is used to launch a package as follows:

  - The package provides a start link that specifies a file path or URL.

  - The package opens an application in Lync Conversation Window Extension.

Rich context provides an easier way for an application to register for events with Lync 2013. For example, by using rich context, Microsoft Visual Studio can examine incoming conversations. When Visual Studio detects an appropriate conversation, it instructs Lync 2013 to dock the conversation window in the Visual Studio environment.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rich context requires a registered package on the target computer. If the package is registered, it can be trusted. For more information about trust, see <a href="establish-trust-on-contextual-conversation-clients.md">Establish trust on contextual conversation clients</a>.</p></td>
</tr>
</tbody>
</table>

## Use Install Registration and Runtime Registration

Contextual conversation packages can be installed to a URL or file path. To simplify package management, install it to a URL, and then register the contextual application with Lync 2013.

  - You can specify a default application that is used to provide a context when none is available. For example, when a sales manager gets a call, a CRM contextual application is specified and then starts. The contextual application provides information about the caller. For more information about default applications, see [Understand the role of the default CWE application registration package](understand-the-role-of-the-default-cwe-application-registration-package.md).

  - After registration is complete, you can provide rich context and applications. For example, when two oil field engineers consult about a field, the company’s line-of-business application starts and displays various graphical displays providing geological data.

There are two ways to register a contextual application:

  - Install Registration

  - Runtime Registration

The recommended practice is to perform Install Registration to install the contextual application, and then Runtime Registration every time that the application starts.

**Install Registration**

Use Install Registration to manage and deploy contextual conversation experience by product installations. The alternative is Runtime Registration. Use Install Registration to improve control of package setup. For more information, see [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md).

**Runtime Registration**

Use Runtime Registration for flexible package setup. Use the ApplicationRegistration class to perform Runtime Registration. For more information, see [How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md).

## In this section

  - [Register contextual conversation packages](register-contextual-conversation-packages.md)

  - [Establish trust on contextual conversation clients](establish-trust-on-contextual-conversation-clients.md)

  - [Understand the role of the default CWE application registration package](understand-the-role-of-the-default-cwe-application-registration-package.md)

  - [Understand the purpose of runtime application registration](understand-the-purpose-of-runtime-application-registration.md)

  - [Consume data and handle events in a contextual conversation](consume-data-and-handle-events-in-a-contextual-conversation.md)

  - [Send and update context in an existing conversation](send-and-update-context-in-an-existing-conversation.md)

  - [Send and update context in a UCMA conversation](send-and-update-context-in-a-ucma-conversation.md)

  - [Add a Silverlight application to Conversation Window Extension](add-a-silverlight-application-to-conversation-window-extension.md)

  - [Client support scenarios](client-support-scenarios.md)

## See also

  - [Beyond the basics: Lync conversations](beyond-the-basics-lync-conversations.md)

  - [Lync Conversation Window Extension](lync-conversation-window-extension.md)

