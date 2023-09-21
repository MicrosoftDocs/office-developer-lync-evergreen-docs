---
title: Lync Server sign-in configuration
TOCTitle: Lync Server sign-in configuration
ms:assetid: baaf34f3-056e-4bff-b6fe-bdd325b083b4
ms:mtpsurl: https://msdn.microsoft.com/library/JJ933176(v=office.15)
ms:contentKeyID: 50877315
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Lync Server sign-in configuration

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn how to configure Lync Server 2013 sign-in settings using the Lync 2013 API to create a custom sign-in settings dialog box in your application and clear the sign-in credential cache.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Server sign-in settings<br />
Clearing the sign-in credential cache<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Server sign-in settings

Server sign-in settings let you set different URL strings for Lync Server 2013 registration servers before a user attempts to sign in to Lync 2013. This gives you the flexibility to programmatically sign a user in to different server topologies depending on current requirements. In addition to letting you set server URL strings and auto-discovery mode, you can read other configuration settings such as password saving mode, intranet sign-in status, sign-in auto-retry status, and the user name string of the currently signed-in user. The **SigninConfiguration** class exposes properties that provide the values for these settings.

Figure 1 shows an example Windows Form that lets a user set and read the properties of the **SigninConfiguration** class before the user signs in to a Lync topology. The Windows Form provides radio button choices for both password saving and transport protocol.

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
<td><p>The <strong>SigninConfiguration</strong> class exposes transport protocol and password saving mode settings as read-write properties but the Lync client does not let you set these two settings programmatically.</p></td>
</tr>
</tbody>
</table>

Figure 1. Sample sign-in configuration settings UI

  
![Sign in configuration dialog sample UI](images/JJ933176.LyncClientSDK_ConnectionSettings_ConversationEvents(Office.15).jpg "Sign in configuration dialog sample UI")

The **Mode** choices in figure 1 let you turn server auto-discovery on or off. When auto-discovery is turned on, any URL strings that you enter for an internal server URL or external server URL are ignored when signing a user in. Instead, Lync parses the user name string for the domain of a registration server. When the domain is identified, the registration server URL is auto-discovered and the user is signed in to that registration server.

If the computer that your application is running on is outside an organization’s Lync Server 2013 topology, a user is signed in to Lync through an Edge server. The external URL string is the URL of the Edge server.

### Getting the current sign-in settings

The Lync 2013 API does not expose an event to be raised when sign-in configuration settings are changed. To show current settings in your application, you must either poll for changes by reading properties on **SigninConfiguration** or read the properties on a UI event such as the clicking of a button or opening the UI form itself.

## Clearing the sign-in credential cache

Lync 2013 caches the SIP address, user name, and password of every user who successfully signs in to Lync 2013 on a local computer. This allows the program to sign the previous user in to Lync again without requiring the user to enter their credentials. Lync 2013 stores credentials for multiple users. Individual users can select to make Lync 2013 clear the credential cache of their credentials by clicking the **Delete my sign-in info** link on the main Lync 2013 window before they sign in.

The Lync 2013 API exposes a method on the [Microsoft.Lync.Model.SignInConfiguration](https://msdn.microsoft.com/library/jj266969\(v=office.15\)) class that removes the cached credentials of the user specified by the SIP address parameter. When the credentials are removed, the user must supply credentials to sign in again.

The following example checks to see whether the client is signed out, removes the ″sip:″ substring from a SIP address obtained from a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/library/jj266463\(v=office.15\)) object, and then calls the [SignInConfiguration.ForgetMe](https://msdn.microsoft.com/library/dn378085\(v=office.15\)) method.

```csharp
        /// <summary>
        /// Clears the credential cache of the credentials of a user
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void ForgetMeButton_Click_1(object sender, RoutedEventArgs e)
        {
            //The Lync client must be signed out when the ForgetMe method is called
            if (lyncClient.State != ClientState.SignedOut)
            {
                return;
            }
            try
            {
                //Strips "sip:" out of the string obtained from the Contact.Uri property
                userSIPUri = userSIPUri.Replace("sip:", " ");
                userSIPUri = userSIPUri.Trim();
                lyncClient.SignInConfiguration.ForgetMe(userSIPUri);
            }
            catch (LyncClientException lce)
            {
                MessageBox.Show("Lync client exception on ForgetMe call " + lce.Message);
            }
        }
```

## See also

  - [Beyond the basics in Lync 2013 SDK](beyond-the-basics-in-lync-2013-sdk.md)

  - [How to: Change sign-in connection settings in Lync SDK](how-to-change-sign-in-connection-settings-in-lync-sdk.md)

