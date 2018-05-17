---
title: Custom presence states
TOCTitle: Custom presence states
ms:assetid: 8d654ff7-eac2-4271-b8fc-aeeba0597bdc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933126(v=office.15)
ms:contentKeyID: 50877273
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Custom presence states

![Beyond the basics topic](images/JJ945548.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the concept of localizing a Lync 2013 API-enabled application by showing custom user activity strings instead of the default activity strings that included with an installation of Lync Server 2013.


_**Applies to:** Lync 2013 | Lync Server 2013_

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Lync custom activity strings<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Lync custom activity strings

There are four components that make up the availability of Lync 2013 to communicate with other users. Two of the components are tokenized and are used in an application to determine which visual UI clue (such as a colored "gumdrop" icon) to be displayed for a given state of availability. The other two components are strings that describe the nature of the user’s activity.


> [!TIP]
> <P>Availability can be thought of as an expression of how much a user is available for conversation. For example, a user is fully available when their availability token is Free. Activity describes what they are currently doing that effects their availability. For example, a user’s availability might be busy and the user’s activity can be "in a meeting." A user’s availability can be free and the activity can be "Available."</P>



The availability tokens are enumerated by the Lync 2013 API and cannot be changed. However, the user’s activity string can be customized for both local language and custom activity. For example, an organization might want to let employees indicate that they are Free but working from home. In that case, a Lync Server 2013 administrator would create a custom activity string "Working from home" and associate it with the availability of Free. If this organization has employees in multiple language cultures, the custom string can be localized to the language displayed by Windows running on a user’s computer.

Figure 1 shows a sample Windows Form that is populated with a [Microsoft.Lync.Controls.PresenceIndicator](presenceindicator-class-microsoft-lync-controls_1.md) that shows the current availability of the user. The four strings on the upper-right of the Form show the availability components where Availability is a token, Activity is a string, Activity Id is a token, and Custom activity is a string. The custom activity string is composed of an LCID for the custom activity string language and the custom activity string itself. In this sample, the Lync Server 2013 administrator has not configured custom activity strings or localized custom activity strings. The default en-us activity string for the availability of **TemporarilyAway** is shown.

Figure 1. Sample application that shows the four components of a user’s availability

  
![Screen shot of sample that shows custom activity](images/JJ937312.LyncClientSDK_CustomActivityStrings(Office.15).jpg "Screen shot of sample that shows custom activity")

The custom activity strings is a **List\<object\>** type. The objects are cast to the [Microsoft.Lync.Model.LocaleString](localestring-class-microsoft-lync-model_2.md) type that exposes a LCID token and corresponding localized string. You get the current language and culture code by reading the System.Globalization.CultureInfo.CurrentCulture.LCID property and comparing the returned value to the LCID token from the **LocaleString** instance. Display the corresponding activity string when a matching LCID is found.

### Publishing custom activity

If an administrator has provisioned Lync Server 2013 with a set of custom activities, a client application can publish a user’s availability with an activity from the set of custom activities. An activity has the following four attributes:

  - ID. This uniquely identifies a custom activity.

  - Availability. This corresponds to an enumerator from the [Microsoft.Lync.Model.ContactAvailability](contactavailability-enumeration-microsoft-lync-model_2.md) enumeration.

  - LCID. The locale ID of the displayed activity string.

  - Activity. The activity string.

The provisioned custom activities are found by calling the [Self.GetPublishableCustomAvailabilityStates](self-getpublishablecustomavailabilitystates-method-microsoft-lync-model_2.md) method. A list of [Microsoft.Lync.Model.CustomAvailabilityState](customavailabilitystate-class-microsoft-lync-model_2.md) is returned for the LCID specified in the method argument. Before publishing a custom activity, you must find a custom activity with the desired availability, LCID, and activity string. When found, you publish user availability with the specified custom activity ID.

## Additional resources

  - [How to: Display and publish custom availability in Lync SDK](how-to-display-and-publish-custom-availability-in-lync-sdk.md)

  - [Core concepts: Enhanced presence](core-concepts-enhanced-presence.md)

  - [What you can do with enhanced presence](what-you-can-do-with-enhanced-presence.md)

  - [Configuring Custom Presence States](http://technet.microsoft.com/en-us/library/gg398997.aspx)

