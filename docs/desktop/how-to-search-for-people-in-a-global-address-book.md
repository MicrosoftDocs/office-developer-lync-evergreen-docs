---
title: 'How to: Search for people in a global address book'
TOCTitle: 'How to: Search for people in a global address book'
ms:assetid: 9d61ae21-738f-4ccd-9e47-c49a0633e1be
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn391639(v=office.15)
ms:contentKeyID: 56293549
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Search for people in a global address book

Learn how to use the Microsoft Lync 2013 SDK to search for people in the Microsoft Office 2013 Unified Contact Store or other global address books.

**Last modified:** July 01, 2013

***Applies to:** Lync 2013*

You search for people because they aren’t in your contact list and you want to add them. You also search for people when you want to start a conversation with someone who you won’t be adding to your contact list. This topic shows you how to do the search operations for people.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Prerequisites<br />
Before searching for people<br />
Searching for people<br />
Keep contact availability fresh<br />
Searching for distribution groups<br />
The Exchange UCS address book<br />
Example: People Finder<br />
Next steps<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for searching for contacts and distribution groups are as follow:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Before searching for people

Before coding a contact search feature in your application, consider the following guidelines.

  - **Look up first and then search**. A person can be in both your contact list and a global address list. Look people up in your contact list before searching for them. A contact list lookup is faster and saves network bandwidth.

  - **Not all contact list items are searchable** A contact list contains people items, telephone number items, distribution group items, and Lync group items. A global address search only returns people and distribution groups.

  - **Lync must be signed in before you look up or search**. Sign in to Lync before looking up someone in the contact list or searching for them in a global address list. Read about the procedure described in [How to: Sign a user in to Lync](how-to-sign-a-user-in-to-lync.md) and be sure that your application logic provides this capability before coding contact search logic.

## Searching for people

