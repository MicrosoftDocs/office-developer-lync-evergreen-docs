---
title: Application sharing modality
TOCTitle: Application sharing modality
ms:assetid: e0442198-d86e-4dd0-aa5b-f9b004716925
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ933213(v=office.15)
ms:contentKeyID: 50877357
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Application sharing modality

![Core concepts](images/JJ933133.mod_icon_CoreConcepts_long(Office.15).png "Core concepts")

Learn about the **ApplicationSharingModality** class and how it enables you to share resources in an application.

**Last modified:** April 16, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Application sharing modality<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Application sharing modality

The [ApplicationSharingModality](https://msdn.microsoft.com/en-us/library/jj275536\(v=office.15\)) object is a component of a conversation that encapsulates the Remote Desktop Protocol (RDP) and represents a sharing relationship between the local user and one other conversation participant. There is an **ApplicationSharingModality** object for each pair of participants in a sharing conversation. For example, if there are three participants in a sharing conversation, the client application at each endpoint hosts three instances of the **ApplicationSharingModality** object for the active conversation.

The **ApplicationSharingModality** object is the channel that carries shared resource screen data and mouse/keyboard control commands for the resource currently shared on the conversation sharing stage. Only a single shared resource can be shown on the sharing stage at a time and the conversation has one sharing stage for all participants. For this reason, all instances of the **ApplicationSharingModality** object across all endpoints in a conversation show the same shared resource.

Figure 1 shows the Focus component of Microsoft Lync Server 2013 and three instances of a custom Lync 2013 API application that are hosting an application sharing conversation with three people. Each application endpoint has instances of **ApplicationSharingModality** for each participant pair and an instance of **ApplicationSharingModality** for the endpoint to conference Focus pair.

Figure 1. ApplicationSharingModality objects in a sharing conversation

  
![Shows the ApplicationSharingModality objects.](images/JJ933213.LyncClient(Office.15).jpg "Shows the ApplicationSharingModality objects.")

### Shareable resources

Use the conversation **ApplicationSharingModality** to obtain a list of the local computer’s resources that can be shared. The [Conversation.Modalities](https://msdn.microsoft.com/en-us/library/jj275560\(v=office.15\)) property returns the conversation **ApplicationSharingModality** object along with all other conversation modalities. You can get local shareable resources when the conversation object is created and before the **ApplicationSharingModality** is connected to the Focus and the conversation is active. This allows you to verify that a desired resource is available before inviting people to the conversation.

As local resources become available or are no longer available, the conversation **ApplicationSharingModality** raises an event that carries information about the newly available shareable resource. Use [ApplicationSharingModality.LocalSharedResourcesChanged](https://msdn.microsoft.com/en-us/library/jj276856\(v=office.15\)) to get the updated shareable resource collection.

### Requesting control of a shared resource

The resource control-related **ApplicationSharingModality** events convey control requests between a shared resource owner and participant who has requested or given control of the resource. For example, if Bob is sharing his own desktop and Sally requests control of the desktop, the control request and response are carried on the **ApplicationSharingModality** object that represents their relationship. The control requests and responses are not seen by the other conversation participants. When offering control of a resource, the **ApplicationSharingModality** representing the local user and a user who is to be offered resource control is used. For example, if Bob has revoked the control of his desktop from Sally and now wants to offer it to Tom, Bob chooses Tom on the conversation roster of his conversation window UI and then the application gets Tom’s **ApplicationSharingModality** object and makes the control offer with that object. Use the [Participant.Modalities](https://msdn.microsoft.com/en-us/library/jj267336\(v=office.15\)) property to get the **ApplicationSharingModality** for a conversation participant.

## See also

  - [Core concepts: Desktop, application, and display sharing in Lync SDK](core-concepts-desktop-application-and-display-sharing-in-lync-sdk.md)

