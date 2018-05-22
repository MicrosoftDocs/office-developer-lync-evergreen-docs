---
title: Submitting a publication request
TOCTitle: Submitting a publication request
ms:assetid: 1fbd105d-cc44-40ac-9d78-44fe62b8b78a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454643(v=office.15)
ms:contentKeyID: 57092889
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Submitting a publication request


_**Applies to:** Lync 2013 | Lync Server 2013_

The final step of publication involves submitting a publication request to the server. This submittal passes the desired category instances to the server and is an asynchronous process. In Microsoft Unified Communications Managed API 4.0, it amounts to calling the **BeginPublishPresence** method on the **LocalOwnerPresence** instance and calling the required **EndPublishPresence** method in a callback function that is specified as an input to the BeginPublishPresence call. This programming pattern appears in the following code examples.

Microsoft Lync Server 2013 supports two types of presence publications. One kind of publication follows the prescribed publication grammars and the other does not follow any underlying publication grammars. The grammars are a set of rules that determine how instances of a given category are published to certain containers and how they may be accessed by potential subscribers. The rules are executed by the server when a publication request is made for the specified category instances. By default, the publication grammars enforce the Microsoft Lync 2013-compatible container semantics and publication rules. For more information, see [Lync-specific features of Enhanced Presence](lync-specific-features-of-enhanced-presence.md).

Grammar-based publications require only the input of the category names and data values. Grammar-free publications require additional input to specify the instance IDs, container IDs and other properties of any to-be-published presence category instances. UCMA 4.0 supports the two types of publications by overloading the **BeginPublishPresence** method. For the grammar-based publication, this method takes a collection of **PresenceCategory** objects as its input parameter. For the grammar-free publication, this method takes a collection of **PresenceCategoryWithMetaData** objects as the input parameter.

The following code example is an excerpt from the UcmaPublisher class that is introduced in [Preparing for category publications](preparing-for-category-publications.md) and shows how to submit a grammar-based presence category publication.

``` csharp
        public void RequestGrammarBasedPresencePublication(string categoryName, string categoryValue)
        {
            PresenceCategory[] categories = new PresenceCategory[] { 
                new CustomPresenceCategory(categoryName, categoryValue) };
            this.RequestGrammarBasedPresencePublication(categories);
        }

        public void RequestGrammarBasedPresencePublication(
            ICollection<PresenceCategory> categories)
        {
            if (categories != null)
            {
                _localPresence.BeginPublishPresence(categories,
                   CallbackOnPublishPresenceReturned, _localPresence);
            }
        }

        void CallbackOnPublishPresenceReturned(IAsyncResult result)
        {
            try
            {
                if (_localPresence == result.AsyncState as LocalOwnerPresence)
                {
                    _localPresence.EndPublishPresence(result);

                    if (OnPublishPresenceCompleted != null)
                        RaiseEvent(OnPublishPresenceCompleted, this, 
                            new AsyncOpStatusEventArgs(AsyncOpStatus.OK, null));
                }
            }
            catch (Exception ex)
            {
                if (OnPublishPresenceCompleted != null)
                    RaiseEvent(OnPublishPresenceCompleted, this, 
                        new AsyncOpStatusEventArgs(AsyncOpStatus.Error, ex));
            }
        }
```

Using this example, a personal note category instance can be published, based the default publication grammars, with the following statements.

``` csharp
Note pNote = new Note("Personal note set by UcmaPublisher");
string pNoteValue = pNote.GetCategoryDataXml();
RequestGrammarBasedPresencePublication("note",pNoteValue);
```

The following example shows how to submit a grammar-free presence category publication.

``` csharp
        /// <summary>
        /// Publish a presence category without following the underlying publication grammar.
        /// </summary>
        /// <param name="categoryName">Category name</param>
        /// <param name="instanceId">Instance ID</param>
        /// <param name="containerId">Container ID</param>
        /// <param name="xmlValue">Category value in XML</param>
        public void RequestGrammarFreePresencePublication(string categoryName, long instanceId, int containerId, string xmlValue)
        {
            PresenceCategoryWithMetaData[] categories = new PresenceCategoryWithMetaData[] {
                this.CreatePresenceCategoryInstance(categoryName, instanceId, containerId, xmlValue) };
            this.RequestGrammarFreePresencePublication(categories);
        }

        /// <summary>
        /// Publish presence categories without following the underlying publication grammar.
        /// </summary>
        /// <param name="categoriesWithMetaData">A collection of the to be published categories.</param>
        public void RequestGrammarFreePresencePublication(
            ICollection<PresenceCategoryWithMetaData> categories)
        {
            _localPresence.BeginPublishPresence(categories,
                CallbackOnPublishPresenceReturned, _localPresence);
        }
```

A personal note category instance can be published to a custom container (Container 1000), independent of the underlying publication grammars, with the following statements.

``` csharp
Note pNote = new Note("Personal note set by UcmaPublisher");
string pNoteValue = pNote.GetCategoryDataXml();
RequestGrammarFreePresencePublication("note", 1, 1000, pNoteValue);
```

## See also

#### Concepts

[Publishing Enhanced Presence](publishing-enhanced-presence.md)

