---
title: 'How to: Create a side-by-side endpoint in Lync SDK'
TOCTitle: 'How to: Create a side-by-side endpoint'
ms:assetid: 74f22eed-9dfb-47e5-9c34-997a08b94c2d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn133125(v=office.15)
ms:contentKeyID: 53352581
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Create a side-by-side endpoint in Lync SDK

Learn how to create a side-by-side Microsoft Lync 2013

**Last modified:** June 04, 2013

***Applies to:** Lync 2013 | Lync Server 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Creating a side-by-side endpoint<br />
Example: StartUpLync<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for creating a side-by-side endpoint are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Lync 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

### Core concepts to know

The following topic explains how side-by-side endpoints work in Lync 2013.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Topic</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-endpoint-types.md">Lync endpoint types</a></p></td>
<td><p>Learn about writing a Microsoft Lync 2013 SDK enabled application that uses a side-by-side LyncClient object to sign in to Microsoft Lync 2013.</p></td>
</tr>
</tbody>
</table>

## Creating a side-by-side endpoint

Creating a side-by-side endpoint is a one step process that involves calling the static [LyncClient.GetClient](https://msdn.microsoft.com/en-us/library/dn378084\(v=office.15\)) method, except that you pass a boolean **true** value in the method if you want a side-by-side endpoint. If you do not provide an argument to this method, the default argument value of **false** is passed and a standard Lync endpoint is created.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The <a href="https://msdn.microsoft.com/en-us/library/jj274980(v=office.15)">Microsoft.Lync.Model.LyncClient</a> object that is returned as a side-by-side endpoint has the same features and is programmed in the same way as a standard UI suppressed client endpoint. Be sure to initialize the endpoint and sign the user in just as you would do so with a standard UI suppressed endpoint.</p></td>
</tr>
</tbody>
</table>

### To create a side-by-side endpoint

  - Call the static [LyncClient.GetClient](https://msdn.microsoft.com/en-us/library/dn378084\(v=office.15\)) method. An object of the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/en-us/library/jj274980\(v=office.15\)) is returned.
    
    ``` csharp
    //If sideBySide == false, a standard endpoint is created
     //Otherwise, a side-by-side endpoint is created
     LyncClient _LyncClient = LyncClient.GetClient(sideBySide);
    ```

## Example: StartUpLync

The following example creates a standard endpoint or a side-by-side endpoint and then if Lync 2013 is in UI suppression mode, initializes the obtained endpoint.

``` csharp
        /// <summary>
        /// Gets the Lync client, initializes if in UI suppression, and 
        /// starts the user sign in process
        /// </summary>
        /// <param name="sideBySide">boolean. Specifies endpoint mode</param> 
        private void StartUpLync(Boolean sideBySide)
        {
            //Calling GetClient a second time in a running process will
            //return the previously cached client. For example, calling GetClient(boolean sideBySideFlag)
            // the first time in a process returns a new endpoint.  Calling the method a second
            //time returns the original endpoint. If you call GetClient(false) to get a client 
            //endpoint and then GetClient(true), the original client enpoint is returned even though
            // a true value argument is passed with the second call.
            if (_LyncClient == null)
            {
                //If sideBySide == false, a standard endpoint is created
                //Otherwise, a side-by-side endpoint is created
                _LyncClient = LyncClient.GetClient(sideBySide);
            }

            try
            {
                if (_LyncClient.InSuppressedMode)
                {
                    ClientDisplayMode_Label.Text = "UI suppression enabled";
                }
                else
                {
                    ClientDisplayMode_Label.Text = "UI suppression disabled";
                }

                //Display the current state of the Lync client.
                ClientStateString_Label.Text = _LyncClient.State.ToString();

                //Register for the three Lync client events needed so that application is notified when:
                // * Lync client signs in or out
                // * A new conversation is added (remotely via invite or locally by user)
                // * A conversation is removed (conversation ends)
                _LyncClient.StateChanged += _LyncClient_StateChanged;
                _LyncClient.ConversationManager.ConversationAdded += ConversationManager_ConversationAdded;
                _LyncClient.ConversationManager.ConversationRemoved += ConversationManager_ConversationRemoved;
                _LyncClient.SignInDelayed += _LyncClient_SignInDelayed;
                _LyncClient.CredentialRequested += _LyncClient_CredentialRequested;

                //Client state of uninitialized means that Lync is configured for UI suppression mode and
                //must be initialized before a user can sign in to Lync
                if (_LyncClient.State == ClientState.Uninitialized)
                {
                    _LyncClient.BeginInitialize(
                        (ar) =>
                        {
                            _LyncClient.EndInitialize(ar);
                            _thisProcessInitializedLync = true;
                        },
                        null);
                }

                //If the Lync client is signed out, sign into the Lync client
                else if (_LyncClient.State == ClientState.SignedOut)
                {
                    SignUserIn();
                }



            }
            catch (NotInitializedException)
            {
                MessageBox.Show("Client is not initialized.  Closing form", "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
            catch (ClientNotFoundException)
            {
                MessageBox.Show("Client is not running.  Closing form", "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
            catch (Exception exc)
            {
                MessageBox.Show("General exception: " + exc.Message, "Lync Client Error", MessageBoxButtons.OK, MessageBoxIcon.Hand);
                this.Close();
            }
        }
```

## Next steps

After you have created either a standard or side-by-side Lync endpoint, you are ready to take the next step.

  - [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md)

## Additional resources

  - [What you can do in Lync SDK](what-you-can-do-in-lync-sdk.md)

  - [How to: Change sign-in connection settings in Lync SDK](how-to-change-sign-in-connection-settings-in-lync-sdk.md)

  - [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md)

