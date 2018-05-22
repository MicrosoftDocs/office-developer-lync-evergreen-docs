---
title: Application sharing for UI suppression mode
TOCTitle: Application sharing for UI suppression mode
ms:assetid: e5c1f218-9eae-4fa8-bd4f-cba82a7f2197
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn133124(v=office.15)
ms:contentKeyID: 53352580
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Application sharing for UI suppression mode

Learn about using the Microsoft Lync 2013 SDK to give your application a conversation application sharing stage feature while in Microsoft Lync 2013 UI suppression mode.

**Last modified:** July 18, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
How does application sharing work in UI suppression?<br />
Additional resources</p></td>
<td><p><img src="images/JJ933201.mod_icon_links_videos(Office.15).png" title="Related videos" alt="Related videos" /><br />
Link to video 1</p>
<p></p></td>
</tr>
</tbody>
</table>

## How does application sharing work in UI suppression?

The Lync SDK provides a visual application sharing stage object that you programmatically embed in your UI. Remotely shared resources such as the Notepad program or a user’s desktop can be viewed by a conversation participant when you add the sharing stage object to your Windows form or WPF window. Put a container control such as a panel in your window at design-time and then when a conversation is started and a user has accepted a resource sharing session, get the sharing stage object and give it the handle of the container. Once the user has accepted application sharing and the stage object has the container handle, it is active and shows the shared application. While the stage object exposes events, your code can safely ignore them in all but advanced scenarios.

In addition to viewing a remotely shared application by using the viewer, you can also share your application processes with remote users while your client Lync 2013 endpoint is running in UI suppression mode or side-by-side endpoint. Use the sharing methods in the conversation application sharing modality to start, manage control, and stop sharing your application process.

The sharing stage object does not show the locally shared application, which means a user may lose track of which local resource is shared. Be sure your application logic gives a user a visual hint about which resource is shared. The Lync 2013 client adds a yellow border around the window frame of a locally shared resource. You can create a similar effect by using the Win32 API and some additional application logic. For information about creating the window border effect, see [How to: Show a bright border around a locally shared resource](how-to-show-a-bright-border-around-a-locally-shared-resource.md).

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Important note" alt="Important note" /><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The viewer only works in UI suppression mode. When a Lync 2013 client UI is not suppressed, the shared resource is viewed in the conversation window</p></td>
</tr>
</tbody>
</table>

### Application sharing view object features

All actions that you can take on the Lync 2013 client application sharing stage are also available through the application sharing modality. If you have already added application sharing logic to your application, then modifying your application for UI suppression is simply a matter of adding the view object described in this section. Application sharing control logic continues to work and requires no changes. For information about application sharing control, see [Sharing resources in a conversation](sharing-resources-in-a-conversation.md).

### Docking the application sharing view object in your application

The sharing stage object is not a control that you can drag onto a window design surface in Visual Studio. The sharing stage object is exposed as a property of the application sharing modality. The **ApplicationSharingView** object shows a view of a resource shared out by a remote user. You cannot view a locally shared resource with this object. Although you can access the ApplicationSharingView object while sharing local resource, setting a property on the object or calling a method on the object raises an exception.

The resource sharing view object is of type [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingView](https://msdn.microsoft.com/en-us/library/dn378597\(v=office.15\)). There is no public constructor for the class. To get an instance of the object, read the [ApplicationSharingModality.View](https://msdn.microsoft.com/en-us/library/dn378588\(v=office.15\)) property of the conversation application sharing modality. You’ll need the handle of the parent container control before you dock the view in your application. Once you have the container control handle, call the [ApplicationSharingView.SetParent](https://msdn.microsoft.com/en-us/library/dn378610\(v=office.15\)) method. You can dock a view in your container at any time after the application sharing modality is available in a conversation, but it is best to dock the view when the application sharing modality state changes to **Connected**. Once the view is docked and the application sharing modality is connected, the docked view shows the shared application resource. In the basic scenario, the steps described here are all you need to do.

### Viewing modes

The viewer lets you set a display mode to fit it into your application form factor. For example, you can allow the viewer dimensions to change as the dimensions of shared resources change. If your application form factor must not let the viewer dimensions change, you can still let a user see the full surface area of the shared resource.

There are two viewing modes which are set by changing a property on the viewer. Depending on the mode you pick, you may need to handle a viewer property change event. The two viewing modes are:

  - [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingViewDisplayMode](https://msdn.microsoft.com/en-us/library/dn378658\(v=office.15\))**.FitToParent**. This mode sets the dimensions of the viewer to fit within the parent container. If the dimensions of the shared resource change, then the font size and resolution of the viewer are adjusted to keep the entire resource in the view. The viewer itself is not resized.

  - [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingViewDisplayMode](https://msdn.microsoft.com/en-us/library/dn378658\(v=office.15\))**.ActualSize**. This mode leaves the font size and resolution of the viewer to match those of the shared resource when the resource is resized. To keep the entire resource in view, the viewer itself is resized. Use the events described in the following section to resize your container control if you do not want horizontal and vertical scroll bars to appear on the container.

### View events

Although the viewer ([Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingView](https://msdn.microsoft.com/en-us/library/dn378597\(v=office.15\))) exposes a state change event, you will rarely find it useful. However, if you have set the display mode of the viewer to **.ActualSize** and you want to resize your container control along with viewer size changes, then you need to handle the [ApplicationSharingView.PropertyChanged](https://msdn.microsoft.com/en-us/library/dn378654\(v=office.15\)) event. The [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingViewProperty](https://msdn.microsoft.com/en-us/library/dn378657\(v=office.15\))**.Height** and **.Width** properties describe the new dimensions of the viewer. You can resize your container control to show the entire viewer and avoid showing scroll bars on the container. If the form factor of your application does not allow you to change the dimensions of the container, the container scroll bars let a user scroll the interesting part of the shared resource into view.

## Additional resources

  - [What you can do with desktop, application, and display sharing](what-you-can-do-with-desktop-application-and-display-sharing.md)

  - [How to: Add an application sharing view to your application](how-to-add-an-application-sharing-view-to-your-application.md)

