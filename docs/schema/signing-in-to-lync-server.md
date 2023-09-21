---
title: Signing in to Lync Server
TOCTitle: Signing in to Lync Server
ms:assetid: 6077336f-a5b3-421b-9adb-950de2c6e51e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454635(v=office.15)
ms:contentKeyID: 57092875
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Signing in to Lync Server


**Applies to:** Lync 2013 | Lync Server 2013

As with any other unified communications operation, you must first sign in to Microsoft Lync Server 2013 before you can publish or subscribe to any presence data by using Microsoft Unified Communications Managed API 4.0. This process includes the following tasks:

1.  Instantiating and initializing a CollaborationPlatform object.

2.  Starting up the initialized collaboration platform.

3.  Creating a LocalEndpoint instance.

4.  Connecting the endpoint to the server.

Step 2 and 4 are asynchronous operations. They are supported by the BeginStartup/EndStartup and BeginEstablish/EndEstablish calls on the platform and endpoint objects, respectively. The details appear in the following code example.

The following code example shows how the previous tasks are implemented. The operations are encapsulated in the UcmaLoginManager class, which can then be reused by your other UCMA applications.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;
using System.Windows.Forms;
using Microsoft.Rtc.Signaling;
using Microsoft.Rtc.Collaboration;

namespace UcmaAppLibrary 
{
    /// <summary>
    /// The class encapsulates the operations to start up a CollaborationPlatform,  
    /// to create a UserEndpoint, and to sign it in to Lync Server.
    /// 
    /// To use this class, the caller does the following:
    /// 1. Instantiate the class
    /// 2. Register for and handle OnSignInCompleted event
    /// 3. Call SignIn method to establish the endpoint, which becomes ready for 
    ///    use once OnSignInCompleted event is raised without errors
    /// 4. Once SignIn completed successfully, call the LocalEndpoint property 
    ///    to obtain the established endpoint.
    /// </summary>
    public partial class UcmaLoginManager : UcmaObject
    {
        #region private fields
        CollaborationPlatform _collabPlatform = null;
        LocalEndpoint _localEndpoint = null;
        string _ownerUri, _serverName;
        string _userName, _domain, _password;
        int _serverPort;
        string[] _categoryNamesAddedToSubscription;
        bool _platformStarted = false;
        #endregion private fields

        #region public events for tracking async operations of SignIn and SignOut of an endpoint.
        public event EventHandler<AsyncOpStatusEventArgs> OnSignInCompleted;
        public event EventHandler<AsyncOpStatusEventArgs> OnSignOutCompleted;
        #endregion public events

        #region public property to return an established endpoint
        public LocalEndpoint LocalEndpoint { get { return this._localEndpoint; } }
        //public CollaborationPlatform CollaborationPlatform { get { return this._collabPlatform; } }
        #endregion public property

        #region public class constructors
        /// <summary>
        /// Constrcutor for handling sign-in using UserEndpoint on a CollaborationPlatform instance 
        /// with ClientPlatformSettings.
        /// </summary>
        /// <param name="appName">name of the application calling this constructor</param>
        /// <param name="transport">SIP Transport used to connect to server</param>
        /// <param name="serverName">Server name</param>
        /// <param name="serverPort">Server port </param>
        /// <param name="categoryNamesAddedToSubscription">Additional categories to be subscribed to</param>
        public UcmaLoginManager(string appName, SipTransportType transport, 
                 string serverName, int serverPort, 
                 params string[] categoryNamesAddedToSubscription)
        {
            try
            {
                ClientPlatformSettings settings = new ClientPlatformSettings(appName, transport);
                _collabPlatform = new CollaborationPlatform(settings);
                _serverName = serverName;
                _serverPort = serverPort;
                _categoryNamesAddedToSubscription = categoryNamesAddedToSubscription;
            }
            catch (Exception ex)
            {
                if (OnSignInCompleted != null)
                    InvokeDelegates(OnSignInCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
            }
            
        }
        #endregion public class constructors

        #region public methods to establish and terminate an endpoint connection to the server
        public void SignIn(string userUri, string userName, string domain, string password)
        {
            _ownerUri = userUri;
            _userName = userName;
            _domain = domain;
            _password = password;

            if (!_platformStarted)
            {
                _collabPlatform.BeginStartup(
                    CallbackOnClientPlatformStartupReturned, _collabPlatform);
            }
            // Process continues in the CallbackOnClientPlatformStartupReturned routine.
        }

        public void SignOut()
        {
            if (_platformStarted)
            {
                _localEndpoint.BeginTerminate(CallbackOnEndpointTerminateReturned, _localEndpoint);
            }
        }
        #endregion public methods

        #region private methods that facilitate the implementation of the public methods
        private void CallbackOnClientPlatformStartupReturned(IAsyncResult result)
        {
            if (!result.IsCompleted)
                return;

            CollaborationPlatform platform = result.AsyncState as CollaborationPlatform;
            if (platform != _collabPlatform)
                return;  // not the right platfom 

            try
            {
                platform.EndStartup(result);
                UserEndpointSettings settings = new UserEndpointSettings(_ownerUri, _serverName, _serverPort);
                if (_categoryNamesAddedToSubscription != null)
                {
                    foreach (string categoryName in _categoryNamesAddedToSubscription)
                        settings.Presence.RemotePresenceSubscriptionCategories.Add(categoryName);
                }

                UserEndpoint userEndpoint = new UserEndpoint(_collabPlatform, settings);
                SetUserEndpointCredentials(ref userEndpoint);
                _localEndpoint = userEndpoint as LocalEndpoint;
                _localEndpoint.BeginEstablish(CallbackOnEndpointEstablishReturned, _localEndpoint);
                // Process continues in the CallbackOnEndpointestablishedReturned routine.
            }
            catch (ConnectionFailureException connFailEx)
            {
                // ConnectionFailureException will be thrown when the platform cannot connect.
                // ClientPlatforms will not throw this exception on startup.
                if (OnSignInCompleted != null)
                    InvokeDelegates(OnSignInCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, connFailEx));
            }
            catch (InvalidOperationException ioe)
            {
                // InvalidOperationException will be thrown when the platform is already started or terminated.
                // It's left to the developer to write real error handling code.
                if (OnSignInCompleted != null)
                    InvokeDelegates(OnSignInCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ioe));
            }
        }

