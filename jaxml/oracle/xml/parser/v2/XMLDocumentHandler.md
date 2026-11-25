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

- **[Prev Class](XMLDocumentFragment.md)**
- **[Next Class](XMLDOMException.md)**

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

## **Interface XMLDocumentHandler**

- **All Superinterfaces:**
  **[DocumentHandler](../../../../org/xml/sax/DocumentHandler.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[CXMLHandlerBase](../../comp/CXMLHandlerBase.md), [DefaultXMLDocumentHandler](DefaultXMLDocumentHandler.md), [DocumentBuilder](DocumentBuilder.md), [XMLTokenizer](XMLTokenizer.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XMLDocumentHandler
      extends DocumentHandler

  **This interface extends the `org.xml.sax.DocumentHandler` interface. SAX Applications requiring Namespace support must implement this interface and register with the SAX Parser via `Parser.setDocumentHandler()`.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type    | Method and Description                                                                                                                             |
    |----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`               | `cDATASection``(char[] ch, int start, int length)`<br>Receive notification of a CDATA Section.                                                     |
    | `void`               | `comment``(java.lang.String data)`<br>Receive notification of a comment.                                                                           |
    | `void`               | `endDoctype``()`<br>Receive notification of end of the DTD.                                                                                        |
    | `void`               | `endElement``(`[`NSName`](NSName.md)` elem)`<br>Receive notification of the end of an element.                                                     |
    | `XMLDocumentHandler` | `getHandler``()`<br>Get the next pipe-line node handler.                                                                                           |
    | `void`               | `setDoctype``(`[`DTD`](DTD.md)` dtd)`<br>Receive notification of a DTD (Document Type node).                                                       |
    | `void`               | `setError``(`[`XMLError`](XMLError.md)` he)`<br>Receive notification of a XMLError handler.                                                        |
    | `void`               | `setHandler``(XMLDocumentHandler h)`<br>Receive notification of a next pipe-line node handler.                                                     |
    | `void`               | `setTextDecl``(java.lang.String version, java.lang.String encoding)`<br>Receive notification of a Text XML Declaration.                            |
    | `void`               | `setXMLDecl``(java.lang.String version, java.lang.String standalone, java.lang.String encoding)`<br>Receive notification of a XML Declaration.     |
    | `void`               | `setXMLSchema``(java.lang.Object s)`<br>Receive notification of a XMLSchema object.                                                                |
    | `void`               | `startElement``(`[`NSName`](NSName.md)` elem, `[`SAXAttrList`](SAXAttrList.md)` attrlist)`<br>Receive notification of the beginning of an element. |

    - ### Methods inherited from interface org.xml.sax.[DocumentHandler](../../../../org/xml/sax/DocumentHandler.md)

      [`characters`](../../../../org/xml/sax/DocumentHandler.md)`, `[`endDocument`](../../../../org/xml/sax/DocumentHandler.md)`, `[`endElement`](../../../../org/xml/sax/DocumentHandler.md)`, `[`ignorableWhitespace`](../../../../org/xml/sax/DocumentHandler.md)`, `[`processingInstruction`](../../../../org/xml/sax/DocumentHandler.md)`, `[`setDocumentLocator`](../../../../org/xml/sax/DocumentHandler.md)`, `[`startDocument`](../../../../org/xml/sax/DocumentHandler.md)`, `[`startElement`](../../../../org/xml/sax/DocumentHandler.md)

<!-- -->

- - ### Method Detail

    - #### startElement

          void startElement(NSName elem,
                            SAXAttrList attrlist)
                     throws SAXException

      Receive notification of the beginning of an element. The Parser will invoke this method at the beginning of every element in the XML document; there will be a corresponding endElement() event for every startElement() event (even when the element is empty). All of the element's content will be reported, inorder, before the corresponding endElement() event.
      By implementing this method instead of `org.xml.sax.DocumentHandler.startElement`, SAX Applications can get the Namespace support provided by `NSName` and `SAXAttrList`.

      Parameters:
      `elem` - NSName object

      `attrlist` - SAXAttrList for the element

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - A `SAXException` could be thrown.

      See Also:
      [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### endElement

          void endElement(NSName elem)
                   throws SAXException

      Receive notification of the end of an element. The SAX parser will invoke this method at the end of every element in the XML document; there will be a corresponding startElement() event for every endElement() event (even when the element is empty).
      By implementing this method instead of `org.xml.sax.DocumentHandler.endElement`, SAX Applications can get the Namespace support provided by `NSName`.

      Parameters:
      `elem` - NSName object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - A `SAXException` could be thrown.

      See Also:
      [`DocumentHandler.endElement(java.lang.String)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### setXMLDecl

          void setXMLDecl(java.lang.String version,
                          java.lang.String standalone,
                          java.lang.String encoding)
                   throws SAXException

      Receive notification of a XML Declaration.
      The Parser will invoke this method once for XML Decl

      Parameters:
      `version` - The version number

      `standalone` - The standalone value (or null, if not specifed)

      `encoding` - The encoding name (or null, if not specifed)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setTextDecl

          void setTextDecl(java.lang.String version,
                           java.lang.String encoding)
                    throws SAXException

      Receive notification of a Text XML Declaration.
      The Parser will invoke this method once for each text XML Decl

      Parameters:
      `version` - The version number (or null, if not specified)

      `encoding` - The encoding name

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### comment

          void comment(java.lang.String data)
                throws SAXException

      Receive notification of a comment.
      The Parser will invoke this method once for each comment found: note that comment may occur before or after the main document element.

      Parameters:
      `data` - The comment data, or null if none was supplied.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### cDATASection

          void cDATASection(char[] ch,
                            int start,
                            int length)
                     throws SAXException

      Receive notification of a CDATA Section.
      The Parser will invoke this method once for each CDATA Section found.

      Parameters:
      `ch` - The CDATA section characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setHandler

          void setHandler(XMLDocumentHandler h)
                   throws SAXException

      Receive notification of a next pipe-line node handler.
      Parameters:
      `h` - The XMLDocumentHandler node

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### getHandler

          XMLDocumentHandler getHandler()

      Get the next pipe-line node handler.
      Returns:
      The XMLDocumentHandler node

    <!-- -->

    - #### setError

          void setError(XMLError he)
                 throws SAXException

      Receive notification of a XMLError handler.
      Parameters:
      `he` - The XMLError object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setXMLSchema

          void setXMLSchema(java.lang.Object s)
                     throws SAXException

      Receive notification of a XMLSchema object.
      Parameters:
      `s` - The XMLSchema object

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setDoctype

          void setDoctype(DTD dtd)
                   throws SAXException

      Receive notification of a DTD (Document Type node).
      The Parser will invoke this method after calling startDocument to register the DTD used.

      Parameters:
      `dtd` - - The DTD node

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### endDoctype

          void endDoctype()
                   throws SAXException

      Receive notification of end of the DTD.
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

- **[Prev Class](XMLDocumentFragment.md)**
- **[Next Class](XMLDOMException.md)**

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
