---
title: Enhanced Presence categories
TOCTitle: Enhanced Presence categories
ms:assetid: 2ec70dde-fe76-4a87-9eb4-e7516777e1a8
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454620(v=office.15)
ms:contentKeyID: 57093013
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Enhanced Presence categories


**Applies to:** Lync 2013 | Lync Server 2013

Enhanced presence data can include various types of information. For example, the availability of a user may be part of the user’s presence state type. Supported audio/video features may be of the user’s presence capabilities type. In a Microsoft Lync Server 2013 deployment, a type of enhanced presence data is known as a presence category or category. In other words, categories are enhanced presence data types.

A category is identified by a name and specifies syntax of the included presence information. A particular piece of presence data of a given category is known as the presence category instance.

Lync Server 2013 uses XML to represent enhanced presence information. In an XML representation, a category may be formally described by an XML Schema Definition (XSD) type and a category instance then corresponds to an XML element of the corresponding XSD type. The following example shows a portion of the XSD type definition of the [state category instance value elements](state-category-instance-value-elements.md) category.

``` 
  <!-- stateType is an abstract type used as a base type for specific state -->
  <xs:complexType name="stateType" abstract="true">
    <xs:sequence>
      <xs:element name="availability" type="xs:unsignedInt" minOccurs="0"/>
      <xs:element name="activity" type="tns:activityType" minOccurs="0" maxOccurs="unbounded"/>
      <xs:element name="endpointLocation" type="tns:endpointLocationEnumEx" minOccurs="0"/>
      
      <xs:element name="extension"  type="tns:extensionType" minOccurs="0" maxOccurs="1"/>

    </xs:sequence>
    <xs:attribute name="manual" type="xs:boolean" use="optional" default="false"/>
    <xs:attribute name="startTime" type="xs:dateTime" use="optional"/>
    <xs:attribute name="majorVersion" type="xs:unsignedInt" use="optional" />
    <xs:attribute name="minorVersion" type="xs:unsignedInt" use="optional" />
    <xs:anyAttribute processContents="lax"/>
  </xs:complexType>
```

According to this XSD type definition, every presence state category instance can contain zero or one [state/availability element](state-availability-element.md) element of the unsignedInt type, zero or more [state/activity element](state-activity-element.md) elements of the activityType, and zero or one [state/endpointLocation element](state-endpointlocation-element.md) element of the endpointLocationEnumEx type. In addition, an [state/extension element](state-extension-element.md) element of extensionType can be used to extend the presence state to include application-specific customization to the presence state definition.

The following shows the XSD definition of the user state category, which extends the abstract state type.

    <!-- userState is a concrete type derived from stateType -->
      <xs:complexType name="userState">
        <xs:complexContent>
          <xs:extension base="tns:stateType">
            <xs:sequence>
              <xs:sequence minOccurs="0" maxOccurs="1">
                <xs:sequence minOccurs="0" maxOccurs="unbounded">
                  <xs:element ref="ct:delimiter"/>
                  <xs:any namespace="##targetNamespace" processContents="lax" minOccurs="0" maxOccurs="unbounded"/>
                </xs:sequence>
                <xs:element ref="ct:end"/>
              </xs:sequence>
              <xs:element ref="ct:extension" minOccurs="0" maxOccurs="1"/>
            </xs:sequence>
          </xs:extension>
        </xs:complexContent>
      </xs:complexType>

The concrete XML type **userState** is derived from the abstract XML type **stateType** and inherits all the declarations from the abstract base type. In addition, **userState** can be extended using a sequence of XML elements from the same namespace or an [extension element](extension-element.md) element from another namespace. The complete XML type definition of the enhanced presence state category is specified in the state.xsd file that can be found in the installation directory of Microsoft Unified Communications Enhanced Presence Schemas for Microsoft Lync Server 2013.

Lync Server 2013 does not require that enhanced presence category elements be validated, although it does require that an XML element be well-formed and that the category names be registered with the server. Lync Server 2013 rejects a publication request when it encounters an unrecognized category name.

Using XSD types to define presence categories helps to facilitate how one application understands the category definition prescribed by other applications. This in turn helps to promote the reuse of enhanced presence categories and to support interoperability between applications.

In addition to defining enhanced presence data, categories as abstract data types can also be used to represent other application data including the system configurations, policies, or roaming data. In a Lync Server 2013 deployment, categories are used to represent contacts and groups, in-band provisioning data that include server configuration and policy settings, access control lists (containers), and other data.

## See also

#### Concepts

[Enhanced Presence category instances](enhanced-presence-category-instances.md)

[Enhanced Presence category schemas](enhanced-presence-category-schemas.md)

[Enhanced Presence data](enhanced-presence-data.md)

