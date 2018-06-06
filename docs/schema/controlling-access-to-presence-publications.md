---
title: Controlling access to presence publications
TOCTitle: Controlling access to presence publications
ms:assetid: 57f50085-572a-4cd5-9b74-7fbfd3e54b41
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454613(v=office.15)
ms:contentKeyID: 57093107
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Controlling access to presence publications


_**Applies to:** Lync 2013 | Lync Server 2013_

**In this article**  
Predefined container  
Custom containers  
Container membership types  

Enhanced Presence containers play an important role in controlling how to make presence available to presence watchers. A container is a place on the server for a presence publisher to drop publishable presence category instances. The server ensures that the newly published category instances are dispatched to registered presence subscribers or to the allowed presence watchers who have submitted a query request.

Containers determine how users view certain data published by the owner of the container. A container holds a pair of lists. One list specifies a set of category instances containing presence data and the other list is a group of users, including one or more classes of users, who can access the specified presence data. A user who is not a member of the container will not get the data contained in that container, except for a blocked container in which the container members receives empty instances of explicitly blocked categories.

A container is identified by a container ID and is created by the server when an unknown container ID is specified by a publishing client. The value of the container ID ranges from 0 to 32767, inclusively. A container can be visible or invisible and it can be blocked or unblocked.

Each container represents a specific type of access control. The logic of the access control inherent in a container, also known as the container semantics, is specified by an application, not by the server. The exception is Container 0. The access control list of this container is fixed and cannot be changed by any client.

## Predefined container

A Microsoft Lync Server 2013 deployment comes with a set of predefined containers. They are used by Microsoft Lync 2013 for publishing enhanced presence data. The default container semantics are defined by Lync 2013 and supported by the server. The following table lists such predefined containers.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Container type</p></th>
<th><p>Container ID</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Default</p></td>
<td><p>0</p></td>
</tr>
<tr class="even">
<td><p>Self</p></td>
<td><p>1</p></td>
</tr>
<tr class="odd">
<td><p>Aggregation</p></td>
<td><p>2 and 3</p></td>
</tr>
<tr class="even">
<td><p>External Contacts</p></td>
<td><p>100</p></td>
</tr>
<tr class="odd">
<td><p>Colleagues</p></td>
<td><p>200</p></td>
</tr>
<tr class="even">
<td><p>Workgroup</p></td>
<td><p>300</p></td>
</tr>
<tr class="odd">
<td><p>Friends and Family</p></td>
<td><p>400</p></td>
</tr>
<tr class="even">
<td><p>Blocked Contacts</p></td>
<td><p>32000</p></td>
</tr>
</tbody>
</table>


The Default container includes in its membership anyone who is not a member of any other containers. It is mainly used for publishing the identity of a presence publisher. The purpose is to make the publishing user discoverable by any other users. The user identity information is provisioned by the server from the underlying Active Directory domain service and the data is read-only. A client cannot modify the server-provisioned identity data in this container. The client cannot alter the membership scope of the default container, either.

The Self container can store any information for use by the local instance of Lync 2013. Useful content includes roaming data for establishing and maintaining communication sessions. The information can include the user’s contact list, self-published presence data and their access control entries, and system configuration. Access to the Self container is limited to the local instance of a Lync Server 2013 client, including Lync 2013.

The Aggregation containers are used for aggregating presence states and capabilities from multiple endpoints from which the presence publisher signs in to Lync Server 2013. Access to the Aggregation containers is limited to the local instance of a Lync Server 2013 client, including Lync 2013.

The other predefined containers are used to control how other users, also known as remote users, access the contained presence data. Container 100 contains publications intended for users of federated networks and is referred to as the **External Contacts** container. Container 200 contains data intended for users of the same network of the local user and is known as the **Colleagues** container. Presence data in Container 300 (the **Workgroup** container) is for the user's team members, and Container 400 (referred to as the **Friends and Family** container) contains data that is published for the user's personal contacts. Container 32000 is used to block access by the contained members and is known as the **Blocked Contacts** container.

For more information about the predefined containers, see [Container semantics defined and conformed by Lync](container-semantics-defined-and-conformed-by-lync.md).

## Custom containers

An application can specify other containers to support application-specific presence publications. The application can also customize the predefined containers. When specifying a container, the container ID value must be greater than 0 and less than 32768.

When an application adds a member or some data to a non-existent container, the server will create the container on behalf of the local user. If the application modifies the membership type or the access control list of a predefined container, it may change the container semantics specified by Lync 2013.

If an application is to interoperate with Lync 2013, it is important that the application follow the Lync 2013–specific container semantics of the predefined containers. If the application intends to merely coexist with Lync 2013, it must not alter the predefined container semantics. One way to achieve that is to use custom containers.

## Container membership types

The membership of a container can fall into the following membership types.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Container membership type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>user</p></td>
<td><p>The container members are specified using a comma-separated list of SIP URIs of users.</p></td>
</tr>
<tr class="even">
<td><p>domain</p></td>
<td><p>The container members are specified by a list of domain addresses and include all the users belonging to the specified domains.</p></td>
</tr>
<tr class="odd">
<td><p>enterprise</p></td>
<td><p>The container members are specified by the sameEnterprise flag and include all the users belonging to the same enterprise network of the container owner. The default membership of Container 200 is specified this way.</p></td>
</tr>
<tr class="even">
<td><p>Federated or public</p></td>
<td><p>The container members are specified by the federated flag and include all the users belonging to any network federated with the enterprise network to which the container owner belongs. The default membership of Container 100 is specified this way.</p></td>
</tr>
</tbody>
</table>


Membership in different containers may overlap. For example, a remote user has membership in Container 300 and Container 200, When subscribing to the presence of the container owner, the remote user will receive the published data from one container. The data received by the remote user comes from the container with the largest container ID value among all the containers of which the remote user is a member. In the example presented here, the remote user gets the data from Container 300.

## See also

#### Concepts

[Programming with Enhanced Presence](programming-with-enhanced-presence.md)

