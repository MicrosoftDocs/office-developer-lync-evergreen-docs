---
title: MSPL Script Syntax (Lync Server 2013 Preview SDK)
TOCTitle: MSPL Script Syntax (Lync Server 2013 Preview SDK)
ms:assetid: a9d51eef-2c32-49db-9f85-ab834ed96c5b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn439066(v=office.15)
ms:contentKeyID: 57096224
ms.date: 07/24/2014
mtps_version: v=office.15
---

# MSPL Script Syntax (Lync Server 2013 Preview SDK)

Learn about the Microsoft SIP Processing Language (MSPL) script syntax. This topic discusses supported and unsupported MSPL features and describes specific syntactical constructs.


**Applies to:** Lync 2013 | Lync Server 2013

## MSPL script syntax

### Supported features

  - Signed numeric constants

  - Unicode string literals

  - Array \[\] type (read-only for flat-file access)

  - Function invocation, with and without parameters

  - The structure member reference operator "." (for example: Structure.Member)

  - The following logical operators: "\!", "==", "\!=", "\<", "\<=", "\>", "\>="

  - Compound expressions

  - Compound statements

  - The "=" assignment operator

  - **if/else** statements

  - **switch/case** statements

  - **break**, **continue**, and **return** statements

  - null keyword

  - true/false keywords

  - Expression statements

  - End-of-line and multiline comments

### Unsupported features

  - Explicit (declarative) data types.

  - Type casting.

  - Pointers.

  - Arithmetic operations.

  - Function composition.

  - Preprocessor statements.

  - Attributes Static or global variables (state is not maintained across script invocations).

  - Declarations (other than basic function declarations, as detailed later in this topic).
    

    > [!NOTE]
    > <P>Although MSPL does not support explicit declaration, assignment expressions and <STRONG>foreach</STRONG> statements implicitly declare variables and set their values. Such variables are statically (lexically) scoped. In other words, the scope of these variables is limited to the local block (for example, a function) in which they are declared.</P>



### String literals

Because string values are delimited by double quotation marks, you must use the backslash (\\) to escape double quotation marks contained in a string. For example, represent the string preamble "message" postamble as follows: "preamble \\"message\\" postamble".

Represent Unicode literals by using the \\u character sequence followed by the specific 4-digit code. For example, represent the Cyrillic capital "psi" character as follows: \\u0470.

Prefixing a string with the "@" (at) symbol to disable backslash escape sequences is not supported.

### Functions

A function is the only declarative element in MSPL. Declare a function in a script by using the following syntax:

**function**identifier (optional\_parameter\_list) statement

For example:

    function ParseDisplayName (displayName) { ...
    }

All function definitions must occur at the beginning of the message filter script, before the body of the message filter script. A function can have zero or more parameters.

Function definitions cannot contain recursion of any type. For example, Function 1 cannot be defined so that it calls Function 1, nor can Function 1 be defined so that it calls Function 2 if Function 2 is defined so that it calls Function 1.

Functions pass parameters by value, and the type of the value that is passed as a parameter implicitly defines the parameter type.

Return value types are also implicitly defined. In other words, the return type is determined by the type of the value that is passed to the return statement. However, the only supported implicit return types are string, bool, int, and float. Functions cannot return collections.

In the following filter function example, if the content that is passed in to the function contains the word "confidential", the function returns true. Otherwise, it returns false.

    function FilterString (content) { filterWord =
    "confidential"; return ContainsString(content, filterWord, true);
    }

### foreach statement

The **foreach** statement lets script authors handle collections that ordinarily occur while processing SIP messages, such as contact header and endpoint collections. A **foreach** loop is invoked by using the following syntax:

**foreach** (elementinexpression) statement

For example:

    foreach (dbEndpoint in QueryEndpoints("someone@example.com")) { ...
    }

