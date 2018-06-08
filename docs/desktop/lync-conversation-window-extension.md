---
title: Lync Conversation Window Extension
TOCTitle: Lync Conversation Window Extension
ms:assetid: 5ad47eb4-d1b5-428b-b9fc-f88534e94160
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ945545(v=office.15)
ms:contentKeyID: 51541354
ms.date: 06/09/2015
mtps_version: v=office.15
---

# Lync Conversation Window Extension

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the Conversation Window Extension (CWE) feature of the Lync 2013 client conversation window and how is opened, closed, and sized.

**Last modified:** June 02, 2015

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
CWE overview<br />
Opening Conversation Window Extension<br />
Closing Conversation Window Extension<br />
Conversation Window Extension size<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## CWE overview

Microsoft Lync 2013 CWE is an embedded browser that allows display of a contextual application with a Lync 2013 conversation. CWE provides a hosting environment that supports traditional and rich Internet applications. To display a Microsoft Silverlight application in CWE, embed the application in an HTML page. For more information, see [How to: Create a Conversation Window Extension application in Lync SDK](how-to-create-a-conversation-window-extension-application-in-lync-sdk.md).  

![Extensibility window](images/JJ945545.LyncExtensibilityWindow1a(Office.15).png "Extensibility window")

## Opening Conversation Window Extension

CWE opens programmatically in the following scenarios:

  - When a registered context package opens in a conversation. For more information, see [Register contextual conversation packages](register-contextual-conversation-packages.md).

  - Use the [BeginOpenExtensibilityWindow](https://msdn.microsoft.com/en-us/library/jj293519\(v=office.15\)) method.

CWE can also be opened manually by selecting an application from the contact card **Options** menu. For more information, see [Add custom commands to Lync menus](add-custom-commands-to-lync-menus.md).

## Closing Conversation Window Extension

To close CWE, click the **Close** button on the tab at the bottom of the window or use the [CloseExtensibilityWindow](https://msdn.microsoft.com/en-us/library/jj275301\(v=office.15\)) method to close the window programatically. Otherwise, CWE closes when the conversation window closes.

## Conversation Window Extension size

There are two ways to specify CWE dimensions:

  - Use the [ConversationWindowExtensionSize](https://msdn.microsoft.com/en-us/library/jj278101\(v=office.15\)) enumeration.

  - During Install Registration, use the ExtensibilityWindowSize registry key for the CWE application. For more information, see [Register contextual conversation packages](register-contextual-conversation-packages.md).

## See also

[Beyond the basics: Lync conversations](beyond-the-basics-lync-conversations.md)

[How to: Create a Conversation Window Extension application in Lync SDK](how-to-create-a-conversation-window-extension-application-in-lync-sdk.md)

[How to: Install a CWE application in Lync SDK](how-to-install-a-cwe-application-in-lync-sdk.md)

[How to: Start an extension application in a Lync conversation window](how-to-start-an-extension-application-in-a-lync-conversation-window.md)

