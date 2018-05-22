---
title: Parsing server configuration
TOCTitle: Parsing server configuration
ms:assetid: 313eb2de-e73c-4f25-b173-f59670288746
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454660(v=office.15)
ms:contentKeyID: 57093336
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Parsing server configuration


_**Applies to:** Lync 2013 | Lync Server 2013_

The server configuration from the provisioned data specifies the currently configured server settings. In Microsoft Unified Communications Managed API (UCMA), the server configuration is encapsulated by a ServerConfiguration object, which exposes the configuration settings as a collection of name-value pairs known as the properties in addition to other server-specific information.

The following code example shows how the server configuration might be parsed by using UCMA.

``` 
        string ParseServerConfiguration(ProvisioningData data)
        {
            if (data == null)
                return null;

            string msg = null;

            if (data.ServerConfiguration != null)
            {
                msg += "\r\nServerConfiguration:\r\n";
                msg += "\tConsoleDownloadExternalUrl = " + data.ServerConfiguration.ConsoleDownloadExternalUrl + "\r\n";
                msg += "\tConsoleDownloadInternalUrl = " + data.ServerConfiguration.ConsoleDownloadInternalUrl + "\r\n";
                msg += "\tEnableSipSecurityMode = " + data.ServerConfiguration.EnableSipSecurityMode + "\r\n";
                msg += "\tHelpdeskExternalUrl = " + data.ServerConfiguration.HelpdeskExternalUrl + "\r\n";
                msg += "\tHelpdeskInternalUrl = " + data.ServerConfiguration.HelpdeskInternalUrl + "\r\n";
                msg += "\tLocationProfile = " + data.ServerConfiguration.LocationProfile + "\r\n";
                msg += "\tOrganization = " + data.ServerConfiguration.Organization + "\r\n";
                msg += "\tPoolUri = " + data.ServerConfiguration.PoolUri + "\r\n";
                msg += "\tVoicemailUri = " + data.ServerConfiguration.VoicemailUri + "\r\n";
                if (data.ServerConfiguration.Properties != null)
                {
                    foreach (string key in data.ServerConfiguration.Properties.Keys)
                        msg += "\tProperty[ " + key + " ] = " + data.ServerConfiguration.Properties[key] + "\r\n";
                }

            }

            return msg;
        }

```

