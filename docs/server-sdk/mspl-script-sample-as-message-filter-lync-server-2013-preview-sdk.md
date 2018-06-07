---
title: MSPL Script Sample as Message Filter (Lync Server 2013 Preview SDK)
TOCTitle: MSPL Script Sample as Message Filter (Lync Server 2013 Preview SDK)
ms:assetid: 3c376523-4d91-41db-9c80-e842784b58d7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439065(v=office.15)
ms:contentKeyID: 57096221
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# MSPL Script Sample as Message Filter (Lync Server 2013 Preview SDK)

In Microsoft Lync Server 2013 SDK, use this MSPL script to filter incoming SIP responses and select a message endpoint.


**Applies to:** Lync 2013 | Lync Server 2013

## Filter incoming SIP responses

This Microsoft SIP Processing Language (MSPL) script example filters incoming SIP responses and attempts to select the best endpoint for each message based on the endpoint ID (EPID).

``` xml
<?xml version="1.0">
<lc:applicationManifest
 lc:appUri="http://www.contoso.com/DefaultRoutingScript"
 xmlns:lc="http://schemas.microsoft.com/lcs/2006/05">
<lc:requestFilter methodNames="INVITE,MESSAGE,INFO,REFER,ACK,BYE,OTHER"
                        strictRoute="false"
                        registrarGenerated="true"
                        domainSupported="true"/ >
<lc:responseFilter reasonCodes="NONE" />
<lc:proxyByDefault action="true" />
<lc:scriptOnly />
<lc:splScript><![CDATA[
    //
    // This script handles default routing of requests to Lync Server.  It
    // looks up all the registered endpoints for the To: user@host and tries
    // to pick the best endpoint to route based on:
    //  EPID
    //
    // Endpoints with no presence or an availability less than 100, or
    // no routing information (for example, set presence without
    // register) are not considered.
    //

    Log( "Debugr", 1, "we have a request - ", sipRequest.Method );

    //
    // Build the user@host from the To: header.
    //
    toUri = GetUri( sipRequest.To );
    toUserAtHost = Concatenate( GetUserName( toUri ), "@", GetHostName( toUri ) );

    //
    // Determine whether this request is already asking for a specific EPID
    // through a parameter in the To: header.
    //
    requestEPID = GetParameterValue( sipRequest.To, "EPID" );

    //
    // Now loop over all the endpoints for the To: user@host.
    //
    bestEPID = "";
    bestAgeOfPresence = 0x7FFFFFFF;
    bestAvailability = 0;
    bestActivity = 0;
    bestContactInfo = "";
    Log( "Debugr", 1, "EPID - ", requestEPID );
    Log( "Debugr", 1, "toUserAtHost - ", toUserAtHost );
    foreach (dbEndpoint in QueryEndpoints( toUserAtHost, true )) {
        Log( "Debugr", 1, "    endpoint.EPID - ", dbEndpoint.EPID );
        Log( "Debugr", 1, "    endpoint.ContactInfo - ", dbEndpoint.ContactInfo );

        //
        // First, determine whether this endpoint supports the method in the request.
        //
        if (!SupportsMethod( sipRequest.Method, dbEndpoint.StandardMethods, dbEndpoint.ExtraMethods )) {
            //
            // Skip this endpoint because it cannot handle the method on this request.
            //
            Log( "Debugr", 1, "        * skipped because of method" );
            continue;
            }

        if (requestEPID != "") {
            if (requestEPID == dbEndpoint.EPID) {
                //
                // The request is already targeted at a specific EPID that can handle the method,
                // so use this endpoint.
                //
                Log( "Debugr", 1, "        * matched EPID" );
                bestContactInfo = dbEndpoint.ContactInfo;
                break;
            }
            else {
                //
                // The request is targeted at a specific EPID, but does not match this endpoint.
                // Skip this endpoint.
                //
                Log( "Debugr", 1, "        * skipped because of EPID" );
                continue;
            }
        }

        bestEPID = dbEndpoint.EPID;
        bestContactInfo = dbEndpoint.ContactInfo;
        Log( "Debugr", 1, "        *** new best contact" );
        }

    //
    // See if an endpoint to proxy to was found.
    //
    if (bestContactInfo == "") {
        /* Uncomment this block of code and the two previous assignments to sawAtLeastOneEndpoint
           if you want to run a UAC application before this one and have this code
           route your messages to the correct home server.
        if (!sawAtLeastOneEndpoint) {
            homeServer = QueryHomeServer( toUserAtHost );
            if (!EqualString( homeServer, FQDN, true )) {
                Log( "Debugr", 1, toUserAtHost, " is homed on ", homeServer );
                newRequestUri = Concatenate( sipRequest.RequestUri, ";maddr=", homeServer );
                Log( "Debugr", 1, "Request is being routed to ", newRequestUri );
                AddHeader( "MS-LBVIA", FQDN );
                ProxyRequest( newRequestUri );
                return;
            }
        }
        */
        Log( "Debugr", 1, "Responding 480 - temporarily unavailable as no suitable endpoint found" );
        Respond( 480, "Temporarily Unavailable" );
    }
    else {
        if (requestEPID == "") {
            Log( "Debugr", 1, "Adding missing EPID '", bestEPID, "' to To header" );
            SetParameterValue( "To", "epid", bestEPID );
            }

        Log( "Debugr", 1, "Proxying request to - ", bestContactInfo );
        ProxyRequest( bestContactInfo );
        }

    return;
]]></lc:splScript>
</lc:applicationManifest>
```


> [!NOTE]
> <P>If the following RequestUri pattern is used, the request is marked as routed without providing a request target. Applications that do not have routing information for a request should not modify request-uri.</P>
> <P>request.RequestUri = ...</P>
> <P>ProxyRequest(sipRequestUri)</P>



## See also

#### Concepts

[Microsoft SIP Processing language Script (Lync Server 2013 Preview SDK)](microsoft-sip-processing-language-script-lync-server-2013-preview-sdk.md)

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

