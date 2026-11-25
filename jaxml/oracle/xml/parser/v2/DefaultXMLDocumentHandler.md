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

- **[Prev Class](BinaryParser.md)**
- **[Next Class](DocumentBuilder.md)**

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

## **Class DefaultXMLDocumentHandler**

- **java.lang.Object**

- - **[org.xml.sax.HandlerBase](../../../../org/xml/sax/HandlerBase.md)**

  - - **oracle.xml.parser.v2.DefaultXMLDocumentHandler**

<!-- -->

- **All Implemented Interfaces:**
  **[XMLDocumentHandler](XMLDocumentHandler.md), [DocumentHandler](../../../../org/xml/sax/DocumentHandler.md), [DTDHandler](../../../../org/xml/sax/DTDHandler.md), [EntityResolver](../../../../org/xml/sax/EntityResolver.md), [ErrorHandler](../../../../org/xml/sax/ErrorHandler.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[CXMLHandlerBase](../../comp/CXMLHandlerBase.md), [DocumentBuilder](DocumentBuilder.md), [XMLTokenizer](XMLTokenizer.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DefaultXMLDocumentHandler
      extends HandlerBase
      implements XMLDocumentHandler

  **This class implements the default behaviour for the `XMLDocumentHandler` interface.**

  **Application writers can extend this class when they need to implement only part of the interface**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                              |
    |--------------------------------------------------------------------------|
    | `DefaultXMLDocumentHandler``()`<br>Constructs a default document handler |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                                                    |
    |-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                        | `cDATASection``(char[] ch, int start, int length)`<br>Receive notification of a CDATA Section.                                                                                                                            |
    | `void`                                        | `comment``(java.lang.String data)`<br>Receive notification of a comment.                                                                                                                                                  |
    | `void`                                        | `endDoctype``()`<br>Receive notification of end of the DTD.                                                                                                                                                               |
    | `void`                                        | `endElement``(`[`NSName`](NSName.md)` elem)`<br>Receive notification of the end of an element.                                                                                                                            |
    | `void`                                        | `endElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName)`<br>Receive notification of the end of an element.                                                                       |
    | `void`                                        | `endPrefixMapping``(java.lang.String prefix)`<br>End the scope of a prefix-URI mapping.                                                                                                                                   |
    | [`XMLDocumentHandler`](XMLDocumentHandler.md) | `getHandler``()`<br>Get the next pipe-line node handler.                                                                                                                                                                  |
    | `void`                                        | `setDoctype``(`[`DTD`](DTD.md)` dtd)`<br>Receive notification of DTD.                                                                                                                                                     |
    | `void`                                        | `setError``(`[`XMLError`](XMLError.md)` he)`<br>Receive notification of a XMLError handler.                                                                                                                               |
    | `void`                                        | `setHandler``(`[`XMLDocumentHandler`](XMLDocumentHandler.md)` h)`<br>Receive notification of a next pipe-line node handler.                                                                                               |
    | `void`                                        | `setTextDecl``(java.lang.String version, java.lang.String encoding)`<br>Receive notification of a Text XML Declaration.                                                                                                   |
    | `void`                                        | `setXMLDecl``(java.lang.String version, java.lang.String standalone, java.lang.String encoding)`<br>Receive notification of an XML Declaration.                                                                           |
    | `void`                                        | `setXMLSchema``(java.lang.Object s)`<br>Receive notification of a XMLSchema object.                                                                                                                                       |
    | `void`                                        | `skippedEntity``(java.lang.String name)`<br>Receive notification of a skipped entity.                                                                                                                                     |
    | `void`                                        | `startElement``(`[`NSName`](NSName.md)` elem, `[`SAXAttrList`](SAXAttrList.md)` attrlist)`<br>Receive notification of the beginning of an element.                                                                        |
    | `void`                                        | `startElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName, `[`Attributes`](../../../../org/xml/sax/Attributes.md)` atts)`<br>Receive notification of the beginning of an element. |
    | `void`                                        | `startPrefixMapping``(java.lang.String prefix, java.lang.String uri)`<br>Begin the scope of a prefix-URI Namespace mapping.                                                                                               |

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

    - #### DefaultXMLDocumentHandler

          public DefaultXMLDocumentHandler()

      Constructs a default document handler

  <!-- -->

  - ### Method Detail

    - #### startElement

          public void startElement(NSName elem,
                                   SAXAttrList attrlist)
                            throws SAXException

      Receive notification of the beginning of an element.
      Specified by:
      [`startElement`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `elem` - NSName object

      `attrlist` - SAXAttrList for the element

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - A `SAXException` could be thrown.

      See Also:
      [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String namespaceURI,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes atts)
                            throws SAXException

      Receive notification of the beginning of an element.
      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified name (with prefix), or the empty string if qualified names are not available.

      `atts` - The attributes attached to the element. If there are no attributes, it shall be an empty Attributes object.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      `endElement(oracle.xml.parser.v2.NSName)`, [`Attributes`](../../../../org/xml/sax/Attributes.md)

    <!-- -->

    - #### endElement

          public void endElement(NSName elem)
                          throws SAXException

      Receive notification of the end of an element.
      Specified by:
      [`endElement`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `elem` - NSName object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - A `SAXException` could be thrown.

      See Also:
      [`DocumentHandler.endElement(java.lang.String)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String namespaceURI,
                                 java.lang.String localName,
                                 java.lang.String qName)
                          throws SAXException

      Receive notification of the end of an element.
      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified XML 1.0 name (with prefix), or the empty string if qualified names are not available.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setDoctype

          public void setDoctype(DTD dtd)
                          throws SAXException

      Receive notification of DTD. Sets the DTD
      Specified by:
      [`setDoctype`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `dtd` - - The DTD node

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### endDoctype

          public void endDoctype()
                          throws SAXException

      Receive notification of end of the DTD.
      Specified by:
      [`endDoctype`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setXMLDecl

          public void setXMLDecl(java.lang.String version,
                                 java.lang.String standalone,
                                 java.lang.String encoding)
                          throws SAXException

      Receive notification of an XML Declaration.
      The Parser will invoke this method once for XML Decl

      Specified by:
      [`setXMLDecl`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `version` - The version number

      `standalone` - The standalone value (or null, if not specifed)

      `encoding` - The encoding name (or null, if not specifed)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setTextDecl

          public void setTextDecl(java.lang.String version,
                                  java.lang.String encoding)
                           throws SAXException

      Receive notification of a Text XML Declaration.
      The Parser will invoke this method once for each text XML Decl

      Specified by:
      [`setTextDecl`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `version` - The version number (or null, if not specified)

      `encoding` - The encoding name

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### comment

          public void comment(java.lang.String data)
                       throws SAXException

      Receive notification of a comment.
      The Parser will invoke this method once for each comment found: note that comment may occur before or after the main document element.

      Specified by:
      [`comment`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `data` - The comment data, or null if none was supplied.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### cDATASection

          public void cDATASection(char[] ch,
                                   int start,
                                   int length)
                            throws SAXException

      Receive notification of a CDATA Section.
      The Parser will invoke this method once for each CDATA Section found.

      Specified by:
      [`cDATASection`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `ch` - The CDATA section characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setHandler

          public void setHandler(XMLDocumentHandler h)
                          throws SAXException

      Receive notification of a next pipe-line node handler.
      Specified by:
      [`setHandler`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `h` - The XMLDocumentHandler node

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### getHandler

          public XMLDocumentHandler getHandler()

      Get the next pipe-line node handler.
      Specified by:
      [`getHandler`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Returns:
      The XMLDocumentHandler node

    <!-- -->

    - #### setError

          public void setError(XMLError he)
                        throws SAXException

      Receive notification of a XMLError handler.
      Specified by:
      [`setError`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `he` - The XMLError object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setXMLSchema

          public void setXMLSchema(java.lang.Object s)
                            throws SAXException

      Receive notification of a XMLSchema object.
      Specified by:
      [`setXMLSchema`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Parameters:
      `s` - The XMLSchema object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### startPrefixMapping

          public void startPrefixMapping(java.lang.String prefix,
                                         java.lang.String uri)
                                  throws SAXException

      Begin the scope of a prefix-URI Namespace mapping.
      Parameters:
      `prefix` - The Namespace prefix being declared.

      `uri` - The Namespace URI the prefix is mapped to.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The client may throw an exception during processing.

      See Also:
      `endPrefixMapping(java.lang.String)`, `startElement(oracle.xml.parser.v2.NSName, oracle.xml.parser.v2.SAXAttrList)`

    <!-- -->

    - #### endPrefixMapping

          public void endPrefixMapping(java.lang.String prefix)
                                throws SAXException

      End the scope of a prefix-URI mapping.
      Parameters:
      `prefix` - The prefix that was being mapping.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The client may throw an exception during processing.

      See Also:
      `startPrefixMapping(java.lang.String, java.lang.String)`, `endElement(oracle.xml.parser.v2.NSName)`

    <!-- -->

    - #### skippedEntity

          public void skippedEntity(java.lang.String name)
                             throws SAXException

      Receive notification of a skipped entity.
      Parameters:
      `name` - The name of the skipped entity. If it is a parameter entity, the name will begin with '%', and if it is the external DTD subset, it will be the string "\[dtd\]".

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

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

- **[Prev Class](BinaryParser.md)**
- **[Next Class](DocumentBuilder.md)**

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
