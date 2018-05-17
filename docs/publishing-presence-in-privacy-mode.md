---
title: Publishing presence in privacy mode
TOCTitle: Publishing presence in privacy mode
ms:assetid: 1f074e2b-002b-4846-8e79-2fe657be9f56
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454677(v=office.15)
ms:contentKeyID: 57093155
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Publishing presence in privacy mode


_**Applies to:** Lync 2013 | Lync Server 2013_

When presence is published in the privacy mode, only the allowed contacts can see the publisher’s presence information. The application must explicitly add the contacts to a container and the contact list. Microsoft Lync 2013 and Microsoft Unified Communications Managed API 4.0 implement this automatically.

The administrator of Microsoft Lync Server 2013 sets a pool-level presence policy to enable the privacy-mode presence publication A client can receive this policy document through in-band provisioning. The document corresponds to an XML element of \<provisionGroup name=”presencePolicyV2”\>.

## Presence policy for privacy-mode publications

The following is a privacy-mode presence policy document set by a server administrator.

``` xml
<provisionGroup name="presencePolicyV2"> 
   <propertyEntryList> 
      <property name="EnablePrivacyMode">true</property> 
      <property name="EnableLocationPrompt">false</property> 
      <property name="AutoInitiateContacts">false</property> 
      <property name="PublishLocationDataDefault">false</property> 
      <property name="DisplayPublishedPhotoDefault">false</property> 
      <property name="PersonalNoteHistoryDepth">0</property> 
   </propertyEntryList> 
</provisionGroup>
```

After receiving the presence privacy policy, the client should enable the privacy mode publication by consulting with and adhering to the privacy-mode publication grammar that is also returned in the in-band provisioning process.

## Privacy-mode publication grammar

The privacy-mode publication grammar is described by an XML element of \<provisionGroup name="privavcyPublicationGrammar"\>. It contains one \<containerManfiest\> element stipulating what containers may be used and how the access control entries may be added to each of the supported containers. It does not contain any \<categoryPublicationManfiest\> element that specifies the rules about how specified category instances be published. In the privacy-mode publication no presence data is published by default and any publication is use-specified.

The following XML fragment is the privacy mode publication grammar defined by Lync 2013.

``` xml
  <provisionGroup name="privacyPublicationGrammar" >
    <containerManifestList   
        xmlns="http://schemas.microsoft.com/2008/09/sip/ContainerManifest"
        xmlns:ct="http://schemas.microsoft.com/2006/09/sip/commontypes"
        minSupportedClientVersion="2.0.0.0">
      <containerManifest>
        <containers>
          <container id="0">
            <visible>false</visible>
            <avoidRedundantMembers>false</avoidRedundantMembers>
          </container>
          <container id="100">
            <visible>true</visible>
            <avoidRedundantMembers>true</avoidRedundantMembers>
          </container>
          <container id="200">
            <visible>true</visible>
            <avoidRedundantMembers>true</avoidRedundantMembers>
          </container>
          <container id="300">
            <visible>true</visible>
            <avoidRedundantMembers>true</avoidRedundantMembers>
          </container>
          <container id="400">
            <visible>true</visible>
            <avoidRedundantMembers>true</avoidRedundantMembers>
          </container>
          <container id="32000">
            <visible>true</visible>
            <avoidRedundantMembers>false</avoidRedundantMembers>
            <blocked>true</blocked>
          </container>
        </containers>
        <members>
          <member role="buddy">
            <allowedContainers type="visibleContainers"/>
            <defaultContainer id="100"/>
            <occurrenceConstraint type="one"/>
            <ct:delimiter/>
            <sourceNetworks>
              <sourceNetwork type="publicCloud"/>
              <sourceNetwork type="federated"/>
            </sourceNetworks>
            <resolutionRules>
              <resolutionRule type="moveToDefaultContainer"/>
            </resolutionRules>
            <ct:end/>
          </member>
          <member role="buddy">
            <allowedContainers type="visibleContainers"/>
            <defaultContainer id="200"/>
            <occurrenceConstraint type="one"/>
            <ct:delimiter/>
            <sourceNetworks>
              <sourceNetwork type="sameEnterprise"/>
            </sourceNetworks>
            <resolutionRules>
              <resolutionRule type="moveToDefaultContainer"/>
            </resolutionRules>
            <ct:end/>
          </member>
          <member type="domain">
            <allowedContainers type="custom">
              <container id="32000"/>
            </allowedContainers>
            <ct:delimiter/>
            <resolutionRules>
              <resolutionRule type="removeFromContainer"/>
            </resolutionRules>
            <ct:end/>
          </member>
          <member type="user">
            <allowedContainers type="custom">
              <container id="32000"/>
            </allowedContainers>
            <ct:delimiter/>
            <resolutionRules>
              <resolutionRule type="forceRole" role="buddy"/>
            </resolutionRules>
            <ct:end/>
          </member>
          <member type="sameEnterprise">
            <allowedContainers type="custom">
              <container id="32000"/>
            </allowedContainers>
            <occurrenceConstraint type="zeroOrOne"/>
            <ct:delimiter/>
            <resolutionRules>
              <resolutionRule type="removeFromContainer"/>
            </resolutionRules>
            <ct:end/>
          </member>
          <member type="federated">
            <allowedContainers type="custom">
              <container id="32000"/>
            </allowedContainers>
            <occurrenceConstraint type="zeroOrOne"/>
            <ct:delimiter/>
            <resolutionRules>
              <resolutionRule type="removeFromContainer"/>
            </resolutionRules>
            <ct:end/>
          </member>
          <member type="publicCloud">
            <allowedContainers type="custom">
              <container id="32000"/>
            </allowedContainers>
            <occurrenceConstraint type="zeroOrOne"/>
            <ct:delimiter/>
            <resolutionRules>
              <resolutionRule type="removeFromContainer"/>
            </resolutionRules>
            <ct:end/>
          </member>
          <member role="delegate">
            <allowedContainers type="custom">
              <container id="300"/>
            </allowedContainers>
            <defaultContainer id="300"/>
            <occurrenceConstraint type="one"/>
            <ct:delimiter/>
            <resolutionRules>
              <resolutionRule type="moveToDefaultContainer"/>
            </resolutionRules>
            <ct:end/>
          </member>
        </members>
        <ct:delimiter/>
        <blockRules>
          <blockRule type="invites">
            <containers type="custom">
              <container id="0"/>
            </containers>
            <sourceNetworks>
              <sourceNetwork type="publicCloud"/>
            </sourceNetworks>
          </blockRule>
          <blockRule type="invites">
            <maxAvailability>11999</maxAvailability>
            <minAvailability>9000</minAvailability>
          </blockRule>
          <blockRule type="invites">
            <containers type="custom">
              <container id="32000"/>
             </containers>
           </blockRule>
           <blockRule type="subscriberPrompt">
             <containers type="custom">
               <container id="32000"/>
             </containers>
           </blockRule>
         </blockRules>
         <rolePrecedence>
           <rolePrecedenceEntry type="delegate"/>
           <rolePrecedenceEntry type="buddy"/>
         </rolePrecedence>
         <ct:end/>
       </containerManifest>
     </containerManifestList>
 </provisionGroup>
```

