---
title: UCMA 4.0 Runtime
TOCTitle: UCMA 4.0 Runtime
ms:assetid: 90679514-7bec-4a91-be50-f1020080a60a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466090(v=office.15)
ms:contentKeyID: 57103180
ms.date: 07/25/2014
mtps_version: v=office.15
---

# UCMA 4.0 Runtime


**Applies to:** Lync 2013 | Lync Server 2013

  

An administrator who is preparing to install a third-party UCMA-enabled application on a deployment computer must download and install UcmaRuntimeSetup.exe. Installing Microsoft Unified Communications Managed API 4.0 Runtime provides all of the UCMA-related functionality needed by a UCMA-enabled application.

## UCMA 4.0 Runtime requirements

The following are the hardware and software requirements for installing UCMA 4.0 Runtime:

- The target platform must be a 64-bit computer.

- Supported operating systems:
    
    - Windows 2012 Server
    
    - Windows Server 2008 R2 Service Pack 1
    
    - Windows 8
    
    - Windows 7 Service Pack 1 (SP1) (64-bit)
        
        Home Premium, Professional, or Ultimate editions
    

    > [!NOTE]
    > <P>Auto-provisioned applications cannot be deployed on computers running Windows 7 or Windows Vista.</P>



- Microsoft .NET Framework 4.5 (Full Profile)
    
    Windows 8 includes .NET Framework 4.5.
    
    Windows Server 2008 R2 Service Pack 1 includes .NET Framework 4.5.
    
    Windows 7 includes .NET Framework 3.5, so you must update to .NET Framework 4.5.

- Antivirus software
    
    Antivirus software can sometimes make such heavy demands on the CPU as to cause audio glitches. For this reason, antivirus software is not recommended for computers running Microsoft Lync Server 2013. For optimal performance for a server that must run antivirus software, include all Communications Server/Lync Server 2013 computers in the antivirus software’s exception list.

## Installing UCMA 4.0 Runtime and related components

This section describes how to install the Microsoft Unified Communications Managed API 4.0 Runtime and related components.

### Installing UCMA 4.0 Runtime

You must have elevated permissions to install UCMA 4.0 Runtime.


> [!NOTE]
> <P>UCMA 4.0 Runtime is installed automatically when you install UCMA 4.0 SDK. For more information, see <A href="installing-ucma-4-0-sdk.md">Installing UCMA 4.0 SDK</A>.</P>



### To install UCMA 4.0 Runtime

1.  Download UcmaRuntimeSetup.exe.

2.  Launch UcmaRuntimeSetup.exe and follow the screens to accept the End-User License Agreement (EULA). The setup wizard will install all the necessary components.

3.  Follow the instructions on the screen to complete the installation.


> [!NOTE]
> <P>UcmaRuntimeSetup.exe installs the English versions of the Speech Recognition and Text-to-Speech engines. The final screen of the installer provides a link to download additional engines for other languages.</P>




> [!NOTE]
> <P>Additional steps are required to install Microsoft Lync Server 2010, Core Components (OCSCore.msi). These steps are described later in this topic.</P>



### UCMA 4.0 Runtime components

UcmaRuntimeSetup.exe installs the following components:

- Microsoft  VC++ 2011 Redistributable (x64) 11.0.50727
    
    Microsoft Unified Communications Managed API 4.0 Runtime is built on .NET Framework 4.5 and Visual C++ 2012 Redistributable Package (x64).

- Microsoft Server Speech Platform Runtime (x64) package

- Microsoft Server Speech Recognition Language – TELE (en-US)

- Microsoft Server Speech Text To Speech Voice (en-US, Helen)

- Microsoft Lync Server 2013, Bootstrapper Prerequisites Installer Package
    
    Copies Lync Server 2013 Core Components MSI (OCSCore.msi) and its prerequisites. OCSCore.msi enables running Lync Server-specific PowerShell cmdlets from the local computer. OCSCore.msi also enables the installation of the local Central Management Store replica, which is required by auto-provisioned UCMA applications.


> [!NOTE]
> <P>Side-by-side installations of UCMA 3.0 and UCMA 4.0 are not supported.</P>



### Installing Microsoft Lync Server 2013 components

OCSCore.msi must be installed by using Bootstrapper Prerequisites Installer Package installed by UcmaRuntimeSetup.exe.

### To install Microsoft Lync Server 2013 components

1.  Confirm that Microsoft PowerShell 3.0 RTM is installed on the deployment computer.
    
    - Windows Server 2008 R2 Service Pack 1
        
        Download WINDOWS6.0-KB2506146-x64.MSU from [Windows Management Framework 3.0](http://www.microsoft.com/en-us/download/details.aspx?id=34595).
    
    - Windows 7
        
        Download WINDOWS6.1-KB2506143-x64.MSU from [Windows Management Framework 3.0](http://www.microsoft.com/en-us/download/details.aspx?id=34595).
    
    - Windows 8
        
        This operating system version comes with PowerShell 3.0.

2.  Find OCSCore.msi by navigating to %Installation drive%\\ProgramData\\Microsoft\\Lync Server\\Deployment\\cache\\\<Build Version\>\\Setup\\ .

3.  Launch OCSCore.msi and use the default settings in the wizard.

For information about activating a UCMA application, see [Activating a UCMA 4.0 trusted application](activating-a-ucma-4-0-trusted-application.md).

## Uninstalling UCMA 4.0 Runtime and bootstrapper prerequisites installer

When a customer application is uninstalled, the application uninstall procedure must not automatically uninstall any of the required components (such as .NET Framework 4.5, Visual C++ 2012 Redistributable Package, or UCMA 4.0 Runtime), because other applications might require them. An administrator who has ensured that there are no dependencies can follow the instructions in the following procedure to uninstall UCMA 4.0 Runtime.

### To uninstall UCMA 4.0 Runtime and bootstrapper prerequisites installer

1.  Navigate to **Programs and Features** in **Control Panel**.

2.  On the right-click menu for the Microsoft Unified Communications Managed API 4.0, Runtime entry, select **Uninstall**.

3.  A wizard titled "Unified Communications Managed API 4.0, Runtime Uninstallation" appears. Follow the instructions on the screen to complete uninstallation.

4.  On the right-click menu for the Lync Server 2013,  Bootstrapper Prerequisites Installer Package entry, select **Uninstall** to remove the installer package.


> [!NOTE]
> <P>Uninstalling the Bootstrapper Prerequisites Installer Package does not automatically uninstall software components that are individually installed by the user, such as Lync Server 2013 Core Components (OCSCore.msi) and others.</P>



## UCMA 4.0 Runtime detection

The following WiX code can be used to detect whether UCMA 4.0 Runtime has been installed on a computer.

    <Fragment>
      <Property Id="PROPERTY_UCMA_RUNTIME_INSTALLED" Secure="yes" />
      <Upgrade Id="{6F863046-E64C-453C-B28C-0BF9C10381DE}">
          <UpgradeVersion Minimum="5.0.8224.0" OnlyDetect="yes" Property="UCMA_PROPERTY_UCMA_RUNTIME_INSTALLED" />
      </Upgrade>
     
        <!-- Verify that the correct version of UCMA Runtime is installed -->
        <Condition Message="[ProductName] installation requires that Microsoft Unified Communications Managed API 4.0, [BuildNumber] already installed. Installation cannot continue.">
            <![CDATA[Installed Or PATCH Or MSIPATCHREMOVE Or EVALTOFULL Or REMOVE Or UCMA_PROPERTY_UCMA_RUNTIME_INSTALLED]]>
        </Condition>
    </Fragment>