The expression evaluates to a collection. Strings and other unary types are treated as single-item collections. Collections cannot be created except by calling a built-in function that returns a collection (such as [QueryEndpoints](https://msdn.microsoft.com/en-us/library/hh364763\(v=office.15\))) or by referencing a built-in variable that contains a collection.

Inside a **foreach** loop, the **continue** statement is used to jump to the next iteration of the loop, ignoring any processing statements subsequent to the **continue** statement before the end of the loop.

### while statement

With the **while** statement, you can iterate the occurrences of certain patterns or states predicated on the specified Boolean statement. A **while** loop includes the following syntax.

    while (booleanExpression) { …;}


> [!NOTE]
> <P>A single <STRONG>while</STRONG> loop cannot exceed 500 iterations.</P>



### break statement

The **break** statement allows for the early termination of a switch/case branch or a **foreach** loop. The syntax is the same as in C\#.

A **break** statement must be present at the end of each **case** branch in a **switch** statement. "Fall-through" caused by case branches without a terminating **break** statement is not allowed.

### null keyword

Script applications can use the null keyword to differentiate between an empty string ("") and values that are not found. Applications written for Live Communications Server 2003 return the empty string. Passing null to any function that expects a string parameter generates a script error and causes the script to be terminated. The following functions return null to indicate a value not found or an error:

  - **GetDisplayName**

  - **GetHostName**

  - **GetParameterValue**

  - **GetScheme**

  - **GetUri**

  - **GetUriParameter**

  - **GetUserName**

  - **GetUserAtHost**

  - **QueryHomeServer**

In addition, **Message.Stamp** and **Message.StampPool** can both return null.

### Flat file access

MSPL supports the access of data in flat files by using the following array syntax, where placeholder values are shown in italic:

flatFileName\[index\].columnName

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Placeholder value</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>flatFileName</p></td>
<td><p>Specifies the value of the name attribute for the &lt;file&gt; element that identifies the file from which you want to read data.</p></td>
</tr>
<tr class="even">
<td><p>Index</p></td>
<td><p>Specifies a zero-based integer or key string. Key strings are valid only if the <strong>keyColumnName</strong> attribute for the &lt;file&gt; element is specified. In this case, the record index is looked up in an in-memory hash table. Integer indexes greater than or equal to the number of records, or a key string value that is not found in the in-memory hash table, cause the reference to return null. Key string references to a flat file together with no in-memory hash table generate a script error and cause script execution to be aborted.</p></td>
</tr>
<tr class="odd">
<td><p>columnName</p></td>
<td><p>Specifies the value of the name attribute for the &lt;column&gt; element from which you want to read data. The specified &lt;column&gt; must be contained within the &lt;file&gt; element specified by the value of <strong>flatFileName</strong>.</p></td>
</tr>
</tbody>
</table>


The \<file\> element as it might appear in an application manifest file appears in the next example. The \<file\> element identifies information about the location and structure of a particular flat file that the application uses.

    <file name="exampleFile"
        path=".\hostname.csv" keyColumnName="keyHostName" ignoreCase="true" static="true"
        delimitedBy="comma">
        <column name="keyHostName"/>
        <column name="valueTargetHost"/>
    </file>

The handle name for the file in this example is "exampleFile", and it is a csv file. When the application loads this file in memory, it creates a hash table that contains two columns named "keyHostName" and "valueTargetName." By assigning the value "keyHostName" to the **keyColumnName** attribute, the example indicates that the values that are contained in the "keyHostName" column serves as key string indexers for the in-memory hash table.

For more information about the content of the \<file\> element, see [file Element](https://msdn.microsoft.com/en-us/library/hh347232\(v=office.15\)).

In the following example script, the **GetHostName** function gets the host name piece of a URI. The MSPL expression on the right side uses the host name as the key string index to look up the corresponding value string in the "valueTargetHost" column of the hash table that is created for "exampleFile", and assigns this value to "targetHost."

    targetHost = exampleFile[GetHostName(sipRequest.RequestUri)].valueTargetHost;

## See also

#### Concepts

[Microsoft SIP Processing language Script (Lync Server 2013 Preview SDK)](microsoft-sip-processing-language-script-lync-server-2013-preview-sdk.md)

[Learn the basics of Lync Server 2013 SDK](learn-the-basics-of-lync-server-2013-sdk.md)

