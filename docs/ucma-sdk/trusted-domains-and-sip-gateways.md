---
title: Trusted domains and SIP gateways
TOCTitle: Trusted domains and SIP gateways
ms:assetid: 924e3808-eb50-4b25-afd1-818744f2b8e3
ms:mtpsurl: https://msdn.microsoft.com/library/Dn466047(v=office.15)
ms:contentKeyID: 57103040
ms.date: 07/25/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Trusted domains and SIP gateways


**Applies to:** Lync 2013 | Lync Server 2013



Microsoft Unified Communications Managed API 4.0 is able to interoperate with third-party SIP peers such as IP-PBXs and SIP PSTN gateways. This topic describes the APIs on the [CollaborationPlatform](https://msdn.microsoft.com/library/hh385176\(v=office.15\)) and related classes that developers must understand when they create applications that interoperate with SIP gateways.

## Configuring trusted domains for the CollaborationPlatform

UCMA 4.0 can be used to create a **CollaborationPlatform** instance using the TCP, TLS or MTLS transport types. For security reasons, it is highly recommended that you use TLS or MTLS.

UCMA 4.0 supports two modes of trusted domains as specified in the [TrustedDomainMode](https://msdn.microsoft.com/library/hh381100\(v=office.15\)) enumeration: **CommunicationsServer** and **Other**. The **CommunicationsServer** value indicates that the trusted domain is a Microsoft Lync Server 2013 server or a Microsoft Edge Server. The **Other** value indicates that the trusted domain is a remote SIP peer, such as a SIP PSTN gateway or IP-PBX.

Most of the SIP messages and call flows in both **TrustedDomainMode** modes are of the same type. The principal differences involve header parsing and the filtering of headers in outgoing messages. These differences between these modes are described later in this topic.

If a **CollaborationPlatform** instance is created with the TLS or MTLS transport type, the default behavior of the platform is to consider the first-hop proxy (specified in the [ProxyHost](https://msdn.microsoft.com/library/hh381683\(v=office.15\)) property on an [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) instance) to be a Lync Server 2010 or Microsoft Office Communications Server 2007 R2/Microsoft Office Communications Server 2007 server (**TrustedDomainMode.CommunicationsServer**). Unless specified by application writer (the application writer can use the [ConnectionContext](https://msdn.microsoft.com/library/hh380911\(v=office.15\)) property on a [CallEstablishOptions](https://msdn.microsoft.com/library/hh381079\(v=office.15\)) instance. to override this behavior), all outgoing messages and INVITE messages are routed to this first-hop proxy.

UCMA 4.0 allows application writers to prepopulate all known trusted domains. This can be done by adding the known domains on the property [TrustedDomains](https://msdn.microsoft.com/library/hh348697\(v=office.15\)) property on a [ServerPlatformSettings](https://msdn.microsoft.com/library/hh382156\(v=office.15\)) instance when the **CollaborationPlatform** is constructed. The **TrustedDomains** property is similar to the obsolete **AllowedDomains** property on the **ServerPlatformSettings** class, except that developers can use the **TrustedDomains** property to choose the type of trusted domain for each entry. For incoming connections this property represents a list of computers that are allowed to make incoming connections, when mutual TLS is used. The subject or subject alternate names (SANs) in the certificate are matched against each [DomainName](https://msdn.microsoft.com/library/hh384107\(v=office.15\)) property (on the [TrustedDomain](https://msdn.microsoft.com/library/hh385045\(v=office.15\)) class) in the **TrustedDomains** collection. For outgoing connections domain names are matched with the fully qualified domain names specified in the connection context.

The following code example demonstrates how to add two trusted domains in platform settings when a **CollaborationPlatform** instance is constructed.

```csharp
private CollaborationPlatform CreateServerPlatform()
{
  ServerPlatformSettings mySettings = new ServerPlatformSettings();
  // Add a known Microsoft Lync Server 2010 server to trusted domains.
  mySettings.TrustedDomains.Add(new TrustedDomain("finance.contoso.com")); 
  // Add a known PSTN gateway to trusted domains.
  mySettings.TrustedDomains.Add(new TrustedDomain("mygateway.contoso.com"), TrustedDomainMode.Other); 
  CollaborationPlatform platform = new CollaborationPlatform(mySettings);
  return platform;
}
```

## Maintaining a dynamic list of trusted domains

In some applications an application might not be aware of all trusted domains at start-up time. In these cases the application can authorize outgoing or incoming connections by registering a handler for the **ConnectionAuthorizationRequested()** event.

The following example demonstrates an implementation of a handler for the **ConnectionAuthorizationRequested** event. In this event handler, an application selectively allows connections that match a specific domain name.

```csharp
private void myConnectionAuthorizationRequested(object sender, 
ConnectionAuthorizationRequestedEventArgs e)
{
  // Accept the incoming connection if it is from the known domain ″finance.contoso.com″, otherwise deny it.
  if (e.Connection.MatchingDomainName == ″finance.contoso.com″)
  {
    e.Allow();
  }
  else
  {
    e.Deny();
  }
}
```

UCMA 4.0 also enables application writers to add trusted domains to or remove them from the **CollaborationPlatform** instance after platform is started. For these purposes, he **CollaborationPlatform** class exposes the [GetTrustedDomains](https://msdn.microsoft.com/library/hh366279\(v=office.15\)), [AddTrustedDomain(TrustedDomain)](https://msdn.microsoft.com/library/hh383029\(v=office.15\)), and [RemoveTrustedDomain(TrustedDomain)](https://msdn.microsoft.com/library/hh349579\(v=office.15\)) methods to maintain a list of trusted domains in the **CollaborationPlatform** instance. When a trusted domain entry is added after the platform is started, the semantics for newly added or removed domains are applied only to new connections and have no any impact on connections created prior to the new entry.

## TrustedDomainMode differences

There are few differences in behavior between the **CommunicationsServer** and **Other** enumeration values of the [TrustedDomainMode](https://msdn.microsoft.com/library/hh381100\(v=office.15\)) enumeration for most call flows and other SIP transactions. The following table describes the differences in header parsing and outgoing header filtering.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>TrustedDomainMode.CommunicationsServer</p></th>
<th><p>TrustedDomainMode.Other</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The Referred-by header is signed with referee and referrer URIs on outgoing REFER message.</p></td>
<td><p>No Microsoft-specific headers (headers starting with a &quot;ms-&quot; prefix ) go out with messages.</p></td>
</tr>
<tr class="even">
<td><p>The &quot;cc-diversion&quot; and &quot;remote-party-id&quot; headers are ignored, if present in incoming messages.</p></td>
<td><p>Relaxed SDP parsing is applied to incoming messages.</p></td>
</tr>
<tr class="odd">
<td><p>A QoE report is published at the end of every audio-video call.</p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>The remote is assumed to be aware of the GRUU so that it is added as the contact header.</p></td>
<td><p>The remote is assumed to be unaware of the GRUU so that connection information will be added as the contact header.</p></td>
</tr>
</tbody>
</table>


## Setting ConnectionContext on an outgoing call

The default behavior of a **CollaborationPlatform** instance is to always route messages to the first-hop proxy that is specified in the [ProxyHost](https://msdn.microsoft.com/library/hh381683\(v=office.15\)) property in the [ApplicationEndpointSettings](https://msdn.microsoft.com/library/hh349433\(v=office.15\)) instance. An application writer who intends to route outgoing message to any destination host other than the first-hop proxy should set the [ConnectionContext](https://msdn.microsoft.com/library/hh380911\(v=office.15\)) property on the [CallEstablishOptions](https://msdn.microsoft.com/library/hh381079\(v=office.15\)) instance for the outgoing call.

The following code sample demonstrates setting connection context on an outgoing call, so that outgoing INVITE messages are routed to the gateway server specified in *options.ConnectionContext*.

```csharp
Conversation conversation = new Conversation(myAppEndpoint);
AudioVideoCall outgoingCall = new AudioVideoCall(conversation);
CallEstablishOptions options = new CallEstablishOptions();
options.ConnectionContext = new ConnectionContext(myGatewayFQDN, gatewayPort);
outgoingCall.BeginEstablish(gatewayUri, options, userCallback, outgoingCall);
```

