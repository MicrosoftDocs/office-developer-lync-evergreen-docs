---
title: 'How to: Sign a user in to Lync'
TOCTitle: 'How to: Sign a user in to Lync'
ms:assetid: 3eda49e1-6826-4bd9-a11d-dd1b62ae7957
ms:mtpsurl: https://msdn.microsoft.com/library/Dn391637(v=office.15)
ms:contentKeyID: 56293547
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
description: Learn how to sign a user into Lync with Microsoft's detailed guide. Understand the process, handle exceptions, and manage unexpected client state changes.
---

# How to: Sign a user in to Lync

Understand the essential elements of the Lync sign in process in a Microsoft Lync 2013 SDK-enabled application. Learn about the conditions that prevent your app from signing a user in to Lync and how your code can gracefully recover from these conditions.



**Applies to**: Lync 2013 | Lync Server 2013

Your Lync 2013 API-enabled application can get contact presence and conversations as long as the user is signed in to Lync. A user can sign in to Lync by using your application if you have coded a Lync 2013 API sign in feature. Alternatively, a user can sign in using the Lync client itself as long as the client UI is not suppressed. The Lync 2013 API-based sign in process described in this article applies to the Lync UI suppression scenario and the standard Lync scenario.

If the user is signed in, her contact list is visible, she can publish her presence and see the presence of other people, and she can start or join conversations. If you application is not able to do these things, then the user is probably not signed in to Lync. This article helps you get a user signed in by showing you the best way to sign a user in, how to deal with any Lync exceptions, and react to unexpected client state changes.



<div class="caption">
Watch the video: Sign In to Lync with UI Suppressed
</div>
<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/5d247b33-af17-45f6-ad7e-9be9f9f7e5cd]

<div class="caption">
Watch the video: Sign In to Lync
</div>
<br />

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8a417ed0-bcab-4da7-b033-d1e2cdb784df]


## Prerequisites

The prerequisites for signing in to Lync 2013 are as follows:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## One Lync endpoint, multiple processes

The Lync client consists of one SIP endpoint encapsulated by either a background process or an application process with a UI. A user can simultaneously run multiple instances of your application and other Lync 2013 API-enabled applications while Lync client is running. All of these processes share the Lync SIP endpoint and the resources in the Lync process. This means that any state-changing action in one process affects the other processes that share the Lync endpoint. For example, if the user signs out of Lync by using one instance of your application process, the user is signed out for all processes. A robust Lync 2013 API application protects itself against the possibility that another process unexpectedly changes the state of Lync. By watching for state changes and then restoring the client state if possible, you can be sure your application continues to show contacts and conversations.

## What is UI suppression?

UI suppression is an operational mode of the Lync client. When UI suppression is enabled, the Lync client runs as a background process and no client UI is displayed. Your own application UI substitutes for the Lync UI. The connection between your application and the Lync background process is the Lync 2013 API that gives you direct access to the running background process.

As you can imagine, when UI suppression is *disabled*, the Lync client UI shows on the desktop and its’ process is an application process. You still use the Lync 2013 API to access the running process, but some operations such as user sign in are different than in UI suppression mode.

## Lync client state transitions, should I care?

