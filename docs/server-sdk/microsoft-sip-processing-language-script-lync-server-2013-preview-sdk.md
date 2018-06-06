---
title: Microsoft SIP Processing language Script (Lync Server 2013 Preview SDK)
TOCTitle: Microsoft SIP Processing language Script (Lync Server 2013 Preview SDK)
ms:assetid: c0cce153-8007-4898-a408-bde909cfbbd6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439067(v=office.15)
ms:contentKeyID: 57096651
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Microsoft SIP Processing language Script (Lync Server 2013 Preview SDK)

Learn about the Microsoft SIP Processing Language (MSPL) script that filters and routes SIP messages.


_**Applies to:** Lync 2013 | Lync Server 2013_

The MSPL script provides basic control for filtering and routing SIP messages. The script block is contained in the **\<splScript\>** element in the application manifest. The to-be-processed message types are also specified in the application manifest.

MSPL supports the message processing through a set of built-in constants, variables, classes, and functions. When a message that matches the type is specified in the application manifest, the server invokes the script and passes the message to the application in the sipRequest, sipResponse, and sipMessage variables. These variables correspond to instances of the [Request](https://msdn.microsoft.com/en-us/library/hh364656\(v=office.15\)), [Response](https://msdn.microsoft.com/en-us/library/hh364638\(v=office.15\)), and [Message](https://msdn.microsoft.com/en-us/library/hh364768\(v=office.15\)) built-in classes. When passed into the script, the message headers can be inspected or adjusted and the message payload can be examined or updated by using the [MSPL built-in functions](https://msdn.microsoft.com/en-us/library/hh347152\(v=office.15\)). The modified message can then be routed back to the server for additional processing by using the [ProxyRequest](https://msdn.microsoft.com/en-us/library/hh364778\(v=office.15\)) or [ProxyResponse](https://msdn.microsoft.com/en-us/library/hh364767\(v=office.15\)) function, depending on whether the message is a sipRequest or sipResponse.

In a more advanced application, the message can also be forked to other endpoints by calling the [Fork](https://msdn.microsoft.com/en-us/library/hh347174\(v=office.15\)) function against each endpoint’s SIP URI. All the **Fork** calls must be enclosed between [BeginFork](https://msdn.microsoft.com/en-us/library/hh364701\(v=office.15\)) and [EndFork](https://msdn.microsoft.com/en-us/library/hh364734\(v=office.15\)) functions.

To debug, you use the **Log** function that traces the script executions to Windows Event Viewer or the Microsoft Lync Server 2013 SDK Logging tool.

MSPL script is intended for simple message processing without reducing server performance and without accessing any external sources of information, such as a database or Active Directory. In the more advanced application scenarios, a MSPL script can delegate additional processing to a managed application component. The built-in function of [Dispatch](https://msdn.microsoft.com/en-us/library/hh364714\(v=office.15\)) is used to forward the message to the managed code from the script.

For a summary of the script syntax, see [MSPL Script Syntax (Lync Server 2013 Preview SDK)](mspl-script-syntax-lync-server-2013-preview-sdk.md). For more information about MSPL, including built-in types, variables, classes, and functions, see [MSPL Scripting Reference](https://msdn.microsoft.com/en-us/library/hh364711\(v=office.15\)).

## See also

#### Concepts

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

