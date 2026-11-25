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

- **[Prev Class](XMLToken.md)**
- **[Next Class](XSLException.md)**

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

## **Class XMLTokenizer**

- **java.lang.Object**

- - **[org.xml.sax.HandlerBase](../../../../org/xml/sax/HandlerBase.md)**

  - - **[oracle.xml.parser.v2.DefaultXMLDocumentHandler](DefaultXMLDocumentHandler.md)**

    - - **oracle.xml.parser.v2.XMLTokenizer**

<!-- -->

- **All Implemented Interfaces:**
  **[XMLDocumentHandler](XMLDocumentHandler.md), [DocumentHandler](../../../../org/xml/sax/DocumentHandler.md), [DTDHandler](../../../../org/xml/sax/DTDHandler.md), [EntityResolver](../../../../org/xml/sax/EntityResolver.md), [ErrorHandler](../../../../org/xml/sax/ErrorHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLTokenizer
      extends DefaultXMLDocumentHandler

  **This class implements an eXtensible Markup Language (XML) 1.0 parser according to the World Wide Web Consortium (W3C) [recommendation](http://www.w3.org/TR/1998/REC-xml-19980210).**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                              |
    |------------------------------------------------------------------------------------------|
    | `XMLTokenizer``()`<br>Creates a new Tokenizer object.                                    |
    | `XMLTokenizer``(`[`XMLToken`](XMLToken.md)` handler)`<br>Creates a new Tokenizer object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                       |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `parseDocument``()`<br>Parses an XML Document                                                                                                                |
    | `void`            | `setErrorHandler``(`[`ErrorHandler`](../../../../org/xml/sax/ErrorHandler.md)` handler)`<br>Applications can use this to register a new error event handler. |
    | `void`            | `setErrorStream``(java.io.OutputStream out)`<br>Register a output stream for errors                                                                          |
    | `void`            | `setToken``(int token, boolean val)`<br>Applications can use this to register a new token for XML tokenizer.                                                 |
    | `void`            | `setTokenHandler``(`[`XMLToken`](XMLToken.md)` handler)`<br>Applications can use this to register a new XML tokenizer event handler.                         |
    | `void`            | `tokenize``(`[`InputSource`](../../../../org/xml/sax/InputSource.md)` in)`<br>Tokenizes the XML from given input source                                      |
    | `void`            | `tokenize``(java.io.InputStream in)`<br>Tokenizes the XML from given input stream.                                                                           |
    | `void`            | `tokenize``(java.io.Reader r)`<br>Tokenizes the XML from given input stream.                                                                                 |
    | `void`            | `tokenize``(java.lang.String in)`<br>Tokenizes the XML from the URL indicated                                                                                |
    | `void`            | `tokenize``(java.net.URL url)`<br>Tokenizes the XML document pointed to by the given URL and creates the corresponding XML document hierarchy.               |

    - ### Methods inherited from class oracle.xml.parser.v2.[DefaultXMLDocumentHandler](DefaultXMLDocumentHandler.md)

      [`cDATASection`](DefaultXMLDocumentHandler.md)`, `[`comment`](DefaultXMLDocumentHandler.md)`, `[`endDoctype`](DefaultXMLDocumentHandler.md)`, `[`endElement`](DefaultXMLDocumentHandler.md)`, `[`endElement`](DefaultXMLDocumentHandler.md)`, `[`endPrefixMapping`](DefaultXMLDocumentHandler.md)`, `[`getHandler`](DefaultXMLDocumentHandler.md)`, `[`setDoctype`](DefaultXMLDocumentHandler.md)`, `[`setError`](DefaultXMLDocumentHandler.md)`, `[`setHandler`](DefaultXMLDocumentHandler.md)`, `[`setTextDecl`](DefaultXMLDocumentHandler.md)`, `[`setXMLDecl`](DefaultXMLDocumentHandler.md)`, `[`setXMLSchema`](DefaultXMLDocumentHandler.md)`, `[`skippedEntity`](DefaultXMLDocumentHandler.md)`, `[`startElement`](DefaultXMLDocumentHandler.md)`, `[`startElement`](DefaultXMLDocumentHandler.md)`, `[`startPrefixMapping`](DefaultXMLDocumentHandler.md)

    <!-- -->

    - ### Methods inherited from class org.xml.sax.[HandlerBase](../../../../org/xml/sax/HandlerBase.md)

      [`characters`](../../../../org/xml/sax/HandlerBase.md)`, `[`endDocument`](../../../../org/xml/sax/HandlerBase.md)`, `[`endElement`](../../../../org/xml/sax/HandlerBase.md)`, `[`error`](../../../../org/xml/sax/HandlerBase.md)`, `[`fatalError`](../../../../org/xml/sax/HandlerBase.md)`, `[`ignorableWhitespace`](../../../../org/xml/sax/HandlerBase.md)`, `[`notationDecl`](../../../../org/xml/sax/HandlerBase.md)`, `[`processingInstruction`](../../../../org/xml/sax/HandlerBase.md)`, `[`resolveEntity`](../../../../org/xml/sax/HandlerBase.md)`, `[`setDocumentLocator`](../../../../org/xml/sax/HandlerBase.md)`, `[`startDocument`](../../../../org/xml/sax/HandlerBase.md)`, `[`startElement`](../../../../org/xml/sax/HandlerBase.md)`, `[`unparsedEntityDecl`](../../../../org/xml/sax/HandlerBase.md)`, `[`warning`](../../../../org/xml/sax/HandlerBase.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[DocumentHandler](../../../../org/xml/sax/DocumentHandler.md)

      [`characters`](../../../../org/xml/sax/DocumentHandler.md)`, `[`endDocument`](../../../../org/xml/sax/DocumentHandler.md)`, `[`endElement`](../../../../org/xml/sax/DocumentHandler.md)`, `[`ignorableWhitespace`](../../../../org/xml/sax/DocumentHandler.md)`, `[`processingInstruction`](../../../../org/xml/sax/DocumentHandler.md)`, `[`setDocumentLocator`](../../../../org/xml/sax/DocumentHandler.md)`, `[`startDocument`](../../../../org/xml/sax/DocumentHandler.md)`, `[`startElement`](../../../../org/xml/sax/DocumentHandler.md)

<!-- -->

- - ### Constructor Detail

    - #### XMLTokenizer

          public XMLTokenizer()

      Creates a new Tokenizer object.

    <!-- -->

    - #### XMLTokenizer

          public XMLTokenizer(XMLToken handler)

      Creates a new Tokenizer object.

  <!-- -->

  - ### Method Detail

    - #### setErrorStream

          public void setErrorStream(java.io.OutputStream out)

      Register a output stream for errors

    <!-- -->

    - #### setErrorHandler

          public void setErrorHandler(ErrorHandler handler)

      Applications can use this to register a new error event handler. This replaces any previous setting for error handling.
      Parameters:
      `handler` - `ErrorHandler` being registered

    <!-- -->

    - #### tokenize

          public final void tokenize(java.net.URL url)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Tokenizes the XML document pointed to by the given URL and creates the corresponding XML document hierarchy.
      Parameters:
      `url` - the url points to the XML document to parse.

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### tokenize

          public final void tokenize(InputSource in)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Tokenizes the XML from given input source
      Parameters:
      `in` - the `org.xml.sax.InputSouce` to parse

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### tokenize

          public final void tokenize(java.lang.String in)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Tokenizes the XML from the URL indicated
      Parameters:
      `in` - the `String` containing the URL to parse from

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

    <!-- -->

    - #### tokenize

          public final void tokenize(java.io.InputStream in)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Tokenizes the XML from given input stream.
      Parameters:
      `in` - the `InputStream` containing XML data to parse.

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](XMLParser.md)

    <!-- -->

    - #### tokenize

          public final void tokenize(java.io.Reader r)
                              throws XMLParseException,
                                     SAXException,
                                     java.io.IOException

      Tokenizes the XML from given input stream.
      Parameters:
      `r` - the `Reader` containing XML data to parse.

      Throws:
      [`XMLParseException`](XMLParseException.md) - if syntax or other error encountered.

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

      See Also:
      [`XMLParser.setBaseURL(java.net.URL)`](XMLParser.md)

    <!-- -->

    - #### setTokenHandler

          public void setTokenHandler(XMLToken handler)

      Applications can use this to register a new XML tokenizer event handler.
      Parameters:
      `handler` - `XMLToken` being registered

    <!-- -->

    - #### setToken

          public void setToken(int token,
                               boolean val)

      Applications can use this to register a new token for XML tokenizer.
      Parameters:
      `token` - `XMLToken` being set

    <!-- -->

    - #### parseDocument

          public void parseDocument()
                             throws SAXException,
                                    java.io.IOException

      Parses an XML Document
      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX Exception, possibly wrapping another exception.

      `java.io.IOException` - IO Error.

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

- **[Prev Class](XMLToken.md)**
- **[Next Class](XSLException.md)**

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
