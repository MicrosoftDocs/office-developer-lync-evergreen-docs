---
title: Reference topology with limited high availability
TOCTitle: Reference topology with limited high availability
ms:assetid: a75b53a5-4951-4a2e-b261-55b1a4bf891b
ms:mtpsurl: https://msdn.microsoft.com/library/Dn465969(v=office.15)
ms:contentKeyID: 57102544
ms.date: 07/25/2014
mtps_version: v=office.15
---

# Reference topology with limited high availability


**Applies to:** Lync 2013 | Lync Server 2013

The reference topology with limited high availability is for an organization that wants to deploy Microsoft Lync Server 2013 communications software functionality at a minimum cost. Typically, the specific topology shown in the following diagram is recommended for organizations with 5,000 or fewer users, although you can support additional users by adding additional Standard Edition servers.

Reference topology with limited high availability

  
![SORG reference](images/Dn465969.SORG(Office.15).jpg "SORG reference")

  - **Active Directory deployment**   All Lync Server 2013 deployments reside in a single Active Directory forest. For this topology, the customer has Lync Server 2013 deployed in the child domain, retail.contoso.com.

  - **Voice pilot**   The organization using the exact topology shown in this diagram is currently running a pilot program of the Enterprise Voice feature of Lync Server 2013. Some users are using Lync Server 2013 as their sole voice solution.
    
    If they go on to fully deploy Enterprise Voice and remove the PBX system, they should provide high availability for their voice solution by deploying a second Standard Edition server or moving to a Front End pool. A single Standard Edition topology as shown in this diagram is recommended only if you're not deploying Enterprise Voice in a production environment. Because being able to make calls is mission critical for almost every organization, you should provide high availability if you use Enterprise Voice as your telephone solution.

  - **Additional Standard Edition servers can be added**   A single Standard Edition server can support up to 5,000 users. If you want to accommodate more users or provide some high availability capability for Enterprise Voice (at a minimum cost), you could add another Standard Edition server to this topology.
    
    For a true high availability solution, you should deploy Enterprise Edition and deploy a Front End pool. Although having multiple Standard Edition servers would maintain Enterprise Voice functionality should one of these servers go down, a Front End pool provides much better continuity of service for other Lync Server 2013 features.

  - **Branch site survivability**   This organization is running the Enterprise Voice pilot with some branch site users as well. The branch office does not have a reliable wide area network (WAN) link to the central site, so a Survivable Branch Appliance is deployed there. With this deployed, if the WAN link goes down users at the branch site can still make and receive calls.

  - **Edge Server recommended**   Although deploying an Edge Server is not required for internal instant messaging (IM), presence and conferencing, it's recommended for small deployments or when external or federated access is required. You can maximize your Lync Server 2013 investment by deploying an Edge Server to provide service to users currently outside your organization’s firewalls. The benefits include the following:
    
      - Your organization’s own users can use Lync Server 2013 functionality, if they are working from home or are out on the road.
    
      - Your users can invite outside users to participate in meetings.
    
      - If you have a partner, vendor or customer organization that also uses Lync Server 2013, you can form a federated relationship with that organization. Your Lync Server 2013 deployment would then recognize users from that federated organization, leading to better collaboration.
    
      - Your users can exchange instant messages with users of public IM services, including any or all of the following: Windows Live, AOL, and Yahoo\!, as well as XMPP-based providers and servers, such as Google Talk and Jabber. A separate license might be required for public IM connectivity with Windows Live, AOL, and Yahoo\!


> [!NOTE]
> <P>In Lync Server 2013, UCMA applications should never be homed on the branch office appliance. Instead, they should be connected directly to the Lync Server 2013 Front End computer or Front End pool.</P>


