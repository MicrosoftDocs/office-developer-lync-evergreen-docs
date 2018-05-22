---
title: Add a Silverlight application to Conversation Window Extension
TOCTitle: Add a Silverlight application to Conversation Window Extension
ms:assetid: 8116ceb5-788f-4a86-b326-3c671b33bfbc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945560(v=office.15)
ms:contentKeyID: 51541363
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Add a Silverlight application to Conversation Window Extension

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about displaying Microsoft Silverlight applications in Lync 2013 CWE during Lync 2013 conversations.

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
Displaying a Silverlight application<br />
Accessing the Conversation object<br />
Additional resources</p></td>
<td><p></p>
<p></p></td>
</tr>
</tbody>
</table>

## Displaying a Silverlight application

When a Lync SDK contextual conversation starts, the application registered with the appropriate GUID opens. A Web application opens in CWE, otherwise the application opens on the desktop. To display a Silverlight application in CWE, embed the application in an HTML page and register the HTML application.

For more information about displaying a Silverlight application in CWE, see [How to: Create a Conversation Window Extension application in Lync SDK](how-to-create-a-conversation-window-extension-application-in-lync-sdk.md).

For more information about registering applications, see [Register contextual conversation packages\_Retired](https://msdn.microsoft.com/en-us/library/gg253680\(v=office.15\)).

## Accessing the Conversation object

In Lync SDK Silverlight applications, use the LyncClient.GetHostingConversation method to get the **Conversation** object that hosts CWE.

``` csharp
Conversation currentConversation = (Conversation) LyncClient.GetHostingConversation();
```

## Additional resources

  - [Contextual Lync conversations](contextual-lync-conversations.md)