The following code example shows how the server configuration might be parsed after the previous code statements are invoked.

    ServerConfiguration:
    ConsoleDownloadExternalUrl = 
    ConsoleDownloadInternalUrl = 
    EnableSipSecurityModeHigh = 
    HelpdeskExternalUrl = 
    HelpdeskInternalUrl = 
    LocationProfile = W13RC1
    Organization = 
    PoolUri = sip:tk5ucdfpl01.exchange.contoso.com@contoso.com;gruu;opaque=srvr:HomeServer:AkqNlc1ANlGQgU_kQeAuUwAA
    VoicemailUrisip:adamb@contoso.com;opaque=app:voicemail
    Property[ qosenabled ] = false
    Property[ voicemailuri ] = sip: adamb@contoso.com;opaque=app:voicemail
    Property[ uclocationprofile ] = W13RC1
    Property[ responsegroupserviceinternalurl ] = https://tk5ucdfpl01.exchange.contoso.com:443/RgsClients/AgentService.svc
    Property[ ucenforcepinlock ] = true
    Property[ ucexchangemwipoll ] = 3
    Property[ updatesserverenabled ] = true
    Property[ updatesserverinternalurl ] = https://tk5ucdfpl01.exchange.contoso.com:443/RequestHandler/ucdevice.upx
    Property[ botsipurifortestcall ] = sip:tk5ucdfpl01.exchange.contoso.com@contoso.com;gruu;opaque=srvr:Microsoft.Rtc.Applications.testbot:gZRWjP73kFOm-I3egDt2hAAA
    Property[ dlxexternalurl ] = https://lslm84.meet.contoso.com:443/groupexpansion/service.svc
    Property[ ucminmediaport ] = 50000
    Property[ ucenablesipsecuritymode ] = High
    Property[ ucvoice802_1p ] = 0
    Property[ ucmaxvideoport ] = 50038
    Property[ ucmaxmediaport ] = 50038
    Property[ mrasuri ] = sip:tk5ucdfes01.exchange.contoso.com@contoso.com;gruu;opaque=srvr:MRAS:k9JWeflVVl6GdopUWZcgWwAA
    Property[ qosuri ] = sip:tk5ucdfpl01.exchange.contoso.com@contoso.com;gruu;opaque=srvr:HomeServer:AkqNlc1ANlGQgU_kQeAuUwAA
    Property[ ucminvideoport ] = 50000
    Property[ ucminaudioport ] = 50000
    Property[ ucmaxsipdynamicport ] = 7102
    Property[ ucdiffservvoice ] = 40
    Property[ ucmaxappsharingport ] = 50038
    Property[ absinternalserverurl ] = https://tk5ucdfpl01.exchange.contoso.com:443/abs/handler
    Property[ ucminfiletransferport ] = 50000
    Property[ responsegroupserviceexternalurl ] = https://lslm84.meet.contoso.com:443/RgsClients/AgentService.svc
    Property[ ucphonetimeout ] = 10
    Property[ focusfactoryuri ] = sip:kdeding@contoso.com;gruu;opaque=app:conf:focusfactory
    Property[ responsegroupserviceexternalagenturl ] = https://lslm84.meet.contoso.com:443/RgsClients/Tab.aspx
    Property[ pooluri ] = sip:tk5ucdfpl01.exchange.contoso.com@contoso.com;gruu;opaque=srvr:HomeServer:AkqNlc1ANlGQgU_kQeAuUwAA
    Property[ ucminpinlength ] = 6
    Property[ cwaexternaluri ] = https://dialdf.contoso.com
    Property[ lisinternalurl ] = https://tk5ucdfpl01.exchange.contoso.com:443/locationinformation/liservice.svc
    Property[ cwainternaluri ] = https://dialdf.contoso.com
    Property[ ucminappsharingport ] = 50000
    Property[ dlxinternalurl ] = https://tk5ucdfpl01.exchange.contoso.com:443/groupexpansion/service.svc
    Property[ ucmaxfiletransferport ] = 50038
    Property[ ucpc2pcavencryption ] = SupportEncryption
    Property[ abwqexternalurl ] = https://lslm84.meet.contoso.com:443/groupexpansion/service.svc
    Property[ abwqinternalurl ] = https://tk5ucdfpl01.exchange.contoso.com:443/groupexpansion/service.svc
    Property[ logginglevel ] = Medium
    Property[ abswebserviceenabled ] = true
    Property[ ucminsipdynamicport ] = 7100
    Property[ ucenableuserlogging ] = true
    Property[ callparkserveruri ] = sip:tk5ucdfpl01.exchange.contoso.com@contoso.com;gruu;opaque=srvr:Microsoft.Rtc.Applications.Cps:-6_tNOSJcFmTWxQQy8HPTAAA
    Property[ ucmaxvideorateallowed ] = Hd720p-1.5M
    Property[ absexternalserverurl ] = https://lslm84.meet.contoso.com:443/abs/handler
    Property[ dlxenabled ] = true
    Property[ ucportrangeenabled ] = true
    Property[ responsegroupserviceinternalagenturl ] = https://tk5ucdfpl01.exchange.contoso.com:443/RgsClients/Tab.aspx
    Property[ updatesserverexternalurl ] = https://lslm84.meet.contoso.com:443/RequestHandlerExt/ucdevice.upx
    Property[ ucmaxaudioport ] = 50038
    Property[ enablebwpolicycheck ] = true

## See also

#### Concepts

[Receiving in-band provisioning data](receiving-in-band-provisioning-data.md)

