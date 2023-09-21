---
title: Activating QoE recording
TOCTitle: Activating QoE recording
ms:assetid: 32254d29-c4be-4d1d-80c1-3ec766f2b6f4
ms:mtpsurl: https://msdn.microsoft.com/library/Dn806347(v=office.15)
ms:contentKeyID: 63005955
ms.date: 02/11/2016
mtps_version: v=office.15
dev_langs:
- powershell
---

# Activating QoE recording

**Applies to**: Lync 2010 | Lync 2013 | Lync Server 2010 | Lync Server 2013
 
If Quality of Experience (QoE) recording has not been activated in the Lync Monintoring server, you must activate it before installing the Lync Software Defined Network (SDN) Interface 2.1.1. You can verify and activate the QoE recording in one of the two ways:

- [Using the Lync Server Control Panel](https://technet.microsoft.com/library/gg520943\(v=ocs.14\).aspx)
- [Using the Lync server Management Shell commands](https://technet.microsoft.com/library/gg398474\(v=ocs.15\).aspx)

## Verify and activate QoE recording using Lync Server Management Shell commands

To verify the QoE recording using Lync Server Management Shell commands, open a Lync Server Management Shell command prompt on a Lync Server computer and issue the following PowerShell command.

``` powershell
Get-CsQoEConfiguration -Identity site:W15Topology
```

If the EnableQoE attribute is set to True in the returned result, the QoE recording has been activated. If the EnableQoE attribute is False, issue the following PowerShell command to activate the QoE recording.

``` powershell
Set-CsQoEConfiguration -Identity site:W15Topology -EnableQoE $True
```

Here, W15Toplogy is the site name assigned to the Lync Server deployment.

For detailed information about the PowerShell commands, see [Lync Server Management Shell cmdlet](http://technet.microsoft.com/library/gg399004.aspx).

## Verify and activate QoE recording using the Lync Server Control Panel

To verify the QoE recording using the Lync Server Control Panel, start the Control Panel and select the **Monitoring and Archiving** tab on the navigation pane on the left, and then, the **Quality of Experience Data** tab on the top.

**Figure 1. Lync Server Control Panel showing QoE activation setting**

![Lync Server Control Panel showing QoE setting](images/Dn806347.lync_sdni_view_qoe_setting_in_control_pannel(Office.15).jpg "Lync Server Control Panel showing QoE setting")

If the QoE column of the specified topology (W15Topology) is checked, the QoE recording is activated. Otherwise, choose the **Edit** menu option and select the **Enable monitoring of QoE data** checkbox for the specified Lync server topology. We recommend that you also select the **Enable purging QoE data** checkbox and specify a maximum number of days to keep the QoE data before purging.
 
![Lync Server Control Panel editing QoE setting](images/Dn806347.lync_sdni_set_qoe_setting_in_control_pannel(Office.15).jpg "Lync Server Control Panel editing QoE setting")

> [!NOTE]
> Some of the parameters might not be available in the Control Panel. To view and set such advanced features, use the PowerShell commands.


## See also

- [Setting up DNS SRV record](setting-up-dns-srv-record.md)
- [Setting up SQL Server for SDNManager database](setting-up-sql-server-for-sdnmanager-database.md)
- [Installing certificates for the LDL, LSM and network controller](installing-certificates-for-the-ldl-lsm-and-network-controller.md)

