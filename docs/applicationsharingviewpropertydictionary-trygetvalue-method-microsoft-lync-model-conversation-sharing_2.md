---
title: ApplicationSharingViewPropertyDictionary.TryGetValue method  (Microsoft.Lync.Model.Conversation.Sharing)
TOCTitle: 'TryGetValue method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingViewPropertyDictionary.TryGetValue(Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingViewProperty,System.Object@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.sharing.applicationsharingviewpropertydictionary.trygetvalue(v=office.15)
ms:contentKeyID: 56371002
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingViewPropertyDictionary.TryGetValue
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ApplicationSharingViewPropertyDictionary.TryGetValue method

**Namespace:**  [Microsoft.Lync.Model.Conversation.Sharing](microsoft-lync-model-conversation-sharing-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Function TryGetValue ( _
    propertyType As ApplicationSharingViewProperty, _
    <OutAttribute> ByRef itemValue As Object _
) As Boolean
'Usage
Dim instance As ApplicationSharingViewPropertyDictionary
Dim propertyType As ApplicationSharingViewProperty
Dim itemValue As Object
Dim returnValue As Boolean

returnValue = instance.TryGetValue(propertyType, _
    itemValue)
```

``` csharp
public bool TryGetValue(
    ApplicationSharingViewProperty propertyType,
    out Object itemValue
)
```

#### Parameters

  - propertyType  
    Type: [Microsoft.Lync.Model.Conversation.Sharing.ApplicationSharingViewProperty](applicationsharingviewproperty-enumeration-microsoft-lync-model-conversation-sharing_2.md)  

<!-- end list -->

  - itemValue  
    Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

#### Return value

Type: [System.Boolean](http://msdn2.microsoft.com/en-us/library/a28wyd50)  

#### Implements

[IDictionary\<TKey, TValue\>.TryGetValue(TKey, TValue)](http://msdn2.microsoft.com/en-us/library/bb299639)  

## See also

#### Reference

[ApplicationSharingViewPropertyDictionary class](applicationsharingviewpropertydictionary-class-microsoft-lync-model-conversation-sharing_2.md)

[ApplicationSharingViewPropertyDictionary members](applicationsharingviewpropertydictionary-members-microsoft-lync-model-conversation-sharing_2.md)

[Microsoft.Lync.Model.Conversation.Sharing namespace](microsoft-lync-model-conversation-sharing-namespace_2.md)

