---
title: Instantiating and initializing an Enhanced Presence data class
TOCTitle: Instantiating and initializing an Enhanced Presence data class
ms:assetid: 5dcce19b-ff0b-4809-9259-33a375be4f21
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Dn454687(v=office.15)
ms:contentKeyID: 57093343
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Instantiating and initializing an Enhanced Presence data class


**Applies to:** Lync 2013 | Lync Server 2013

**In this article**  
Include generated classes in Visual Studio projects  
Instantiate and initialize the Enhanced Presence data class for note  
Instantiate and initialize the Enhanced Presence data class for machine state  

To generate the XML elements for Enhanced Presence data in a .NET Framework application, you must add the generated classes or their references to the application's project, instantiate desired presence data classes, assign appropriate values to the presence object, and then serialize them into their XML representation. The first three steps are discussed in this topic, and the fourth step is discussed in [Serializing an Enhanced Presence data object to an XML element](serializing-an-enhanced-presence-data-object-to-an-xml-element.md).

## Include generated classes in Visual Studio projects

After you create the C\# classes using Unified Communications Enhanced Presence Schema and XML Schema Definition (XSD) files, you can incorporate them into your project in one of the following ways:

  - Include the source (.cs) file directly in your project.

  - Include the compiled assembly (.dll) containing the Enhanced Presence Data classes in your project and add a reference to it.

### To include the source files in a Visual Studio project

1.  Start Microsoft Visual Studio development system.

2.  On the File menu, select New Project to create a new project or select Open Project to open an existing one.

3.  In Solution Explorer, right-click the project name, click Add, and then click Existing Item.

4.  In the Add Existing Item dialog box, locate the directory containing the generated presence data classes, highlight all the files of interest, and then click Add.

### To include the assembly in a Visual Studio project

1.  Start Visual Studio.

2.  On the File menu, select New Project to create a new project or select Open Project to open an existing one.

3.  In Solution Explorer, right-click the project name, and then click Add Reference.

4.  In the **Add Reference** dialog box, select the **Browse** tab, locate the directory containing the assembly compiled from the presence data class source files, and then click the file name.

## Instantiate and initialize the Enhanced Presence data class for note

Enhanced Presence note data is represented by a **\<note\>** element as defined in the note.xsd file. The structure of the **\<note\>** element is prescribed by the complex type named noteType. Xsd.exe, the XML Schema Definition executable program, translates this type into a C\# class of the same name. To generate a **\<note\>** element in a C\# application, you instantiate the noteType class and assign appropriate values to the newly created noteType instance, and then serialize this initialized noteType object into a **\<note\>** element according to the definition of the XSD type named noteType. These steps appear in the following example.

``` csharp
            noteType note = new noteType();
            noteTypeBody body = new noteTypeBody();
            body.Value = "My Note Text2!";
            note.body = new noteTypeBody[] { body };
            body.type = "personal";
            body.uri = "";
            string _noteXml = Serialize(note, typeof(noteType));
```

In the previous example, Serialize is a method that serializes the **note** object into a **\<note\>** element as prescribed by the noteType in the note.xsd file. The implementation of the Serialize method is discussed in [Serializing an Enhanced Presence data object to an XML element](serializing-an-enhanced-presence-data-object-to-an-xml-element.md). The second parameter of the Serialize method determines what type of XML element is created to hold the data contained in the first parameter.

The output from the previous example.

    <note xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
          xmlns="http://schemas.microsoft.com/2006/09/sip/note">
       <body
          type="personal"
          uri="">My Note Text2!
       </body>
    </note>

## Instantiate and initialize the Enhanced Presence data class for machine state

In the state.xsd file, there is a complex type named machineState, but the XML element representing a machineState instance is **\<state\>**. **\<state\>** is used because the machineState type is derived from the abstract stateType type. An abstract type in XSD corresponds to an abstract class in the generated C\# code and cannot be instantiated.

To generate an XML element for a machine state in a .NET Framework application, you must instantiate the machineState class, assign appropriate values, and then serialize the initialized machineState object into a **\<state\>** element that is prescribed by the stateType type.

``` csharp
            uint _onlineAvail = 3500;
            machineState mState = new machineState();
            mState.availability = (uint)_onlineAvail;
            mState.availabilitySpecified = true;
            mState.manual = false;
            string _machineStateXml = Serialize(mState, typeof(stateType));
```

The stateType must be specified in the second parameter passed into the Serialize method. The output from the previous example.

    <state xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
           xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xsi:type="machineState" 
           xmlns="http://schemas.microsoft.com/2006/09/sip/state">
       <availability>3500</availability>
    </state>

If you pass typeof(machineState) as the second parameter into the Serialize method in the previous example, the output changes.

    <machineState xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
                  xmlns:xsd="http://www.w3.org/2001/XMLSchema">
       <availability xmlns="http://schemas.microsoft.com/2006/09/sip/state">3500</availability>
    </machineState>

Unfortunately, this type of element is not defined by the Enhanced Presence state schema and any publication of this element is ignored.

## See also

#### Concepts

[Creating Enhanced Presence data classes from the XML schemas](creating-enhanced-presence-data-classes-from-the-xml-schemas.md)

[Serializing an Enhanced Presence data object to an XML element](serializing-an-enhanced-presence-data-object-to-an-xml-element.md)

[Serialization of Enhanced Presence category instances](serialization-of-enhanced-presence-category-instances.md)

