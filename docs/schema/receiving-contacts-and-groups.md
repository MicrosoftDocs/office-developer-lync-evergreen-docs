---
title: Receiving contacts and groups
TOCTitle: Receiving contacts and groups
ms:assetid: 1d00013d-08a9-4e35-95ec-28fcc1270291
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454633(v=office.15)
ms:contentKeyID: 57093011
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Receiving contacts and groups


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Starting to receive contacts and groups  
Stopping contacts and groups subscription  
Refreshing the contact list  

After the ContactGroupServices object is initialized and the desired event handlers are registered with it, an application can start to receive the self-published contact list by submitting a SUBSCRIBE request that contains *contacts* and *groups* category names in the message body. In Microsoft Unified Communications Managed API 4.0, the operation is asynchronous and the SUBSCRIBE request corresponds to the call to BeginSubscribe/EndSubscribe on the ContactGroupServices object. The results are returned in the NotificationReceived events that are raised by the ContactGroupServices object.

## Starting to receive contacts and groups

The following code example shows how to start to receive a published contact list by using UCMA.

``` csharp
        /// <summary>
        /// Start to receive the contacts and groups category instances. The results 
        /// are returned in ContactAdded or GroupAdded events
        /// </summary>
        public void StartToReceiveContactsAndGroups()
        {
            if (_cgServices.CurrentState != CollaborationSubscriptionState.Subscribed)
            {
                _cgServices.BeginSubscribe(CallbackOnBeginSubscribe, _cgServices);
            }
        }

        void CallbackOnBeginSubscribe(IAsyncResult result)
        {
            try
            {
                _cgServices.EndSubscribe(result);
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message, "UcmaContactManager.CallbackOnBeginSubscribe");
            }
        }
```

The results of this operation are returned in the NotificationReceived events that are raised by ContactGroupServices. When the request succeeds, the subscription state changes from Idle to Subscribed. The changes are returned in the SubscriptionStateChanged events that are raised by the ContactGroupServices object as well. The last published contacts and groups are returned as the initial results. Subsequent updates to the contact list such as an addition or removal of a contact or a group, are returned as incremental changes. For more information about event handlers, see [Preparing to receive a contact list](preparing-to-receive-a-contact-list.md).

## Stopping contacts and groups subscription

The following code example shows how to stop an active subscription to receive the contact list.

``` csharp
        /// <summary>
        /// Stop receiving contacts and groups category instances
        /// </summary>
        public void StopToReceiveContactsAndGroups()
        {
            if (_cgServices.CurrentState == CollaborationSubscriptionState.Subscribed)
            {
                _cgServices.BeginUnsubscribe(CallbackOnBeginUnsubscribe, _cgServices);
            }           
        }

        void CallbackOnBeginUnsubscribe(IAsyncResult result)
        {
            try
            {
                _cgServices.EndUnsubscribe(result);

                this.UnsubscribeToContactsPresence();
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message, "UcmaContactManager.CallbackOnBeginUnsubscribe");
            }
        }
```

As a result, the final subscription state is Terminated.

## Refreshing the contact list

To refresh the contact list, submit a SUBSCRIBE request on the ContactGroupServices object when the contact list is already subscribed to.

``` 
        /// <summary>
        /// Refresh the contact list (obtained through the ContactGroupServices instance)
        /// </summary>
        public void RefreshContactsAndGroups()
        {
            _cgServices.BeginRefresh(CallbackOnBeginRefresh, _cgServices);

        }

        void CallbackOnBeginRefresh(IAsyncResult result)
        {
            try
            {
                if (_cgServices == result.AsyncState as ContactGroupServices)
                {
                    if (result.IsCompleted)
                    {
                        // Complete the contact list refresh request.
                        _cgServices.EndRefresh(result);

                        // Refresh contacts presence
                        this.RefreshContactsPresence();
                    }
                }

            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message, "UcmaContactManager.CallbackOnBeginRefresh");
            }
        }

```

## See also

#### Concepts

[Managing self-published contact lists](managing-self-published-contact-lists.md)

