---
title: Unattended installation of LSM and LDL
TOCTitle: Unattended installation of LSM and LDL
ms:assetid: f2eba9a3-9888-4a1b-b689-567a83ebcb90
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn785205(v=office.15)
ms:contentKeyID: 62952689
ms.date: 02/16/2015
mtps_version: v=office.15
---

# Unattended installation of LSM and LDL

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013

In production, you often have to install the Lync SDN Manager and Lync Dialog Listener in an unattended mode. This article describes the parameters that are used for an unattended installation.

## Unattended installation of LDL

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>INSTALLDIR</p></td>
<td><p>Specifies the installation destination for the binaries.</p></td>
</tr>
<tr class="even">
<td><p>SUBMITURI</p></td>
<td><p>URI to locate the LSM, e.g. SUBMITURI=http://localhost:9333/LDL.</p></td>
</tr>
<tr class="odd">
<td><p>ALTERNATIVEURI</p></td>
<td><p>URI to locate the secondary LSM or secondary LSM pool. This URI is used in case of a fail-over from the primary LSM or LSM pool.</p></td>
</tr>
<tr class="even">
<td><p>ACCOUNTYPE</p></td>
<td><p>Type of account to run LDL, 0 for Network Service account and 1 user account.</p></td>
</tr>
<tr class="odd">
<td><p>APPLIED_SERVICE_USERNAME</p></td>
<td><p>Domain/username for the LDL Windows Service account.</p></td>
</tr>
<tr class="even">
<td><p>APPLIED_SERVICE_PASSWORD</p></td>
<td><p>Password for the LDL Windows Service account.</p></td>
</tr>
<tr class="odd">
<td><p>THUMBPRINT</p></td>
<td><p>Thumbprint of the client certificate needed to contact the LSM.</p></td>
</tr>
<tr class="even">
<td><p>USE_SRV_RECORD_BOOL</p></td>
<td><p>(e.g. USE_SRV_RECORD_BOOL=True) Instead of using the SubmitURI, retrieve the location of the LSM from the DNS SRV record.</p></td>
</tr>
<tr class="odd">
<td><p>SKIPREGISTRATION</p></td>
<td><p>During the installation, a PowerShell script is executed to register the LDL with Lync Server. Set SKIPREGISTRATION=1 to skip executing this script. You must manually perform this registration and start the LDL Windows service. An example of this script can be found under C:\ProgramData\Microsoft\Lync Dialog Listener\Register.ps1</p></td>
</tr>
</tbody>
</table>

> [!NOTE]
> When DNS "Service Location (SRV)" records are used by LDL, any configured value for the parameter submitURI is ignored. Instead, the URI specified in the SRV record is used.

An installation using the SKIPREGISTRATION=1 option offers an interesting alternative installation option. This script executed has three major purposes: Perform the registration of Lync SDN Interface with Lync, so that Lync forwards request and response messages to the LyncDialogListener service, attempt to activate sending of Incall Quality messages, and to start the service itself.

The registration and activation are only required once for the entire pool and the LDL Windows service can be started manually as well as using several other options. As the script also uses some lengthy verifications whether Lync Server is ready and setup correctly, this step could be skipped, speeding up deployment and specifically upgrade processes for experienced administrators.

## Unattended installation of LSM

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Parameter</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>INSTALLDIR</p></td>
<td><p>Specifies the installation destination for the binaries.</p></td>
</tr>
<tr class="even">
<td><p>SUBMITURI</p></td>
<td><p>URIs and filters to locate the Network Controller(s)</p></td>
</tr>
<tr class="odd">
<td><p>TOPOLOGY</p></td>
<td><p>describes the desired deployment scenario:</p>
<div class="tableSection">
<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>(Cache) Use an in-memory cache for settings and call state</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>(Split) Use an in-memory cache for call state but share the settings through the SDNManager database</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>(Database) Use the SDNManager database to store and share the settings as well as call state</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p>DATABASE_SERVER</p></td>
<td><p>(e.g. DATABASE_SERVER=ContosoBE\Monitoring) specify the SQL server as well as SQL instance, if appropriate.</p></td>
</tr>
<tr class="odd">
<td><p>SQL_ADMIN_USER</p></td>
<td><p>Account to use to create and setup the database. Do not specify when using SQL integrated security with the current user running the setup.</p></td>
</tr>
<tr class="even">
<td><p>SQL_ADMIN_PASSWORD</p></td>
<td><p>Password for the SQL admin account if SQL Authentication is used.</p></td>
</tr>
<tr class="odd">
<td><p>SQLUSER</p></td>
<td><p>Account to use as the LSM to access the SDNManager database. Do not specify for Windows integrated security using the Network Service account</p></td>
</tr>
<tr class="even">
<td><p>SQLPASSWORD</p></td>
<td><p>Password for the SQL account if SQL Authentication is used</p></td>
</tr>
<tr class="odd">
<td><p>SETUPDB</p></td>
<td><p>Setting this parameter to 1 causes the installer to create the SDNManager database. This parameter must be set (SETUPDB=1) for the first LSM installation when a database for call state or settings should be created.</p></td>
</tr>
</tbody>
</table>


## Doing an unattended uninstall

To do an unattended uninstall, do the following:

- **For LDL**: In the command line, type: 

`C:\Windows\System32\msiexec.exe /X{C741381E-92CE-4867-BBCB-E329637606DE}`

- **For LSM**: In the command line, type: 

`C:\Windows\System32\msiexec.exe /X{60A580F2-7B7A-4665-9696-07BE5D9AF15F}`

## See also

- [Installing Lync SDN Manager](installing-lync-sdn-manager.md)
- [Lync SDN Interface Schema Reference](lync-sdn-interface-schema-reference.md)

