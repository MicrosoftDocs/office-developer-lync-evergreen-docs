---
title: ContactInformationChangedEventArgs.ChangedContactInformation property  (Microsoft.Lync.Model)
TOCTitle: 'ChangedContactInformation property '
ms:assetid: P:Microsoft.Lync.Model.ContactInformationChangedEventArgs.ChangedContactInformation_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.contactinformationchangedeventargs.changedcontactinformation_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48592736
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.ContactInformationChangedEventArgs.ChangedContactInformation
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactInformationChangedEventArgs.ChangedContactInformation property

Returns the contact information that have changed.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public ReadOnly Property ChangedContactInformation As IList(Of ContactInformationType)
    Get
'Usage
Dim instance As ContactInformationChangedEventArgs
Dim value As IList(Of ContactInformationType)

value = instance.ChangedContactInformation
```

``` csharp
public IList<ContactInformationType> ChangedContactInformation { get; }
```

#### Property value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[ContactInformationType](contactinformationtype-enumeration-microsoft-lync-model_2.md)\>  

## See also

#### Reference

[ContactInformationChangedEventArgs class](contactinformationchangedeventargs-class-microsoft-lync-model_2.md)

[ContactInformationChangedEventArgs members](contactinformationchangedeventargs-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

