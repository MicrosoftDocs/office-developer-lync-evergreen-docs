---
title: Migrate an application to Lync 2013 SDK
TOCTitle: Migrate an application to Lync 2013 SDK
ms:assetid: f2c7ab6e-7e20-4043-9dba-c46f2e65490b
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933253(v=office.15)
ms:contentKeyID: 50877399
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Migrate an application to Lync 2013 SDK

![What's new topic](images/JJ937254.mod_icon_whatsnew_long(Office.15).png "What's new topic")

Learn how to migrate your existing Microsoft Lync 2010 SDK-enabled application to Microsoft Lync 2013 SDK. The migration tasks include changes to assemblies that are referenced in your project and the installation of the latest Microsoft Silverlight development support tools.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Side-by-side SDK installation<br />
Project changes<br />
Registry changes for conversation window extension applications<br />
Silverlight development tools<br />
Code behavior changes<br />
Additional resources</p></td>
</tr>
</tbody>
</table>

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
<td><p>No code changes are required to recompile your existing Lync SDK-enabled application that references the Lync SDK assembly. There are API behavior changes that you should be aware of. For information about these changes, see the Code behavior changes section.<br />
<br />
Add new Lync SDK features to your application by using the classes and types described in <a href="what-s-new-in-lync-2013-sdk.md">What's new in Lync 2013 SDK</a>.</p></td>
</tr>
</tbody>
</table>

## Side-by-side SDK installation

If you have installed Microsoft Lync 2010 SDK on your computer, you should uninstall it before you install Microsoft Lync 2013 SDK. The assemblies, samples, and documentation are installed in different folders but the Microsoft.Office.UC.dll for both versions of the SDK is installed in the Global Assembly Cache. A side-by-side installation of the SDK versions might not destabilize your applications but it's not supported by Microsoft.

Microsoft Lync 2013 SDK includes a new redistribution application (redist.msi) that installs a new version of Microsoft.Office.UC.dll that supports your Lync 2013 API-enabled application. Be sure to uninstall previous versions of the runtime on computers that host your application.

## Project changes

For Windows Forms or Windows Presentation Foundation (WPF) applications, you must replace the Microsoft.Lync.Model.dll assembly that was installed with Microsoft Lync 2010 SDK. Microsoft Lync 2013 SDK installs a new set of assemblies with the same names as the Lync SDK assemblies. The assemblies for Lync SDK have a default *%Program Files%*\\Microsoft Office\\Office15\\LyncSDK\\Assemblies\\Desktop installation path.

For Silverlight applications, replace your existing Lync assemblies with the set of assemblies that are found in the *%Program Files%*\\Microsoft Office\\Office15\\LyncSDK\\Assemblies\\Silverlight folder.

## Registry changes for conversation window extension applications

Silverlight browser applications for conversation window extension tabs and Persistent Chat Addin tabs require a dedicated local computer registry entry in a new registry key. The new key enables better security for the local Lync 2013 user. It gives explicit Lync 2013-access permission to Silverlight browser applications that are intended to extend Lync without giving the same permission to web sites and domains generally. For information about the new registry key, see [Lync 2013 system registry keys](lync-2013-system-registry-keys.md).

## Silverlight development tools

If you develop Silverlight browser applications that use Microsoft Lync 2010 Controls and you're migrating these applications to Microsoft Lync 2013 Controls, you must download and install the following tools:

  - Silverlight 4 Tools for Visual Studio 2010 is the minimal requirement for Silverlight development. However, the Silverlight 5 runtime is required to support Conversation Window Extension applications and Persistent Chat window add-in applications that are hosted on Lync x64.

  - You can optionally install [Silverlight 5 Tools for Visual Studio 2010 Service Pack 1](http://go.microsoft.com/fwlink/?linkid=229318).

  - [Developer Runtime for Windows (32 bit)](http://go.microsoft.com/fwlink/?linkid=229323).

  - [Developer Runtime for Windows (64 bit)](http://go.microsoft.com/fwlink/?linkid=229324).

## Code behavior changes

A code behavior change is a non-syntax API revision that changes the runtime behavior of a Lync 2013 API-based application. Lync 2013 API code behavior changes are as follows:

### Contact presence subscription changes

The Lync 2013 API requires that every [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) object that you want presence publication notification for is added to a [Microsoft.Lync.Model.ContactSubscription](https://msdn.microsoft.com/library/jj268195\(v=office.15\)) before registering for the [Contact.ContactInformationChanged](https://msdn.microsoft.com/library/jj275543\(v=office.15\)) event. The Lync 2013 client maintains a contact subscription for all contacts that are scrolled into view on the client UI contact list. As contacts are scrolled out of view on the UI contact list, they are removed from the client-maintained contact subscription. If you want to continue to get presence publication notifications for out-of-view contacts, you must create and maintain a **ContactSubscription** object in your application logic.

Contacts that have been obtained from a search operation through the API are not contained in the subscription maintained by the Lync client. To ensure that you get updated presence, maintain your own **ContactSubscription** for all contacts. For information about subscribing to contact presence, see [How to: Subscribe to enhanced presence content](how-to-subscribe-to-enhanced-presence-content.md).

### Collection class range exceptions

Collection classes that implement the **this\[System.Int32\]** property threw an **IndexOutOfRange** exception when an invalid index was specified. With the behavior change, an invalid index causes the **ArgumentOutofRangeException** exception to be raised. The [Microsoft.Lync.Model.ContactEndpointCollection](https://msdn.microsoft.com/library/jj293449\(v=office.15\)) class shows an example of this change.

Collection classes that implement the **this\[someKey\]** property threw an **IndexOutOfRange** exception when an invalid key was specified. With the behavior change, an invalid key causes the **KeyNotFoundException** exception to be raised. The [Microsoft.Lync.Model.ClientSettings](https://msdn.microsoft.com/library/jj293531\(v=office.15\)) class shows an example of this change.

### Duplicated content sharing conversations

If your application starts or accepts content sharing conversations in a non-UI suppression mode, your application should be able to identify and ignore duplicate content sharing conversation objects. The duplicated conversation object is exposed in the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event. Your event handler for this event should identify and ignore the duplicated conversation.

The duplicated conversation is created after the content sharing modality is connected when these conditions are met:

  - UI Suppression is disabled.

  - The signed-in user has selected **Enable tabbed conversations** on the local Microsoft Lync 2013 instance.

  - The signed-in user has selected **Reopen my conversations when I sign in to Lync**.

The Lync 2013 API does not provide a way to see whether a user has made these conversation configuration selections. Detect a duplicated conversation by testing for these conditions:

  - The [Conversation.SelfParticipant](https://msdn.microsoft.com/library/jj266427\(v=office.15\)) property returns null.

  - None of the conversation modalities are in the ModalityState.Notified state. Check for these conversation characteristics in the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event.

If both conditions are met, the conversation is duplicated and should be ignored.

The following example identifies a "shadow" conversation. This method should be called in the registered callback method for the [ConversationManager.ConversationAdded](https://msdn.microsoft.com/library/jj266470\(v=office.15\)) event.

```csharp
        /// <summary>
        /// Handles the event raised when a new conversation is added. 
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void ConversationManager_ConversationAdded(object sender, ConversationManagerEventArgs e)
        {

            if (IsShadowConversation(e.Conversation))
            {
                return;
            }
            //Your logic here...
        }

        /// <summary>
        /// Returns true if the new conversation is a "shadow" conversation that is
        /// created because the ContentSharingModality is now connected in an existing conversation
        /// where local user has enabled tabbed conversations, conversation state saving is enabled, and 
        /// UI Suppression is not enabled.
        /// </summary>
        /// <param name="newConversation"></param>
        /// <returns></returns>
        private Boolean IsShadowConversation(Conversation newConversation)
        {
            if (newConversation.SelfParticipant != null)
            {
                return false;
            }

            foreach (Modality m in newConversation.Modalities.Values)
            {
                if (m.State == ModalityState.Notified)
                {
                    return false;
                }
            }
            return true;
        }
```

## See also

  - [What's new in Lync 2013 SDK](what-s-new-in-lync-2013-sdk.md)

