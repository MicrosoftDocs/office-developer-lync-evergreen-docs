---
title: Parsing meeting policy
TOCTitle: Parsing meeting policy
ms:assetid: e1c6d1da-2271-47d1-9628-7b4eb66b42e1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454639(v=office.15)
ms:contentKeyID: 57093389
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing meeting policy


_**Applies to:** Lync 2013 | Lync Server 2013_

The meeting policy from the provisioned data specifies how meetings can be conducted for the user. In Microsoft Unified Communications Managed API (UCMA), the meeting policy is encapsulated by a MeetingPolicyConfiguration object, which exposes the meeting policy as a collection of name-value pairs known as the properties of the meeting policy configuration.

The following code example shows how the meeting policy might be parsed by using UCMA.

```SCR

        string ParseMeetingPolicyConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.MeetingPolicyConfiguration != null && data.MeetingPolicyConfiguration.Properties != null)
            {
                msg += "\r\nMeetingPolicyConfiguration:\r\n";
                foreach (string key in data.MeetingPolicyConfiguration.Properties.Keys)
                {
                    msg += "\tProperty[ " + key + " ] = " + data.MeetingPolicyConfiguration.Properties[key] + "\r\n";
                }
            }

            return msg;
        }

```

The following example output is generated when the previous code statements are invoked.

    MeetingPolicyConfiguration:
    Property[ enablep2pvideo ] = true
    Property[ enablep2pfiletransfer ] = true
    Property[ allowappsharingforexternalmeeting ] = Desktop
    Property[ allowexternalusercontrol ] = true
    Property[ audiobitrate ] = 200
    Property[ allowpolls ] = true
    Property[ meetingsize ] = 400
    Property[ allowusertoschedulemeetingswithappsharing ] = true
    Property[ allowedappdesktopsharinglevel ] = Desktop
    Property[ allowrecording ] = true
    Property[ enablep2precording ] = true
    Property[ retainpptforexternalmeeting ] = true
    Property[ allowannotations ] = true
    Property[ filetransferbitrate ] = 2000
    Property[ allowipaudio ] = true
    Property[ allowipvideo ] = true
    Property[ videobitrate ] = 2000
    Property[ allowfiletransfer ] = true
    Property[ maxconferencevideoresolution ] = VGA
    Property[ allowparticipantcontrol ] = true
    Property[ allowexternaluserrecording ] = false
    Property[ enablepstnconferencing ] = true
    Property[ allowanonymousparticipants ] = true
    Property[ enableappdesktopsharing ] = true
    Property[ appsharingbitrate ] = 50000
    Property[ allowexternaluserstosavecontent ] = true
    Property[ enabledatacollaboration ] = true
    Property[ trustedconferencingpinrequired ] = false
    Property[ allowpresentertorecord ] = true

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

