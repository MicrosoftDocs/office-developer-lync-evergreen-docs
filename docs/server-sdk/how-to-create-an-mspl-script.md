---
title: 'How to: Create an MSPL script'
TOCTitle: 'How to: Create an MSPL script'
ms:assetid: 5dc2fa7d-dc56-45fe-8115-9d30923204ce
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439080(v=office.15)
ms:contentKeyID: 57096236
ms.date: 02/11/2016
mtps_version: v=office.15
---

# How to: Create an MSPL script

Learn how to create a Microsoft Lync Server 2013 SDK message filter MSPL script.


**Applies to**: Lync Server 2013

## Writing a message filter script

A message filter is an Microsoft SIP Processing Language (MSPL) scripting application that traps SIP messages that are based on one or more criteria, and then either processes the messages or dispatches them to a managed code application for processing.

### Tips for writing message filter scripts

  - Ensure that you always handle a request when you call a function like [Fork](https://msdn.microsoft.com/library/hh347174\(v=office.15\)) by enclosing it in an if (\!sipResponse) { ... } section. For response-specific functions like [ProxyResponse](https://msdn.microsoft.com/library/hh364767\(v=office.15\)), an if (\!sipRequest) { ... } section is similarly appropriate. Remember, every time that a function attempts to process a message type it cannot handle, a critical MSPL error is raised against your application and recorded in the server event log. If ten of these errors occur, your application is disabled by Microsoft Lync Server 2013. Divide your filter into discrete sections for handling each class of message—response and request—and implement their processing separately.

  - [Log](https://msdn.microsoft.com/library/hh364642\(v=office.15\)) is the only effective mechanism you have to debug your code logic. Although the ComipleSPL.exe (for a script-only SIP application) or ApplicationManifest.Compile method (for a managed SIP application) will catch syntactical errors, code logic errors must be debugged by using ApiLogger.exe (ApiLogger.exe is distributed with Lync Server 2013). Call **Log** if a message with a specific SIP method is identified, or when any meaningful action is taken when a message is processed.

  - When forking a message, [BeginFork](https://msdn.microsoft.com/library/hh364701\(v=office.15\)), [Fork](https://msdn.microsoft.com/library/hh347174\(v=office.15\)), and [EndFork](https://msdn.microsoft.com/library/hh364734\(v=office.15\)) must be called in the implied order. Calling one out of order generates an error. [Fork](https://msdn.microsoft.com/library/hh347174\(v=office.15\)) can be called as many times for as many messages as appropriate as long as [BeginFork](https://msdn.microsoft.com/library/hh364701\(v=office.15\)) has not been closed with a subsequent call to [EndFork](https://msdn.microsoft.com/library/hh364734\(v=office.15\)). When [EndFork](https://msdn.microsoft.com/library/hh364734\(v=office.15\)) is called, all of the messages previously specified with calls to [Fork](https://msdn.microsoft.com/library/hh347174\(v=office.15\)) after the initial [BeginFork](https://msdn.microsoft.com/library/hh364701\(v=office.15\)), are forked. If you do not call [EndFork](https://msdn.microsoft.com/library/hh364734\(v=office.15\)), the forked messages are not sent, and an error is generated.

  - If your application is declared as script-only by using the [scriptOnly Element](https://msdn.microsoft.com/library/hh347182\(v=office.15\)), compilation fails if you attempt to call the [Dispatch](https://msdn.microsoft.com/library/hh364714\(v=office.15\)) function.

## See also

#### Concepts

[Microsoft SIP Processing language Script (Lync Server 2013 Preview SDK)](microsoft-sip-processing-language-script-lync-server-2013-preview-sdk.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

