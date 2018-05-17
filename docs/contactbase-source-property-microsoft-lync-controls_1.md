---
title: ContactBase.Source property  (Microsoft.Lync.Controls)
TOCTitle: 'Source property '
ms:assetid: P:Microsoft.Lync.Controls.ContactBase.Source_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.controls.contactbase.source_di_3_uc_ocs14mreflyncwpf(v=office.15)
ms:contentKeyID: 48595824
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Controls.ContactBase.Source
dev_langs:
- CSharp
- JScript
- VB
- other
---

# ContactBase.Source property

Specifies a contact or distribution group to which this control should be bound.

**Namespace:**  [Microsoft.Lync.Controls](microsoft-lync-controls-namespace_1.md)  
**Assembly:**  Microsoft.Lync.Controls (in Microsoft.Lync.Controls.dll)

## Syntax

``` vb
'Declaration
Public Property Source As Object
    Get
    Set
'Usage
Dim instance As ContactBase
Dim value As Object

value = instance.Source

instance.Source = value
```

``` csharp
public Object Source { get; set; }
```

#### Property value

Type: [System.Object](http://msdn2.microsoft.com/en-us/library/e5kfa45b)  

## Exceptions

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Exception</th>
<th>Condition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a href="http://msdn2.microsoft.com/en-us/library/3w1b3114">ArgumentException</a></td>
<td><p>Thrown when an invalid object type is provided.</p></td>
</tr>
</tbody>
</table>


## Remarks

Valid values for this property include: TypeValuestringSearch fragment, such as **\[mary\]**stringSIP URI, such as **\[sip:mary@contoso.com\]**Contact[Contact](contact-class-microsoft-lync-model_2.md) object, obtained using the Lync Platform API.DistributionGroup[DistributionGroup](distributiongroup-class-microsoft-lync-model-group_2.md) object, obtained using the Lync Platform API.DistributionGroup These options are shown in increasing order of performance. If a search fragment is used, the control will perform a best-effort match (non-deterministic)

## See also

#### Reference

[ContactBase class](contactbase-class-microsoft-lync-controls_1.md)

[ContactBase members](contactbase-members-microsoft-lync-controls_1.md)

[Microsoft.Lync.Controls namespace](microsoft-lync-controls-namespace_1.md)

