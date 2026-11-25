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

- **[Prev Class](ParserConfigurationException.md)**
- **[Next Class](SAXParserFactory.md)**

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

**javax.xml.parsers**

## **Class SAXParser**

- **java.lang.Object**

- - **javax.xml.parsers.SAXParser**

<!-- -->

- **Direct Known Subclasses:**
  **[JXSAXParser](../../../oracle/xml/jaxp/JXSAXParser.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class SAXParser
      extends java.lang.Object

  **Defines the API that wraps an `org.xml.sax.XMLReader` implementation class. In JAXP 1.0, this class wrapped the `org.xml.sax.Parser` interface, however this interface was replaced by the `XMLReader`. For ease of transition, this class continues to support the same name and interface as well as supporting new methods. An instance of this class can be obtained from the `SAXParserFactory.newSAXParser` method. Once an instance of this class is obtained, XML can be parsed from a variety of input sources. These input sources are InputStreams, Files, URLs, and SAX InputSources.**
  **This static method creates a new factory instance based on a system property setting or uses the platform default if no property has been defined.**

  **The system property that controls which Factory implementation to create is named "javax.xml.parsers.SAXParserFactory". This property names a class that is a concrete subclass of this abstract class. If no property is defined, a platform default will be used.**

  **As the content is parsed by the underlying parser, methods of the given `HandlerBase` or the `DefaultHandler` are called.**
  **Implementors of this class which wrap an underlaying implementation can consider using the `org.xml.sax.helpers.ParserAdapter` class to initially adapt their SAX1 impelemntation to work under this revised class.**

  **Since:**
  **JAXP 1.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                                                                                                                  |
    |-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`Parser`](../../../org/xml/sax/Parser.md)       | `getParser``()`<br>Returns the SAX parser that is encapsultated by the implementation of this class.                                                                                                                                                                    |
    | `abstract java.lang.Object`                                 | `getProperty``(java.lang.String name)`<br>returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader.                                                                                                                      |
    | `abstract `[`XMLReader`](../../../org/xml/sax/XMLReader.md) | `getXMLReader``()`<br>Returns the XMLReader that is encapsulated by the implementation of this class.                                                                                                                                                                   |
    | `abstract boolean`                                          | `isNamespaceAware``()`<br>Indicates whether or not this parser is configured to understand namespaces.                                                                                                                                                                  |
    | `abstract boolean`                                          | `isValidating``()`<br>Indicates whether or not this parser is configured to validate XML documents.                                                                                                                                                                     |
    | `void`                                                      | `parse``(java.io.File f, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh)`<br>Parse the content of the file specified as XML using the specified `org.xml.sax.helpers.DefaultHandler`.                                                          |
    | `void`                                                      | `parse``(java.io.File f, `[`HandlerBase`](../../../org/xml/sax/HandlerBase.md)` hb)`<br>Parse the content of the file specified as XML using the specified `org.xml.sax.HandlerBase`.                                                                                   |
    | `void`                                                      | `parse``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` is, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh)`<br>Parse the content given `org.xml.sax.InputSource` as XML using the specified `org.xml.sax.helpers.DefaultHandler`.     |
    | `void`                                                      | `parse``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` is, `[`HandlerBase`](../../../org/xml/sax/HandlerBase.md)` hb)`<br>Parse the content given `org.xml.sax.InputSource` as XML using the specified `org.xml.sax.HandlerBase`.                              |
    | `void`                                                      | `parse``(java.io.InputStream is, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh)`<br>Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.helpers.DefaultHandler`.                            |
    | `void`                                                      | `parse``(java.io.InputStream is, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh, java.lang.String systemId)`<br>Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.helpers.DefaultHandler`. |
    | `void`                                                      | `parse``(java.io.InputStream is, `[`HandlerBase`](../../../org/xml/sax/HandlerBase.md)` hb)`<br>Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.HandlerBase`.                                                     |
    | `void`                                                      | `parse``(java.io.InputStream is, `[`HandlerBase`](../../../org/xml/sax/HandlerBase.md)` hb, java.lang.String systemId)`<br>Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.HandlerBase`.                          |
    | `void`                                                      | `parse``(java.lang.String uri, `[`DefaultHandler`](../../../org/xml/sax/helpers/DefaultHandler.md)` dh)`<br>Parse the content described by the giving Uniform Resource Identifier (URI) as XML using the specified `org.xml.sax.helpers.DefaultHandler`.                |
    | `void`                                                      | `parse``(java.lang.String uri, `[`HandlerBase`](../../../org/xml/sax/HandlerBase.md)` hb)`<br>Parse the content described by the giving Uniform Resource Identifier (URI) as XML using the specified `org.xml.sax.HandlerBase`.                                         |
    | `abstract void`                                             | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Sets the particular property in the underlying implementation of org.xml.sax.XMLReader.                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### parse

          public void parse(java.io.InputStream is,
                            HandlerBase hb)
                     throws SAXException,
                            java.io.IOException

      Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.HandlerBase`. *Use of the DefaultHandler version of this method is recommended as the HandlerBase class has been deprecated in SAX 2.0*
      Parameters:
      `is` - InputStream containing the content to be parsed.

      `hb` - The SAX HandlerBase to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the given InputStream is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(java.io.InputStream is,
                            HandlerBase hb,
                            java.lang.String systemId)
                     throws SAXException,
                            java.io.IOException

      Parse the content of the given `java.io.InputStream` instance as XML using the specified `org.xml.sax.HandlerBase`. *Use of the DefaultHandler version of this method is recommended as the HandlerBase class has been deprecated in SAX 2.0*
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

          public void parse(java.lang.String uri,
                            HandlerBase hb)
                     throws SAXException,
                            java.io.IOException

      Parse the content described by the giving Uniform Resource Identifier (URI) as XML using the specified `org.xml.sax.HandlerBase`. *Use of the DefaultHandler version of this method is recommended as the HandlerBase class has been deprecated in SAX 2.0*
      Parameters:
      `uri` - The location of the content to be parsed.

      `hb` - The SAX HandlerBase to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the uri is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(java.lang.String uri,
                            DefaultHandler dh)
                     throws SAXException,
                            java.io.IOException

      Parse the content described by the giving Uniform Resource Identifier (URI) as XML using the specified `org.xml.sax.helpers.DefaultHandler`.
      Parameters:
      `uri` - The location of the content to be parsed.

      `dh` - The SAX DefaultHandler to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the uri is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(java.io.File f,
                            HandlerBase hb)
                     throws SAXException,
                            java.io.IOException

      Parse the content of the file specified as XML using the specified `org.xml.sax.HandlerBase`. *Use of the DefaultHandler version of this method is recommended as the HandlerBase class has been deprecated in SAX 2.0*
      Parameters:
      `f` - The file containing the XML to parse

      `hb` - The SAX HandlerBase to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the File object is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(java.io.File f,
                            DefaultHandler dh)
                     throws SAXException,
                            java.io.IOException

      Parse the content of the file specified as XML using the specified `org.xml.sax.helpers.DefaultHandler`.
      Parameters:
      `f` - The file containing the XML to parse

      `dh` - The SAX DefaultHandler to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the File object is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(InputSource is,
                            HandlerBase hb)
                     throws SAXException,
                            java.io.IOException

      Parse the content given `org.xml.sax.InputSource` as XML using the specified `org.xml.sax.HandlerBase`. *Use of the DefaultHandler version of this method is recommended as the HandlerBase class has been deprecated in SAX 2.0*
      Parameters:
      `is` - The InputSource containing the content to be parsed.

      `hb` - The SAX HandlerBase to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the InputSource is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public void parse(InputSource is,
                            DefaultHandler dh)
                     throws SAXException,
                            java.io.IOException

      Parse the content given `org.xml.sax.InputSource` as XML using the specified `org.xml.sax.helpers.DefaultHandler`.
      Parameters:
      `is` - The InputSource containing the content to be parsed.

      `dh` - The SAX DefaultHandler to use.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      `java.lang.IllegalArgumentException` - If the InputSource is null.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### getParser

          public abstract Parser getParser()
                                    throws SAXException

      Returns the SAX parser that is encapsultated by the implementation of this class.
      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### getXMLReader

          public abstract XMLReader getXMLReader()
                                          throws SAXException

      Returns the XMLReader that is encapsulated by the implementation of this class.
      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### isNamespaceAware

          public abstract boolean isNamespaceAware()

      Indicates whether or not this parser is configured to understand namespaces.

    <!-- -->

    - #### isValidating

          public abstract boolean isValidating()

      Indicates whether or not this parser is configured to validate XML documents.

    <!-- -->

    - #### setProperty

          public abstract void setProperty(java.lang.String name,
                                           java.lang.Object value)
                                    throws SAXNotRecognizedException,
                                           SAXNotSupportedException

      Sets the particular property in the underlying implementation of org.xml.sax.XMLReader. A list of the core features and properties can be found at <http://www.megginson.com/SAX/Java/features.html>
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

          public abstract java.lang.Object getProperty(java.lang.String name)
                                                throws SAXNotRecognizedException,
                                                       SAXNotSupportedException

      returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader.
      Parameters:
      `name` - The name of the property to be retrieved.

      Returns:
      Value of the requested property.

      Throws:
      [`SAXNotRecognizedException`](../../../org/xml/sax/SAXNotRecognizedException.md) - When the underlying XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../org/xml/sax/SAXNotSupportedException.md) - When the underlying XMLReader recognizes the property name but doesn't support the property.

      See Also:
      [`XMLReader.getProperty(java.lang.String)`](../../../org/xml/sax/XMLReader.md)

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

- **[Prev Class](ParserConfigurationException.md)**
- **[Next Class](SAXParserFactory.md)**

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
