---
title: Properties element (LyncDiagnostics element) (Lync SDN API Schema A)
TOCTitle: Properties element (LyncDiagnostics element)
ms:assetid: 04f8d9a3-f3a9-8d19-70ff-4276ce984b52
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn775133(v=office.15)
ms:contentKeyID: 62626107
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- xml
---

# Properties element (LyncDiagnostics element) 

(Lync SDN API Schema A)

Details of the Error.


**Applies to**: Lync 2013

## Element information

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Element type</strong></p></td>
<td><p>Not defined</p></td>
</tr>
<tr class="even">
<td><p><strong>Namespace</strong></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Schema file</strong></p></td>
<td><p>LyncSdnApi.Schema.A.xsd</p></td>
</tr>
</tbody>
</table>


## Definition

``` xml
<xs:element name="Properties" minOccurs="0">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="MSDiagnosticsPublic" minOccurs="0"></xs:element>
            <xs:element name="MSDiagnosticsClient" minOccurs="0"></xs:element>
            <xs:element name="MSDiagnostics" type="xs:string" minOccurs="0"></xs:element>
            <xs:element name="ResponseCode">
                <xs:attribute name="Code" type="xs:unsignedShort" use="required" />
            </xs:element>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as sequence, minOccurs, maxOccurs, and choice, see the definition section.

### Parent elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lyncdiagnostics-element-lync-sdn-api-schema-a.md">LyncDiagnostics</a></p></td>
<td><p>Not defined</p></td>
<td><p>The root element for output from the Lync SDN Manager.</p></td>
</tr>
</tbody>
</table>


### Child elements

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Element</p></th>
<th><p>Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="msdiagnostics-element-sdn-api-schema-a.md">MSDiagnostics</a></p></td>
<td><p>xs:string</p></td>
<td><p>Lync-specific diagnostics message for this error.</p></td>
</tr>
<tr class="even">
<td><p><a href="msdiagnosticsclient-element-sdn-api-schema-a.md">MSDiagnosticsClient</a></p></td>
<td><p>Not defined</p></td>
<td><p>Lync-specific diagnostics message from the client.</p></td>
</tr>
<tr class="odd">
<td><p><a href="msdiagnosticspublic-element-sdn-api-schema-a.md">MSDiagnosticsPublic</a></p></td>
<td><p>Not defined</p></td>
<td><p>Lync-specific public diagnostics message.</p></td>
</tr>
<tr class="even">
<td><p><a href="responsecode-element-sdn-api-schema-a.md">ResponseCode</a></p></td>
<td><p>Not defined</p></td>
<td><p>Message describing the error.</p></td>
</tr>
</tbody>
</table>


### Attributes

None.

