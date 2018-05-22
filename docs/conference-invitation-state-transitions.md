---
title: Conference invitation state transitions
TOCTitle: Conference invitation state transitions
ms:assetid: fbab93a0-9137-41af-9f42-4e84d083eb24
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466001(v=office.15)
ms:contentKeyID: 57102905
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Conference invitation state transitions


_**Applies to:** Lync 2013 | Lync Server 2013_

State transitions for the [ConferenceInvitation](https://msdn.microsoft.com/en-us/library/hh349823\(v=office.15\)) class are described in this topic, both for inbound invitations as well as outbound invitations.

## Inbound invitation

The [ConferenceInvitation](https://msdn.microsoft.com/en-us/library/hh349823\(v=office.15\)) state transitions for inbound invitations are shown in the following illustration.

![ConferenceInvitation - Inbound](images/Dn466001.StateMach_ConfInvitation_Inbound(Office.15).jpg "ConferenceInvitation - Inbound")

**ConferenceInvitation** state transitions occur in response to the value of the [ConferenceInvitationStateTransitionReason](https://msdn.microsoft.com/en-us/library/hh384299\(v=office.15\)) enumeration.

1.  The transition from **Incoming** to **Terminating** occurs when the **ConferenceInvitationStateTransitionReason** value is **TerminatedLocally** or **TerminatedRemotely**.

2.  The transition from **Terminating** to **Terminated** occurs when the **ConferenceInvitationStateTransitionReason** value is **TerminatedLocally** or **TerminateRemotely**.

## Outbound invitation

The **ConferenceInvitation** state transitions for outbound invitations are shown in the following illustration.

![ConferenceInvitation - Outbound](images/Dn466001.StateMach_ConfInvitation_Outbound(Office.15).jpg "ConferenceInvitation - Outbound")

1.  The transition from **Idle** to **Delivering** occurs when the **ConferenceInvitationStateTransitionReason** value is **Delivering** or **Ringing**.

2.  The transition from **Delivering** to **Delivering** (that is, no change in state) occurs when the **ConferenceInvitationStateTransitionReason** value is one of the following: **Ringing**, **Deflected**, **DeflectedWithUnknownReason**, **DeflectedToAnotherDestination**, **DeflectedToDelegate**, or **FallingBackToMcuDialOut**.

3.  The transition from **Delivering** to **Terminating** occurs when the **ConferenceInvitationStateTransitionReason** value is one of the following: **None**, **Accepted**, **DeliverFailed**, **TerminatedLocally**, or **TerminatedRemotely**.

4.  The transition from **Terminating** to **Terminated** occurs when the **ConferenceInvitationStateTransitionReason** value is one of the following: **Accepted**, **DeliverFailed**, **TerminatedLocally**, or **TerminatedRemotely**.

