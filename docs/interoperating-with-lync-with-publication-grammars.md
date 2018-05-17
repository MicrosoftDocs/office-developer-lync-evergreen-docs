---
title: Interoperating with Lync with publication grammars
TOCTitle: Interoperating with Lync with publication grammars
ms:assetid: 2f3cfcf4-2aa3-44c8-8ca7-9413f13e040b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454681(v=office.15)
ms:contentKeyID: 57093215
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Interoperating with Lync with publication grammars


_**Applies to:** Lync 2013 | Lync Server 2013_

To interoperate with Microsoft Lync 2013, an enhanced presence application must follow the publication grammars defined by Lync 2013. This involves obtaining an XML document of the publication grammar, determining the rules, and implementing the logic.

## Receiving publication grammars

At the SIP level, receiving the publication grammars set by a server administrator involves submitting a SUBSCRIBE request, specifying publictationGrammar as the name of one of the provisionGroups elements. The result is returned in a SIP response of 200 OK. For details about the SIP messages used, see [Receiving in-band provisioning data](receiving-in-band-provisioning-data.md).

By default there are two publication grammars: one for the open-mode presence publication and the other the privacy-mode publication. The open-mode publication grammar is specified by a container manifest and a category publication manifest. The privacy-mode publication grammar contains only a container manifest.

A container manifest is described by an XML element of \<[containerManifestList element](containermanifestlist-element.md)\>. It has the following high-level structure.

``` xml
<provisionGroup name="publicationGrammar">
   <containerManifestList>
      <containerManifest>
         <containers>...</containers>
         <members>...</members>
         <blockRules>...</blockRules>
         <rolePrecedence>...</rolePrecedence>
      </containerManifest>
   </containerManifestList>
</provisionGroup>
```

The [containers element](containers-element.md) element declares what containers should be used for remote presence publications. The [members element](members-element.md) element stipulates the access control entries for specified containers and how they should be assigned to the containers. The [blockRules element](blockrules-element.md) element describes the types and sources of blocking operations. Finally, the [rolePrecedence element](roleprecedence-element.md) element specifies the conflict resolution when a user taking multiple roles is added to a container.

A category publication manifest is described by [categoryPublicationManifest element](categorypublicationmanifest-element.md) and it has the following high-level structure.

``` xml
<categoryPublicationManifest>
   <publicationList>
      <publicationRule>...</publicationRule>

      <!-- more publicationRule element -->
      ......
   </publicationList>
</categoryPublicationManifest>
```

A category publication manifest is a list of publication rules, each being described by a [publicationRule element](publicationrule-element.md) element. A publication rule stipulates that a given type of category should be placed into a specified container in a publication request. Additionally, instance ID, expiration type and a category data value can also be specified for a particular publication. The specification of the category data value is typically generated from the enclosed XSLT routine.

In Microsoft Unified Communications Managed API 4.0, only the publication grammar compatible with the currently enabled privacy policy is exposed. An application can obtain this grammar by reading the ContainerManifest or CategoryPublicationManifest property on a LocalOwnerPresence object.

## Enforce Lync 2013-compatible presence publications for remote watchers

To make a presence application interoperable with Lync 2013, the client must enforce the Lync 2013-compatible publication grammars for presence publications. Enforcing the publication grammars involves the following tasks, after obtaining the publication grammar appropriate for the presence privacy policy:

  - Enumerate the grammar-specified containers for remote presence watchers. These include Containers 0, 100, 200, 300, 400 and 32000.

  - Assign members to the containers according to specification of the publication grammar. The expected behavior is discussed in [Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md).

  - Publish a given category data following the applicable publication rules as specified in the grammar. The expected behavior is discussed in [Presence category instances published or used by Lync](presence-category-instances-published-or-used-by-lync.md).
    
    To help illustrate this point, let us look an example of publishing the following [note category instance value element](note-category-instance-value-element.md) category instance, created after a user has set a personal note message.
    
        <nt:note xmlns:nt="http://schemas.microsoft.com/2006/09/sip/note">
           <nt:body type="personal">I'm away today.</nt:body>
        </nt:note>
    
    To have this note published in the Lync 2013-compatible way, an application should apply the following publication rules.
    
    ``` 
        <publicationRule ruleType="transformation" categoryName="note" containerId="100">
          <categoryData>
            <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 
                 version="1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
                 xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" 
                 xmlns:tns="http://schemas.microsoft.com/2006/09/sip/note" 
                 exclude-result-prefixes="tns ct"> 
              <xsl:output method="xml" encoding="utf-8" indent="yes"/> 
              <xsl:strip-space elements="*"/> 
              <xsl:template match="node()"> 
                <xsl:apply-templates select="//tns:note"/> 
              </xsl:template> 
              <xsl:template match="tns:note"> 
                <xsl:copy /> 
              </xsl:template> 
            </xsl:stylesheet>
          </categoryData> 
        </publicationRule>
        <publicationRule ruleType="transformation" categoryName="note" containerId="200" /> 
        <publicationRule ruleType="transformation" categoryName="note" containerId="300" /> 
        <publicationRule ruleType="transformation" categoryName="note" containerId="400" preferredSelfConsumption="true" /> 
        <publicationRule ruleType="transformation" categoryName="note" containerId="32000">
          <categoryData>
            <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" 
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
                xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes" 
                xmlns:tns="http://schemas.microsoft.com/2006/09/sip/note" 
                exclude-result-prefixes="tns ct"> 
              <xsl:output method="xml" encoding="utf-8" indent="yes"/> 
              <xsl:strip-space elements="*"/> 
              <xsl:template match="node()"> 
                <xsl:apply-templates select="//tns:note"/> 
              </xsl:template> 
              <xsl:template match="tns:note"> 
                <xsl:copy /> 
              </xsl:template> 
            </xsl:stylesheet>
          </categoryData> 
        </publicationRule>
    ```
    
    According to this grammar, there are five rules to be applied to Containers 100, 200, 300, 400, and 32000, respectively. To Containers 200, 300, and 400, the [note category instance value element](note-category-instance-value-element.md) category instance should be published as is. For Containers 100 and 32000, the enclosed XSLT routine modifies the original note category instance to produce an empty note category instance.

In Microsoft Unified Communications Managed API 4.0, this grammar-based publication is supported by calling the BeginPublishPresence/EndPublishPresence while encapsulating the note message in a CustomPresenceCategory instance. For more information, see [Publishing Enhanced Presence](publishing-enhanced-presence.md). In Microsoft Lync 2013 SDK, grammar-based presence publication is automatically enforced.

## See also

#### Concepts

[Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)

