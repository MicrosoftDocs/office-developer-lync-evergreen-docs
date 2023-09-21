---
title: Create a Lync Server API managed application project in Visual Studio
TOCTitle: Create a Lync Server API managed application project in Visual Studio
ms:assetid: 6d2473d1-e6fb-44f3-a2da-352ecba697ec
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439062(v=office.15)
ms:contentKeyID: 57096219
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Create a Lync Server API managed application project in Visual Studio

To create a Microsoft Lync Server 2013 SIP Application API application, write an application manifest or create a Visual Studio project.


**Applies to**: Lync Server 2013

  - Write a Lync Server 2013 SIP Application API application manifest that specifies the identity of the application and contains a MSPL script to process designated SIP messages. For more information, see [How to: Create an application manifest](how-to-create-an-application-manifest.md).

  - Create a Visual Studio project for a managed Lync Server 2013 SIP Application API application, if the message processing is delegated to the managed code component by using the [Microsoft.Rtc.Sip](https://msdn.microsoft.com/library/jj266253\(v=office.15\)) namespace.

### To create a Visual Studio project for a managed Lync Server SIP application

1.  Create a new Visual Studio project, and then select a project template (for example, **C\# Console Application**).

2.  In the **New Project** dialog box, specify the project name, and then choose **OK**.

3.  In **Solution Explorer**, add references to the [Microsoft.Rtc.Sip](https://msdn.microsoft.com/library/jj266253\(v=office.15\)) namespace by doing the following:
    
    1.  Right-click **References** under the newly created project.
    
    2.  Select **Add Reference**.
    
    3.  Navigate to the **bin** directory under the main installation directory of the Lync Server 2013 SIP Application API. By default, this directory path is "%progfile%\\Microsoft Lync Server 2013\\SDK\\bin".
    
    4.  Double-click the ServerAgent.DLL file.

4.  Import the Microsoft.Rtc.Sip and other dependent namespaces into the application project by inserting the following statements at the end of the using block in every code file that references the Lync Server 2013 SIP Application API.
    
    ```csharp
    using Microsoft.Rtc.Sip;
    ```

## See also

#### Concepts

[Get started with Lync Server 2013 SDK](get-started-with-lync-server-2013-sdk.md)

