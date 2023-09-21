﻿---
title: 'In-meeting: during the conference'
TOCTitle: 'In-meeting: during the conference'
ms:assetid: 73aa07e8-0188-4b32-bc08-e28d028a5f59
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465925(v=office.15)
ms:contentKeyID: 57102419
ms.date: 07/25/2014
mtps_version: v=office.15
---

# In-meeting: during the conference


**Applies to:** Lync 2013 | Lync Server 2013

 

From the perspective of an end-user, there are two main types of conferences:

  - Scheduled conferences that are referenced in meeting invitations.
    
    Participants of this type of conference join by clicking a Web URL or by dialing into the Audio Conference bridge with information retrieved from their calendar.

  - *Ad hoc* conferences (impromptu collaboration meetings)
    
    *Ad hoc* conferences usually result from the escalation of a peer-to-peer conversation to a conference or from a meet-now feature invocation.

Several conference-join and in-meeting features are present in UCMA 4.0 and Lync Server 2013. These new features consist of the following actions:

  - Joining the conference lobby before being admitted into the Conference.

  - Managing the conference lobby.

  - Enabling or disabling PSTN lobby bypass.

  - Changing the conference Access Level.

  - Modifying the Automatic Presenter Assignment.

  - Being notified when the conference Termination Countdown is activated.

  - Being notified when participants are recording the Conference.

  - Muting all participants of the conference.

  - Enabling or disabling the conference entry/exit announcements.


> [!NOTE]
> <P>These features are not available for use when joining a conference hosted by Office Communications Server 2007 or Office Communications Server 2007 R2 with UCMA 3.0. This usually happens when Lync Server 2010 and Office Communications Server 2007 or Office Communications Server 2007 R2 coexist on customer premises or when these server versions are federated with each other.</P>



## Join the conference lobby

Participants who join the lobby of a conference with UCMA 4.0 can wait to be admitted into or declined from the conference. The conference Join operation completes only when the lobby participant is either granted access to the conference by a presenter or denied access to the conference on time-out or following the intervention of a presenter.


> [!NOTE]
> <P>The conference lobby is disabled for conferences hosted by Lync Server 2010 and migrated from Office Communications Server 2007 or Office Communications Server 2007 R2 (that is, the conferences were originally scheduled on Office Communications Server 2007 or Office Communications Server 2007 R2, and the organizer’s home pool was moved to Lync Server 2010). Consequently, when these conferences are locked, UCMA 4.0 treats them as UCMA 2.0 used to by gracefully failing to join the conference. Similar to UCMA 2.0 behavior, UCMA 4.0 gracefully fails at joining a locked conference hosted by Office Communications Server 2007 or Office Communications Server 2007 R2, because the conference lobby does not exist in these server versions.</P>
> <P>In addition, a participant who is escalated to a conference, and who is placed into the lobby will systematically fail at joining the conference with UCMA 4.0. This is a limitation of the API.</P>



## Manage the conference lobby

Conference leaders can manage a UCMA 4.0 conference lobby. They can admit lobby participants into the conference one-by-one or in batches. They can also deny lobby participants access to the conference.

Leaders and attendees of UCMA 4.0 conferences are made aware of when a participant joins or leaves the conference lobby as well as the reason (the participant left, was admitted into the conference, or was ejected due to time out or presenter action).


> [!NOTE]
> <P>Opening the lobby (by changing the conference Access Level to <STRONG>Everyone</STRONG>) applies only to new participants entering the lobby. It does not result in admitting existing lobby participants, as the operation is not retroactive. The application writer is responsible for admitting current lobby participants.</P>



## Change the lobby bypass assignment

Conference leaders can enable or disable the PSTN conference Lobby Bypass feature in UCMA 4.0 meetings. Depending on whether PSTN conference Lobby Bypass is enabled, anonymous phone users dialing into the conference through SIP PSTN gateways will either join the audio portion of the conference directly or will need to wait in the lobby.

## Change the access level of a conference

The leader of a conference hosted by Lync Server 2013 can modify the Access Level of a conference after joining it. For example, the leader can change the Access Level of a conference to **Everyone**, which is equivalent to opening the lobby.


