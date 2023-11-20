---
title: Advanced contact search
TOCTitle: Advanced contact search
ms:assetid: 15afb8c7-6c42-432c-a213-185f8f549f26
ms:mtpsurl: https://msdn.microsoft.com/library/JJ937269(v=office.15)
ms:contentKeyID: 50877088
ms.date: 07/24/2014
mtps_version: v=office.15
description: Master advanced contact search with Microsoft Lync 2013 SDK. Learn to create a custom search feature for Lync 2013 users and distribution groups.
---

# Advanced contact search

![Beyond the basics topic](images/JJ937254.mod_icon_beyondbasics_long(Office.15).png "Beyond the basics topic")

Learn about custom Lync contact search by using Microsoft Lync 2013 SDK.



**Applies to**: Lync 2013 | Lync Server 2013

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Search for contacts<br />
Additional resources</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

## Search for contacts

The contact search-related Lync 2013 API enables you to create a contact search feature in your application that can query multiple contact search providers for Lync 2013 users and distribution groups. The search field and search option choices that you make through the API make it possible to build a contact search feature that lets a user scope down a search result set when a default search returns a large number of contacts.

### Search providers

The Lync 2013 contact search feature uses a common Office contact store which is synchronized with six individual search providers from the following list:

  - Exchange service

  - Expert search service

  - Global address list

  - Other contact list

  - Personal contact list

  - Windows address book

You can do a contact search operation that uses these search providers individually or in combination. In order to get search results, you must use a search provider that is synchronized with the common Office contact store. The Other contact list, personal contact list, and Windows address book are always in a synchronized state. The Exchange, Expert, and Global address list search providers are periodically re-synchronized with the common Office contact store. These three providers do not return results while in a non-synchronized state. You can look at the synchronization state of any search provider before starting a search operation that uses that search provider.

Perform a search that returns results using the providers that are fully synchronized with Microsoft Lync 2013. Attempting a search using a partially synchronized search provider can return partial results. You discover the synchronization state of a search provider by calling into [ContactManager.GetSearchProviderStatus](https://msdn.microsoft.com/library/jj267663\(v=office.15\)).

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933089.alert_caution(Office.15).gif" title="Caution note" alt="Caution note" /><strong>Caution</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Attempting to call into <a href="https://msdn.microsoft.com/library/jj267663(v=office.15)">GetSearchProviderStatus</a> with the enumerators <a href="https://msdn.microsoft.com/library/jj278060(v=office.15)">SearchProviders</a><strong>.Default</strong>,<a href="https://msdn.microsoft.com/library/jj278060(v=office.15)">SearchProviders</a><strong>.OtherContacts</strong>, <a href="https://msdn.microsoft.com/library/jj278060(v=office.15)">SearchProviders</a><strong>.WindowsAddressBook</strong>, or <a href="https://msdn.microsoft.com/library/jj278060(v=office.15)">SearchProviders</a><strong>.PersonalContacts</strong> raises an exception. These search providers are always fully synchronized.</p></td>
</tr>
</tbody>
</table>

For the search providers that are always synchronized with the common Office contact store, you can use them in search operations at any time. Do not call the **GetSearchProviderStatus** method for these always-synchronized providers.

You can perform a single search against one or more search providers with the exception of the SearchProviders.Expert search provider. The expert search provider must be used in a search operation individually. An Expert search is actually an HTTP query against a Web page. For this reason, it cannot be combined with other search providers in a search process.

One search provider can have advantages over another search provider because individual providers can support a different set of search options and search fields. You may choose to specify multiple search providers in a single search so that the combination of options and search fields are supported by your search request.

#### Expert search

Expert search capability is available for Lync Server 2013 when an administrator has configured the server with an expert search query URL. If a search query URL has not been configured at the server, no results are returned in an expert search.

An expert search is a search for people using keywords instead of a name, e-mail, alias, or company. The expert search depends on the nature of the data store you're searching. A good example of such a data store is the Microsoft SharePoint data store. SharePoint indexed fields include fields describing skills, interests, responsibilities, knowledge, and authored documents.

An expert search query is a string composed of keywords such as first names, last names, business titles, or responsibility areas. The following expert search example finds people whose SharePoint profile includes the strings "programming writer 2" and "Alvord."

Alvord "programming writer 2"

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ933112.alert_note(Office.15).gif" title="Note" alt="Note" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>The previous search example specified search values rather than search fields. Because of this, people results are returned where these search values exist in any searchable field. To return a smaller and more meaningful result set, you should create a search string containing full values. Include double quotation marks around such elements as job titles to avoid returning irrelevant results.</p>
<p>For example, use &quot;Alford&quot; instead of &quot;Al&quot; and &quot;programming writer 2&quot; instead of programming writer 2.</p></td>
</tr>
</tbody>
</table>

Due to the complexity of an expert search operation, it can be difficult to determine the reason why an expert search can return no results. The [Microsoft.Lync.Model.SearchException](https://msdn.microsoft.com/library/jj293959\(v=office.15\)) class is designed to give you hints that help find the reason for an expert search failure. Surround your call into [ContactManager.EndSearch](https://msdn.microsoft.com/library/jj277082\(v=office.15\)) with a try/catch block and catch the [Microsoft.Lync.Model.SearchException](https://msdn.microsoft.com/library/jj293959\(v=office.15\)).

For information about SharePoint Expertise search syntax, see [Enterprise Search Keyword Reference](http://go.microsoft.com/fwlink/?linkid=192230).

#### Exchange service

Exchange Service search is a Web service that searches for people in the local user’s Microsoft Outlook contact list.

#### Global Address List

The Global Address List (GAL) search is used to find people or distribution groups in an organization’s Active Directory data store. Results can be returned from a search on a partial display name or an email address. If you iterate on the collection of results returned by [SearchResults.AllResults](https://msdn.microsoft.com/library/jj276716\(v=office.15\)), you must get the type of result and cast the individual result to the corresponding class.

#### Windows AddressBook

Searches the Windows AddressBook.

#### Other contacts and personal contacts

Limits a search to people contacts in a user’s contact list. If the searched person is in the organization but not in the local user’s contact list, no results are returned.

### Search options

The [SearchOptions](https://msdn.microsoft.com/library/jj274803\(v=office.15\)) enumeration provides a default search option that does not restrict a search to a whole word match. [SearchOptions](https://msdn.microsoft.com/library/jj274803\(v=office.15\)) returns both contacts and distribution groups and returns all results in one asynchronous callback. You can change the behavior of a search by combining one or more search options in a search operation. For example, you might want to see only contacts in a result set. Not every supported search provider supports all of the search options enumerated by [SearchOptions](https://msdn.microsoft.com/library/jj274803\(v=office.15\)).

### Search fields

A search field is an index that a search provider uses to enable a search through its data store. Not all of the search fields enumerated by [SearchFields](https://msdn.microsoft.com/library/jj276185\(v=office.15\)) are supported as indexes by individual search providers. If you specify a search on a search provider using a search field that is not supported as an index, no search results are returned. If you're not sure whether a search provider supports a specific search field, you can use the [SearchFields](https://msdn.microsoft.com/library/jj276185\(v=office.15\))**.AllFields** enumerator in the search. In this case, the search is conducted on the search provider using whatever indexes are supported by the search provider.

## See also

  - [Beyond the basics: Lync contact lists](beyond-the-basics-lync-contact-lists.md)

