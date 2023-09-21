---
title: 'How to: Register a SIP application'
TOCTitle: 'How to: Register a SIP application'
ms:assetid: c6bb747a-1d68-4da4-8038-85ef68a2c320
ms:mtpsurl: https://msdn.microsoft.com/library/Dn439078(v=office.15)
ms:contentKeyID: 57096669
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- powershell
---

# How to: Register a SIP application

Learn how to compile and then register a SIP application manifest with the Microsoft Lync Server 2013 instance.


**Applies to**: Lync Server 2013

When the application manifest is created and the Microsoft SIP Processing Language (MSPL) script is inserted into it, you can register the application manifest with the Lync Server 2013 computer on which the SIP application runs. Registering the SIP application manifest is also known as registering the SIP application. For a script-only SIP application, the registration also loads the manifest into the server and the embedded MSPL script is then ready to be invoked. For a managed SIP application, the registration of the application does not load the manifest. Instead, it is loaded into the server by the managed SIP application that is running. In either case, the application manifest should be compiled successfully before the registration continues.

## Compiling a SIP application manifest

To compile a SIP application manifest, use the CompileSPL.exe compiler that is distributed with the Microsoft Lync Server 2013 SDK. By default, this compiler is located in the "%progfile%\\Microsoft Lync Server 2013\\SDK\\Bin" directory.

On a computer where the Lync Server 2013 SDK is installed, open a Windows Command window and type the following command from the directory where the application manifest is located.

    "%progfile%\Microsoft Lync Server 2013\SDK\Bin\CompileSPL HelloWorld.am"

In this topic, the application manifest file is called HelloWorld.am and is located in the current working directory.


> [!NOTE]
> <P>On a computer where the Lync Server 2013 SDK is not installed, you must copy the CompileSPL.exe to the computer before you run the previous command. The previous directory path might need to be modified to point to the ComipleSPL.exe compiler.</P>



## Registering a SIP application with Lync Server

A SIP application must be registered with the Lync Server 2013 computer that is used to run the application. As discussed in the following procedures, the registration of a script-only SIP application differs slightly from the registration of a managed SIP application.


> [!NOTE]
> <P>SIP applications must run from an account that belongs to the RTC Server Application local group. For a script-only SIP application, this implies that it must be registered from an account in the RTC Server Applications Group. To add a user to the RTC Server Applications local group, choose <STRONG>Start, Computer, Manage</STRONG> on the computer that is used to run the application. In the <STRONG>Server Manager</STRONG> window, choose <STRONG>Configuration, Local Users and Groups, Groups</STRONG>. Under the <STRONG>Groups</STRONG> pane, open the <STRONG>RTC Server Applications</STRONG> shortcut menu, and then choose <STRONG>Add to Group</STRONG>.</P>



### To register script-only SIP application

1.  Copy the HelloWorld.am application manifest file to the "%progfile\\Microsoft Lync Server 2013\\Server\\Core" directory.

2.  In the Lync Server Management Shell console, type the following Microsoft Windows PowerShell cmdlet command.
    
    ``` powershell
    New-CsServerApplication -uri "http://www.contoso.com/HelloWorld" -identity "service:registrar:lync-se.Contoso.com/HelloWorld" -critical $false -priority 6 -scriptname HelloWorld.am -enabled $true
    ```
    
    In the previous command, the uri parameter value must be identical to the appUri attribute value in the \<applicationManifest\> element that is declared in HelloWorld.am. In the identity parameter value the "service:registrar" part is specified because the SIP application runs on a Lync Server of the Front End role. The "lync-se.contoso.com" string specifies the FQDN of the Lync Server computer and "HelloWorld" is a name assigned to this SIP application that is associated with HelloWorld.am. The application name in the identity parameter can be different from the application manifest file name, without the .am extension, and is not correlated with the "HelloWorld" substring of the uri parameter value.
    
    A smaller priority parameter value indicates a higher priority level on which the application runs. If the application’s priority level is higher than that of the UserServices application, the \<allowRegistrationBeforeUserServices/\> element must be specified in the application manifest. In any case, the application priority level must be set higher than the DefaultRouting application. You can review these settings by using the **Get-CsServerApplication** cmdlet from a Lync Server Management Shell console.

### To register managed SIP application

1.  Copy the application manifest file (HelloWorld.am) to the managed SIP application directory (where the executable is located).

2.  Enter the following PowerShell cmdlet in the application directory from a Lync Server Management Shell console.
    
    ``` powershell
    New-CsServerApplication -uri "http://www.contoso.com/HelloWorld" -identity "service:registrar:lync-se.Contoso.com/HelloWorld" -critical $false -priority 6 -enabled $true
    ```
    
    Other than the omission of the scriptName parameter, the cmdlet that registers a managed SIP application is the same as the cmdlet that registers a script-only SIP application. The same priority issues apply.

## See also

#### Concepts

[How to use Lync Server 2013 SDK](how-to-use-lync-server-2013-sdk.md)

[Lync Server 2013 SDK general reference](lync-server-2013-sdk-general-reference.md)

