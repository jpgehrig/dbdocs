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

- **[Prev Package](../../w3c/dom/validation/package-summary.md)**
- **[Next Package](ext/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package org.xml.sax**

**SAX is Simple API for XML, this package provides the core SAX APIs.**

**See: Description**

- **Interface Summary**

  | Interface                             | Description                                                                                                                                   |
  |---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
  | [AttributeList](AttributeList.md)     | Deprecated<br>This interface has been replaced by the SAX2 [`Attributes`](Attributes.md) interface, which includes Namespace support.         |
  | [Attributes](Attributes.md)           | Interface for a list of XML attributes.                                                                                                       |
  | [ContentHandler](ContentHandler.md)   | Receive notification of the logical content of a document.                                                                                    |
  | [DocumentHandler](DocumentHandler.md) | Deprecated<br>This interface has been replaced by the SAX2 [`ContentHandler`](ContentHandler.md) interface, which includes Namespace support. |
  | [DTDHandler](DTDHandler.md)           | Receive notification of basic DTD-related events.                                                                                             |
  | [EntityResolver](EntityResolver.md)   | Basic interface for resolving entities.                                                                                                       |
  | [ErrorHandler](ErrorHandler.md)       | Basic interface for SAX error handlers.                                                                                                       |
  | [Locator](Locator.md)                 | Interface for associating a SAX event with a document location.                                                                               |
  | [Parser](Parser.md)                   | Deprecated<br>This interface has been replaced by the SAX2 [`XMLReader`](XMLReader.md) interface, which includes Namespace support.           |
  | [XMLFilter](XMLFilter.md)             | Interface for an XML filter.                                                                                                                  |
  | [XMLReader](XMLReader.md)             | Interface for reading an XML document using callbacks.                                                                                        |

- **Class Summary**

  | Class                         | Description                                                                                           |
  |-------------------------------|-------------------------------------------------------------------------------------------------------|
  | [HandlerBase](HandlerBase.md) | Deprecated<br>This class works with the deprecated [`DocumentHandler`](DocumentHandler.md) interface. |
  | [InputSource](InputSource.md) | A single input source for an XML entity.                                                              |

- **Exception Summary**

  | Exception                                                 | Description                                     |
  |-----------------------------------------------------------|-------------------------------------------------|
  | [SAXException](SAXException.md)                           | Encapsulate a general SAX error or warning.     |
  | [SAXNotRecognizedException](SAXNotRecognizedException.md) | Exception class for an unrecognized identifier. |
  | [SAXNotSupportedException](SAXNotSupportedException.md)   | Exception class for an unsupported operation.   |
  | [SAXParseException](SAXParseException.md)                 | Encapsulate an XML parse error or warning.      |

## **Package org.xml.sax Description**

**SAX is Simple API for XML, this package provides the core SAX APIs.
**

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

- **[Prev Package](../../w3c/dom/validation/package-summary.md)**
- **[Next Package](ext/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
