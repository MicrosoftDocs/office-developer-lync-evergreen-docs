---
title: Activating a UCMA 4.0 trusted application
TOCTitle: Activating a UCMA 4.0 trusted application
ms:assetid: f75a02e0-6bc2-4e18-81fd-17907b06fb7d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466114(v=office.15)
ms:contentKeyID: 57103407
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Activating a UCMA 4.0 trusted application


**Applies to:** Lync 2013 | Lync Server 2013

A UCMA trusted application is an application based on Microsoft Unified Communications Managed API 4.0 that is trusted by Microsoft Lync Server 2013. This trust relationship is summarized in the following list:

  - Trusted applications are not challenged for authentication by Lync Server 2013.

  - Trusted applications are not throttled by Lync Server 2013 for SIP transactions, connections, or outgoing Voice over Internet Protocol (VoIP) calls.

  - Trusted applications can impersonate any user and can join conferences without appearing in rosters.

  - Trusted applications are highly available and resilient.

Activating an application is the process by which UCMA 4.0 applications are configured to take advantage of Lync Server 2013 functionality. Most of the commonly-used configuration data exists in Active Directory, the Central Management Store, and the computer that hosts the application’s local certificate store.

Activation is needed not only for deploying a ready-to-ship application, but also must be performed in order to test an application during the application development phase.


> [!NOTE]
> <P>It is recommended that the computer running the trusted application be joined to the domain in which Lync Server 2013 is running. However, if there is no intent to run Lync Server 2013 PowerShell cmdlets from the application server or to make use of UCMA auto-provisioning capabilities, then the application can be run on a computer that is not joined to the domain.</P>



## Prerequisites for activation

  - UCMA 4.0 SDK or UCMA 4.0 Runtime has been installed with Microsoft Lync Server 2013, Core Components.
    
    Microsoft Lync Server 2013 Core Components provide access to PowerShell cmdlets needed for activating the application, and include the binaries that are needed to enable a local replica, or copy, of the Central Management Store.

  - A valid server topology with Microsoft Lync Server 2013 and an Active Directory domain controller exist for the application to run against.

  - Appropriate permissions and memberships are set.
    
    An application that runs as a trusted application must be a member of the appropriate groups. These groups are created during Lync Server 2013 setup so that group members can carry out their intended tasks. The following table provides more information.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Role</p></th>
<th><p>Group membership</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 Administrator</p></td>
<td><p><strong>Domain Admins</strong> security group</p></td>
</tr>
<tr class="even">
<td><p>Trusted Application Operator</p></td>
<td><p><strong>RTCUniversalServerAdmins</strong> security group</p>
<p><strong>Administrators</strong> local group</p></td>
</tr>
<tr class="odd">
<td><p>Trusted Application Service Account</p></td>
<td><p><strong>RTC Component Local Group</strong> local group</p></td>
</tr>
</tbody>
</table>



> [!NOTE]
> <P>After Lync Server 2013 has been installed, administrators must manually create users with the previously listed permissions to act in the Trusted Application Administrator and Trusted Application Service Account roles.</P>




> [!NOTE]
> <P>A <EM>security group</EM> is an entity that exists in the domain and is stored in Active Directory. Security groups can be managed using the Active Directory Users and Computers Microsoft Management Console (MMC). A <EM>local group</EM> is an entity that exists in the computer on which the trusted application is running. Local groups can be managed by using the Local Users and Groups MMC.</P>



The following table summarizes the tasks that can be performed by the three different roles.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Task</p></th>
<th><p>Lync Server 2013 Administrator</p></th>
<th><p>Trusted Application Operator</p></th>
<th><p>Trusted Application Service Account</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Install UCMA 4.0 SDK or UCMA 4.0 Runtime</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Manage trusted application pools and trusted application computers</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Request and set certificates</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Manage trusted applications</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Manage trusted application endpoints</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="even">
<td><p>Install and activate a local Central Management Store replica</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>No</p></td>
</tr>
<tr class="odd">
<td><p>Run UCMA-based applications</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
<td><p>Yes</p></td>
</tr>
</tbody>
</table>


## In this section

The remaining topics in this section discuss how activation, provisioning, and deployment are different in UCMA 4.0 and list the activation steps that are required for all trusted applications, as well as the activation steps required by either auto-provisioned or manually-provisioned applications:

  - [General application activation](general-application-activation.md). Activation steps needed by all trusted applications

  - [Activating an auto-provisioned application](activating-an-auto-provisioned-application.md). Activation steps needed by auto-provisioned applications
    
    Auto-provisioned applications require a local copy of the Central Management Store.

  - [Activating a manually-provisioned application](activating-a-manually-provisioned-application.md). Activation steps needed for manually provisioned applications
    
    Manually-provisioned applications do not require a local copy of the Central Management Store.

  - [Activating applications programmatically](activating-applications-programmatically.md). Steps required to run Lync Server 2013 PowerShell cmdlets programmatically.

  - [Deactivation best practices](deactivation-best-practices.md)

