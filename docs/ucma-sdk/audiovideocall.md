﻿---
title: AudioVideoCall
TOCTitle: AudioVideoCall
ms:assetid: bb378db5-96e7-47df-937d-9f912e33d609
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466040(v=office.15)
ms:contentKeyID: 57103033
ms.date: 07/25/2014
mtps_version: v=office.15
---

# AudioVideoCall


**Applies to:** Lync 2013 | Lync Server 2013

An [AudioVideoCall](https://msdn.microsoft.com/library/hh383901\(v=office.15\)) object represents an SDP-based audio/video session between a local participant and a remote participant. An **AudioVideoCall** object cannot exist on its own and must be associated with a [Conversation](https://msdn.microsoft.com/library/hh349224\(v=office.15\)) object.

The **AudioVideoCall** class handles the "audio" and "video" media types.

## AudioVideoCall state transitions - outbound calls

The **AudioVideoCall** state transitions for an outbound call are shown in the following illustration.

![Outbound AudioVideoCall state transitions](images/Dn466040.StateMach_AVCall_Out(Office.15).jpg "Outbound AudioVideoCall state transitions")

1.  The transition from **Idle** to **Establishing** occurs when the application calls [BeginEstablish()](https://msdn.microsoft.com/library/hh349055\(v=office.15\)) on the call.

2.  The transition from **Establishing** to **Establishing** occurs when the application receives the first ringing notification from the remote side while the call is in the **Establishing** state.

3.  The transition from **Establishing** to **Terminating** occurs when **BeginEstablish** fails, or when the application calls [BeginTerminate](https://msdn.microsoft.com/library/hh383376\(v=office.15\)) on the call, or when the application calls **BeginTerminate** on the conversation that contains this call.

4.  The transition from **Establishing** to **Established** occurs when [EndEstablish](https://msdn.microsoft.com/library/hh349248\(v=office.15\)) completes successfully.

5.  The transition from **Established** to **Transferring** occurs when the application calls **BeginTransfer** on the **AudioVideoCall** instance.

6.  The transition from **Transferring** to **Established** occurs when **BeginTransfer** is unsuccessful.

7.  The transition from **Established** to **Terminating** occurs when the application calls **BeginTerminate** on the call, or when the remote side terminates the call, or when the application calls **BeginTerminate** on the conversation that contains this call.

8.  The transition from **Idle** to **Terminating** occurs when the application calls **BeginTerminate** on the call, or when the application calls **BeginTerminate** on the conversation that contains this call.

9.  The transition from **Transferring** to **Terminating** occurs when the transfer operation completes successfully, or when the application calls **BeginTerminate** on the call, or when the application calls **BeginTerminate** on the conversation that contains this call.

10. The transition from **Established** to **Parking** occurs when the application requests that a call be parked on a call park server using the [BeginPark(CallParkOptions, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh384250\(v=office.15\)) method on the **AudioVideoCall** instance.

11. The transition from **Parking** to **Established** occurs when the park operation fails.

12. The transition from **Parking** to **Terminating** occurs when a park operation completes successfully. Additionally, this can occur when the application calls **BeginTerminate** on the call, or when the application calls **BeginTerminate** on the conversation that contains this call, during a park operation.

13. The transition from **Terminating** to **Terminated** occurs when [EndTerminate](https://msdn.microsoft.com/library/hh383074\(v=office.15\)) completes.

## AudioVideoCall state transitions - inbound calls

The **AudioVideoCall** state transitions for an inbound call are shown in the following illustration.

![Inbount AudioVideoCall state transitions](images/Dn466040.StateMach_AVCall_In(Office.15).jpg "Inbount AudioVideoCall state transitions")

1.  The transition from **Incoming** to **Establishing** occurs when the application calls **BeginAccept** on the call.

2.  The transition from **Establishing** to **Terminating** occurs when the call is not accepted, or when the application calls **BeginTerminate**, or when the application calls **BeginTerminate** on the conversation that contains this call.

3.  The transition from **Establishing** to **Established** occurs when the call is accepted (when [BeginAccept](https://msdn.microsoft.com/library/hh383161\(v=office.15\)) returns successfully).

4.  The transition from **Established** to **Transferring** occurs when the application calls [BeginTransfer()](https://msdn.microsoft.com/library/hh348986\(v=office.15\)) on the call.

5.  The transition from **Transferring** to **Established** occurs when **BeginTransfer** is unsuccessful.

6.  The transition from **Established** to **Terminating** occurs when the application calls **BeginTerminate** on the call, or when the remote side terminates the call, or when the application calls **BeginTerminate** on the conversation that contains this call.

7.  The transition from **Incoming** to **Terminating** occurs when the application calls **Decline**, **Forward**, or **BeginTerminate** on the call, or when the application calls **BeginTerminate** on the conversation that contains this call, or when the remote side cancels its call request.

8.  The transition from **Transferring** to **Terminating** occurs when a transfer operation completes successfully. Additionally, this can occur when the application calls **BeginTerminate** on the call, or when the application calls **BeginTerminate** on the conversation that contains this call, during a transfer operation.

9.  The transition from **Established** to **Parking** occurs when the application requests that a call be parked on a call server, using the [BeginPark(CallParkOptions, AsyncCallback, Object)](https://msdn.microsoft.com/library/hh384250\(v=office.15\)) method on the **AudioVideoCall** instance.

10. The transition from **Parking** to **Established** occurs when the park operation fails.

11. The transition from **Parking** to **Terminating** occurs when a park operation completes successfully. Additionally, this can occur when the application calls **BeginTerminate** on the call, or when the application calls **BeginTerminate** on the conversation that contains this call, during a park operation.

12. The transition from **Terminating** to **Terminated** occurs when **EndTerminate** completes.

