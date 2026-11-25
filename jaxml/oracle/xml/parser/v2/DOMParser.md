Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DocumentBuilder.md)**
- **[Next Class](DTD.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.parser.v2**

## **Class DOMParser**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLParser](XMLParser.md)**

  - - **oracle.xml.parser.v2.DOMParser**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class DOMParser
      extends XMLParser

  **This class implements an eXtensible Markup Language (XML) 1.0 parser according to the World Wide Web Consortium (W3C) [recommendation](http://www.w3.org/TR/1998/REC-xml-19980210). to parse a XML document and build a DOM tree.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                         |
    |---------------------------|-----------------------------------------------------------------------------------------------|
    | `static int`              | `ACCESS_MODE_ID`                                                                              |
    | `static int`              | `BINARY_FORMAT_ID`                                                                            |
    | `static java.lang.String` | `COMPACT_DOC`<br>Set flag to turn compact DOM off                                             |
    | `static int`              | `COMPACT_DOC_ID`                                                                              |
    | `static int`              | `CONNECTION_ID`                                                                               |
    | `static int`              | `CXML_RESULT_ID`                                                                              |
    | `static java.lang.String` | `DEBUG_MODE`<br>Sets Debug Mode Boolean.TRUE or Boolean.FALSE                                 |
    | `static int`              | `DEBUG_MODE_ID`                                                                               |
    | `static java.lang.String` | `ERROR_ENCODING`<br>Encoding for errors report via error stream (only if ERROR_STREAM is set) |
    | `static int`              | `ERROR_ENCODING_ID`                                                                           |
    | `static java.lang.String` | `ERROR_STREAM`<br>Error stream for reporting errors.                                          |
    | `static int`              | `ERROR_STREAM_ID`<br>Attributes supported by DOMParser                                        |
    | `static int`              | `KIND_ID`                                                                                     |
    | `static java.lang.String` | `NODE_FACTORY`<br>Set NodeFactory to build custom Nodes                                       |
    | `static int`              | `NODE_FACTORY_ID`                                                                             |
    | `static java.lang.String` | `ORACLE_JAXP_FEATURE_COMPACT_DOC`                                                             |
    | `static int`              | `PAGE_MANAGER_ID`                                                                             |
    | `static int`              | `PARTIAL_DOM_ID`                                                                              |
    | `static int`              | `QNAME_LOCAL_CACHE_ID`                                                                        |
    | `static int`              | `SCHEMA_PSVI_ID`                                                                              |
    | `static java.lang.String` | `SHOW_WARNINGS`<br>Boolean to ignore warnings Boolean.TRUE or Boolean.FALSE                   |
    | `static int`              | `SHOW_WARNINGS_ID`                                                                            |

    -

      ### **Fields inherited from class oracle.xml.parser.v2.[XMLParser](XMLParser.md)**

      **[`BASE_URL`](XMLParser.md)`, `[`BASE_URL_ID`](XMLParser.md)`, `[`CONTENT_MODEL_DETERMINISTIC`](XMLParser.md)`, `[`DEFAULT_ENTITY_EXPANSION_DEPTH`](XMLParser.md)`, `[`DEFAULT_ENTITY_EXPANSION_DEPTH_SECURE`](XMLParser.md)`, `[`DTD_OBJECT`](XMLParser.md)`, `[`DTD_OBJECT_ID`](XMLParser.md)`, `[`ENTITY_EXPANSION_DEPTH`](XMLParser.md)`, `[`ENTITY_EXPANSION_DEPTH_ID`](XMLParser.md)`, `[`EXPAND_ENTITYREF`](XMLParser.md)`, `[`EXPAND_ENTITYREF_ID`](XMLParser.md)`, `[`IGNORE_DUPLICATE_ID`](XMLParser.md)`, `[`PARSER`](XMLParser.md)`, `[`PARSER_CDATA`](XMLParser.md)`, `[`PARSER_DTD`](XMLParser.md)`, `[`RESOLVE_ENTITY_DEFAULT`](XMLParser.md)`, `[`RESOLVE_ENTITY_DEFAULT_ID`](XMLParser.md)`, `[`SCHEMA_LANGUAGE`](XMLParser.md)`, `[`SCHEMA_LANGUAGE_ID`](XMLParser.md)`, `[`SCHEMA_OBJECT`](XMLParser.md)`, `[`SCHEMA_OBJECT_ID`](XMLParser.md)`, `[`SCHEMA_SOURCE`](XMLParser.md)`, `[`SCHEMA_SOURCE_ID`](XMLParser.md)`, `[`STANDALONE`](XMLParser.md)`, `[`STANDALONE_ID`](XMLParser.md)`, `[`USE_DTD_ONLY_FOR_VALIDATION`](XMLParser.md)`, `[`USE_DTD_ONLY_FOR_VALIDATION_ID`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_DEFAULT`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_ID`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_SECURE`](XMLParser.md)`, `[`XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING`](XMLParser.md)`, `[`XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING_ID`](XMLParser.md)`, `[`XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC`](XMLParser.md)`, `[`XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC_ID`](XMLParser.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                     |
    |-------------------------------------------------|
    | `DOMParser``()`<br>Creates a new parser object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                                                                                              |
    |---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`              | `getAttribute``(java.lang.String name)`<br>Allows the user to retrieve specific attributes on the underlying implementation.                                                        |
    | [`DTD`](DTD.md)                 | `getDoctype``()`<br>Get the DTD                                                                                                                                                     |
    | [`XMLDocument`](XMLDocument.md) | `getDocument``()`<br>Gets the document                                                                                                                                              |
    | `long`                          | `getTotalBytesRead``()`<br>This function returns the total number of bytes read by the xml reader.                                                                                  |
    | `long`                          | `getTotalCharsRead``()`<br>This function returns the total number of chars read by the xml reader.                                                                                  |
    | `void`                          | `parseDTD``(`[`InputSource`](../../../../org/xml/sax/InputSource.md)` in, java.lang.String rootName)`<br>Parses the XML External DTD from given input source                        |
    | `void`                          | `parseDTD``(java.io.InputStream in, java.lang.String rootName)`<br>Parses the XML External DTD from given input stream.                                                             |
    | `void`                          | `parseDTD``(java.io.Reader r, java.lang.String rootName)`<br>Parses the XML External DTD from given input stream.                                                                   |
    | `void`                          | `parseDTD``(java.lang.String in, java.lang.String rootName)`<br>Parses the XML External DTD from the URL indicated                                                                  |
    | `void`                          | `parseDTD``(java.net.URL url, java.lang.String rootName)`<br>Parses the XML External DTD document pointed to by the given URL and creates the corresponding XML document hierarchy. |
    | `void`                          | `reset``()`<br>Resets the parser state                                                                                                                                              |
    | `void`                          | `retainCDATASection``(boolean flag)`<br>Switch to determine whether to retain CDATA sections                                                                                        |
    | `void`                          | `setAttribute``(int id, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                    |
    | `void`                          | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                     |
    | `void`                          | `setDebugMode``(boolean flag)`<br>Sets a flag to turn on debug information in the document                                                                                          |
    | `void`                          | `setErrorStream``(java.io.OutputStream out)`<br>Creates an output stream for the output of errors and warnings.                                                                     |
    | `void`                          | `setErrorStream``(java.io.OutputStream out, java.lang.String enc)`<br>Creates an output stream for the output of errors and warnings.                                               |
    | `void`                          | `setErrorStream``(java.io.PrintWriter out)`<br>Creates an output stream for the output of errors and warnings.                                                                      |
    | `void`                          | `setNodeFactory``(`[`NodeFactory`](NodeFactory.md)` factory)`<br>Set the node factory.                                                                                              |
    | `void`                          | `showWarnings``(boolean flag)`<br>Switch to determine whether to print warnings                                                                                                     |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLParser](XMLParser.md)

      [`getBaseURL`](XMLParser.md)`, `[`getEntityResolver`](XMLParser.md)`, `[`getErrorHandler`](XMLParser.md)`, `[`getReleaseVersion`](XMLParser.md)`, `[`getValidationMode`](XMLParser.md)`, `[`getValidationModeValue`](XMLParser.md)`, `[`getXMLProperty`](XMLParser.md)`, `[`isXMLPropertyReadOnly`](XMLParser.md)`, `[`isXMLPropertySupported`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`setBaseURL`](XMLParser.md)`, `[`setDoctype`](XMLParser.md)`, `[`setEntityResolver`](XMLParser.md)`, `[`setErrorHandler`](XMLParser.md)`, `[`setLocale`](XMLParser.md)`, `[`setPreserveWhitespace`](XMLParser.md)`, `[`setSchemaValidationMode`](XMLParser.md)`, `[`setSchemaValidatorProperty`](XMLParser.md)`, `[`setSecureProcessing`](XMLParser.md)`, `[`setValidationMode`](XMLParser.md)`, `[`setValidationMode`](XMLParser.md)`, `[`setXMLProperty`](XMLParser.md)`, `[`setXMLSchema`](XMLParser.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ERROR_STREAM_ID

          public static final int ERROR_STREAM_ID

      Attributes supported by DOMParser
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ERROR_ENCODING_ID

          public static final int ERROR_ENCODING_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_WARNINGS_ID

          public static final int SHOW_WARNINGS_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DEBUG_MODE_ID

          public static final int DEBUG_MODE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NODE_FACTORY_ID

          public static final int NODE_FACTORY_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CONNECTION_ID

          public static final int CONNECTION_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### KIND_ID

          public static final int KIND_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PARTIAL_DOM_ID

          public static final int PARTIAL_DOM_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### BINARY_FORMAT_ID

          public static final int BINARY_FORMAT_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACCESS_MODE_ID

          public static final int ACCESS_MODE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPACT_DOC_ID

          public static final int COMPACT_DOC_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CXML_RESULT_ID

          public static final int CXML_RESULT_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PAGE_MANAGER_ID

          public static final int PAGE_MANAGER_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_PSVI_ID

          public static final int SCHEMA_PSVI_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### QNAME_LOCAL_CACHE_ID

          public static final int QNAME_LOCAL_CACHE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ERROR_STREAM

          public static final java.lang.String ERROR_STREAM

      Error stream for reporting errors. The object can be OutputStream or PrintWriter. This attribute is ignored if ErrorHandler is set.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ERROR_ENCODING

          public static final java.lang.String ERROR_ENCODING

      Encoding for errors report via error stream (only if ERROR_STREAM is set)
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SHOW_WARNINGS

          public static final java.lang.String SHOW_WARNINGS

      Boolean to ignore warnings Boolean.TRUE or Boolean.FALSE
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DEBUG_MODE

          public static final java.lang.String DEBUG_MODE

      Sets Debug Mode Boolean.TRUE or Boolean.FALSE
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NODE_FACTORY

          public static final java.lang.String NODE_FACTORY

      Set NodeFactory to build custom Nodes
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPACT_DOC

          public static final java.lang.String COMPACT_DOC

      Set flag to turn compact DOM off
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ORACLE_JAXP_FEATURE_COMPACT_DOC

          public static final java.lang.String ORACLE_JAXP_FEATURE_COMPACT_DOC

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### DOMParser

          public DOMParser()

      Creates a new parser object.

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Resets the parser state
      Overrides:
      [`reset`](XMLParser.md) in class [`XMLParser`](XMLParser.md)

    <!-- -->

    - #### getDocument

          public XMLDocument getDocument()

      Gets the document
      Returns:
      The document being parsed

    <!-- -->

    - #### setErrorStream

          public final void setErrorStream(java.io.PrintWriter out)
                                    throws java.io.IOException

      Creates an output stream for the output of errors and warnings. If an output stream for errors is not specified, the parser will use the standard error output stream `System.err` for outputting errors and warnings.
      Parameters:
      `out` - The `PrintWriter` to use for errors and warnings

      Throws:
      `java.io.IOException` - if I/O error occurs in setting the error stream.

    <!-- -->

    - #### setErrorStream

          public final void setErrorStream(java.io.OutputStream out)
                                    throws java.io.IOException

      Creates an output stream for the output of errors and warnings. If an output stream for errors is not specified, the parser will use the standard error output stream `System.err` for outputting errors and warnings.
      Parameters:
      `out` - The output stream to use for errors and warnings

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### setErrorStream

          public final void setErrorStream(java.io.OutputStream out,
                                           java.lang.String enc)
                                    throws java.io.IOException

      Creates an output stream for the output of errors and warnings. If an output stream for errors is not specified, the parser will use the standard error output stream `System.err` for outputting errors and warnings. Additionally, an .exception is thrown if the encoding specified is unsupported.
      Parameters:
      `out` - The output stream to use for errors and warnings

      `enc` - the encoding to use

      Throws:
      `java.io.IOException` - if an unsupported encoding is specified

    <!-- -->

    - #### setNodeFactory

          public void setNodeFactory(NodeFactory factory)
                              throws XMLParseException

      Set the node factory. Applications can extend the NodeFactory and register it through this method. The parser will then use the user supplied NodeFactory to create nodes of the DOM tree.
      Parameters:
      `factory` - The `NodeFactory` to set

      Throws:
      [`XMLParseException`](XMLParseException.md) - if an invalid factory is set

      See Also:
      [`NodeFactory`](NodeFactory.md)

    <!-- -->

    - #### getDoctype

          public DTD getDoctype()

      Get the DTD
      Returns:
      The `DTD`

    <!-- -->

    - #### showWarnings

          public void showWarnings(boolean flag)

      Switch to determine whether to print warnings
      Parameters:
      `flag` - determines whether warnings should be shown

    <!-- -->

    - #### retainCDATASection

          public void retainCDATASection(boolean flag)

      Switch to determine whether to retain CDATA sections
      Parameters:
      `flag` - FALSE - convert CDATASection to Text nodes (default)
      TRUE - keep CDATASections

    <!-- -->

    - #### setDebugMode

          public void setDebugMode(boolean flag)

      Sets a flag to turn on debug information in the document
      Parameters:
      `flag` - determines whether debug info is stored

    <!-- -->

    - #### parseDTD

          public final void parseDTD(InputSource in,
                                     java.lang.String rootName)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Parses the XML External DTD from given input source
      Parameters:
      `in` - the `org.xml.sax.InputSouce` to parse

      `rootName` - the element to be used as root Element

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parseDTD

          public final void parseDTD(java.lang.String in,
                                     java.lang.String rootName)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Parses the XML External DTD from the URL indicated
      Parameters:
      `in` - the `String` containing the URL to parse from

      `rootName` - the element to be used as root Element

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parseDTD

          public final void parseDTD(java.net.URL url,
                                     java.lang.String rootName)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Parses the XML External DTD document pointed to by the given URL and creates the corresponding XML document hierarchy.
      Parameters:
      `url` - the url points to the XML document to parse.

      `rootName` - the element to be used as root Element

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parseDTD

          public final void parseDTD(java.io.InputStream in,
                                     java.lang.String rootName)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Parses the XML External DTD from given input stream. The base URL should be set for resolving external entities and DTD.
      Parameters:
      `in` - the `InputStream` containing XML data to parse.

      `rootName` - the element to be used as root Element

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](XMLParser.md)

    <!-- -->

    - #### parseDTD

          public final void parseDTD(java.io.Reader r,
                                     java.lang.String rootName)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Parses the XML External DTD from given input stream. The base URL should be set for resolving external entities and DTD.
      Parameters:
      `r` - the `Reader` containing XML data to parse.

      `rootName` - the element to be used as root Element

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](XMLParser.md)

    <!-- -->

    - #### getTotalBytesRead

          public final long getTotalBytesRead()

      This function returns the total number of bytes read by the xml reader.
      Returns:
      Number of bytes read.

    <!-- -->

    - #### getTotalCharsRead

          public final long getTotalCharsRead()

      This function returns the total number of chars read by the xml reader.
      Returns:
      Number of chars read.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Overrides:
      [`setAttribute`](XMLParser.md) in class [`XMLParser`](XMLParser.md)

      Parameters:
      `name` - The name of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### setAttribute

          public void setAttribute(int id,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Overrides:
      [`setAttribute`](XMLParser.md) in class [`XMLParser`](XMLParser.md)

      Parameters:
      `id` - The id of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.String name)
                                        throws java.lang.IllegalArgumentException

      Allows the user to retrieve specific attributes on the underlying implementation.
      Overrides:
      [`getAttribute`](XMLParser.md) in class [`XMLParser`](XMLParser.md)

      Parameters:
      `name` - The name of the attribute.

      Returns:
      value The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DocumentBuilder.md)**
- **[Next Class](DTD.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
