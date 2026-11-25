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
- **[Next Class](DOMBuilderBeanInfo.md)**

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

**oracle.xml.async**

## **Class DOMBuilder**

- **java.lang.Object**

- - **oracle.xml.async.DOMBuilder**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, java.lang.Runnable**

  ------------------------------------------------------------------------

  **
  **

      public class DOMBuilder
      extends java.lang.Object
      implements java.io.Serializable, java.lang.Runnable

  **This class encapsulates an eXtensible Markup Language (XML) 1.0 parser to parse an XML document and build a DOM tree. The parsing is done in a separate thread and DOMBuilderListener interface must be used for notification when the tree is built.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                            |
    |------------------------------------------------------------------------|
    | `DOMBuilder``()`<br>Creates a new parser object.                       |
    | `DOMBuilder``(int id)`<br>Creates a new parser object with a given id. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                              |
    |------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                         | `addDOMBuilderErrorListener``(`[`DOMBuilderErrorListener`](DOMBuilderErrorListener.md)` p0)`<br>Adds DOMBuilderErrorListener                                                        |
    | `void`                                         | `addDOMBuilderListener``(`[`DOMBuilderListener`](DOMBuilderListener.md)` p0)`<br>Adds DOMBuilderListener                                                                            |
    | [`DTD`](../parser/v2/DTD.md)                   | `getDoctype``()`<br>Get the DTD                                                                                                                                                     |
    | [`XMLDocument`](../parser/v2/XMLDocument.md)   | `getDocument``()`<br>Gets the document                                                                                                                                              |
    | `int`                                          | `getId``()`<br>Returns the parser object id.                                                                                                                                        |
    | `java.lang.String`                             | `getReleaseVersion``()`<br>Returns the release version of the Oracle XML Parser                                                                                                     |
    | [`Document`](../../../org/w3c/dom/Document.md) | `getResult``()`<br>Gets the document                                                                                                                                                |
    | `boolean`                                      | `getValidationMode``()`<br>Returns the validation mode                                                                                                                              |
    | `void`                                         | `parse``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` in)`<br>Parses the XML from given input source                                                                      |
    | `void`                                         | `parse``(java.io.InputStream in)`<br>Parses the XML from given input stream.                                                                                                        |
    | `void`                                         | `parse``(java.io.Reader r)`<br>Parses the XML from given input stream.                                                                                                              |
    | `void`                                         | `parse``(java.lang.String in)`<br>Parses the XML from the URL indicated                                                                                                             |
    | `void`                                         | `parse``(java.net.URL url)`<br>Parses the XML document pointed to by the given URL and creates the corresponding XML document hierarchy.                                            |
    | `void`                                         | `parseDTD``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` in, java.lang.String rootName)`<br>Parses the XML External DTD from given input source                           |
    | `void`                                         | `parseDTD``(java.io.InputStream in, java.lang.String rootName)`<br>Parses the XML External DTD from given input stream.                                                             |
    | `void`                                         | `parseDTD``(java.io.Reader r, java.lang.String rootName)`<br>Parses the XML External DTD from given input stream.                                                                   |
    | `void`                                         | `parseDTD``(java.lang.String in, java.lang.String rootName)`<br>Parses the XML External DTD from the URL indicated                                                                  |
    | `void`                                         | `parseDTD``(java.net.URL url, java.lang.String rootName)`<br>Parses the XML External DTD document pointed to by the given URL and creates the corresponding XML document hierarchy. |
    | `void`                                         | `removeDOMBuilderErrorListener``(`[`DOMBuilderErrorListener`](DOMBuilderErrorListener.md)` p0)`<br>Remove DOMBuilderErrorListener                                                   |
    | `void`                                         | `removeDOMBuilderListener``(`[`DOMBuilderListener`](DOMBuilderListener.md)` p0)`<br>Remove DOMBuilderListener                                                                       |
    | `void`                                         | `run``()`<br>This method runs in a thread                                                                                                                                           |
    | `void`                                         | `setBaseURL``(java.net.URL url)`<br>Set the base URL for loading external enitites and DTDs.                                                                                        |
    | `void`                                         | `setDebugMode``(boolean flag)`<br>Sets a flag to turn on debug information in the document                                                                                          |
    | `void`                                         | `setDoctype``(`[`DTD`](../parser/v2/DTD.md)` dtd)`<br>Set the DTD                                                                                                                   |
    | `void`                                         | `setErrorStream``(java.io.OutputStream out)`<br>Creates an output stream for the output of errors and warnings.                                                                     |
    | `void`                                         | `setErrorStream``(java.io.OutputStream out, java.lang.String enc)`<br>Creates an output stream for the output of errors and warnings.                                               |
    | `void`                                         | `setErrorStream``(java.io.PrintWriter out)`<br>Creates an output stream for the output of errors and warnings.                                                                      |
    | `void`                                         | `setNodeFactory``(`[`NodeFactory`](../parser/v2/NodeFactory.md)` factory)`<br>Set the node factory.                                                                                 |
    | `void`                                         | `setPreserveWhitespace``(boolean flag)`<br>Set the white space preserving mode                                                                                                      |
    | `void`                                         | `setValidationMode``(boolean yes)`<br>Set the validation mode                                                                                                                       |
    | `void`                                         | `showWarnings``(boolean yes)`<br>Switch to determine whether to print warnings                                                                                                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DOMBuilder

          public DOMBuilder()

      Creates a new parser object.

    <!-- -->

    - #### DOMBuilder

          public DOMBuilder(int id)

      Creates a new parser object with a given id.
      Parameters:
      `id` - The `DOMBuilder` id.

  <!-- -->

  - ### Method Detail

    - #### getId

          public int getId()

      Returns the parser object id.
      Returns:
      The `DOMBuilder` id

    <!-- -->

    - #### run

          public void run()

      This method runs in a thread
      Specified by:
      `run` in interface `java.lang.Runnable`

    <!-- -->

    - #### addDOMBuilderListener

          public void addDOMBuilderListener(DOMBuilderListener p0)

      Adds DOMBuilderListener
      Parameters:
      `p0` - The `DOMBuilderListener` to add

    <!-- -->

    - #### addDOMBuilderErrorListener

          public void addDOMBuilderErrorListener(DOMBuilderErrorListener p0)

      Adds DOMBuilderErrorListener
      Parameters:
      `p0` - The `DOMBuilderErrorListener` to add

    <!-- -->

    - #### removeDOMBuilderListener

          public void removeDOMBuilderListener(DOMBuilderListener p0)

      Remove DOMBuilderListener
      Parameters:
      `p0` - The `DOMBuilderListener` to remove

    <!-- -->

    - #### removeDOMBuilderErrorListener

          public void removeDOMBuilderErrorListener(DOMBuilderErrorListener p0)

      Remove DOMBuilderErrorListener
      Parameters:
      `p0` - The `DOMBuilderErrorListener` to remove

    <!-- -->

    - #### getResult

          public Document getResult()

      Gets the document
      Returns:
      The document being parsed

    <!-- -->

    - #### getDoctype

          public DTD getDoctype()

      Get the DTD
      Returns:
      The `DTD`

    <!-- -->

    - #### setDebugMode

          public void setDebugMode(boolean flag)

      Sets a flag to turn on debug information in the document
      Parameters:
      `flag` - determines whether debug info is stored

    <!-- -->

    - #### showWarnings

          public void showWarnings(boolean yes)

      Switch to determine whether to print warnings
      Parameters:
      `yes` - determines whether warnings should be shown

    <!-- -->

    - #### setErrorStream

          public final void setErrorStream(java.io.PrintWriter out)
                                    throws java.io.IOException

      Creates an output stream for the output of errors and warnings. If an output stream for errors is not specified, the parser will use the standard error output stream `System.err` for outputting errors and warnings.
      Parameters:
      `out` - The `PrintWriter` to use for errors and warnings

      Throws:
      `java.io.IOException`

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

    - #### getDocument

          public XMLDocument getDocument()

      Gets the document
      Returns:
      The document being parsed

    <!-- -->

    - #### setNodeFactory

          public void setNodeFactory(NodeFactory factory)
                              throws XMLParseException

      Set the node factory. Applications can extend the NodeFactory and register it through this method. The parser will then use the user supplied NodeFactory to create nodes of the DOM tree.
      Parameters:
      `factory` - The `NodeFactory` to set

      Throws:
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if an invalid factory is set

      See Also:
      [`NodeFactory`](../parser/v2/NodeFactory.md)

    <!-- -->

    - #### setDoctype

          public void setDoctype(DTD dtd)

      Set the DTD
      Parameters:
      `dtd` - `DTD` to set and used while parsing

    <!-- -->

    - #### setValidationMode

          public void setValidationMode(boolean yes)

      Set the validation mode
      Parameters:
      `yes` - determines whether the XML parser should be validating

    <!-- -->

    - #### setBaseURL

          public void setBaseURL(java.net.URL url)

      Set the base URL for loading external enitites and DTDs. This method should to be called if the parse(InputStream) is used to parse the XML Document
      Parameters:
      `url` - The base URL

    <!-- -->

    - #### setPreserveWhitespace

          public void setPreserveWhitespace(boolean flag)

      Set the white space preserving mode
      Parameters:
      `flag` - preserving mode

    <!-- -->

    - #### getValidationMode

          public boolean getValidationMode()

      Returns the validation mode
      Returns:
      `true` if the XML parser is validating `false` if not

    <!-- -->

    - #### getReleaseVersion

          public java.lang.String getReleaseVersion()

      Returns the release version of the Oracle XML Parser
      Returns:
      the release version string

    <!-- -->

    - #### parse

          public final void parse(InputSource in)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML from given input source
      Parameters:
      `in` - the `org.xml.sax.InputSouce` to parse

      Throws:
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parse

          public final void parse(java.lang.String in)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML from the URL indicated
      Parameters:
      `in` - the `String` containing the URL to parse from

      Throws:
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parse

          public final void parse(java.net.URL url)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML document pointed to by the given URL and creates the corresponding XML document hierarchy.
      Parameters:
      `url` - the url points to the XML document to parse.

      Throws:
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### parse

          public final void parse(java.io.InputStream in)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML from given input stream. The base URL should be set for resolving external entities and DTD.
      Parameters:
      `in` - the `InputStream` containing XML data to parse.

      Throws:
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](../parser/v2/XMLParser.md)

    <!-- -->

    - #### parse

          public final void parse(java.io.Reader r)
                           throws XMLParseException,
                                  SAXException,
                                  java.io.IOException

      Parses the XML from given input stream. The base URL should be set for resolving external entities and DTD.
      Parameters:
      `r` - the `Reader` containing XML data to parse.

      Throws:
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](../parser/v2/XMLParser.md)

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
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

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
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

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
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

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
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](../parser/v2/XMLParser.md)

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
      [`XMLParseException`](../parser/v2/XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](../parser/v2/XMLParser.md)

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
- **[Next Class](DOMBuilderBeanInfo.md)**

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
