---
title: Call admission control usage scenarios
TOCTitle: Call admission control usage scenarios
ms:assetid: fa499ce2-b28a-4b66-8e37-f8ce0fd8961e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn466097(v=office.15)
ms:contentKeyID: 57103270
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Call admission control usage scenarios


**Applies to:** Lync 2013 | Lync Server 2013

Bandwidth management can be applied in a number of scenarios. The following list presents several of the scenarios that occur most often.

### Basic success

John in Spokane places a Microsoft Lync 2013 audio call to his company’s general information line, an interactive voice-response (IVR) application. The WAN link is free, so John’s call proceeds as normal, after checking with the Policy Distribution Point. The call is established and audio flows between John’s endpoint and the IVR.

### Basic failure

John in Spokane places a Lync 2013 call to his company’s general information line, an IVR. The WAN link is overburdened, and John’s call cannot be redirected to PSTN, so it fails. John is informed that the call has failed due to the Call Admission Control’s failure to provision the WAN link. John’s network administrator, Bob, is able to determine that this failure occurs frequently. To provide better network management, Bob purchases a larger link. Additionally, the application is informed of the failure, and the reason (CAC failure).

### Redirect to PSTN

Gordon is on Lync Web App from the Zurich Office. He calls in to an audio-only conference hosted in Redmond. The WAN link from Zurich to Redmond is slightly overburdened, so Gordon’s session with the conference is redirected to PSTN through the Zurich Branch Office Appliance. The call completes successfully, and Gordon listens to the conference. (The user interface informs Gordon that he has been redirected, in a manner similar to that of the Lync 2013 user interface.)

