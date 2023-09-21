---
title: Creating Enhanced Presence data classes from the XML schemas
TOCTitle: Creating Enhanced Presence data classes from the XML schemas
ms:assetid: 188c95cc-f3ec-41e9-ab4b-11283f08c18e
ms:mtpsurl: https://msdn.microsoft.com/library/Dn454686(v=office.15)
ms:contentKeyID: 57093253
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Creating Enhanced Presence data classes from the XML schemas


**Applies to:** Lync 2013 | Lync Server 2013

You can create C\# code from the schemas with Xsd.exe, the XML Schema Definition executable program.

For example, the schema for the presence note data types in the Unified Communications Enhanced Presence Schema is defined in the note.xsd file. According to the Enhanced Presence Schema, the presence note is represented by a **\<note\>** element that consists of a set of sub-elements as well as the majorVersion, minorVersion, and a possible custom attribute (\<anyAttribute\>). The sub-elements of the **\<note\>** element are defined to consist of the following:

  - One or more **\<body\>** elements.

  - An optional set of zero or more \<ct:delimiter\> and \<\#any\> element pairs where the optional set is closed by a \<ct:end\> element. \<ct:delimiter\> and \<ct:end\> are defined in the commontypes.xsd file.

  - An optional \<ct:extension\> element. \<ct:extension\> is defined in commontypes.xsd.

The **\<body\>** element contains the following attributes:

  - type, indicating the type of the note.

  - LCID, specifying the language ID of the note.

  - uri, identifying the publisher of the note.

  - startTime, showing the start time of the note publication.

  - endTime, showing the end time of the note publication.

For the complete presence note schema specification, see the note.xsd and commontypes.xsd files.

Because note.xsd makes references to the elements imported from commontypes.xsd, both files must be specified in order to generate the .NET Framework classes for the presence note.

The following command demonstrates how to generate C\# classes for presence note types.

    Xsd.exe /c note.xsd commontypes.xsd

The command flag **/c** is abbreviated for /class. It indicates that the transformation produces .NET Framework classes from the specified XML Schema Definition (XSD) files. The output is a C\# source file and the name of the output file is note\_commontypes.cs. To generate Visual Basic code, use the following command.

    Xsd.exe /c /l:VB note.xsd commontypes.xsd

The command parameter **/l** is abbreviated for /language. The value of this parameter indicates the programming language of the generated source code. In the previous example, the generated source code is Visual Basic. The name of the output file from the previous command example becomes note\_commontypes.vb.

To assign a namespace for the generated source code, use the following command.

    Xsd.exe /c /n:EnhancedPresence.Note note.xsd commontypes.xsd

The command parameter **/n** is abbreviated for /namespace , and the value of this parameter, EnhancedPresence.Note, is the C\# code namespace for the generated source code.

This procedure can be used with other schema files to generate additional Enhanced Presence data classes.

    Xsd.exe /c /n:EnhancedPresence.Calendata calendardata.xsd calendardatatypes.xsd commontypes.xsd
    xsd.exe /c /n:EnhancedPresence.ContactCard contactcard.xsd commontypes.xsd
    xsd.exe /c /n:EnhancedPresence.Device device.xsd commontypes.xsd
    xsd.exe /c /n:EnhancedPresence.Note note.xsd commontypes.xsd
    xsd.exe /c /n:EnhancedPresence.Options options-Alerts.xsd options-OtherOptions.xsd options-RccOptions.xsd options-UserInformation.xsd commontypes.xsd
    xsd.exe /c /n:EnhancedPresence.Service service.xsd commontypes.xsd
    xsd.exe /c /n:EnhancedPresence.State state.xsd commontypes.xsd 
    xsd.exe /c /n:EnhancedPresence.UserProperties userProperties.xsd commontypes.xsd

After the source files are created, you can also build a .NET Framework assembly using the following command.

    csc /out:enhancedPresence.dll /t:library /r:system.dll contactcard_commontypes.cs calendardata_calendardatatypes_commontypes.cs device_commontypes.cs note_commontypes.cs options-Alerts_options-OtherOptions_options-RccOptions_options-UserInformation_commontypes.cs service_commontypes.cs state_commontypes.cs userProperties_commontypes.cs

The output of this command is enhancedPresence.dll, a .NET Framework library.

With the assembly or the source files, you can now begin to instantiate the presence data classes, initialize the objects, and generate their corresponding XML representations using XML serialization supported by .NET Framework.

## See also

#### Concepts

[Instantiating and initializing an Enhanced Presence data class](instantiating-and-initializing-an-enhanced-presence-data-class.md)

[Serializing an Enhanced Presence data object to an XML element](serializing-an-enhanced-presence-data-object-to-an-xml-element.md)

[Serialization of Enhanced Presence category instances](serialization-of-enhanced-presence-category-instances.md)

