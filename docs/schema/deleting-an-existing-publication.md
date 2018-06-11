---
title: Deleting an existing publication
TOCTitle: Deleting an existing publication
ms:assetid: d5517dea-b7e1-472d-ae06-4d1a5f8c9dc6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454649(v=office.15)
ms:contentKeyID: 57092899
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Deleting an existing publication


**Applies to:** Lync 2013 | Lync Server 2013

On the protocol level, removing a published category instance from a publication is equal to republishing the category instance as a time-bound instance with the expiration time set to zero. The following example is a SIP message sent to the server when a SERVICE request to delete the publication of a [note category instance value element](note-category-instance-value-element.md) category instance is submitted.

    SERVICE sip:adamb@contoso.com SIP/2.0
    FROM: <sip:adamb@contoso.com>;epid=6C801B691B;tag=ff76c3f124
    TO: <sip:adamb@contoso.com>;epid=6C801B691B
    CSEQ: 7 SERVICE
    CALL-ID: 68f271a55a574ac197afccabe755d56b
    MAX-FORWARDS: 70
    VIA: SIP/2.0/TLS 192.168.0.199:25849;branch=z9hG4bKb2809a28
    AUTHORIZATION: NTLM realm="SIP Communications Service",targetname="tuk-ocdr1-03.contoso.com",response="0100000000000000815295211eb3dd60",crand="f99070ee",cnum="11",opaque="5431637F",qop="auth"
    CONTACT: <sip:adamb@contoso.com;opaque=user:epid:gAXJXq9AgVCiWynxdwgUSwAA;gruu>;text;audio;video;image
    CONTENT-LENGTH: 249
    SUPPORTED: gruu-10
    USER-AGENT: RTCC/4.0.0.0 PresPub
    CONTENT-TYPE: application/msrtc-category-publish+xml
    <publish xmlns="http://schemas.microsoft.com/2006/09/sip/rich-presence">
       <publications uri="sip:adamb@contoso.com">
          <publication categoryName="note" instance="1" container="100" version="0" expireType="time" expires="0" />
       </publications>
    </publish>

As with presence publications, removing a category instance from a publication can also be grammar-based or grammar-free. The SIP request in the previous example originates from a grammar-free deletion of the publication.

On the API level, presence deletion can be exposed in a set of methods that are dedicated to this particular kind of operation. In the following example, the deletion is implemented as the asynchronous programming pattern of BeginDeletePresence/EndDeletePresence in UCMA. For grammar-free presence deletion, the BeginDeletePresence takes a collection of PresenceCategory objects in its input. For grammar-based presence deletion, the BeginDeletePresence method takes a collection of PresenceCategoryWithMetaData object in its input.

```csharp
        public void RequestGrammarBasedPresencePublicationRemoval(string categoryName)
        {
            CustomPresenceCategory category = new CustomPresenceCategory(categoryName, string.Empty /* null */);
            PresenceCategory[] categories = new PresenceCategory[] { category };
            _localPresence.BeginDeletePresence(categories, CallbackOnDeletePresenceReturned, _localPresence);
        }

        public void RequestGrammarFreePresencePublicationRemoval(string catName, long instanceId, int containerId)
        {
            PresenceCategoryWithMetaData[] categories = new PresenceCategoryWithMetaData[] {
                new PresenceCategoryWithMetaData(catName, instanceId, containerId) };
            _localPresence.BeginDeletePresence(categories, CallbackOnDeletePresenceReturned, _localPresence);
        }

        void CallbackOnDeletePresenceReturned(IAsyncResult result)
        {
            try
            {
                if (_localPresence == result.AsyncState as LocalOwnerPresence)
                {
                    _localPresence.EndDeletePresence(result);

                    if (OnDeletePresenceCompleted != null)
                        RaiseEvent(OnDeletePresenceCompleted, this,
                            new AsyncOpStatusEventArgs(AsyncOpStatus.OK, null));

                }
            }
            catch (Exception ex)
            {
                if (OnDeletePresenceCompleted != null)
                    RaiseEvent(OnDeletePresenceCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
            }
        }
```

In addition to calling BeginDeletePresence/EndDeletePresence, you can use UCMA to implement the presence deletion as a publication of time-bound category instances with the expiration time set to zero. The following example shows this process.

``` 
        public void RequestGrammarFreePresencePublicationToDeletePresenceCategory(string catName, long instanceId, int containerId)
        {           
            PresenceCategoryWithMetaData pcm = new PresenceCategoryWithMetaData(catName, instanceId, containerId);
            pcm.ExpiryPolicy = ExpiryPolicy.Time;
            pcm.Expires = 0;
            this.RequestGrammarFreePresencePublication(new PresenceCategoryWithMetaData[] { pcm });
        }
```

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

