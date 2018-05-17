---
title: ContactSearch.InitializationFailed property  (Microsoft.Lync.Controls)
TOCTitle: 'InitializationFailed property '
ms:assetid: P:Microsoft.Lync.Controls.ContactSearch.InitializationFailed_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactsearch.initializationfailed_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48598178
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactSearch.InitializationFailed
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactSearch.InitializationFailed property

Gets a boolean value indicating whether initialization of the layer between Lync and the Lync controls has failed.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property InitializationFailed As Boolean
    Get
    Private Set
'Usage
Dim instance As ContactSearch
Dim value As Boolean

value = instance.InitializationFailed
```

``` csharp
public bool InitializationFailed { get; private set; }
```

#### Property value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  
True if initialization failed, false if initialization succeeded. The default value is false.  

## See also

#### Reference

[ContactSearch class](contactsearch-class-microsoft-lync-controls_1.md)

[ContactSearch members](contactsearch-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