This Lync 2013-defined privacy-mode publication grammar document consists of four types of rules that specify the containers used to hold publications. The rules include what containers may be used, what members the containers may have, what constraints are imposed for container members, and how any conflict in membership assignment should be resolved. These rules are expressed by the \<containers\>, \<members\>, \<blockRules\> and \<rolePrecedence\> elements. Together, they stipulate the following:

  - Containers 0, 100, 200, 300, 400, and 32000 can be used.
    
      - Container 0 is invisible and can have duplicated member specifications. (An example of duplicated membership is a container that has both a domain member and a user member of the same domain.) This container does not have any membership specified.
    
      - Container 100 is visible, but cannot have redundant membership specification. This is the default container for public or federated network users who can be assigned to this container as a contact (i.e., the members are of a buddy role.
    
      - Container 200 is visible, but cannot have redundant membership. This is the default container for the same enterprise network users who can be assigned to this container as a contact.
    
      - Container 300 is visible, but cannot have redundant membership. This is the default container for users who can be assigned to this container as a delegate (i.e., a member of the delegate role.)
    
      - Container 400 is visible, but cannot have redundant membership. The container does not have any default membership specification.
    
      - Container 32000 is visible and can have redundant membership. This container is to serve as the blocked container and the attached blockrules element specifies what should be blocked. The container can take members of the domain, user, sameEnterprise, federated or publicCloud type.

  - If a membership assignment results in conflicts with an existing assignment or violates the membership occurrence constraint, they should be resolved according the specified resolution rules, which are summarized as follows:
    
      - If a public or federated network user is assigned to multiple containers, he or she should be moved to the designated default container, which is Container 100.
    
      - If an enterprise network user is assigned to multiple containers, he or she should be moved to the default container, which is Container 200.
    
      - If a member of the delegate role is assigned to multiple containers or is not assigned to the default container, he or she should be moved to the default container, which is Container 300.
    
      - If a member of the domain, sameEnterprise, federated or publicCloud type is added to Container 32000 and another container, remove this member from the blocked container. If a user is added to the blocked container as a delegate, switch his or her role to that of buddy. .

  - The blocking semantics is defined by the \<blockRules\> element. They are summarized as follows:
    
      - Inbound calls from the public cloud members of Container 0 should be blocked.
    
      - Inbound calls and subscriber prompts by members of Container 32000 should be blocked.
    
      - Inbound calls should be blocked when the container owner’s availability value falls between 9000 and 11999. This availability value range indicates that the container owner is in the Do Not Disturb state.

  - When a member is assigned to multiple roles, the delegate role should take the precedence over the buddy role, unless it is specified otherwise.

## See also

#### Concepts

[Publication grammar, privacy, and interoperability](publication-grammar-privacy-and-interoperability.md)

