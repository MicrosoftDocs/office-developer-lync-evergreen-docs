---
title: UI suppression
TOCTitle: UI suppression
ms:assetid: ece4a03a-c397-485a-ad53-61ab649f3c6d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933224(v=office.15)
ms:contentKeyID: 50877368
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# UI suppression

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about the UI suppression operating mode in the Microsoft Lync 2013 client and the most common scenario that uses the Lync 2013 client in UI suppression mode.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
UI suppression overview<br />
Lync-enabled kiosk application<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## UI suppression overview

An important feature of Lync 2013 is its ability to start up and run on a computer without showing a UI. When run in this mode, the Lync 2013 process still handles all of the contact and communication management that your application relies on, but leaves the UI responsibilities to your application. This is useful when you're required to embed communication features in your application without exposing the Microsoft brand associated with the Lync client. An additional requirement might be that your application must restrict a signed-in user to a subset of the features available on the Lync client. For example, you might want to restrict your user to communicating with a small set of other users in a predefined contact list that the user cannot add to. You might also want to restrict the conversation modalities that can be used in a conversation. For example, you might decide that a user should only make audio calls to a PSTN telephone number or a group of internal contacts.

Frequently, a company creates public-facing applications that apply both of these restrictions and then host the application in a kiosk in a building lobby or retail store. The kiosk presents the user with a rich communication experience that is strongly branded with the company’s own brand. The contact and conversation restrictions built into the kiosk application provide the company with the security required in a public installation of the kiosk. The Lync 2013 API provides the power and features that you need to enable a public kiosk. Because the API is managed code and designed along .NET framework design guidelines, you can leverage your familiarity with .NET programming to easily implement communication features into your application.

The Microsoft Lync 2013 UI gives users many useful features that enable them to have conversations in any of several modes with any Lync user in the contact list or contact search results list. In addition, the Lync UI lets a user sign in and out of Lync, access the meeting recording manager, and set many options such as connection settings, response groups, and call forwarding options. Although these UI features are appropriate in private organizational setting where an employee should have complete access to the features, the UI features might not be appropriate when the Lync client is running on a public computer such as a kiosk in a corporate headquarters lobby or department store foyer. For these public Lync installations, you should be able to lock many of these UI features.

Although the Lync 2013 client cannot be configured to disable items feature by feature, you can hide the UI completely. The underlying Lync process continues to run and support any applications that implement the Microsoft Lync 2013 API. This API support in UI suppression mode lets you create your own UI to replace the suppressed Lync UI. Because you can design your UI to present almost any Lync functionality, your UI can be almost as full-featured as Lync itself or limited to those features that are appropriate to the public scenario for which you're designing.

### Determine the UI suppression mode

There are three methods to determine the current UI suppression mode:

  - Check the [LyncClient.InSuppressedMode](https://msdn.microsoft.com/library/jj275500\(v=office.15\)) property.
    
    ```csharp
    if (LyncClient.GetClient().InSuppressedMode == true)
    {
        MessageBox.Show("Lync is configured for full UI suppression");
        return;
    }
    ```

  - Discover the value by trying to obtain an instance of the [Automation](https://msdn.microsoft.com/library/jj293816\(v=office.15\)) class and catching the resulting exception that is raised if UI suppression is enabled.

  - Read the **\[HKEY\_CURRENT\_USER\]\\Software\\Microsoft\\Office\\15.0\\Lync\\UISuppressionMode** key in the local registry. If the value is dword:00000001, UI suppression is enabled.

### Set the UI suppression mode at Lync client installation time

You can set the Lync 2013 suppression mode when you install the Lync client. At the command prompt, start the Lync installation .exe with a command-line argument in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Argument</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>/Install</p></td>
<td><p>Installs all files.</p></td>
</tr>
<tr class="even">
<td><p>/Uninstall</p></td>
<td><p>Removes all files.</p></td>
</tr>
<tr class="odd">
<td><p>/Silent</p></td>
<td><p>Installer UI does not appear.</p></td>
</tr>
<tr class="even">
<td><p>/FullUisuppression</p></td>
<td><p>Lync 2013 is installed so that Lync runs but the UI does not appear.</p></td>
</tr>
</tbody>
</table>

If you want to suppress the Lync UI after it's installed with the UI enabled, you must first uninstall Lync and then reinstall it with the /FullUisuppression command-line argument.

### Start Lync in UI suppression mode

Normally, a user starts Lync 2013 by clicking the Lync icon on the Windows **Start** menu and then providing credentials when challenged by the client. When the Lync UI is suppressed, the **Start** menu icon is still visible, but clicking it does not start Lync. The Lync process can only be started by your application programmatically. When started, the Lync.exe process is shown in the **Windows Task Manager** Processes list.

Your application is also responsible for collecting user credentials, passing the credentials to Microsoft Lync Server 2013 for validation and sign in, and handling cases in which the credentials are invalid. Although multiple instances of your application can run at the same time on one computer, all instances share the same Lync process endpoint. This means that when you sign a user in using an instance of your application, the user is signed in for all other instances. Signing a user out from one instance signs a user out for all instances.

Just as your application can start the Lync process, it can also stop the process. If there are other instances of a Lync 2013 API-enabled application that is running on the same computer, the Lync.exe process is stopped for them too. For this reason, your application must keep track of whether it started the Lync process. If your process did not start Lync.exe, it must not stop it.

### UI suppression limitations

The running UI suppressed Lync process gives your application access to the same Lync client endpoint, SIP processing, and all media processing that an unsuppressed Lync client uses with the following limitations. The visible components of the SDK are not available except for the video window. Components such as the Microsoft Lync 2013 Controls for Silverlight browser or WPF applications and the meeting content and resource sharing modalities cannot be used in your application when UI suppression is enabled. In addition, you cannot use the objects in the [Microsoft.Lync.Model.Extensibility](https://msdn.microsoft.com/library/jj278382\(v=office.15\)) namespace to automate starting conversations or meetings.

The [Microsoft.Lync.Model.Conversation.AudioVideo.VideoWindow](https://msdn.microsoft.com/library/jj268233\(v=office.15\)) is a special exception to the previously described rule. In this case, the **VideoWindow** is designed to replace the Lync video window that is lost when the Lync client UI is suppressed. If you implement the video window in your application, you can provide the full range of basic communication modes, from IM to audio/video and even Persistent Chat.

## Lync-enabled kiosk application

A Lync 2013 API-enabled kiosk application is an application that runs in the public area of an organization such as a company with a public lobby. It usually runs on a computer that has a simple touch-screen display, a webcam, and a keyboard. The purpose of this application is to let a building visitor find an employee in a company directory and then start an IM conversation or audio/video conversation with that employee. In most cases, the conversation is brief and intended to announce the presence of the visitor. In other uses, the public kiosk is useful in a large retail department store where a customer uses the kiosk as both a store directory and a contact point for conversations with store staff.

The most important feature of the kiosk application is that it restricts the contact list to a predefined users and enables conversations with restricted modes. Normally, the kiosk implements its own conversation window so that the visitor cannot invite more people to the conversation or add more conversation modes. The kiosk UI is completely custom, simplified, and designed to match the company brand.

You can build a custom unified communications application or enhance your line-of-business application to meet any requirements that include the following:

  - A completely custom unified communications UI.

  - Lync 2013 feature restrictions that range from no restrictions to the implementation of a single feature.

## See also

  - [Beyond the basics: Lync 2013 SDK](beyond-the-basics-lync-2013-sdk.md)

  - [How to: Sign in to and out of Lync](https://msdn.microsoft.com/library/jj937241\(v=office.15\))

