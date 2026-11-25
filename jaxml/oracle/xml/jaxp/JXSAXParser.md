Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](JXDocumentBuilderFactory.md)**
- **[Next Class](JXSAXParserFactory.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.jaxp**

## **Class JXSAXParser**

- **java.lang.Object**

- - **[javax.xml.parsers.SAXParser](../../../javax/xml/parsers/SAXParser.md)**

  - - **oracle.xml.jaxp.JXSAXParser**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class JXSAXParser
      extends SAXParser

  **Defines the API that wraps an `org.xml.sax.XMLReader` implementation class. In JAXP 1.0, this class wrapped the `org.xml.sax.Parser` interface, however this interface was replaced by the `XMLReader`. For ease of transition, this class continues to support the same name and interface as well as supporting new methods. An instance of this class can be obtained from the `SAXParserFactory.newSAXParser` method. Once an instance of this class is obtained, XML can be parsed from a variety of input sources. These input sources are InputStreams, Files, URLs, and SAX InputSources.**
  **This static method creates a new factory instance based on a system property setting or uses the platform default if no property has been defined.**

  **The system property that controls which Factory implementation to create is named "javax.xml.style.TransformFactory". This property names a class that is a concrete subclass of this abstract class. If no property is defined, a platform default will be used.**

  **As the content is parsed by the underlying parser, methods of the given `HandlerBase` are called.**
  **Since:**
  **JAXP 1.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                                                                                                  |
    |--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Parser`](../../../org/xml/sax/Parser.md)       | `getParser``()`<br>Deprecated. <br>Use getXMLReader()                                                                                                                                                                                                                   |
    | `java.lang.Object`                               | `getProperty``(java.lang.String name)`<br>returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader.                                                                                                                      |
    | [`XMLReader`](../../../org/xml/sax/XMLReader.md) | `getXMLReader``()`<br>Returns the XMLReader that is encapsulated by the implementation of this class.                                                                                                                                                                   |
    | `boolean`                                        | `isNamespaceAware``()`<br>Indicates whether or not this parser is configured to understand namespaces.                                                                                                                                                                  |
    | `boolean`                                        | `isValidating``()`<br>Indicates whether or not this parser is configured to validate XML documents.                                                                                                                                                                     |
    | `void`                                           | `parse``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` is, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh)`<br>Parse the content given `org.xml.sax.InputSource` as XML using the specified `org.xml.sax.helpers.DefaultHandler`.     |
    | `void`                                           | `parse``(java.io.InputStream is, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh)`<br>Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.helpers.DefaultHandler`.                            |
    | `void`                                           | `parse``(java.io.InputStream is, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh, java.lang.String systemId)`<br>Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.helpers.DefaultHandler`. |
    | `void`                                           | `parse``(java.io.InputStream is, `[`HandlerBase`](../../../org/xml/sax/HandlerBase.md)` hb, java.lang.String systemId)`<br>Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.HandlerBase`.                          |
    | `void`                                           | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Sets the particular property in the underlying implementation of org.xml.sax.XMLReader.                                                                                                               |

    - ### Methods inherited from class javax.xml.parsers.[SAXParser](../../../javax/xml/parsers/SAXParser.md)

      [`parse`](../../../javax/xml/parsers/SAXParser.md)`, `[`parse`](../../../javax/xml/parsers/SAXParser.md)`, `[`parse`](../../../javax/xml/parsers/SAXParser.md)`, `[`parse`](../../../javax/xml/parsers/SAXParser.md)`, `[`parse`](../../../javax/xml/parsers/SAXParser.md)`, `[`parse`](../../../javax/xml/parsers/SAXParser.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getParser

          public Parser getParser()
                           throws SAXException

      Deprecated. Use getXMLReader()
      Returns the SAX parser that is encapsultated by the implementation of this class.
      Specified by:
      [`getParser`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### getXMLReader

          public XMLReader getXMLReader()
                                 throws SAXException

      Returns the XMLReader that is encapsulated by the implementation of this class.
      Specified by:
      [`getXMLReader`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### isNamespaceAware

          public boolean isNamespaceAware()

      Indicates whether or not this parser is configured to understand namespaces.
      Specified by:
      [`isNamespaceAware`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

    <!-- -->

    - #### isValidating

          public boolean isValidating()

      Indicates whether or not this parser is configured to validate XML documents.
      Specified by:
      [`isValidating`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String name,
                                  java.lang.Object value)
                           throws SAXNotRecognizedException,
                                  SAXNotSupportedException

      Sets the particular property in the underlying implementation of org.xml.sax.XMLReader.
      Specified by:
      [`setProperty`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Parameters:
      `name` - The name of the property to be set.

      `value` - The value of the property to be set.

      Throws:
      [`SAXNotRecognizedException`](../../../org/xml/sax/SAXNotRecognizedException.md) - When the underlying XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../org/xml/sax/SAXNotSupportedException.md) - When the underlying XMLReader recognizes the property name but doesn't support the property.

      See Also:
      [`XMLReader.setProperty(java.lang.String, java.lang.Object)`](../../../org/xml/sax/XMLReader.md)

    <!-- -->

    - #### getProperty

          public java.lang.Object getProperty(java.lang.String name)
                                       throws SAXNotRecognizedException,
                                              SAXNotSupportedException

      returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader.
      Specified by:
      [`getProperty`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Parameters:
      `name` - The name of the property to be retrieved.

      Returns:
      Value of the requested property.

      Throws:
      [`SAXNotRecognizedException`](../../../org/xml/sax/SAXNotRecognizedException.md) - When the underlying XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../org/xml/sax/SAXNotSupportedException.md) - When the underlying XMLReader recognizes the property name but doesn't support the property.

      See Also:
      [`XMLReader.getProperty(java.lang.String)`](../../../org/xml/sax/XMLReader.md)

    <!-- -->

    - #### parse

          public void parse(java.io.InputStream is,
                            HandlerBase hb,
                            java.lang.String systemId)
                     throws SAXException,
                            java.io.IOException

      Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.HandlerBase`. *Use of the DefaultHandler version of this method is recommended as the HandlerBase class has been deprecated in SAX 2.0*
      Overrides:
      [`parse`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Parameters:
      `is` - InputStream containing the content to be parsed.

      `hb` - The SAX HandlerBase to use.

      `systemId` - The systemId which is needed for resolving relative URIs.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the given InputStream is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`version of this method instead.`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(java.io.InputStream is,
                            DefaultHandler dh)
                     throws SAXException,
                            java.io.IOException

      Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.helpers.DefaultHandler`.
      Overrides:
      [`parse`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Parameters:
      `is` - InputStream containing the content to be parsed.

      `dh` - The SAX DefaultHandler to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the given InputStream is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(java.io.InputStream is,
                            DefaultHandler dh,
                            java.lang.String systemId)
                     throws SAXException,
                            java.io.IOException

      Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.helpers.DefaultHandler`.
      Overrides:
      [`parse`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Parameters:
      `is` - InputStream containing the content to be parsed.

      `dh` - The SAX DefaultHandler to use.

      `systemId` - The systemId which is needed for resolving relative URIs.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the given InputStream is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`version of this method instead.`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(InputSource is,
                            DefaultHandler dh)
                     throws SAXException,
                            java.io.IOException

      Parse the content given `org.xml.sax.InputSource` as XML using the specified `org.xml.sax.helpers.DefaultHandler`.
      Overrides:
      [`parse`](../../../javax/xml/parsers/SAXParser.md) in class [`SAXParser`](../../../javax/xml/parsers/SAXParser.md)

      Parameters:
      `is` - The InputSource containing the content to be parsed.

      `dh` - The SAX DefaultHandler to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the InputSource is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](JXDocumentBuilderFactory.md)**
- **[Next Class](JXSAXParserFactory.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