> [!NOTE]
> <P>An application developer should verify which allowed conference Access Levels (if any) can be used after joining a conference. The allowed conference Access Levels vary from conference to conference and cannot be inferred from the conferencing capabilities. For example, it's possible that no conference Access Level change is allowed when joining a Microsoft Office Communications Server 2007 R2 conference during migration.</P>



**Locking a conference**

There are two ways to lock a conference using UCMA 4.0. The first way consists of changing the conference Access Level to **Locked**. After the conference is locked, the application developer, conference owner, or conference presenter must supply a new Access Level for the conference to unlock the conference.

The second way of locking the conference consists of using a dedicated set of APIs to lock and unlock the conference. After the conference has been unlocked, its Access Level prior to being locked is reverted to. The application developer, conference owner, or conference presenter do not need to specify a new conference Access Level.

## Change the automatic leader role Assignment

In addition to enabling conference leaders to change the role of a participant from Attendee to Leader (promotion), UCMA 4.0 also enables conference Leaders to control the automatic Leader Role Assignment in a meeting. For example, the automatic promotion to **Leader** can be changed from **Everyone** to **SameEnterprise** to avoid anonymous users taking control of a meeting. Alternatively, automatic Leader Role Assignment can simply be turned off.


> [!NOTE]
> <P>An application developer should first decide which allowed automatic Leader Role assignment (if any) can be used after joining a conference.</P>



## Conference termination countdown

UCMA 4.0 informs the application developer of when the conference Termination Countdown is fired. This typically results from the last authenticated (**SameEnterprise**) user of the conference leaving it and consists of a grace period after which the conference is deactivated.


> [!NOTE]
> <P>During this grace period, if an authenticated (<STRONG>SameEnterprise</STRONG>) user rejoins the conference, the conference Termination Countdown is stopped.</P>



## Conference recording

Conference participants are aware of the conference Recording Policy when they join a UCMA 4.0 meeting. This policy, which is honored by, but not enforced by Lync Server 2013, indicates whether **Everyone**, a **SameEnterprise** user, or no one is authorized to record the conference.

Conference recording (which is initiated by a conference participant) differs from conference archiving (which is initiated by an Administrator). There is no conference Archiving Policy available with Lync Server 2013 and UCMA 4.0.

Participants of a conference who have joined with UCMA 4.0 are notified of the participants who are currently recording the conference. However, these participants are unable to let other conference participants know that they are recording with UCMA 4.0; this is a limitation of the API.


> [!IMPORTANT]
> <P>Just because there is no indication of participants who are recording a conference, this does not guarantee that no participants are doing so. Honoring the conference recording policy is left to application implementers.</P>



## Inviting new participants

Conference participants can send individual conference invitations, allowing new participants to join the conference from the invitation. The conference invitation automatically falls back to a Multipoint Control Unit (MCU) dial-out if the remote participant does not understand the semantics of the invitation.

UCMA 4.0 gives all the information necessary to track the status of a pending conference invitation. This makes it possible for the invitation to be forwarded to another participant.

## Mute-All mode

In addition to the continued support for letting attendees mute themselves in an audio conference and letting presenters individually mute other participants, UCMA 4.0 provides an effective way to mute all participants in an audio conference. This feature is particularly useful to avoid interruptions due to background noise or other nuisance sounds during a presentation.

When a conference leader enables the Mute-All mode in a conference, everyone but the presenter who invoked the feature is muted. After enabling this mode, the presenter can choose to let all participants unmute themselves or allow only conference leaders to unmute themselves.

When the Mute-All mode is enabled, new participants joining the meeting are automatically muted. When the Mute-All mode is exited, conference leaders and attendees who are already in the conference remain muted but can unmute themselves; this includes attendees who may not have been able to unmute themselves while Mute-All was enabled. New participants join the conference unmuted.


> [!NOTE]
> <P>Note that before muting all, the application developer should verify that the conference supports Mute-All.</P>



## Entry-Exit announcement

UCMA 4.0 supports turning the Entry-Exit announcement on or off in an audio conference. This announcement is played to all participants of the conference when a participant enters or leaves the conference. The announcement includes the name of the participant who is entering or leaving.


> [!NOTE]
> <P>Before toggling Entry Exit announcements, an application developer should first verify whether the audio conference supports toggling the Entry Exit announcement.</P>


