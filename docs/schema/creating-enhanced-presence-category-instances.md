---
title: Creating Enhanced Presence category instances
TOCTitle: Creating Enhanced Presence category instances
ms:assetid: 98009fe0-7e47-419a-ac0b-03c0b2a6bc11
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454651(v=office.15)
ms:contentKeyID: 57092904
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Creating Enhanced Presence category instances


_**Applies to:** Lync 2013 | Lync Server 2013_

On the protocol level, a category instance is represented by an XML string. To publish the category instance, you set up the XML string so it is used with the specified containers on the server. For example, the following SIP message shows what is sent over the wire in a request of publication for a note category instance.

    SERVICE sip:adamb@contoso.com SIP/2.0
    FROM: <sip:adamb@contoso.com>;epid=6C801B691B;tag=127ef2ce7
    TO: <sip:adamb@contoso.com>;epid=6C801B691B
    CSEQ: 6 SERVICE
    CALL-ID: 3e66afc936ee4733b5ccf058dc3f3844
    MAX-FORWARDS: 70
    VIA: SIP/2.0/TLS 192.168.0.199:25849;branch=z9hG4bKf4bc868
    AUTHORIZATION: NTLM realm="SIP Communications Service",targetname="tuk-ocdr1-03.contoso.com",response="0100000000000000ba6552871eb3dd60",crand="fa6b06d4",cnum="9",opaque="5431637F",qop="auth"
    CONTACT: <sip:adamb@contoso.com;opaque=user:epid:gAXJXq9AgVCiWynxdwgUSwAA;gruu>;text;audio;video;image
    CONTENT-LENGTH: 482
    SUPPORTED: gruu-10
    USER-AGENT: RTCC/4.0.0.0 PresPub
    CONTENT-TYPE: application/msrtc-category-publish+xml
    <publish 
       xmlns="http://schemas.microsoft.com/2006/09/sip/rich-presence">
       <publications uri="sip:adamb@contoso.com">
          <publication categoryName="note" instance="1" 
              container="100" version="3" expireType="endpoint">
            <note xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                  xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
                  xmlns="http://schemas.microsoft.com/2006/09/sip/note">
               <body type="personal">Personal note set by myApp</body>
            </note>
          </publication>
       </publications>
    </publish>

Here, the \<publication\> element corresponds to the specified category instance to be published. The child element (the [note category instance value element](note-category-instance-value-element.md) element in this example) specifies the category data. You can manually create the XML string and include it in the SIP message payload. However, creating such an XML string by hand is tedious and error-prone.

On an API level, a category instance may be encapsulated by an API-specific type. In Microsoft Lync 2013 API, category instances are exposed only through API types, whereas in Microsoft Unified Communications Managed API 4.0, commonly used category instances are encapsulated by API types and their XML string representations are also supported.

In UCMA a generic category instance is represented by the PresenceCategoryWithMetaData type. With this class, the attributes (such as category name, instance ID, container ID, version number, expiry policy and expiration time, etc.) of a category instance are exposed by the appropriate properties. The value of the category instance is specified by an XML string. UCMA requires that instances of this class be used in grammar-free publications.

The following code example shows how to create category instances for grammar-free publications. It is a method of the UcmaPublisher class that is introduced in [Preparing for category publications](preparing-for-category-publications.md).

``` csharp
public PresenceCategoryWithMetaData CreatePresenceCategoryInstance(
      string name, long instanceId, int containerId, string xmlValue)
{
     PresenceCategoryWithMetaData categoryInstance = null;
     if (xmlValue == null)
     {
         categoryInstance = new PresenceCategoryWithMetaData(
                     name, instanceId, containerId);
     }
     else
     {
         CustomPresenceCategory categoryValue = 
                     new CustomPresenceCategory(name, xmlValue);
                
         categoryInstance = new PresenceCategoryWithMetaData(
                     instanceId, containerId, categoryValue);
     }
     return categoryInstance;
}
```

Calling the following statements create a personal note presence category instance that can be used for a grammar-free publication to Container 1000.

    string presenceNoteValue = 
             "<note xmlns:xsi=\"http://www.w3.org/2001/XMLSchema-instance\"" + 
             "      xmlns:xsd=\"http://www.w3.org/2001/XMLSchema\"" + 
             "      xmlns=\"http://schemas.microsoft.com/2006/09/sip/note\">" + 
             "  <body type=\"personal\" uri=\"\">Personal Note Value</body>" + 
             "</note>";
    
    PresenceCategoryWithMetaData pcm = CreatePresenceCategoryInstance(
                        "note", 0, 1000, presenceNoteValue);

An application can set other properties on the category instance. These include **ExpiryPolicy** and **Expires**. The **ExpiryPolicy** property describes how a published category instance expires. The choices are specified in fields enumerated in the **ExpiryPolicy** type. The default expiry policy is endpoint bound (**ExpiryPolicy.Endpoint**). With **ExpiryPolicy.Endpoint**, the published category instance expires when the endpoint from which the publication request is submitted is no longer connected to the server. You can change this policy to make the category instance static (**ExpiryPolicy.Persistent**), user-bound (**ExpiryPolicy.User**) or time-bound (**ExpiryPolicy.Time**). If **ExpiryPolicy.Time** is used, the **Expires** property is used to set the number of ticks as the duration in which the publication persists before it expires. Other properties, such as the **Version** number and publication time (**PublicationTime**), are set by the API.

In grammar-based publications, specifications of the instance ID, container ID, and expiry policies are dictated by the underlying publication grammar, and a category instance can then be specified using only the category name and data. In this case, a category instance is referred to by an instance of the abstract PresenceCategory class. UCMA requires that this type of category instances be supplied in grammar-based publications. You can create such category instances by instantiating the CustomPresenceCategory type with a category name and the corresponding XML string.

In Microsoft Unified Communications Managed API 4.0 instances of the [contactCard category instance value element](contactcard-category-instance-value-element.md), [note category instance value element](note-category-instance-value-element.md), [services category instance value element](services-category-instance-value-element.md) and [state category instance value elements](state-category-instance-value-elements.md) categories are further encapsulated by the more specific API classes of ContactCard, Note, Services and PresenceState. The following code example shows how to create such type-specific category instance in UCMA.

``` csharp
string _presenceNoteXml = null;

Note pNoteXml = new Note("Personal note set by UcmaPublisher");
presenceNote = pNote.GetCategoryDataXml();

PresenceState uState = new PresenceState(
               PresenceStateType.UserState, 4500, null);
presenceStateXml = uState.GetCategoryDataXml();
```

To create custom presence category instances or any other enhanced presence category instances, which are not encapsulated by any API types, hand-crafted XML string may be necessary. If the categories are schematized, you can use the XSD.EXE tool from .NET Framework to create Common Language Runtime (CLR) classes from the XML schemas, initialize the CLR objects by setting appropriate properties, and serialize the initialized CLR objects to produce the required XML strings that are guaranteed to be well-formed. For more information, see [Serialization of Enhanced Presence category instances](serialization-of-enhanced-presence-category-instances.md).

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

