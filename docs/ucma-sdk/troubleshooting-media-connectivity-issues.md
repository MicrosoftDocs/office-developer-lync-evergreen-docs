---
title: Troubleshooting media connectivity issues
TOCTitle: Troubleshooting media connectivity issues
ms:assetid: 4476d182-c84a-4ecc-be1a-a8291b21c995
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466064(v=office.15)
ms:contentKeyID: 57103057
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Troubleshooting media connectivity issues


**Applies to:** Lync 2013 | Lync Server 2013

Several classes that are part of Microsoft Unified Communications Managed API 4.0 that can be used to provide information on call failures due to media connectivity errors. These classes can help to alert administrators of potential deployment problems.

## MediaTroubleshootingDataReportedEventArgs class

The [MediaTroubleshootingDataReportedEventArgs](https://msdn.microsoft.com/library/hh349570\(v=office.15\)) class provides troubleshooting data to the application, regarding a media connectivity error that involves a remote, external Microsoft Lync 2013 call (a corporate user who is not logged into the corporate network).

An application can register a handler for the [MediaTroubleshootingDataReported](https://msdn.microsoft.com/library/hh383527\(v=office.15\)) event on the [AudioVideoCall](https://msdn.microsoft.com/library/hh383901\(v=office.15\)) class. The second parameter of the handler is of type [MediaTroubleshootingDataReportedEventArgs](https://msdn.microsoft.com/library/hh349570\(v=office.15\)).

The [MediaChannelEstablishmentDataCollection](https://msdn.microsoft.com/library/hh382882\(v=office.15\)) property on a **MediaTroubleshootingDataReportedEventArgs** instance returns a list of [MediaChannelEstablishmentData](https://msdn.microsoft.com/library/hh383850\(v=office.15\)) instances.

## Media connectivity troubleshooting

After the call terminates, determine whether there was a media connectivity problem by checking the [EstablishmentStatus](https://msdn.microsoft.com/library/hh383434\(v=office.15\)) property on a [MediaChannelEstablishmentData](https://msdn.microsoft.com/library/hh383850\(v=office.15\)) object. An **EstablishmentStatus** value of **Failed** indicates there was a problem, while a value of **Succeeded** indicates that media establishment occurred successfully.

If the value of the **EstablishmentStatus** property is **Failed**, the application can call the [GetDiagnosticsReason](https://msdn.microsoft.com/library/hh384673\(v=office.15\)) method to obtain diagnostics information. The **GetDiagnostics** method returns a value of the [MediaChannelEstablishmentDiagnosticsReason](https://msdn.microsoft.com/library/hh383063\(v=office.15\)) enumeration.

  - If the value returned by **GetDiagnosticsReason** is either **MediaEdgeAuthenticationServiceDiscoveryFailed** or **MediaEdgeAuthenticationServiceCredentialsAquisitionFail**, raise "Alert 1".

  - If the value returned by **GetDiagnosticsReason** is **MediaEdgeResourceAllocationFailed**, raise "Alert 2".

The following are suggested alert messages for these two alerts:

Alert 1: "Lync Server 2013 calls involving remote users (located outside the Enterprise) might be failing using the current Lync Server 2013 Audio/Video Edge resources. Please contact the appropriate administrator and verify that the Lync Server 2013 Audio/Video Authentication Service is properly configured and operational."

Alert 2: "Lync Server 2013 calls involving remote users (located outside the Enterprise) might be failing using the current Lync Server 2013 Audio/Video Edge resources. Please contact the appropriate administrator and verify that the Lync Server 2013 Audio/Video Edge is properly configured and operational.


> [!NOTE]
> <P>An application should implement a throttling mechanism based on specific alert keys so that warnings do not flood the system.</P>


