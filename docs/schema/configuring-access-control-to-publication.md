---
title: Configuring access control to publication
TOCTitle: Configuring access control to publication
ms:assetid: cdb7f036-576f-4a7a-9dda-3753859de82d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454627(v=office.15)
ms:contentKeyID: 57092871
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Configuring access control to publication


**Applies to:** Lync 2013 | Lync Server 2013

Before starting any publication, you must first decide who can view or access your publication by selecting one or more containers, adding desired user or membership scopes to any new containers or removing certain members from any existing containers.

If you intend to use containers specified by other applications, you need to respect the container semantics set by others. Otherwise, your application may not interoperate with the other applications. If your application uses custom containers and wishes to interoperate with other applications, you will need to document your container semantics and make it available to other application developers.

As shown in the following example, in Microsoft Unified Communications Managed API 4.0, adding or removing specified membership scopes to or from a specified container is encapsulated by the **ContainerUpdateOperation** class. The supported membership scopes include individual users as specified by the corresponding SIP URIs (for example, sip:user@contoso.com), network domains as described by the domain names (for example, contoso.com), or source network types as described by the fields of the **SourceNetwork** enumeration type. Configuring container memberships is asynchronous and involves calling **BeginUpdateContainerMembership** on a **LocalOwnerPresence** instance to submit the request and calling **EndUpdateContainerMembership** to receive the operational status of the process.

``` csharp

public void AddContainerMembership(int containerId, string[] domains, 
                                   string[] uris, SourceNetwork[] srcNets)
{
       ContainerUpdateOperation updateOp = 
                         new ContainerUpdateOperation(containerId);

      if (domains != null)
           foreach (string domain in domains)
                updateOp.AddDomain(domain);
      if (uris != null)
           foreach (string uri in uris)
                updateOp.AddUri(uri);
      if (srcNets != null)
           foreach (SourceNetwork srcNet in srcNets)
                updateOp.AddSourceNetwork(srcNet);

      UpdateContainerMembership(
           new ContainerUpdateOperation[] { updateOp });
}

public void DeleteContainerMembership(int containerId, string[] domains, 
                                    string[] uris, SourceNetwork[] srcNets)
{
     ContainerUpdateOperation updateOp = 
                     new ContainerUpdateOperation(containerId);

     if (domains != null)
          foreach (string domain in domains)
                    updateOp.DeleteDomain(domain);
     if (uris != null)
                foreach (string uri in uris)
                    updateOp.DeleteUri(uri);
     if (srcNets != null)
                foreach (SourceNetwork srcNet in srcNets)
                    updateOp.DeleteSourceNetwork(srcNet);

     UpdateContainerMembership(new ContainerUpdateOperation[] { updateOp });
}
      
public void UpdateContainerMembership(
                            ICollection<ContainerUpdateOperation> updateOps)
{
     _localPresence.BeginUpdateContainerMembership(updateOps,
                CallbackOnUpdateContainerMembershipReturned, _localPresence);
}

void CallbackOnUpdateContainerMembershipReturned(IAsyncResult result)
{
     try
     {
         if (_localPresence == result.AsyncState as LocalOwnerPresence)
         {
             _localPresence.EndUpdateContainerMembership(result);

             if (OnUpdateContainerMembershipCompleted != null)
                  RaiseEvent(OnUpdateContainerMembershipCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.OK, null));

         }
     }
     catch (Exception ex)
     {
         if (OnUpdateContainerMembershipCompleted != null)
              RaiseEvent(OnUpdateContainerMembershipCompleted, this,
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
     }
}
```

The above code snippet should be inserted into the UcmaPublisher class presented in [Preparing for category publications](preparing-for-category-publications.md).

Using the previous example, the following statements add sip:user@contoso.com to the membership of Container 1000.

``` csharp
int containerId = 1000;
string[] uris = new string[] { "sip:user@contoso.com" };
string[] domains = null;
SourceNetwork[] srcNets = null;
AddContainerMembership(containerId, domains, uris, srcNets);
```

If Container 1000 does not exist, the server will create it upon receiving the **AddContainerMembership** request. Similarly, the following statements will remove the user from the container’s membership, if the container is already created and the user is a member of the container.

``` csharp
int containerId = 1000;
string[] uris = new string[] { "sip:user@contoso.com" };
string[] domains = null;
SourceNetwork[] srcNets = null;
DeleteContainerMembership(containerId, domains, uris, srcNets);
```

Attempts to remove membership from a non-existent container will be ignored and no exceptions will be thrown. Also, attempts to delete a non-existent membership scope from an existing container will be ignored and no exception will be thrown.

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

