---
title: Self.GetPublishableCustomAvailabilityStates method  (Microsoft.Lync.Model)
TOCTitle: 'GetPublishableCustomAvailabilityStates method '
ms:assetid: M:Microsoft.Lync.Model.Self.GetPublishableCustomAvailabilityStates(System.Int32)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.self.getpublishablecustomavailabilitystates(v=office.15)
ms:contentKeyID: 48595826
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Self.GetPublishableCustomAvailabilityStates
dev_langs:
- CSharp
- JScript
- VB
- other
---

# Self.GetPublishableCustomAvailabilityStates method

Returns the array of CustomAvailabilityState objects based on the optional locale id.

**Namespace:**  [Microsoft.Lync.Model](microsoft-lync-model-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function GetPublishableCustomAvailabilityStates ( _
    localeId As Integer _
) As IList(Of CustomAvailabilityState)
'Usage
Dim instance As Self
Dim localeId As Integer
Dim returnValue As IList(Of CustomAvailabilityState)

returnValue = instance.GetPublishableCustomAvailabilityStates(localeId)
```

``` csharp
public IList<CustomAvailabilityState> GetPublishableCustomAvailabilityStates(
    int localeId
)
```

#### Parameters

  - localeId  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

#### Return value

Type: [System.Collections.Generic.IList](http://msdn2.microsoft.com/en-us/library/5y536ey6)\<[CustomAvailabilityState](customavailabilitystate-class-microsoft-lync-model_2.md)\>  
IEnumerable{System.Object}  

## See also

#### Reference

[Self class](self-class-microsoft-lync-model_2.md)

[Self members](self-members-microsoft-lync-model_2.md)

[Microsoft.Lync.Model namespace](microsoft-lync-model-namespace_2.md)

