---
title: Utilities.BeginScheduleMeeting method (Contact, String, AsyncCallback, Object) (Microsoft.Lync.Model)
TOCTitle: BeginScheduleMeeting method (Contact, String, AsyncCallback, Object)
ms:assetid: M:Microsoft.Lync.Model.Utilities.BeginScheduleMeeting(Microsoft.Lync.Model.Contact,System.String,System.AsyncCallback,System.Object)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.utilities.beginschedulemeeting(v=office.15)
ms:contentKeyID: 48600594
ms.date: 07/28/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Utilities.BeginScheduleMeeting method (Contact, String, AsyncCallback, Object)

Launches a new Outlook Meeting window pre-populated with the email address of the specified contact and meeting subject string passed in the first two arguments of this method.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function BeginScheduleMeeting ( _
    to As Contact, _
    subject As String, _
    utilitiesCallback As AsyncCallback, _
    state As Object _
) As IAsyncResult
'Usage
Dim instance As Utilities
Dim to As Contact
Dim subject As String
Dim utilitiesCallback As AsyncCallback
Dim state As Object
Dim returnValue As IAsyncResult

returnValue = instance.BeginScheduleMeeting(to, _
    subject, utilitiesCallback, state)
```

``` csharp
public IAsyncResult BeginScheduleMeeting(
    Contact to,
    string subject,
    AsyncCallback utilitiesCallback,
    Object state
)
```

#### Parameters

  - to  
    Type: [Microsoft.Lync.Model.Contact](contact-class-microsoft-lync-model_2.md)  

<!-- end list -->

  - subject  
    Type: [System.String](http://msdn2.microsoft.com/en-us/library/s1wwdcbf)  

<!-- end list -->

  - utilitiesCallback  
    Type: [System.AsyncCallback](http://msdn2.microsoft.com/en-us/library/ckbe7yh5)  

<!-- end list -->

  - state  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.IAsyncResult](http://msdn2.microsoft.com/en-us/library/ft8a6455)  

## See also

#### Reference

[Utilities class](utilities-class-microsoft-lync-model_2.md)

[Utilities members](utilities-members-microsoft-lync-model_2.md)

[BeginScheduleMeeting overload](utilities-beginschedulemeeting-method-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

