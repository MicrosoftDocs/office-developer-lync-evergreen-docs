---
title: 'How to: Manage a SIP application'
TOCTitle: 'How to: Manage a SIP application'
ms:assetid: f82cabc4-119d-4d54-a87c-798be642c305
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439087(v=office.15)
ms:contentKeyID: 57096670
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- powershell
---

# How to: Manage a SIP application

Learn how to manage a SIP application in a Microsoft Lync Server 2013 deployment.


**Applies to**: Lync Server 2013

## Managing a SIP application on Lync Server

To manage a Lync Server 2013 SIP application, you should inspect and modify the application settings and rehearse how to remove the application. You can use the following Microsoft Windows PowerShell commands to manage the application.

  - To inspect an application’s settings, you can issue the following cmdlet in a Lync Server Management Shell console.
    
    ``` powershell
    get-CsServerApplication
    ```
    
    The previous cmdlet displays all of the Lync Server SIP applications that are currently registered with the local Lync Server deployment.
    
    To inspect a specific SIP application, you can pass in to the cmdlet the identity of the application as shown in the following example.
    
    ``` powershell
    Get-CsServerApplication –identity "service:registrar:lync-se.contoso.com/HelloWorld"
    ```
    
    In the previous example, the identity parameter value corresponds to the assigned identity of the application when it is registered by using the **New-CsServerApplication** cmdlet, as discussed in [How to: Register a SIP application](how-to-register-a-sip-application.md).

  - To change an application’s settings, you can call the **Set-CsServerApplication** cmdlet to supply appropriate parameter values. For example, the following cmdlet changes the priority of the HelloWorld application that is discussed in [How to: Register a SIP application](how-to-register-a-sip-application.md).
    
    ``` powershell
    set-CsServerApplication –identity "service:registrar:lync-se.contoso.com/HelloWorld" –priority 7
    ```

  - To cancel the registration of an application, you simply remove it from the Lync Server instance by calling **Remove-CsServerApplication**. For the HelloWorld application that is discussed in [How to: Register a SIP application](how-to-register-a-sip-application.md), calling the following cmdlet remove it from the Lync Server topology.
    
    ``` powershell
    remove-CsServerApplication –identity "service.registrar:lync-se.contoso.com/HelloWorld"
    ```


> [!NOTE]
> <P>The commands appearing in this topic can be run without shutting down the server.</P>



## See also

#### Concepts

[Managed SIP Application API](managed-sip-application-api.md)

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