People searching is done by specifying address books to search through for matching names. The Lync 2013 API refers to these address books as **search providers** which are enumerated by [Microsoft.Lync.Model.SearchProviders](https://msdn.microsoft.com/en-us/library/jj278060\(v=office.15\)). If you want to search for people based on a skill set, you’ll need to learn about [Advanced contact search](advanced-contact-search.md), which uses an **Expert** search provider. Search results are returned asynchronously. You can get these results by providing a callback method that is invoked when the search is complete. The callback method gets the results by calling the **EndSearch** method and caching the return value.

### Search for people in Exchange 2013 contact lists

An Exchange 2013 contact list unifies people lists from sources such as Outlook recipient lists and Lync IM conversation history. This unified list is the Exchange 2013-hosted Unified Contact Store (UCS) and is also accessible in third-party applications. A third-party application can provide its own people lists to UCS. When you search in UCS, you are potentially searching beyond Outlook email recipient history or IM chat history. Because of third-party connectivity, UCS can store a persona for someone outside of your organization Active Directory Domain Services (AD DS) people store.

People in UCS are represented by persona objects. A persona object can have just the email address of a person or an aggregation of people information such as the persons first and last name. The default people source for a people search is the UCS. Just provide a search string and the default people search finds people in the UCS by the best identifying information that matches the search string. Normally, the person’s name is matched against the search string, but an email address or telephone number can also be matched.

Figure 1 shows the search logic that you add to your application.

Figure 1. People search logic diagram.

  
![Logic for UCS people search](images/Dn391639.OCOM_PeopleSearch_UCS(Office.15).jpg "Logic for UCS people search")

### To search for people in the UCS address book

1.  Get the string used as the name search criteria.

2.  Call the [ContactManager.BeginSearch](https://msdn.microsoft.com/en-us/library/jj278297\(v=office.15\)) method.

3.  In a lambda expression or a callback method passed in the second argument of **BeginSearch**, get the results of the search by calling the [ContactManager.EndSearch](https://msdn.microsoft.com/en-us/library/jj277082\(v=office.15\)) method.
    
    A [Microsoft.Lync.Model.SearchResults](https://msdn.microsoft.com/en-us/library/jj293514\(v=office.15\)) object is returned.

4.  Get the number of people in the search results by reading the [SearchResults.Contacts](https://msdn.microsoft.com/en-us/library/jj276984\(v=office.15\))**Count** property. If the number is zero, nobody in the address book matched the search criteria.
    
    The following example iterates the contact collection returned by the [SearchResults.Contacts](https://msdn.microsoft.com/en-us/library/jj276984\(v=office.15\)) property.
    
    ```csharp
                    //All global address books
                    _LyncClient.ContactManager.BeginSearch(
                        searchName,
                        SearchResultsCallback,
                        searchName);
    ```
    
    The following example ends the people search and adds the search results to a list of **Contact** objects.
    
    ```csharp
            /// Handles callback containing results of a search
            /// </summary>
            /// <param name="source"></param>
            /// <param name="results"></param>
            /// <param name="_asyncOperation"></param>
            public void SearchResultsCallback(IAsyncResult ar)
            {
                SearchResults results = null;
                results = _LyncClient.ContactManager.EndSearch(ar);
    
                if (results == null)
                {
                    return;
                }
    
                if (results.AllResults.Count == 0)
                {
                    MessageBox.Show("0 instances found for " + ar.AsyncState.ToString());
                    return;
                }
                foreach (SearchResult searchResult in results.AllResults)
                {
    
                    if (searchResult.Result is Contact)
                    {
                        Contact foundContact = searchResult.Result as Contact;
    
                        //array for use of list box
                        _FoundContacts.Add(foundContact);
                    }
                }
            }
    ```

The previous procedure just displayed the names of contacts in the console screen. You can add the contact names to a list on your UI so that a user can choose contacts to add to the Lync contact list so that the user doesn’t need to search for them again. If the user just wants to start a new conversation, you can create the conversation and then add the contact to the conversation without adding them to the contact list.

### Search for people in other address books

When you search for people in other address books, you need to select the address books that you want to search through before you can start a search.

Figure 2 shows the search logic that you add to your application.

Figure 2. People search logic diagram.

  
![Logic for people search with global address books](images/Dn391639.OCOM_PeopleSearch_AddrBooks(Office.15).jpg "Logic for people search with global address books")

### To search for a contact by using a list of search providers

1.  Obtain a user’s partial or full name as a string to be used as a search key.

2.  Call the [ContactManager.BeginSearch](https://msdn.microsoft.com/en-us/library/jj278297\(v=office.15\)) method.

3.  In a lambda expression or a callback method passed in the second argument of **BeginSearch**, get the results of the search by calling the [ContactManager.EndSearch](https://msdn.microsoft.com/en-us/library/jj277082\(v=office.15\)) method.
    
    A [Microsoft.Lync.Model.SearchResults](https://msdn.microsoft.com/en-us/library/jj293514\(v=office.15\)) object is returned.

4.  Read the [SearchResults.Contacts](https://msdn.microsoft.com/en-us/library/jj276984\(v=office.15\))**Count** property, and then continue this procedure if the property value returns one or more contacts.
    
    The following example iterates the contact collection returned by the [SearchResults.Contacts](https://msdn.microsoft.com/en-us/library/jj276984\(v=office.15\)) property.
    
    ```csharp
            /// <summary>
            /// Searches in a specified global address book for people whose names
            /// match the search string
            /// </summary>
            /// <param name="searchName">string. The search key</param>
            /// <param name="addressBook">string. Abbreviation of global address book name</param>
            private void SearchForPerson(string searchName, string addressBook)
            {
                //Get the default people attribute search fields
                SearchFields searchFields = _LyncClient.ContactManager.GetSearchFields();
    
                SearchProviders chosenProvider = SearchProviders.Invalid;
                switch (addressBook)
                {
                    case "ucs":
                        //Unified Contact Store
                        chosenProvider = SearchProviders.ExchangeService;
                        break;
                    case "gal":
                        chosenProvider = SearchProviders.GlobalAddressList;
                        break;
                    case "none":
                        break;
                    default:
                        //UCS and GAL searched
                        chosenProvider = SearchProviders.Default;
                        break;
                }
    
                if (chosenProvider == SearchProviders.Invalid)
                {
                    //No address book specified, UCS searched.
                    _LyncClient.ContactManager.BeginSearch(
                        searchName,
                        SearchResultsCallback,
                        searchName);
                }
                else
                {
    
                    //Start asynchronous global address book search with 
                    //search key, default list of person searchable attributes,
                    //default search options, max of 100 results per result page,
                    //async calllback method to be invoked 
                    _LyncClient.ContactManager.BeginSearch(
                        searchName
                        , chosenProvider
                        , searchFields
                        , SearchOptions.Default
                        , 100
                        , SearchResultsCallback
                        , searchName);
                }
    
            }
    ```

## Coding guidelines

**Search result scoping:** A search operation can return a large number of contact and distribution group results, depending on the length of the search string. For example, a search string of "J" returns all users whose first name content includes the string "J" whereas "John Smith" returns only contacts whose name is John Smith.

To help users refine their search, display each set of results in a UI list so the user can review the results. If the search results contain less relevant items, let the user enter a longer search string and perform the search operation again. When the result set is scoped down to a manageable size, you can find who you are looking for in the results.

To make the user contact search experience in your application more enjoyable, consider the following guidelines when you write your code.

**When you should start a search:** You can prevent unnecessary network SIP traffic by looking in your contact list before searching a network resource like an address book. A user may not know if someone is in their contact list and will use a UI search element like a list locator to find a person. Your application should look up the person by name in the contact list and then present the look up result. If the person you want is not in the result list, search for her in a global address book. Both look up and search are asynchronous, but only search requires calls to an Exchange Server web service.

**Contact list item types:** People, telephone numbers, and distribution groups can be looked up in the contact list while Lync groups are accessed directly from the [ContactManager.Groups](https://msdn.microsoft.com/en-us/library/jj277988\(v=office.15\)) property. Contact list items can be added to the contact list from the Unified Contact Store (UCS) or the organization-wide Exchange Server global address list (GAL) after finding them in an address book search. You can also add items to a contact list through an activity such as starting an Lync audio call or sending an IM to someone in an external PIC system such as Yahoo.

**Keep contact availability fresh:** As soon as you get a set of contacts from a search, you can ask for a snapshot of the availability of any of the contacts. These snapshots get stale as people go on line, idle, busy, or off line. For example, a search returns Omar Snook and you request his availability as of now. The response says Omar is available for a conversation but you aren’t ready to talk to him. When you are ready for Omar, you try to start a conversation with him. Because Omar has gone off line since you got the snapshot, the conversation isn’t started.

It is better to ask for an event from Lync that tells you when a contact’s availability changes. You can use the event to update Omar’s availability in your application UI. The mechanism that Lync uses to get availability change notifications is called **presence subscription**. It is a good idea to start your own subscription when you get the [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) object for Omar in search results. Read about availability subscription: [How to: Subscribe to enhanced presence content](how-to-subscribe-to-enhanced-presence-content.md)

**Searching for distribution groups:** You can also search for distribution groups. If distribution group search results are returned, add individual group members to a new conversation or your contact list. If you want to add a complete distribution group to your contact list, you can do that too. You can even use the [Microsoft.Lync.Model.Utilities](https://msdn.microsoft.com/en-us/library/jj293806\(v=office.15\)) class to start an email with the whole distribution group on the to: line. Searching for distribution groups is very similar to searching for a person except that result parsing logic is a little bit different. For information about this, read [How to: Search for a distribution group](how-to-search-for-a-distribution-group.md).

**The Exchange UCS address book:** The Exchange UCS keeps a history of the user’s Lync conversation participants and recipients of email sent by the user. UCS should be used when you only want to see a people search result list that contains the email addresses of people you have sent email to. The UCS address book contents are not limited to people in your organization.

## Example: People Finder

The following example is a helper class that looks a person up or searches for people in global address books. The SearchForGroupOrContact method takes a string to search, a string abbreviation of a global address list name, and a Boolean flag that tells the method to look the person up before starting a search. If the look up operation doesn’t return any people, a search is started.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;

namespace SimpleContactList
{
    #region delegates
    public delegate void SearchResultDelegate(List<Contact> foundContacts);
    #endregion

    public class SearchModel
    {
        
        #region events
        public event SearchResultDelegate SearchChangedEvent;
        #endregion

        #region private fields
        private List<Contact> _FoundContacts = new List<Contact>();
        private LyncClient _LyncClient;
        #endregion

        #region public properties

        public List<Contact> ResultContactArray
        {
            get
            {
                return this._FoundContacts;
            }
        }
        #endregion


        #region public methods

        /// <summary>
        /// Searches through global address list for name entered on form
        /// Results captured in SearchResultCallback
        /// <param name="searchName">Typed entry on form</param>
        public void SearchForGrouporContact(string searchName, string addressBook, Boolean lookupFirst)
        {

            //initiate search for entity based on entry in txtContactName

            _FoundContacts.Clear();

            if (_LyncClient.State != ClientState.SignedIn)
            {
                return;
            }

            if (lookupFirst)
            {
                //BeginLookup searches in the United Contact Store if the searchName is a telephone number
                _LyncClient.ContactManager.BeginLookup(searchName,
                    (ar) =>
                    {
                        try
                        {
                            object lookupResult = _LyncClient.ContactManager.EndLookup(ar);
                            if (lookupResult is Contact)
                            {
                                Contact foundContact = lookupResult as Contact;

                                //array for use of list box
                                _FoundContacts.Add(foundContact);

                            }
                            else if (lookupResult is DistributionGroup)
                            {
                                if (lookupResult is DistributionGroup)
                                {
                                    foreach (Contact c in (DistributionGroup)lookupResult)
                                    {
                                        //array for use of list box
                                        _FoundContacts.Add(c);
                                    }
                                }
                            }
                            if (SearchChangedEvent != null)
                            {
                                SearchChangedEvent(_FoundContacts);
                            }

                        }

                        //Person was not found in the contact list
                        //Starting a global address search
                        catch (ItemNotFoundException)
                        {
                            SearchForPerson(searchName, addressBook);
                        }
                    },
                    null);
            }
            else
            {
                SearchForPerson(searchName, addressBook);
            }

        }

        /// <summary>
        /// Searches in a specified global address book for people whose names
        /// match the search string
        /// </summary>
        /// <param name="searchName">string. The search key</param>
        /// <param name="addressBook">string. Abbreviation of global address book name</param>
        private void SearchForPerson(string searchName, string addressBook)
        {
            //Get the default people attribute search fields
            SearchFields searchFields = _LyncClient.ContactManager.GetSearchFields();

            SearchProviders chosenProvider = SearchProviders.Invalid;
            switch (addressBook)
            {
                case "ucs":
                    //Unified Contact Store
                    chosenProvider = SearchProviders.ExchangeService;
                    break;
                case "gal":
                    chosenProvider = SearchProviders.GlobalAddressList;
                    break;
                case "none":
                    break;
                default:
                    //UCS and GAL searched
                    chosenProvider = SearchProviders.Default;
                    break;
            }

            if (chosenProvider == SearchProviders.Invalid)
            {
                //No address book specified, UCS searched.
                _LyncClient.ContactManager.BeginSearch(
                    searchName,
                    SearchResultsCallback,
                    searchName);
            }
            else
            {

                //Start asynchronous global address book search with 
                //search key, default list of person searchable attributes,
                //default search options, max of 100 results per result page,
                //async calllback method to be invoked 
                _LyncClient.ContactManager.BeginSearch(
                    searchName
                    , chosenProvider
                    , searchFields
                    , SearchOptions.Default
                    , 100
                    , SearchResultsCallback
                    , searchName);
            }

        }
        #endregion
        #region callbacks

        /// Handles callback containing results of a search
        /// </summary>
        /// <param name="source"></param>
        /// <param name="results"></param>
        /// <param name="_asyncOperation"></param>
        public void SearchResultsCallback(IAsyncResult ar)
        {
            SearchResults results = null;
            results = _LyncClient.ContactManager.EndSearch(ar);

            if (results == null)
            {
                return;
            }

            if (results.AllResults.Count == 0)
            {
                MessageBox.Show("0 instances found for " + ar.AsyncState.ToString());
                return;
            }
            foreach (SearchResult searchResult in results.AllResults)
            {

                if (searchResult.Result is Contact)
                {
                    Contact foundContact = searchResult.Result as Contact;

                    //array for use of list box
                    _FoundContacts.Add(foundContact);
                }
            }
            if (SearchChangedEvent != null)
            {
                SearchChangedEvent(_FoundContacts);
            }

        }
        #endregion

         #region constructors
        public SearchModel(ClientModel pClient)
        {
            _LyncClient = pClient.MSLyncClient;
            _FoundContacts = new List<Contact>();
        }

        #endregion

    }
}
```

## Next steps

  - [How to: Add or remove a person from a contact list](how-to-add-or-remove-a-person-from-a-contact-list.md)

  - [How to: Start a Lync IM conversation](how-to-start-a-lync-im-conversation.md)

  - [How to: Search for a distribution group](how-to-search-for-a-distribution-group.md)

## See also

  - [Advanced contact search](advanced-contact-search.md)

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

  - [What you can do with Lync conversations](what-you-can-do-with-lync-conversations.md)

  - [Unified Contact Store in EWS in Exchange 2013](http://msdn.microsoft.com/en-us/library/exchange/jj190895\(v=exchg.150\).aspx)

