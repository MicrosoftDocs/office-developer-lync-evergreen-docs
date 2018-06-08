---
title: Lync endpoint types
TOCTitle: Lync endpoint types
ms:assetid: fa01986d-7b7c-4f8c-a64c-24811e8b48e8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn345988(v=office.15)
ms:contentKeyID: 56253172
ms.date: 02/11/2016
mtps_version: v=office.15
---

# Lync endpoint types

Learn about writing a Microsoft Lync 2013 SDK enabled application that uses side-by-side Microsoft Lync 2013 endpoints to sign in to Lync with a unique set of user credentials for each endpoint.

**Last modified:** December 07, 2015

***Applies to:** Lync 2013 | Lync Server 2013*

## Lync endpoints

A user can sign in to Lync from one or two endpoints on a computer at the same time. Each endpoint can accept a different set of user credentials. The endpoint type that you use depends on the usage scenario that you are enabling through your code. When two endpoints are being used, one of the endpoints is the Lync 2013 client and the other endpoint is the side-by-side endpoint encapsulated by your custom application. The Lync 2013 endpoint types that you can use include the following:

  - The client endpoint

  - The UI suppressed side-by-side endpoint.

The following sections describe how these endpoint types enable typical Lync 2013 usage scenarios.

### The client endpoint

Use the client endpoint if you are creating conversation window or chat window extensions, adding Lync features to your line-of-business application. In these scenarios, a user signs in to the Lync client endpoint and your application acts as a user agent for that user under her credentials.

The client endpoint singleton is initialized when the Lync 2013 client is started. This endpoint supports the client and any custom applications that use the client endpoint. The client endpoint accepts one set of user credentials and all custom applications that use the client endpoint act as a user agent for the person whose credentials are used to sign in to Lync. If UI suppression is enabled, the client endpoint can only be accessed by an Lync 2013 API-enabled application.

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
<td><p>UI suppression settings apply only to the Lync 2013 client endpoint. If you disable UI suppression by setting the value of <strong>HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\UISuppressionMode</strong> to 0, there is no effect on the behavior of side-by-side endpoints.</p></td>
</tr>
</tbody>
</table>

### The Side-by-side endpoint

A Lync 2013 platform background process hosts the side-by-side endpoint which is accessed through the Lync 2013 API. You can start up a side-by-side endpoint and use it to sign a user in with different credentials than used with the client endpoint. A single Lync 2013 API-enabled application process can't host more than one Lync endpoint of either type. Calling the **GetClient** method again within an application process returns the originally created endpoint.

The side-by-side endpoint is always initialized in UI suppression mode, regardless of how UI suppression is configured in the computer registry. After you initialize it, use it to sign a user in and then it provides all the Lync features of the client endpoint. The side-by-side endpoint runs in its own process and has no dependencies on the client endpoint. It doesn’t matter if the client endpoint is in UI suppression or not, the side-by-side endpoint is always treated as a UI suppressed endpoint.

A side-by-side endpoint has access to all of the resources of a Lync endpoint. This means that your side-by-side endpoint application can get contact lists, publish presence, and start conversations with all modalities available to a stand-alone Lync endpoint. The side-by-side application is the user-agent for the person whose credentials are used to sign in to the side-by-side endpoint.

If audio/video conversations are to be hosted on the side-by-side endpoint and on the stand-alone Lync endpoint, an audio/video USB device such as a headset must be provided for each endpoint. You can programmatically assign an individual USB device to your side-by-side application before it starts or accepting an audio/video conversation.

### Side-by-side application scenarios

Side-by-side endpoint scenarios include both development testing and live customer use scenarios.

#### Application development testing

Having a second endpoint on a computer lets you test your Lync 2013 API code without signing in to Lync on a second computer. With only one endpoint per computer, you needed to sign in to two computers to test communication logic in a two-person conversation. If only one computer is available to you and that computer does not support Hyper-V or another virtual machine technology, you needed to find another person willing to participate in Lync conversations. With side-by-side endpoints, sign in to the Lync client by using a set of credentials, and your custom side-by-side endpoint powered application together with other credentials. You can publish a user’s presence in the client and step through API code in your custom client as it reacts to the publication event.

You should not use the multiple endpoint feature to test applications which use Lync 2013 audio/video modalities. Audio/video streaming from an endpoint on computer to another endpoint on the same computer is not supported.

#### Real-world two endpoint applications

Are two endpoint scenarios useful in live customer scenarios? A help desk technician that has two sets of credentials can sign in to Lync to take support calls with one set and communicate coworkers with the other set. Help desk credentials are usually aliased so that the identity of the technician is shielded from the caller. A help desk application is a good place to use the side-by-side endpoint to add a limited set of communication features suited for support calls. At the same time, the technician should have full communication features for interacting with coworkers. For this, the technician signs in to the Lync client by using her own credentials. She signs in to the help desk application with aliased credentials and Lync with her own credentials.

## See also

  - [Core concepts: Lync 2013 SDK](core-concepts-lync-2013-sdk.md)

  - [How to: Create a side-by-side endpoint in Lync SDK](how-to-create-a-side-by-side-endpoint-in-lync-sdk.md)

