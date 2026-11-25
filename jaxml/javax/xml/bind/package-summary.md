Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../../jcr/version/package-summary.md)**
- **[Next Package](../parsers/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package javax.xml.bind**

**Provides a runtime binding framework for client applications including unmarshalling, marshalling, and validation capabilities.**

**See: Description**

- **Interface Summary**

  | Interface                                           | Description                                                                                                                                                                                 |
  |-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [Element](Element.md)                               | This is an element marker interface.                                                                                                                                                        |
  | [Marshaller](Marshaller.md)                         | The `Marshaller` class is responsible for governing the process of serializing Java content trees back into XML data.                                                                       |
  | [NotIdentifiableEvent](NotIdentifiableEvent.md)     | This event indicates that a problem was encountered resolvin an ID/IDREF.                                                                                                                   |
  | [ParseConversionEvent](ParseConversionEvent.md)     | This event indicates that a problem was encountered while converting a string from the XML data into a value of the target Java data type.                                                  |
  | [PrintConversionEvent](PrintConversionEvent.md)     | This event indicates that a problem was encountered while converting data from the Java content tree into its lexical representation.                                                       |
  | [Unmarshaller](Unmarshaller.md)                     | The `Unmarshaller` class governs the process of deserializing XML data into newly created Java content trees, optionally validating the XML data as it is unmarshalled.                     |
  | [UnmarshallerHandler](UnmarshallerHandler.md)       | Unmarshaller implemented as SAX ContentHandler.                                                                                                                                             |
  | [ValidationEvent](ValidationEvent.md)               | This event indicates that a problem was encountered while validating the incoming XML data during an unmarshal operation or while performing on-demand validation of the Java content tree. |
  | [ValidationEventHandler](ValidationEventHandler.md) | A basic event handler interface for validation errors.                                                                                                                                      |
  | [ValidationEventLocator](ValidationEventLocator.md) | Encapsulate the location of a ValidationEvent.                                                                                                                                              |
  | [Validator](Validator.md)                           | The `Validator` class is responsible for controlling the validation of content trees during runtime.                                                                                        |

- **Class Summary**

  | Class                         | Description                                                                |
  |-------------------------------|----------------------------------------------------------------------------|
  | [JAXBContext](JAXBContext.md) | The `JAXBContext` class provides the client's entry point to the JAXB API. |

- **Exception Summary**

  | Exception                                             | Description                                                                                                                          |
  |-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
  | [JAXBException](JAXBException.md)                     | This is the root exception class for all JAXB exceptions.                                                                            |
  | [MarshalException](MarshalException.md)               | This exception indicates that an error has occured while performing a marshal operation that the provider is unable to recover from. |
  | [PropertyException](PropertyException.md)             | This exception indicates that an error was encountered while getting or setting a property.                                          |
  | [TypeConstraintException](TypeConstraintException.md) | This exception indicates that a violation of a dynamically checked type constraint was detected.                                     |
  | [UnmarshalException](UnmarshalException.md)           | This exception indicates that an error has occured while performing an unmarshal operation.                                          |
  | [ValidationException](ValidationException.md)         | This exception indicates that an error has occured while performing a validate operation.                                            |

## **Package javax.xml.bind Description**

**Provides a runtime binding framework for client applications including unmarshalling, marshalling, and validation capabilities.**

**`JaxbContext` is the client-entry point to the runtime binding framework.**

## **Package Specification**

- **[JAXB Specification](http://java.sun.com/xml/downloads/jaxb.html)**

## **Related Documentation**

**For overviews, tutorials, examples, guides, and tool documentation, please see:**

- **The [JAXB Website](http://java.sun.com/xml/jaxb/index.html)**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../../jcr/version/package-summary.md)**
- **[Next Package](../parsers/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