        void SetUserEndpointCredentials(ref UserEndpoint userEndpoint)
        {
            NetworkCredential credential;
            if (_userName == null || _password == null)
            {
                credential = CredentialCache.DefaultNetworkCredentials;
            }
            else
            {
                credential = new NetworkCredential();
                if (_userName != null)
                    credential.UserName = _userName;
                if (_password != null)
                    credential.Password = _password;
                if (_domain != null)
                    credential.Domain = _domain;
            }
            userEndpoint.Credential = credential;
        }

        private void CallbackOnEndpointEstablishReturned(IAsyncResult result)
        {
            try
            {
                _localEndpoint.EndEstablish(result);
                if (result.IsCompleted)
                {
                    _platformStarted = true;
                    // Report SignIn success to the caller
                    if (OnSignInCompleted != null)
                        InvokeDelegates(OnSignInCompleted, this,
                            new AsyncOpStatusEventArgs(AsyncOpStatus.OK, null));
                }
            }
            catch (Exception ex)
            {
                // Report SingIn error to the caller.
                if (OnSignInCompleted != null)
                    InvokeDelegates(OnSignInCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
            }
        }

        private void CallbackOnEndpointTerminateReturned(IAsyncResult result)
        {
            try
            {
                _localEndpoint.EndTerminate(result);
                _platformStarted = false;
                if (OnSignOutCompleted != null)
                    InvokeDelegates(OnSignOutCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.OK, null));
            }
            catch (Exception ex)
            {
                // Report SingOut error to the caller.
                if (OnSignOutCompleted != null)
                    InvokeDelegates(OnSignOutCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
            }
        }

        #endregion private methods

    }
}
```

In the following example, the base class (UcmaObject) is used to encapsulate the common operations to support the asynchronous calls.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.ComponentModel;
using System.Windows.Forms;

namespace UcmaAppLibrary 
{
    public class UcmaObject
    {
        public static void InvokeDelegates(MulticastDelegate mDelegate, object sender, EventArgs e)
        {
            if (mDelegate == null)
                return;

            Delegate[] delegates = mDelegate.GetInvocationList();
            if (delegates == null)
                return;

            // Invoke delegates within their threads
            foreach (Delegate _delegate in delegates)
            {
                if (_delegate.Target.GetType().ContainsGenericParameters)
                {
                    MessageBox.Show("Cannot invoke event handler on a generic type.");
                    return;
                }

                object[] contextAndArgs = { sender, e };
                ISynchronizeInvoke syncInvoke = _delegate.Target as ISynchronizeInvoke;
                {
                    if (syncInvoke != null)
                    {
                        // This case applies to the situation when Delegate.Target is a 
                        // Control with an open window handle.
                        syncInvoke.Invoke(_delegate, contextAndArgs);
                    }
                    else
                    {
                        _delegate.DynamicInvoke(contextAndArgs);
                    }
                }
            }
        }
        public static void RaiseEvent(MulticastDelegate mDelegate, object sender, EventArgs e)
        {
            InvokeDelegates(mDelegate, sender, e);
        }

        public static void Trace(string msg)
        {
            Console.WriteLine(msg);
        }
        public static string NewLine { get { return Environment.NewLine; } }
        public static string Tab { get { return "\t"; } }
    }

}
```

In the following example, the types to support the asynchronous operation status report are listed.

```csharp
    public enum AsyncOpStatus { OK, Error };

    public class AsyncOpStatusEventArgs : EventArgs
    {
        Exception _exception;
        AsyncOpStatus _status;
        public AsyncOpStatusEventArgs(AsyncOpStatus status, Exception exception)
        {
            _exception = exception;
            _status = status;
        }
        public Exception Exception { get { return this._exception; } }
        public AsyncOpStatus Status { get { return this._status; } }
    }
```

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

