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

- **Prev Class**
- **[Next Class](DocumentBuilderFactory.md)**

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

## **Class DocumentBuilder**

- **java.lang.Object**

- - **javax.xml.parsers.DocumentBuilder**

<!-- -->

- **Direct Known Subclasses:**
  **[JXDocumentBuilder](../../../oracle/xml/jaxp/JXDocumentBuilder.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class DocumentBuilder
      extends java.lang.Object

  **Defines the API to obtain DOM Document instances from an XML document. Using this class, an application programmer can obtain a `org.w3c.dom.Document` from XML.**
  **An instance of this class can be obtained from the `DocumentBuilderFactory.newDocumentBuilder` method. Once an instance of this class is obtained, XML can be parsed from a variety of input sources. These input sources are InputStreams, Files, URLs, and SAX InputSources.**

  **Note that this class reuses several classes from the SAX API. This does not require that the implementor of the underlying DOM implmenetation use a SAX parser to parse XML document into a `Document`. It merely requires that the implementation communicate with the application using these existing APIs.**

  **Since:**
  **JAXP 1.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                                                                          |
    |-----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`DOMImplementation`](../../../org/w3c/dom/DOMImplementation.md) | `getDOMImplementation``()`<br>Obtain an instance of a DOMImplementation object.                                                                                                                 |
    | `abstract boolean`                                                          | `isNamespaceAware``()`<br>Indicates whether or not this parser is configured to understand namespaces.                                                                                          |
    | `abstract boolean`                                                          | `isValidating``()`<br>Indicates whether or not this parser is configured to validate XML documents.                                                                                             |
    | `abstract `[`Document`](../../../org/w3c/dom/Document.md)                   | `newDocument``()`<br>Obtain a new instance of a DOM Document object to build a DOM tree with.                                                                                                   |
    | [`Document`](../../../org/w3c/dom/Document.md)                              | `parse``(java.io.File f)`<br>Parse the content of the given file as an XML document and return a new DOM Document object.                                                                       |
    | `abstract `[`Document`](../../../org/w3c/dom/Document.md)                   | `parse``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` is)`<br>Parse the content of the given input source as an XML document and return a new DOM Document object.                    |
    | [`Document`](../../../org/w3c/dom/Document.md)                              | `parse``(java.io.InputStream is)`<br>Parse the content of the given InputStream as an XML document and return a new DOM Document object.                                                        |
    | [`Document`](../../../org/w3c/dom/Document.md)                              | `parse``(java.io.InputStream is, java.lang.String systemId)`<br>Parse the content of the given InputStream as an XML document and return a new DOM Document object.                             |
    | [`Document`](../../../org/w3c/dom/Document.md)                              | `parse``(java.lang.String uri)`<br>Parse the content of the given URI as an XML document and return a new DOM Document object.                                                                  |
    | `abstract void`                                                             | `setEntityResolver``(`[`EntityResolver`](../../../org/xml/sax/EntityResolver.md)` er)`<br>Specify the `EntityResolver` to be used to resolve entities present in the XML document to be parsed. |
    | `abstract void`                                                             | `setErrorHandler``(`[`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)` eh)`<br>Specify the `ErrorHandler` to be used to resolve entities present in the XML document to be parsed.         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### parse

          public Document parse(java.io.InputStream is)
                         throws SAXException,
                                java.io.IOException

      Parse the content of the given InputStream as an XML document and return a new DOM Document object.
      Parameters:
      `is` - InputStream containing the content to be parsed.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - If any parse errors occur.

      `java.lang.IllegalArgumentException` - If the InputStream is null

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public Document parse(java.io.InputStream is,
                                java.lang.String systemId)
                         throws SAXException,
                                java.io.IOException

      Parse the content of the given InputStream as an XML document and return a new DOM Document object.
      Parameters:
      `is` - InputStream containing the content to be parsed.

      `systemId` - Provide a base for resolving relative URIs.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - If any parse errors occur.

      `java.lang.IllegalArgumentException` - If the InputStream is null

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public Document parse(java.lang.String uri)
                         throws SAXException,
                                java.io.IOException

      Parse the content of the given URI as an XML document and return a new DOM Document object.
      Parameters:
      `uri` - The location of the content to be parsed.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - If any parse errors occur.

      `java.lang.IllegalArgumentException` - If the URI is null

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public Document parse(java.io.File f)
                         throws SAXException,
                                java.io.IOException

      Parse the content of the given file as an XML document and return a new DOM Document object.
      Parameters:
      `f` - The file containing the XML to parse

      Throws:
      `java.io.IOException` - If any IO errors occur.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - If any parse errors occur.

      `java.lang.IllegalArgumentException` - If the file is null

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### parse

          public abstract Document parse(InputSource is)
                                  throws SAXException,
                                         java.io.IOException

      Parse the content of the given input source as an XML document and return a new DOM Document object.
      Parameters:
      `is` - InputSource containing the content to be parsed.

      Throws:
      `java.io.IOException` - If any IO errors occur.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - If any parse errors occur.

      `java.lang.IllegalArgumentException` - If the InputSource is null

      See Also:
      [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### isNamespaceAware

          public abstract boolean isNamespaceAware()

      Indicates whether or not this parser is configured to understand namespaces.

    <!-- -->

    - #### isValidating

          public abstract boolean isValidating()

      Indicates whether or not this parser is configured to validate XML documents.

    <!-- -->

    - #### setEntityResolver

          public abstract void setEntityResolver(EntityResolver er)

      Specify the `EntityResolver` to be used to resolve entities present in the XML document to be parsed. Setting this to `null` will result in the underlying implementation using it's own default implementation and behavior.

    <!-- -->

    - #### setErrorHandler

          public abstract void setErrorHandler(ErrorHandler eh)

      Specify the `ErrorHandler` to be used to resolve entities present in the XML document to be parsed. Setting this to `null` will result in the underlying implementation using it's own default implementation and behavior.

    <!-- -->

    - #### newDocument

          public abstract Document newDocument()

      Obtain a new instance of a DOM Document object to build a DOM tree with.

    <!-- -->

    - #### getDOMImplementation

          public abstract DOMImplementation getDOMImplementation()

      Obtain an instance of a DOMImplementation object.

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

- **Prev Class**
- **[Next Class](DocumentBuilderFactory.md)**

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