If you want to transition the shared Lync endpoint from **Uninitialized** to **SignedIn**, you need to handle state change events on the Lync process. In your event handling logic, call the Lync 2013 API method that takes the endpoint to the next state, as shown in figure 1. If your application can’t sign a user in to Lync, isn’t reacting to conversation invitations, or misses a presence update from a contact, then the application probably missed a state change to **SignedOut**. Your application gets each new state by handling the [Client.StateChanged](https://msdn.microsoft.com/library/jj276368\(v=office.15\)) event. The following table lists all states that the Lync client transitions through from initial state to signed in.

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
<td><p>Don’t forget to register an event handler for the <a href="https://msdn.microsoft.com/library/jj266470(v=office.15)">ConversationManager.ConversationAdded</a> event. Unless you do that, your application won’t get conversation invitations even though the user is signed in.</p>
<p>You also need to register a handler for a contact presence event so the contact list refreshes with current contact availability. This process isn’t complicated, but you should check out the How to topic on subscription: <a href="how-to-subscribe-to-enhanced-presence-content.md">How to: Subscribe to enhanced presence content</a>.</p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>State</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.Uninitialized</strong></p></td>
<td><p>This state only applies when Lync is in UI suppression mode.</p>
<p>The Lync background process is started but the client is not yet initialized. Call the <strong>BeginInitialize</strong> method to move the client to the next state.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.Initializing</strong></p></td>
<td><p>The Lync background process is started and the client is initializing. Wait for the next client state.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.SignedOut</strong></p></td>
<td><p>The client is initialized. Call the <strong>BeginSignIn</strong> method to move the client to the next state.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.SigningIn</strong></p></td>
<td><p>The client is signing in. If a user doesn’t want to continue waiting, call the <strong>BeginSignOut</strong> method. If there are no network connectivity issues, the client quits trying to sign in.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.SignedIn</strong></p></td>
<td><p>The sign in process is finished and the client has cached the user’s contact list and is ready for new conversations.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.SigningOut</strong></p></td>
<td><p>The user is trying to sign out. An instance of your application may have called the <strong>BeginSignOut</strong> method or the user has signed out by using the Lync client.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.SignedOut</strong></p></td>
<td><p>The sign out process is finished. If the client is in UI suppression mode, it is ready to be shut down</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/jj275269(v=office.15)">Microsoft.Lync.Model.ClientState</a><strong>.ShuttingDown</strong></p></td>
<td><p>This state only applies when Lync is in UI suppression mode.</p>
<p>One of the running processes has called the <strong>BeginShutDown</strong> method, and the client is still shutting down. When the shut-down process is finished, the hosting Lync background process stops.</p></td>
</tr>
</tbody>
</table>

Figure 1 shows the state transitions and sign in-related operations that move the client from state to state.

Figure 1. Important client sign in process state transitions.

  
![State change: Uninitialized-SignedOut-SignedIn](images/Dn391637.OCOM_ClientStateTransitions(Office.15).jpg "State change: Uninitialized-SignedOut-SignedIn")

After you’ve called the [LyncClient.GetClient](https://msdn.microsoft.com/library/jj278213\(v=office.15\)) method, check the current state of the client before calling any of the methods in figure 1. The client can be in any of the states shown in the figure.

## Look for the causes of sign in failure

The Lync sign in process is pretty reliable and only fails when the user has provided an incorrect sign-in URI, user name, or password. The less likely, but still possible cause is a network outage that occurs when a computer network interface card is disabled, a mouse chews through an Ethernet cable under the desk, a hub needs to be reset, or a router fails. Incorrect credentials can be re typed and re submitted but network issues cannot be solved by using the Lync 2013 API. Instead, your application can inform the user that sign in is delayed and then let the user decide if she wants to continue to try to sign in.

### Incorrect user credentials are submitted

The Lync client shows two distinct reactions to incorrect user credentials at sign-in time. It is simple to predict which behavior Lync will show and let you code for either behavior. If the client is in [UI suppression](ui-suppression.md) mode and the user tries to sign in with incorrect credentials, sign-in is interrupted and the [LyncClient.CredentialRequested](https://msdn.microsoft.com/library/jj267649\(v=office.15\)) event is raised. Use this event to ask the user to re-type their credentials and then submit the updated credentials to complete the sign in. You can see an example of this credential submission process below.

If the client UI is not suppressed, no event is raised for incorrect credentials. Instead, the client remains in the **SigningIn** state until the user completes signing in by using the Lync client. If you passed a callback method in the **BeginSignIn** call, it isn’t invoked until the user is signed in. Once the sign in is completed, your application is notified that the state is now **SignedIn**.

### Unexpected user is signed in

In this failure case, after sign in, the contact list fills with people who do not belong to the current user and new conversations are started with the wrong local user name. How can this happen? If your application calls the [LyncClient.BeginSignIn](https://msdn.microsoft.com/library/jj274512\(v=office.15\)) and passes empty strings in the first three arguments, then Lync uses previously cached credentials to sign the current user in. You can clear the credential cache by calling the [SignInConfiguration.ForgetMe](https://msdn.microsoft.com/library/dn378085\(v=office.15\)) method and pass the sign in URI of the user whose credentials were used by the client.

To be sure that the right user is always signed in, verify that the three string arguments are not empty before calling **BeginSignIn**. If you pass correctly formed strings in the first three arguments of the method, Lync uses them to sign the user in. If the arguments are not empty, but are incorrectly formed, an **ArgumentException** is thrown by **BeginSignIn**

### Sign in and auto-recovery delay

These delays are the result of network bandwidth or server utilization issues. For this reason, you can’t correct the problem at the client. Instead, use the [LyncClient.SignInDelayed](https://msdn.microsoft.com/library/jj293478\(v=office.15\)) event to tell the user about the status of the sign in operation and how long it is taking. The only way that you can cancel the sign in operation is to call the **BeginSignOut** method. Call this method if the user doesn’t want to continue waiting.

### Lost network connectivity

If the user’s computer loses network connectivity before or during sign in, the [LyncClient.SignInDelayed](https://msdn.microsoft.com/library/jj293478\(v=office.15\)) event is raised every 30 seconds starting when network outage is detected. The status code that is returned in the event data (0x80EE00BD) tells you that the sign in operation has timed out. You can’t call the **BeginSignOut** method in this situation because that operation needs network access. Instead, shut down your application or ask the user if she wants to wait until connectivity is restored.

## Sign in logic to use in your application

Now that you know all of the state transitions and potential sign in blocking conditions, you’re ready to look at the logic behind a robust sign in process. Figure 2 shows the logic flow of the sign in process. The details of how to handle each state change event are explained in the following How to procedures.

Figure 2. A robust sign in process

  
![OCOM\_SignIn\_NotInitialized](images/Dn391637.OCOM_SignIn_NotInitialized(Office.15).jpg "OCOM_SignIn_NotInitialized")

## Sign a user in to Lync 2013

The procedure in this section handles three of the most likely client states that your application sees after getting the [Microsoft.Lync.Model.LyncClient](https://msdn.microsoft.com/library/jj274980\(v=office.15\)) object from the static [LyncClient.GetClient](https://msdn.microsoft.com/library/jj278213\(v=office.15\)) method. The sign in process is started in the main thread of your application, either when the window is loaded or when a user clicks a window command button. Most of the sign in logic is done in the event callback methods for the client events you already registered for.

### To initialize and sign in the Lync client

1.  Register callbacks for the [Client.StateChanged](https://msdn.microsoft.com/library/jj276368\(v=office.15\)), [LyncClient.SignInDelayed](https://msdn.microsoft.com/library/jj293478\(v=office.15\)), and [LyncClient.CredentialRequested](https://msdn.microsoft.com/library/jj267649\(v=office.15\)) events.

2.  Read the [Client.State](https://msdn.microsoft.com/library/jj274837\(v=office.15\)) property.

3.  If the client state is **Uninitialized**, Lync is in UI suppression mode. Your application starts Lync as a background process by calling the [LyncClient.BeginInitialize](https://msdn.microsoft.com/library/jj267355\(v=office.15\)) method..

4.  Call the [LyncClient.EndInitialize](https://msdn.microsoft.com/library/jj278150\(v=office.15\)) method in the lambda expression or callback method that you passed in the **BeginInitialize** method.

5.  If the client state is **SignedOut** then the Lync client is initialized and running as a background process or a first class client UI. Sign the user in by calling [LyncClient.BeginSignIn](https://msdn.microsoft.com/library/jj274512\(v=office.15\)) method.
    
    Don’t worry about the **Initializing** state. It is transient and unless there is an OS fault, the transition from **Uninitialized** through **SignedOut** is a small fraction of a second. In the **Initializing** state, no API calls method calls are allowed.

6.  If the state of the client is **SigningIn**, then the Lync process is waiting for a response from Lync Server 2013.

The following example shows the steps in this procedure.

```csharp
                //1) Register for the three Lync client events needed so that application is notified when:
                // * Lync client signs in or out
                _LyncClient.StateChanged += _LyncClient_StateChanged;
                _LyncClient.SignInDelayed += _LyncClient_SignInDelayed;
                _LyncClient.CredentialRequested += _LyncClient_CredentialRequested;



                //2-4) Client state of uninitialized means that Lync is configured for UI suppression mode and
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

                //5) If the Lync client is signed out, sign into the Lync client
                else if (_LyncClient.State == ClientState.SignedOut)
                {
                    SignUserIn();
                }
                //6) A sign in operation is pending
                else if (_LyncClient.State == ClientState.SigningIn)
                {
                    if (MessageBox.Show(
                        "Lync is signing in. Do you want to continue waiting?",
                        "Sign in delay",
                        MessageBoxButtons.YesNo,
                        MessageBoxIcon.Question) == System.Windows.Forms.DialogResult.No)
                    {
                        this.Close();
                    }
                }
```

The following example is a helper method that signs a Rosie McBride from Contoso, Ltd. in to Lync.

```csharp
        /// <summary>
        /// Signs a user in to Lync as one of two possible users. User that is
        /// signed in depends on whether side-by-side client is chosen.
        /// </summary>
        public void SignUserIn()
        {

            try
            {
                _LyncClient.BeginSignIn(
                    "rosiem@contoso.com",
                    "rosiem@contoso.com",
                    "Xvf__3ed",
                    (ar) =>
                    {
                        try
                        {
                            _LyncClient.EndSignIn(ar);

                        }
                        catch (Exception exc)
                        {
                            MessageBox.Show("exception on endsignin: " + exc.Message);
                        }
                    },
                    null);
            }
            catch (ArgumentException ae)
            {
                MessageBox.Show("exception on beginsignin: " + ae.Message);
            }

        }
```

### To handle the StateChanged event

1.  Get the old and new states of the client

2.  Call the [LyncClient.BeginSignIn](https://msdn.microsoft.com/library/jj274512\(v=office.15\)) method if the new state is **SignedOut** and the old state is **Initializing**.

3.  Call the **LyncClientBeginShutDown(AsyncCallback, Object)** if the new client state is **SignedOut**, the old state is **SigningOut** and the client is in UI suppression mode.

4.  Close your application if the new client state is **Uninitialized** and the old state was **ShuttingDown**.
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>In the Lync UI suppression mode, the Lync background process can’t re-start after your application has shut it down. Stop and restart your application and then initialize a new instance of the Lync background process.</p></td>
    </tr>
    </tbody>
    </table>

The following example handles the [Client.StateChanged](https://msdn.microsoft.com/library/jj276368\(v=office.15\)) event.

```csharp
        /// <summary>
        /// Handles the event raised when a user signs in to or out of the Lync client.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _LyncClient_StateChanged(object sender, ClientStateChangedEventArgs e)
        {
            switch (e.NewState)
            {
                case ClientState.SignedOut:
                    if (e.OldState == ClientState.Initializing)
                    {
                        SignUserIn();
                    }
                    if (e.OldState == ClientState.SigningOut && _LyncClient.InSuppressedMode == true)
                    {
                        _LyncClient.BeginShutdown((ar) =>
                        {
                            _LyncClient.EndShutdown(ar);
                        }, null);
                    }
                    break;
                case ClientState.Uninitialized:
                    if (e.OldState == ClientState.ShuttingDown)
                    {
                        _LyncClient.StateChanged -= _LyncClient_StateChanged;
                        this.Close();
                    }
                    break;
            }
        }
```

## Handle credentials needed event

The [LyncClient.CredentialRequested](https://msdn.microsoft.com/library/jj267649\(v=office.15\)) event is raised when a network service such as Lync Server 2013 requests authenticating credentials. If you do not handle the event, then in the case of Lync Server 2013, the client state does not transition from **SigningIn** to **SignedIn**. Other network services that are awaiting credentials will not respond until their credentials are submitted.

### To handle invalid credentials

1.  Get the credential type that is requested.

2.  If the credential type is **LyncAutodiscover**, then one or more elements of the credentials that the user typed are not valid. Call the [LyncClient.BeginSignOut](https://msdn.microsoft.com/library/jj277581\(v=office.15\)) method to abandon the sign in process and then start to sign the user in again. Be sure to ask the user for credentials again.
    
    Although you can call the [CredentialRequestedEventArgs.Submit](https://msdn.microsoft.com/library/jj276532\(v=office.15\)) method to submit a replacement user name and password, you can’t submit a sign in URL. If the original sign in URL was not correct, the only way you can correct it is to sign out and then start the sign in operation over again after getting new credentials.
    
    ```csharp
            /// <summary>
            /// Raised when user's credentials are rejected by Lync or a service that
            /// Lync depends on requests credentials
            /// </summary>
            /// <param name="sender"></param>
            /// <param name="e"></param>
            void _LyncClient_CredentialRequested(object sender, CredentialRequestedEventArgs e)
            {
                //If the request for credentials comes from Lync server then sign out, get new creentials
                //and sign in.
                if (e.Type == CredentialRequestedType.LyncAutodiscover)
                {
                    try
                    {
                        _LyncClient.BeginSignOut((ar) =>
                        {
                            _LyncClient.EndSignOut(ar);
                            //Ask user for credentials and attempt to sign in again
                            SignUserIn();
                        }, null);
                    }
                    catch (Exception ex)
                    {
    
                        MessageBox.Show(
                            "Exception on attempt to sign in, abandoning sign in: " +
                            ex.Message,
                            "Lync Client sign in delay",
                            MessageBoxButtons.OK, MessageBoxIcon.Information);
                    }
                }
                else
                {
                    SignInCreds getCreds;
                    getCreds = new SignInCreds(e.Type.ToString());
                    if (getCreds.ShowDialog() == DialogResult.OK)
                    {
                        string userUri = getCreds.UserName;
                        string userPassword = getCreds.Password;
                        getCreds.Close();
                        e.Submit(userUri, userPassword, false);
                    }
    
                }
            }
    ```

## Handle sign in delayed

A sign in delay can be caused by network connectivity issues. In this case, all you can do is let the user know that there is a problem and ask if the user would like to continue to wait or abandon the sign in process.

### To handle SignInDelayed event

1.  Get the estimated time that the sign in delay started and the associated delay status code.

2.  Show the user how long the delay is and then ask the user if she wants to continue to wait.

3.  If she does not want to continue waiting, abandon the sign in process by calling the [LyncClient.BeginSignOut](https://msdn.microsoft.com/library/jj277581\(v=office.15\)) method.

```csharp
        /// <summary>
        /// Raised when the sign in operation is delayed because of 1) invalid user credentials or
        /// 2) network connectivity issues which may be transient.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _LyncClient_SignInDelayed(object sender, SignInDelayedEventArgs e)
        {
            if (MessageBox.Show(
                "Delay started at " +
                e.EstimatedStartDelay.ToString() +
                " Status code:" +
                e.StatusCode.ToString(),
                "Lync Client sign in delay",
                MessageBoxButtons.YesNo, MessageBoxIcon.Information) == System.Windows.Forms.DialogResult.No)
            {
                this.close();
            }
            else
            {
                try
                {
                    _LyncClient.BeginSignOut((ar) => { _LyncClient.EndSignOut(ar); }, null);
                }
                catch (LyncClientException lce)
                {
                    MessageBox.Show("Exception on sign out in SignInDelayed event: " + lce.Message);
                }
            }

        }
```

## Example: UserSignIn class

The following example encapsulates the complete sign in process in a class.

```csharp
using System;
using Microsoft.Lync.Model;
using System.Windows.Forms;

namespace ShareResources
{
    class UserSignIn
    {
        public delegate void SetWindowCursorDelegate(Cursor newCursor);
        //Client state requires a change to the window cursor. 
        public event SetWindowCursorDelegate SetWindowCursor;

        public delegate void CloseAppConditionDelegate();
        //An error condition or client shut down requires parent window to close.
        public event CloseAppConditionDelegate CloseAppConditionHit;

        public delegate void UserIsSignedInDelegate();
        //User has signed in to Lync
        public event UserIsSignedInDelegate UserIsSignedIn;

        public delegate void ClientStateChangedDelegate(string newState);
        //The state of the Lync client has changed.
        public event ClientStateChangedDelegate ClientStateChanged;

        /// <summary>
        /// Flag that indicates that this instance of the ShareResources
        /// process initialized Lync. Other instances of ShareResources must not
        /// attempt to shut down Lync
        /// </summary>
        private Boolean _thisProcessInitializedLync = false;

        /// <summary>
        /// Indicates the user is starting a Side-by-side instance of Lync
        /// </summary>
        private Boolean _inSideBySideMode = false;

        /// <summary>
        /// Lync client platform. The entry point to the API
        /// </summary>
        Microsoft.Lync.Model.LyncClient _LyncClient;

        ShareResources.ShareResources_Form _shareResources;
        string _UserUri;

        public Microsoft.Lync.Model.LyncClient Client
        {
            get
            {
                return _LyncClient;
            }
        }
        public Boolean ThisProcessInitializedLync
        {
            get
            {
                return _thisProcessInitializedLync;
            }
        }
        public UserSignIn(LyncClient lyncClient, ShareResources.ShareResources_Form shareResources)
        {
            _LyncClient = lyncClient;
            _shareResources = shareResources;
        }

        /// <summary>
        /// Gets the Lync client, initializes if in UI suppression, and 
        /// starts the user sign in process
        /// </summary>
        /// <param name="sideBySide">boolean. Specifies endpoint mode</param> 
        internal void StartUpLync(Boolean sideBySide)
        {
            //Calling GetClient a second time in a running process will
            //return the previously cached client. For example, calling GetClient(boolean sideBySideFlag)
            // the first time in a process returns a new endpoint.  Calling the method a second
            //time returns the original endpoint. If you call GetClient(false) to get a client 
            //endpoint and then GetClient(true), the original client enpoint is returned even though
            // a true value argument is passed with the second call.

            try
            {
                if (_LyncClient == null)
                {
                    //If sideBySide == false, a standard endpoint is created
                    //Otherwise, a side-by-side endpoint is created
                    _LyncClient = LyncClient.GetClient(sideBySide);
                }
                _inSideBySideMode = sideBySide;

                //Display the current state of the Lync client.
                if (ClientStateChanged != null)
                {
                    ClientStateChanged(_LyncClient.State.ToString());
                }

                //Register for the three Lync client events needed so that application is notified when:
                // * Lync client signs in or out
                _LyncClient.StateChanged += _LyncClient_StateChanged;
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
                else if (_LyncClient.State == ClientState.SigningIn)
                {
                    if (MessageBox.Show(
                        "Lync is signing in. Do you want to continue waiting?", 
                        "Sign in delay",
                        MessageBoxButtons.YesNo, 
                        MessageBoxIcon.Question) == System.Windows.Forms.DialogResult.No)
                    {
                        if (CloseAppConditionHit != null)
                        {
                            CloseAppConditionHit();
                        }

                    }
                }



            }
            catch (NotInitializedException)
            {
                MessageBox.Show(
                    "Client is not initialized.  Closing form", 
                    "Lync Client Error", 
                    MessageBoxButtons.OK, MessageBoxIcon.Hand);
                if (CloseAppConditionHit != null)
                {
                    CloseAppConditionHit();
                }

            }
            catch (ClientNotFoundException)
            {
                MessageBox.Show(
                    "Client is not running.  Closing form", 
                    "Lync Client Error", 
                    MessageBoxButtons.OK, MessageBoxIcon.Hand);
                if (CloseAppConditionHit != null)
                {
                    CloseAppConditionHit();
                }

            }
            catch (Exception exc)
            {
                MessageBox.Show(
                    "General exception: " +
                    exc.Message, "Lync Client Error",
                    MessageBoxButtons.OK, MessageBoxIcon.Hand);
                if (CloseAppConditionHit != null)
                {
                    CloseAppConditionHit();
                }

            }
        }

        /// <summary>
        /// Raised when user's credentials are rejected by Lync or a service that
        /// Lync depends on requests credentials
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _LyncClient_CredentialRequested(object sender, CredentialRequestedEventArgs e)
        {
            //If the request for credentials comes from Lync server then sign out, get new creentials
            //and sign in.
            if (e.Type == CredentialRequestedType.LyncAutodiscover)
            {
                try
                {
                    _LyncClient.BeginSignOut((ar) =>
                    {
                        _LyncClient.EndSignOut(ar);
                        //Ask user for credentials and attempt to sign in again
                        SignUserIn();
                    }, null);
                }
                catch (Exception ex)
                {
                    if (SetWindowCursor != null)
                    {
                        SetWindowCursor(Cursors.Arrow);
                    }
                    MessageBox.Show(
                        "Exception on attempt to sign in, abandoning sign in: " +
                        ex.Message,
                        "Lync Client sign in delay",
                        MessageBoxButtons.OK, MessageBoxIcon.Information);
                }
            }
            else
            {
                SignInCreds getCreds;
                getCreds = new SignInCreds(e.Type.ToString());
                if (getCreds.ShowDialog() == DialogResult.OK)
                {
                    string userUri = getCreds.UserName;
                    string userPassword = getCreds.Password;
                    getCreds.Close();
                    e.Submit(userUri, userPassword, false);
                }

            }
        }

        void _LyncClient_SignInDelayed(object sender, SignInDelayedEventArgs e)
        {
            if (MessageBox.Show(
                "Delay started at " + 
                e.EstimatedStartDelay.ToString() + 
                " Status code:" + 
                e.StatusCode.ToString(), 
                "Lync Client sign in delay", 
                MessageBoxButtons.YesNo, MessageBoxIcon.Information) == System.Windows.Forms.DialogResult.No)
            {
                if (CloseAppConditionHit != null)
                {
                    CloseAppConditionHit();
                }
            }
            else
            {
                try
                {
                    _LyncClient.BeginSignOut((ar) => { _LyncClient.EndSignOut(ar); }, null);
                }
                catch (LyncClientException lce)
                {
                    MessageBox.Show("Exception on sign out in SignInDelayed event: " + lce.Message);
                }
            }

        }
        /// <summary>
        /// Handles the event raised when a user signs in to or out of the Lync client.
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        void _LyncClient_StateChanged(object sender, ClientStateChangedEventArgs e)
        {
            switch (e.NewState)
            {
                case ClientState.SignedOut:
                    if (e.OldState == ClientState.Initializing)
                    {
                        SignUserIn();
                    }
                    if (e.OldState == ClientState.SigningOut)
                    {
                        _LyncClient.BeginShutdown((ar) =>
                        {
                            _LyncClient.EndShutdown(ar);
                        }, null);
                    }
                    break;
                case ClientState.Uninitialized:
                    if (e.OldState == ClientState.ShuttingDown)
                    {
                        _LyncClient.StateChanged -= _LyncClient_StateChanged;
                        try
                        {
                            if (CloseAppConditionHit != null)
                            {
                                CloseAppConditionHit();
                            }
                        }
                        catch (InvalidOperationException oe)
                        {
                            System.Diagnostics.Debug.WriteLine("Invalid operation exception on close: " + oe.Message);
                        }
                    }
                    break;
                case ClientState.SignedIn:
                    if (UserIsSignedIn != null)
                    {
                        UserIsSignedIn();
                    }
                    break;
            }
            if (ClientStateChanged != null)
            {
                ClientStateChanged(e.NewState.ToString());
            }


        }

        /// <summary>
        /// Signs a user in to Lync as one of two possible users. User that is
        /// signed in depends on whether side-by-side client is chosen.
        /// </summary>
        public void SignUserIn()
        {
            //Set the display cursor to indicate that user must wait for
            //sign in to complete
            if (SetWindowCursor != null)
            {
                SetWindowCursor(Cursors.WaitCursor);
            }

            //Set the sign in credentials of the user to the
            //appropriate credentials for the endpoint mode
            string userUri = string.Empty;
            string userName = string.Empty;
            string userPassword = string.Empty;


            SignInCreds getCreds;
            getCreds = new SignInCreds("Sign in");
            if (getCreds.ShowDialog() == DialogResult.OK)
            {
                userName = getCreds.UserName;
                userUri = getCreds.SignInURL;
                userPassword = getCreds.Password;
                getCreds.Close();
            }

            _UserUri = userUri;



            _LyncClient.BeginSignIn(
                userUri,
                userName,
                userPassword,
                (ar) =>
                {
                    try
                    {
                        _LyncClient.EndSignIn(ar);
                        if (UserIsSignedIn != null)
                        {
                            UserIsSignedIn();
                        }

                    }
                    catch (Exception exc)
                    {
                        MessageBox.Show("exception on endsignin: " + exc.Message);
                    }
                },
                null);

        }

    }
}
```

The following example is the interaction logic behind a Windows form with

```csharp
using System;
using System.Windows.Forms;

namespace ShareResources
{
    public partial class SignInCreds : Form
    {
        public string UserName
        {
            get
            {
                return UserName_textBox.Text;
            }
        }
        public string Password
        {
            get
            {
                return Password_textBox.Text;
            }
        }
        public string SignInURL
        {
            get
            {
                return SignInURL_Textbox.Text;
            }
        }


        public SignInCreds()
        {
            InitializeComponent();
        }
        public SignInCreds(string credentialType)
        {
            InitializeComponent();
            this.Text = credentialType + " credentials needed";
        }
    }
}
```

## Next steps

  - [How to: Change sign-in connection settings in Lync SDK](how-to-change-sign-in-connection-settings-in-lync-sdk.md)

## See also

  - [What you can do in Lync SDK](what-you-can-do-in-lync-sdk.md)

  - [UI suppression](ui-suppression.md)

  - [Lync Server sign-in configuration](lync-server-sign-in-configuration.md)

