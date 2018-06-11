---
title: Deactivation best practices
TOCTitle: Deactivation best practices
ms:assetid: ac1ed606-5d62-463f-9891-1308b3cf31dc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466141(v=office.15)
ms:contentKeyID: 57103471
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Deactivation best practices


**Applies to:** Lync 2013 | Lync Server 2013

An application can be deactivated by following the steps in the following procedure.

### To deactivate an application

1.  Running as a Lync Server Administrator, launch Lync Server Management Shell.
    
    On the **Start** menu, select **All Programs**, select **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Remove the Active Directory contacts and [ApplicationEndpoint](https://msdn.microsoft.com/en-us/library/hh384825\(v=office.15\)) instances that you no longer need by running following PowerShell cmdlet.
    
    Remove-CsTrustedApplicationEndpoint -Identity sip:ExternalApp@mydomain.com
    

    > [!NOTE]
    > <P>Use the appropriate identity for your <STRONG>ApplicationEndpoint</STRONG> instance.</P>



3.  Remove the application service port entries that you no longer need by running the following PowerShell cmdlet.
    
    Remove-CSTrustedApplication -Identity "TrustedApps.contoso.com/urn:application:ucmasampleapplication"
    

    > [!NOTE]
    > <P>This cmdlet also cleans up any contact objects or <STRONG>ApplicationEndpoint</STRONG> instances tied to the application.</P>



4.  If the computer hosting your application from your topology is no longer needed in the topology, remove it using the following PowerShell cmdlet.
    
    Remove-CsTrustedApplicationComputer -identity "MyAppBox.contoso.com"
    

    > [!NOTE]
    > <P>Use the appropriate identity for the computer being removed.</P>



5.  If the trusted application pool is no longer needed, remove it using the following PowerShell cmdlet.
    
    Remove-CsTrustedApplicationPool -identity "MyAppPool.contoso.com"
    

    > [!NOTE]
    > <P>Use the appropriate identity for your pool.</P>

    

    > [!NOTE]
    > <P>This cmdlet also cleans up any contact objects or <STRONG>ApplicationEndpoint</STRONG> instances tied to the pool.</P>



6.  Run the Enable-CsTopology cmdlet to finalize the changes to the topology.
    
    Enable-CsTopology

