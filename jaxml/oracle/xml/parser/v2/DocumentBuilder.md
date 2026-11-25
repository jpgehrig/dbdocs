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

- **[Prev Class](DefaultXMLDocumentHandler.md)**
- **[Next Class](DOMParser.md)**

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

## **Class DocumentBuilder**

- **java.lang.Object**

- - **[org.xml.sax.HandlerBase](../../../../org/xml/sax/HandlerBase.md)**

  - - **[oracle.xml.parser.v2.DefaultXMLDocumentHandler](DefaultXMLDocumentHandler.md)**

    - - **oracle.xml.parser.v2.DocumentBuilder**

<!-- -->

- **All Implemented Interfaces:**
  **[XMLDocumentHandler](XMLDocumentHandler.md), [ContentHandler](../../../../org/xml/sax/ContentHandler.md), [DocumentHandler](../../../../org/xml/sax/DocumentHandler.md), [DTDHandler](../../../../org/xml/sax/DTDHandler.md), [EntityResolver](../../../../org/xml/sax/EntityResolver.md), [ErrorHandler](../../../../org/xml/sax/ErrorHandler.md), [DeclHandler](../../../../org/xml/sax/ext/DeclHandler.md), [LexicalHandler](../../../../org/xml/sax/ext/LexicalHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DocumentBuilder
      extends DefaultXMLDocumentHandler
      implements ContentHandler, LexicalHandler, DeclHandler

  **This class implements XMLDocumentHandler (deprecated) and ContentHandler to build a DOM Tree from SAX 2.0 events. XMLDocumentHandler events are supported for backward compatibility**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                   |
    |-----------------------------------------------|
    | `DocumentBuilder``()`<br>Default Constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                    |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `attributeDecl``(java.lang.String eName, java.lang.String aName, java.lang.String type, java.lang.String valueDefault, java.lang.String value)`<br>Report an attribute type declaration.                                  |
    | `void`                                          | `cDATASection``(char[] ch, int start, int length)`<br>Receive notification of CDATA Section data inside an element.                                                                                                       |
    | `void`                                          | `characters``(char[] ch, int start, int length)`<br>Receive notification of character data inside an element.                                                                                                             |
    | `void`                                          | `comment``(char[] ch, int start, int length)`<br>Report an XML comment anywhere in the document.                                                                                                                          |
    | `void`                                          | `comment``(java.lang.String data)`<br>Receive notification of a comment.                                                                                                                                                  |
    | `void`                                          | `elementDecl``(java.lang.String name, java.lang.String model)`<br>Report an element type declaration.                                                                                                                     |
    | `void`                                          | `endCDATA``()`<br>Report the end of a CDATA section.                                                                                                                                                                      |
    | `void`                                          | `endDoctype``()`<br>Receive notification of end of the DTD.                                                                                                                                                               |
    | `void`                                          | `endDocument``()`<br>Receive notification of the end of the document.                                                                                                                                                     |
    | `void`                                          | `endDTD``()`<br>Report the end of DTD declarations.                                                                                                                                                                       |
    | `void`                                          | `endElement``(`[`NSName`](NSName.md)` elem)`<br>Receive notification of the end of an element.                                                                                                                            |
    | `void`                                          | `endElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName)`<br>Receive notification of the end of an element.                                                                       |
    | `void`                                          | `endEntity``(java.lang.String name)`<br>Report the end of an entity.                                                                                                                                                      |
    | `void`                                          | `endPrefixMapping``(java.lang.String prefix)`<br>End the scope of a prefix/URI namespace mapping.                                                                                                                         |
    | `void`                                          | `externalEntityDecl``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Report a parsed external entity declaration.                                                                       |
    | [`XMLDocument`](XMLDocument.md)                 | `getDocument``()`<br>Get the document being build                                                                                                                                                                         |
    | [`Locator`](../../../../org/xml/sax/Locator.md) | `getLocator``()`<br>Get the locator reported by the Reader using setDocumentLocator                                                                                                                                       |
    | [`XMLNode`](XMLNode.md)                         | `getRoot``()`<br>Get the root of tree being built                                                                                                                                                                         |
    | `void`                                          | `ignorableWhitespace``(char[] ch, int start, int length)`<br>Receive notification of ignorable whitespace in element content.                                                                                             |
    | `void`                                          | `internalEntityDecl``(java.lang.String name, java.lang.String value)`<br>Report an internal entity declaration.                                                                                                           |
    | `void`                                          | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Receive notification of a processing instruction.                                                                                            |
    | `void`                                          | `reset``()`<br>Resets the document builder state                                                                                                                                                                          |
    | `void`                                          | `resetNodeFactory``()`<br>Reset the NodeFactory and go back to the original behaviour.                                                                                                                                    |
    | `void`                                          | `retainCDATASection``(boolean flag)`<br>Sets a flag to retain CDATA sections                                                                                                                                              |
    | `void`                                          | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                           |
    | `void`                                          | `setDebugMode``(boolean flag)`<br>Sets a flag to turn on debug information in the document                                                                                                                                |
    | `void`                                          | `setDoctype``(`[`DTD`](DTD.md)` dtd)`<br>Receive notification of DTD Sets the DTD                                                                                                                                         |
    | `void`                                          | `setDocumentLocator``(`[`Locator`](../../../../org/xml/sax/Locator.md)` locator)`<br>Receive a Locator object for document events.                                                                                        |
    | `void`                                          | `setNodeFactory``(`[`NodeFactory`](NodeFactory.md)` f)`<br>Set a optional NodeFactory to be used for creating custom DOM trees                                                                                            |
    | `void`                                          | `setNodeFactory``(`[`XMLDocument`](XMLDocument.md)` doc)`<br>Set document as the factory to create nodes                                                                                                                  |
    | `void`                                          | `setTextDecl``(java.lang.String version, java.lang.String encoding)`<br>Receive notification of a Text XML Declaration.                                                                                                   |
    | `void`                                          | `setXMLDecl``(java.lang.String version, java.lang.String standalone, java.lang.String encoding)`<br>Receive notification of a XML Declaration.                                                                            |
    | `void`                                          | `startCDATA``()`<br>Report the start of a CDATA section.                                                                                                                                                                  |
    | `void`                                          | `startDocument``()`<br>Receive notification of the beginning of the document.                                                                                                                                             |
    | `void`                                          | `startDTD``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Report the start of DTD declarations, if any.                                                                                |
    | `void`                                          | `startElement``(`[`NSName`](NSName.md)` elem, `[`SAXAttrList`](SAXAttrList.md)` attrlist)`<br>Receive notification of the beginning of an element.                                                                        |
    | `void`                                          | `startElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName, `[`Attributes`](../../../../org/xml/sax/Attributes.md)` atts)`<br>Receive notification of the beginning of an element. |
    | `void`                                          | `startEntity``(java.lang.String name)`<br>Report the beginning of some internal and external XML entities.                                                                                                                |
    | `void`                                          | `startPrefixMapping``(java.lang.String prefix, java.lang.String uri)`<br>Begin the scope of a prefix/URI namespace mapping.                                                                                               |

    - ### Methods inherited from class oracle.xml.parser.v2.[DefaultXMLDocumentHandler](DefaultXMLDocumentHandler.md)

      [`getHandler`](DefaultXMLDocumentHandler.md)`, `[`setError`](DefaultXMLDocumentHandler.md)`, `[`setHandler`](DefaultXMLDocumentHandler.md)`, `[`setXMLSchema`](DefaultXMLDocumentHandler.md)`, `[`skippedEntity`](DefaultXMLDocumentHandler.md)

    <!-- -->

    - ### Methods inherited from class org.xml.sax.[HandlerBase](../../../../org/xml/sax/HandlerBase.md)

      [`endElement`](../../../../org/xml/sax/HandlerBase.md)`, `[`error`](../../../../org/xml/sax/HandlerBase.md)`, `[`fatalError`](../../../../org/xml/sax/HandlerBase.md)`, `[`notationDecl`](../../../../org/xml/sax/HandlerBase.md)`, `[`resolveEntity`](../../../../org/xml/sax/HandlerBase.md)`, `[`startElement`](../../../../org/xml/sax/HandlerBase.md)`, `[`unparsedEntityDecl`](../../../../org/xml/sax/HandlerBase.md)`, `[`warning`](../../../../org/xml/sax/HandlerBase.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md)

      [`skippedEntity`](../../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[DocumentHandler](../../../../org/xml/sax/DocumentHandler.md)

      [`endElement`](../../../../org/xml/sax/DocumentHandler.md)`, `[`startElement`](../../../../org/xml/sax/DocumentHandler.md)

<!-- -->

- - ### Constructor Detail

    - #### DocumentBuilder

          public DocumentBuilder()

      Default Constructor. Creates a document builder that can be used as XMLDocumentHandler

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Resets the document builder state

    <!-- -->

    - #### startPrefixMapping

          public void startPrefixMapping(java.lang.String prefix,
                                         java.lang.String uri)
                                  throws SAXException

      Begin the scope of a prefix/URI namespace mapping.
      Specified by:
      [`startPrefixMapping`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startPrefixMapping`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

      Parameters:
      `prefix` - The namespace prefix being declared.

      `uri` - The namespace URI the prefix is mapped to (namespace name).

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The client may throw an exception during processing.

      See Also:
      `endPrefixMapping(java.lang.String)`, `startElement(oracle.xml.parser.v2.NSName, oracle.xml.parser.v2.SAXAttrList)`

    <!-- -->

    - #### endPrefixMapping

          public void endPrefixMapping(java.lang.String prefix)
                                throws SAXException

      End the scope of a prefix/URI namespace mapping.
      Specified by:
      [`endPrefixMapping`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`endPrefixMapping`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

      Parameters:
      `prefix` - The prefix that was being mapped.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The client may throw an exception during processing.

      See Also:
      `startPrefixMapping(java.lang.String, java.lang.String)`, `endElement(oracle.xml.parser.v2.NSName)`

    <!-- -->

    - #### startElement

          public void startElement(NSName elem,
                                   SAXAttrList attrlist)
                            throws SAXException

      Receive notification of the beginning of an element.
      Specified by:
      [`startElement`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Overrides:
      [`startElement`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

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
      Specified by:
      [`startElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startElement`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

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

      Overrides:
      [`endElement`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

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
      Specified by:
      [`endElement`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`endElement`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or the empty string if the element has no Namespace URI or if Namespace processing is not being performed.

      `localName` - The local name (without prefix), or the empty string if Namespace processing is not being performed.

      `qName` - The qualified XML 1.0 name (with prefix), or the empty string if qualified names are not available.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Receive a Locator object for document events.
      By default, do nothing. Application writers may override this method in a subclass if they wish to store the locator for use with other document events.

      Specified by:
      [`setDocumentLocator`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`setDocumentLocator`](../../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`setDocumentLocator`](../../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `locator` - A locator for all SAX document events.

      See Also:
      [`DocumentHandler.setDocumentLocator(org.xml.sax.Locator)`](../../../../org/xml/sax/DocumentHandler.md), [`Locator`](../../../../org/xml/sax/Locator.md)

    <!-- -->

    - #### getLocator

          public Locator getLocator()

      Get the locator reported by the Reader using setDocumentLocator
      Returns:
      locator

    <!-- -->

    - #### getDocument

          public XMLDocument getDocument()

      Get the document being build
      Returns:
      XMLDocument

    <!-- -->

    - #### getRoot

          public XMLNode getRoot()

      Get the root of tree being built
      Returns:
      the root node

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Receive notification of the beginning of the document.
      Specified by:
      [`startDocument`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`startDocument`](../../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`startDocument`](../../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../../org/xml/sax/HandlerBase.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.startDocument()`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Receive notification of the end of the document.
      Specified by:
      [`endDocument`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`endDocument`](../../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`endDocument`](../../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../../org/xml/sax/HandlerBase.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.endDocument()`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### setDoctype

          public void setDoctype(DTD dtd)
                          throws SAXException

      Receive notification of DTD Sets the DTD
      Specified by:
      [`setDoctype`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Overrides:
      [`setDoctype`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

      Parameters:
      `dtd` - set the DTD for the document

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### endDoctype

          public void endDoctype()
                          throws SAXException

      Receive notification of end of the DTD.
      Specified by:
      [`endDoctype`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Overrides:
      [`endDoctype`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### characters

          public void characters(char[] ch,
                                 int start,
                                 int length)
                          throws SAXException

      Receive notification of character data inside an element.
      Specified by:
      [`characters`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`characters`](../../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`characters`](../../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `ch` - The characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.characters(char[], int, int)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### cDATASection

          public void cDATASection(char[] ch,
                                   int start,
                                   int length)
                            throws SAXException

      Receive notification of CDATA Section data inside an element.
      Specified by:
      [`cDATASection`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Overrides:
      [`cDATASection`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

      Parameters:
      `ch` - The CDATA characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.characters(char[], int, int)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] ch,
                                          int start,
                                          int length)
                                   throws SAXException

      Receive notification of ignorable whitespace in element content.
      Specified by:
      [`ignorableWhitespace`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`ignorableWhitespace`](../../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`ignorableWhitespace`](../../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `ch` - The whitespace characters.

      `start` - The start position in the character array.

      `length` - The number of characters to use from the character array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.ignorableWhitespace(char[], int, int)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Receive notification of a processing instruction.
      Specified by:
      [`processingInstruction`](../../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`processingInstruction`](../../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`processingInstruction`](../../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `target` - The processing instruction target.

      `data` - The processing instruction data, or null if none is supplied.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.processingInstruction(java.lang.String, java.lang.String)`](../../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### setXMLDecl

          public void setXMLDecl(java.lang.String version,
                                 java.lang.String standalone,
                                 java.lang.String encoding)
                          throws SAXException

      Receive notification of a XML Declaration.
      The Parser will invoke this method once for XML Decl

      Specified by:
      [`setXMLDecl`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Overrides:
      [`setXMLDecl`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

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

      Overrides:
      [`setTextDecl`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

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
      Specified by:
      [`comment`](XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](XMLDocumentHandler.md)

      Overrides:
      [`comment`](DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](DefaultXMLDocumentHandler.md)

      Parameters:
      `data` - The comment data, or null if none was supplied.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### startDTD

          public void startDTD(java.lang.String name,
                               java.lang.String publicId,
                               java.lang.String systemId)
                        throws SAXException

      Report the start of DTD declarations, if any.
      Specified by:
      [`startDTD`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The document type name.

      `publicId` - The declared public identifier for the external DTD subset, or null if none was declared.

      `systemId` - The declared system identifier for the external DTD subset, or null if none was declared.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `endDTD()`, `startEntity(java.lang.String)`

    <!-- -->

    - #### endDTD

          public void endDTD()
                      throws SAXException

      Report the end of DTD declarations.
      Specified by:
      [`endDTD`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `startDTD(java.lang.String, java.lang.String, java.lang.String)`

    <!-- -->

    - #### startEntity

          public void startEntity(java.lang.String name)
                           throws SAXException

      Report the beginning of some internal and external XML entities.
      All start/endEntity events must be properly nested.

      Specified by:
      [`startEntity`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%', and if it is the external DTD subset, it will be "\[dtd\]".

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `endEntity(java.lang.String)`, [`DeclHandler.internalEntityDecl(java.lang.String, java.lang.String)`](../../../../org/xml/sax/ext/DeclHandler.md), [`DeclHandler.externalEntityDecl(java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/ext/DeclHandler.md)

    <!-- -->

    - #### endEntity

          public void endEntity(java.lang.String name)
                         throws SAXException

      Report the end of an entity.
      Specified by:
      [`endEntity`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The name of the entity that is ending.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `startEntity(java.lang.String)`

    <!-- -->

    - #### startCDATA

          public void startCDATA()
                          throws SAXException

      Report the start of a CDATA section.
      Specified by:
      [`startCDATA`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `endCDATA()`

    <!-- -->

    - #### endCDATA

          public void endCDATA()
                        throws SAXException

      Report the end of a CDATA section.
      Specified by:
      [`endCDATA`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `startCDATA()`

    <!-- -->

    - #### comment

          public void comment(char[] ch,
                              int start,
                              int length)
                       throws SAXException

      Report an XML comment anywhere in the document.
      Specified by:
      [`comment`](../../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `ch` - An array holding the characters in the comment.

      `start` - The starting position in the array.

      `length` - The number of characters to use from the array.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### elementDecl

          public void elementDecl(java.lang.String name,
                                  java.lang.String model)
                           throws SAXException

      Report an element type declaration.
      Specified by:
      [`elementDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `name` - The element type name.

      `model` - The content model as a normalized string.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### attributeDecl

          public void attributeDecl(java.lang.String eName,
                                    java.lang.String aName,
                                    java.lang.String type,
                                    java.lang.String valueDefault,
                                    java.lang.String value)
                             throws SAXException

      Report an attribute type declaration.
      Specified by:
      [`attributeDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `eName` - The name of the associated element.

      `aName` - The name of the attribute.

      `type` - A string representing the attribute type.

      `valueDefault` - A string representing the attribute default ("#IMPLIED", "#REQUIRED", or "#FIXED") or null if none of these applies.

      `value` - A string representing the attribute's default value, or null if there is none.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

    <!-- -->

    - #### internalEntityDecl

          public void internalEntityDecl(java.lang.String name,
                                         java.lang.String value)
                                  throws SAXException

      Report an internal entity declaration.
      Specified by:
      [`internalEntityDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%'.

      `value` - The replacement text of the entity.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `externalEntityDecl(java.lang.String, java.lang.String, java.lang.String)`, [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/DTDHandler.md)

    <!-- -->

    - #### externalEntityDecl

          public void externalEntityDecl(java.lang.String name,
                                         java.lang.String publicId,
                                         java.lang.String systemId)
                                  throws SAXException

      Report a parsed external entity declaration.
      Specified by:
      [`externalEntityDecl`](../../../../org/xml/sax/ext/DeclHandler.md) in interface [`DeclHandler`](../../../../org/xml/sax/ext/DeclHandler.md)

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%'.

      `publicId` - The declared public identifier of the entity, or null if none was declared.

      `systemId` - The declared system identifier of the entity.

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - The application may raise an exception.

      See Also:
      `internalEntityDecl(java.lang.String, java.lang.String)`, [`DTDHandler.unparsedEntityDecl(java.lang.String, java.lang.String, java.lang.String, java.lang.String)`](../../../../org/xml/sax/DTDHandler.md)

    <!-- -->

    - #### setDebugMode

          public void setDebugMode(boolean flag)

      Sets a flag to turn on debug information in the document
      Parameters:
      `flag` - determines whether debug info is stored

    <!-- -->

    - #### retainCDATASection

          public void retainCDATASection(boolean flag)

      Sets a flag to retain CDATA sections
      Parameters:
      `flag` - determines whether CDATA sections are retained

    <!-- -->

    - #### setNodeFactory

          public void setNodeFactory(XMLDocument doc)

      Set document as the factory to create nodes
      Parameters:
      `doc` - the document to be used

    <!-- -->

    - #### setNodeFactory

          public void setNodeFactory(NodeFactory f)

      Set a optional NodeFactory to be used for creating custom DOM trees
      Parameters:
      `f` - NodeFactory

    <!-- -->

    - #### resetNodeFactory

          public void resetNodeFactory()

      Reset the NodeFactory and go back to the original behaviour.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Parameters:
      `name` - The name of the attribute.

      `value` - The value of the attribute.

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

- **[Prev Class](DefaultXMLDocumentHandler.md)**
- **[Next Class](DOMParser.md)**

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
