---
title: Create a Persistent Chat API application project in Visual Studio
TOCTitle: Create a Persistent Chat API application project in Visual Studio
ms:assetid: fe81a4f8-13d7-4386-b806-807a3ca81ef9
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439208(v=office.15)
ms:contentKeyID: 57101341
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Create a Persistent Chat API application project in Visual Studio


**Applies to:** Lync 2013 | Lync Server 2013

### To create a Visual Studio project for a Persistent Chat application

1.  Start Visual Studio from the Windows desktop by clicking **Start-\>Microsoft Visual Studio 2010**.

2.  Create a new project in Visual Studio by clicking **File-\>New-\>Project**.

3.  Select a project template (for example, **C\# Console Application**), specify the project name in the **New Project** box, and then click **OK**.

4.  In Solution Explorer, add references to Lync Server 2013 Persistent Chat API assembly by right-clicking **References** under the newly created project in Solution Explorer, followed by selecting the **Add Reference** menu item, navigating to the directory where the Lync Server 2013 Persistent Chat API library is installed, and then double-click the Microsoft.Rtc.Colllaboration.PersistentChat.DLL file.

5.  Import the Microsoft.Rtc.Collaboration, Microsoft.Rtc.Collaboration.PersistentChat and Microsoft.Rtc.Collaboration.PersistentChat.Management namespaces into the application project by inserting the following statements at the end of the using block in every code file referencing the Lync Server 2013 Persistent Chat API.
    
    ```csharp
    using Microsoft.Rtc.Collaboration;
    using Microsoft.Rtc.Collaboration.PersistentChat;
    using Microsoft.Rtc.Collaboration.PersistentChat.Management;
    ```


> [!NOTE]
> <P>If Lync or Persistent Chat is already installed before the Lync Server 2013 Persistent Chat SDK is installed and an exception of the BadImageException type is thrown when you attempt to access the Lync Server 2013 Persistent Chat API after the Lync Server 2013 Persistent Chat SDK is installed, it is possible that a 32-bit image of a dependent component of the Lync Server 2013 Persistent Chat SDK (for example, SIPEPS.dll) is used instead of the 64-bit version. In this case, select the <STRONG>Platform Target</STRONG> of the <STRONG>Build</STRONG> options in the Visual Studio project file and make sure all the components share a common target. Alternatively, you might need to uninstall Lync or Persistent Chat, reinstall the Lync Server 2013 Persistent Chat SDK, and then reinstall Lync or the Persistent Chat client.</P>



## See also

#### Concepts

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

