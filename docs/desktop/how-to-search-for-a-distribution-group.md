---
title: 'How to: Search for a distribution group'
TOCTitle: 'How to: Search for a distribution group'
ms:assetid: 6648d555-1dee-4575-9df0-e533adf061b4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn391638(v=office.15)
ms:contentKeyID: 56293548
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Search for a distribution group

Learn about searching for and expanding Exchange 2013 distribution groups by using the Microsoft Lync 2013 API.

**Last modified:** June 06, 2013

***Applies to:** Lync 2013*

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>In this article</strong><br />
Example: Distribution group list<br />
<br />
Prerequisites<br />
Search for a distribution group<br />
Additional resources</p></td>
<td></td>
</tr>
</tbody>
</table>

Searching for groups is very similar to searching for contacts because you call the same two methods as in the previous section but you read the [SearchResults.Groups](https://msdn.microsoft.com/en-us/library/jj268253\(v=office.15\)) property in the search results.

A distribution group can contain other distribution groups in addition to a collection of contacts. For this reason, you may consider using a recursion algorithm to successively expand and list nested groups and their members.

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
<td><p>A distribution group that contains a set of deeply nested distribution groups can quickly use up computer resources if automatically expanded to the deepest level. It is better to display the contacts in the top level distribution group plus the unexpanded distribution groups at that level. Let a user select an individual distribution group to expand to the next level and then display the users and groups at that level.</p></td>
</tr>
</tbody>
</table>

## Prerequisites

The prerequisites for searching for contacts and distribution groups are as follow:

  - Microsoft Lync 2013 must be installed and running on the development computer.

  - You must have sign-in credentials for Microsoft Lync Server 2013.

  - Microsoft Lync 2013 SDK must be installed on the development computer.

## Search for a distribution group

Searching for groups is very similar to searching for contacts because you call the same two methods as in the previous section but you read the [SearchResults.Groups](https://msdn.microsoft.com/en-us/library/jj268253\(v=office.15\)) property in the search results.

A distribution group can contain other distribution groups in addition to a collection of contacts. For this reason, you may consider using a recursion algorithm to successively expand and list nested groups and their members.

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
<td><p>A distribution group that contains a set of deeply nested distribution groups can quickly use up computer resources if automatically expanded to the deepest level. It is better to display the contacts in the top level distribution group plus the unexpanded distribution groups at that level. Let a user select an individual distribution group to expand to the next level and then display the users and groups at that level.</p></td>
</tr>
</tbody>
</table>

### To search for a distribution group

1.  Obtain the partial or full name of a distribution group as a string to be used as a search key.

2.  Call the [ContactManager.BeginSearch](https://msdn.microsoft.com/en-us/library/jj278297\(v=office.15\)) method.
    
    <table>
    <colgroup>
    <col style="width: 100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><img src="images/JJ933112.alert_note(Office.15).gif" title="Tip" alt="Tip" /><strong>Tip</strong></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>If you want to run an advanced group search, call the <a href="https://msdn.microsoft.com/en-us/library/jj278297(v=office.15)">ContactManager.BeginSearch</a> method and specify the search provider and a set of distribution group property fields to search against.</p></td>
    </tr>
    </tbody>
    </table>
    
    In either a lambda expression or a callback method passed in the second argument of **BeginSearch**, get the results of the search by calling the [ContactManager.EndSearch](https://msdn.microsoft.com/en-us/library/jj277082\(v=office.15\)) method. A [Microsoft.Lync.Model.SearchResults](https://msdn.microsoft.com/en-us/library/jj293514\(v=office.15\)) object is returned.

3.  Read the [SearchResults.Groups](https://msdn.microsoft.com/en-us/library/jj268253\(v=office.15\))**Count** property, and then continue this procedure if the property value returns 1 or more distribution groups.
    
    The following example iterates the group collection returned by the [SearchResults.Groups](https://msdn.microsoft.com/en-us/library/jj268253\(v=office.15\)) property.
    
    ```csharp
            /// <summary>
            /// Searches for any distribution group whose name contains the supplied
            /// search key
            /// </summary>
            /// <param name="searchKey">string. Group name or partial name to search on.</param>
            private void SearchForGroups(string searchKey)
            {
                Console.WriteLine(
                    "Searching for groups on " + 
                    searchKey);
    
                _LyncClient.ContactManager.BeginSearch(
                    searchKey,
                    (ar) =>
                    {
                        SearchResults searchResults = _LyncClient.ContactManager.EndSearch(ar);
                        if (searchResults.Groups.Count > 0)
                        {
                            Console.WriteLine(
                                searchResults.Groups.Count.ToString() + 
                                " found");
    
                            foreach (Group group in searchResults.Groups)
                            {
                                Console.WriteLine(System.Environment.NewLine + group.Name);
                                DistributionGroup dGroup = group as DistributionGroup;
                                DGLister.Program.DGExpander(dGroup);
                            }
                        }
                        else
                        {
                            Console.WriteLine(
                                "No groups found for search on " + 
                                searchKey);
                        }
                    },
                    null);
    
            }
    ```

### To expand a distribution group

1.  Read the [DistributionGroup.IsExpanded](https://msdn.microsoft.com/en-us/library/jj275697\(v=office.15\)) property.
    
    If the returned value is **false**, the distribution group must be expanded before you can access its contacts.

2.  Call the [DistributionGroup.BeginExpand](https://msdn.microsoft.com/en-us/library/jj274816\(v=office.15\)) method.

3.  In the lambda expression or callback method passed in the first argument of the **BeginExpand** method, call the [DistributionGroup.EndExpand](https://msdn.microsoft.com/en-us/library/jj293275\(v=office.15\)) method.

4.  Iterate on the distribution group as a [Microsoft.Lync.Model.Contact](https://msdn.microsoft.com/en-us/library/jj266463\(v=office.15\)) collection to get individual contacts.

5.  Read the **Count** property of the [DistributionGroup.NestedGroups](https://msdn.microsoft.com/en-us/library/jj278008\(v=office.15\)) property.

6.  If the count value returned in the previous step is greater than zero, iterate on the value returned by the [DistributionGroup.NestedGroups](https://msdn.microsoft.com/en-us/library/jj278008\(v=office.15\)) to get the nested distribution groups.
    
    The following example expands a distribution group if not already expanded, prints the display name of each group contact, and then recursively expands any nested distribution groups.
    
    ```csharp
            /// <summary>
            /// Expands any groups found in search results 
            /// </summary>
            /// <param name="workMaterial"></param>
            static void DGExpander(DistributionGroup DGGroup)
            {
    
                //Only distribution groups can be expanded.
                //_Group is a class field that references the Microsoft.Lync.Model.Group.Group instance
                //encapsulated by the GroupModel class.
                if (DGGroup.Type != GroupType.DistributionGroup)
                {
                    return;
                }
    
                //If the distribution group has not been expanded yet,
                //it must be expanded before group members are visible
                if (DGGroup.IsExpanded == false)
                {
                    Console.WriteLine(
                        " -- Expanding " + 
                        DGGroup.Name + 
                        " -- ");
    
                    DGGroup.BeginExpand(
                        (ar) => 
                        {
                            try
                            {
                                DGGroup.EndExpand(ar);
                            }
                            catch (LyncClientException)
                            {
                                Console.WriteLine(
                                    "Lync Client Exception on expand " + 
                                    DGGroup.Name);
                            }
                            DGLister.Program.PrintDGDetail(DGGroup);
                        },
                        null);
                }
                else
                {
                    DGLister.Program.PrintDGDetail(DGGroup);
                }
            }
    ```

## Example: Distribution group list

The following example is a command-line program that accepts two string parameters: search object type and search string. If the search object type is "Group," the example queries for distribution groups whose name contains the search string. The returned groups are parsed and the names of the contacts within the groups are written to the console. If a distribution group has nested distribution groups, those groups are parsed for contacts.

If the search object is "Contact," the example queries for users whose display name contains the search string.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.Lync.Model;
using Microsoft.Lync.Model.Group;

namespace DGLister
{
    class Program
    {
        private LyncClient _LyncClient;
        
        static void Main(string[] args)
        {
            Program program = new Program(args);
            Console.ReadLine();
        }
        private Program(string[] args)
        {
            try
            {
                _LyncClient = LyncClient.GetClient();

                if (_LyncClient.State != ClientState.SignedIn)
                {
                    Console.WriteLine("Lync client is not signed in.");
                    Console.ReadLine();
                }
                else
                {
                    if (args.Length > 0)
                    {
                        if (args[0].ToString().Contains("Group"))
                        {
                            SearchForGroups(args[1]);
                        }
                        if (args[0].ToString().Contains("Contact"))
                        {
                            SearchForContacts(args[1]);
                        }
                    }
                }
            }
            catch (ClientNotFoundException) { Console.WriteLine("Lync client was not found on startup"); }

        }

        /// <summary>
        /// Searches for any user whose display name contains the supplied
        /// search key
        /// </summary>
        /// <param name="searchKey">string. User name or partial name to search on</param>
        private void SearchForContacts(string searchKey)
        {
            Console.WriteLine(
                "Searching for contacts on " + 
                searchKey);

            _LyncClient.ContactManager.BeginSearch(
                searchKey, 
                (ar) => 
                {
                    SearchResults searchResults = _LyncClient.ContactManager.EndSearch(ar);
                    if (searchResults.Contacts.Count > 0)
                    {
                        Console.WriteLine(
                            searchResults.Contacts.Count.ToString() + 
                            " found");

                        foreach (Contact contact in searchResults.Contacts)
                        {
                            Console.WriteLine(
                                contact.GetContactInformation(ContactInformationType.DisplayName).ToString());
                        }
                    }
                }, 
                null);
        }

        /// <summary>
        /// Searches for any distribution group whose name contains the supplied
        /// search key
        /// </summary>
        /// <param name="searchKey">string. Group name or partial name to search on.</param>
        private void SearchForGroups(string searchKey)
        {
            Console.WriteLine(
                "Searching for groups on " + 
                searchKey);

            _LyncClient.ContactManager.BeginSearch(
                searchKey,
                (ar) =>
                {
                    SearchResults searchResults = _LyncClient.ContactManager.EndSearch(ar);
                    if (searchResults.Groups.Count > 0)
                    {
                        Console.WriteLine(
                            searchResults.Groups.Count.ToString() + 
                            " found");

                        foreach (Group group in searchResults.Groups)
                        {
                            Console.WriteLine(System.Environment.NewLine + group.Name);
                            DistributionGroup dGroup = group as DistributionGroup;
                            DGLister.Program.DGExpander(dGroup);
                        }
                    }
                    else
                    {
                        Console.WriteLine(
                            "No groups found for search on " + 
                            searchKey);
                    }
                },
                null);

        }
        /// <summary>
        /// Expands any groups found in search results 
        /// </summary>
        /// <param name="workMaterial"></param>
        static void DGExpander(DistributionGroup DGGroup)
        {

            //Only distribution groups can be expanded.
            //_Group is a class field that references the Microsoft.Lync.Model.Group.Group instance
            //encapsulated by the GroupModel class.
            if (DGGroup.Type != GroupType.DistributionGroup)
            {
                return;
            }

            //If the distribution group has not been expanded yet,
            //it must be expanded before group members are visible
            if (DGGroup.IsExpanded == false)
            {
                Console.WriteLine(
                    " -- Expanding " + 
                    DGGroup.Name + 
                    " -- ");

                DGGroup.BeginExpand(
                    (ar) => 
                    {
                        try
                        {
                            DGGroup.EndExpand(ar);
                        }
                        catch (LyncClientException)
                        {
                            Console.WriteLine(
                                "Lync Client Exception on expand " + 
                                DGGroup.Name);
                        }
                        DGLister.Program.PrintDGDetail(DGGroup);
                    },
                    null);
            }
            else
            {
                DGLister.Program.PrintDGDetail(DGGroup);
            }
        }

        /// <summary>
        /// Iterates on the contact collection in a distribution group and then
        /// prints the contact name + URI or recursively calls DGExpander when nested
        /// distribution groups are found.
        /// </summary>
        /// <param name="DGGroup"></param>
        static void PrintDGDetail(DistributionGroup DGGroup)
        {
            Console.WriteLine(
                System.Environment.NewLine + 
                " -- Getting contacts for " + 
                DGGroup.Name + " -- ");

            if (DGGroup.Count > 0)
            {
                foreach (Contact contact in DGGroup)
                {
                    Console.WriteLine(
                        "\t" + 
                        contact.GetContactInformation(ContactInformationType.DisplayName).ToString());
                }
            }
            if (DGGroup.NestedGroups.Count > 0)
            {
                foreach (Group group in DGGroup.NestedGroups)
                {
                    DistributionGroup dGroup = group as DistributionGroup;
                    Console.WriteLine(
                        System.Environment.NewLine + 
                        "\t\t #### Recursively calling DGExpander for " + 
                        group.Name + 
                        " ####");

                    DGLister.Program.DGExpander(dGroup);
                }
            }
        }

    }
}
```

## See also

  - [What you can do with Lync contact lists](what-you-can-do-with-lync-contact-lists.md)

