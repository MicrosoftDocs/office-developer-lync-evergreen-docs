---
title: 'How to: Connect to a Persistent Chat server'
TOCTitle: 'How to: Connect to a Persistent Chat server'
ms:assetid: 4e263bd9-a530-47f6-901e-f36eeae5f12d
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465896(v=office.15)
ms:contentKeyID: 57101347
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Connect to a Persistent Chat server

Learn how to use the Microsoft Lync Server 2013 Persistent Chat API to connect to a Persistent Chat server.


**Applies to:** Lync 2013 | Lync Server 2013

To call any Lync Server 2013 Persistent Chat API functionality, an application must first establish a connection to the underlying Persistent Chat server. This involves connecting to a Microsoft Lync Server 2013 instance by using Microsoft Unified Communications Managed API (UCMA) on a [LocalEndpoint](https://msdn.microsoft.com/library/hh349887\(v=office.15\)) instance and then connecting to the underlying Persistent Chat server on a [PersistentChatEndpoint](https://msdn.microsoft.com/library/jj267567\(v=office.15\)) instance.

In UCMA, a [LocalEndpoint](https://msdn.microsoft.com/library/hh349887\(v=office.15\)) is either a [UserEndpoint](https://msdn.microsoft.com/library/hh348819\(v=office.15\)) or an [ApplicationEndpoint](https://msdn.microsoft.com/library/hh384825\(v=office.15\)). A client-side Lync Server 2013 Persistent Chat API application will most likely use **UserEndpoint**. An implementation of connecting to Lync Server 2013 computer on a **UserEndpoint** is illustrated as follows.

```csharp
    ClientPlatformSettings platformSettings = new ClientPlatformSettings(_appName, transport);
    CollaborationPlatform collabPlatform = new CollaborationPlatform(platformSettings);
    collabPlatform.EndStartup(collabPlatform.BeginStartup(null, null));

    UserEndpointSettings userEndpointSettings = new UserEndpointSettings(userSipUri, lyncServer);
    userEndpointSettings.Credential = usingSso ?
        SipCredentialCache.DefaultCredential : new NetworkCredential(username, password);
    UserEndpoint userEndpoint = new UserEndpoint(collabPlatform, userEndpointSettings);
    userEndpoint.EndEstablish(userEndpoint.BeginEstablish(null, null));
```

As shown in the code, connecting a **UserEndpoint** instance to Lync Server 2013 requires a specification of the transport protocol (transport of the **Tls** or **Tcp** value), the address of the server instance or pool (lyncServer of the "server.contoso.com" format), the user’s SIP URI (userSipUri of "sip:user@domain"), and credentials. When Single-Sign-On In is used (usingSso=true), Windows credentials of the currently logged-on user is used. Otherwise, the user name (userName of "user@domain") and password (password) must be explicitly supplied.

A server-side or middle-tier Lync Server 2013 Persistent Chat API application must use an **ApplicationEndpoint** to connect to the underlying Lync Server 2013. An implementation is illustrated as follows.

            public static ApplicationEndpoint ConnectLyncServerWithAppEndpoint(string userSipUri)
            {
                // Create a UCMA ApplicationEndpoint to connect to Lync server
                Console.WriteLine("Connecting to Lync Server... ");
    
                // Trusted app uses MTLS. Dig for our cert here.
                X509Store certificateStore = new X509Store(StoreName.My, StoreLocation.LocalMachine);
                certificateStore.Open(OpenFlags.ReadOnly);
    
                X509Certificate2Collection certs = certificateStore.Certificates.Find(X509FindType.FindBySubjectName, "client.contoso.com", true);
                if (certs.Count < 1)
                {
                    return null;
                }
    
                X509Certificate2 cert = certs[0];
    
                // Init platform (parameters have to match the objects created with New-CsTrustedApplication(Pool/computer) cmdlets)
                ServerPlatformSettings platformSettings = new ServerPlatformSettings("PersistentChat.Test", // App type, good for urn
                                                                                     "client.contoso.com", // App FQDN
                                                                                     4585,                // App port
                                                                                     @"sip:client.contoso.com@contoso.com;gruu;opaque=srvr:grsample:uCFg9SltSVSXRkVxjKxvJwAA", // Trusted app GRUU
                                                                                     cert);
    
                CollaborationPlatform collabPlatform = new CollaborationPlatform(platformSettings);
    
                // 
    
                // Initialize the platform
                collabPlatform.EndStartup(collabPlatform.BeginStartup(null, null));
    
                // Active Directory User object-based ApplicationEndpointSettings:
                ApplicationEndpointSettings appEndpointSettings = new ApplicationEndpointSettings(userSipUri);
                ApplicationEndpoint appEndpoint = new ApplicationEndpoint(collabPlatform, appEndpointSettings);
    
                // Set the outbound proxy (the Lync pool)
                appEndpoint.SetProxyInformation("pool0.contoso.com", 5061);
                // Sign in to Lync server.
                appEndpoint.EndEstablish(appEndpoint.BeginEstablish(null, null));
    
                Console.WriteLine("\tSuccess");
                return appEndpoint;
            }

The SIP URI used to create an ApplicationEndpoint must correspond to an Active Directory User object.

When the [LocalEndpoint](https://msdn.microsoft.com/library/hh349887\(v=office.15\)) instance is connected to Lync Server 2013, the application can proceed to connect to a **PersistentChatEndpoint**. This is shown in the following code.

```csharp
     // Extract default Persistent Chat server uri via in-band provisioning

    ProvisioningData provisioningData = appEndpoint.EndGetProvisioningData(appEndpoint.BeginGetProvisioningData(null, null));
                    
    PersistentChatConfiguration ChatConfiguration = provisioningData.PersistentChatConfiguration;
    Uri ChatServerUri = new Uri(ChatConfiguration.DefaultPersistentChatUri);

    // Connect to Persistent Chat Server
    PersistentChatEndponit ChatEndpoint = new PersistentChatEndpoint(ChatServerUri, localEndpoint);
    ChatEndpoint.EndEstablish(ChatEndpoint.BeginEstablish(null, null));
```

Here, localEndpoint is either userEndpoint or appEndpoint mentioned in the code listings discussed earlier. ChatServerUri identifies the services of the underlying Microsoft Lync Server 2013 Persistent Chat computer. For Microsoft Lync Server 2010 Group Chat, the default chat server URI is "sip:ocschat@domain.com", where "domain" stands for the domain name of the enterprise network. In Microsoft Lync Server 2013 Persistent Chat, the chat server URI is explicitly configured by the server administrator as part of server installation. The application can retrieve the chat server URI value using in-band provisioning by reading the **DefaultPersistentChatUri()** property.

Before connecting to the Lync Server 2013 Persistent Chat by calling [BeginEstablish(AsyncCallback, Object)](https://msdn.microsoft.com/library/jj267868\(v=office.15\)) and [EndEstablish(IAsyncResult)](https://msdn.microsoft.com/library/jj267198\(v=office.15\)) on the newly instantiated **PersistentChatEndpoint** object, the application might want to register interested events raised by the chat endpoint. To get notified of any invitation from a chat room, register and handle the [ChatRoomInvitationReceived](https://msdn.microsoft.com/library/jj267568\(v=office.15\)) events. To receive notifications when the connection state changes on the **PersistentChatEndpoint** instance, register and handle the [ConnectionStateChanged](https://msdn.microsoft.com/library/jj267332\(v=office.15\)) events.

## See also

#### Concepts

[Learn the basics of Lync Server 2013 Persistent Chat SDK](learn-the-basics-of-lync-server-2013-persistent-chat-sdk.md)

[How to use Persistent Chat API (Lync Server 2013 Persistent Chat SDK)](how-to-use-persistent-chat-api-lync-server-2013-persistent-chat-sdk.md)

[Get started with Lync Server 2013 Persistent Chat SDK](get-started-with-lync-server-2013-persistent-chat-sdk.md)

[Lync Server 2013 Persistent Chat SDK general reference](lync-server-2013-persistent-chat-sdk-general-reference.md)

