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
- **[Next Class](CXMLParser.md)**

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

**oracle.xml.comp**

## **Class CXMLHandlerBase**

- **java.lang.Object**

- - **[org.xml.sax.HandlerBase](../../../org/xml/sax/HandlerBase.md)**

  - - **[oracle.xml.parser.v2.DefaultXMLDocumentHandler](../parser/v2/DefaultXMLDocumentHandler.md)**

    - - **oracle.xml.comp.CXMLHandlerBase**

<!-- -->

- **All Implemented Interfaces:**
  **[XMLDocumentHandler](../parser/v2/XMLDocumentHandler.md), [ContentHandler](../../../org/xml/sax/ContentHandler.md), [DocumentHandler](../../../org/xml/sax/DocumentHandler.md), [DTDHandler](../../../org/xml/sax/DTDHandler.md), [EntityResolver](../../../org/xml/sax/EntityResolver.md), [ErrorHandler](../../../org/xml/sax/ErrorHandler.md), [LexicalHandler](../../../org/xml/sax/ext/LexicalHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public class CXMLHandlerBase
      extends DefaultXMLDocumentHandler
      implements ContentHandler, LexicalHandler

  **The SAX compression is implemented using SAX Handler which compresses the data based on SAX events. To use the SAX compression, the application needs to implement this interface and register with the SAX parser via `Parser.setDocumentHandler()`**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `CXMLHandlerBase``()`<br>Default Constructor                                                                          |
    | `CXMLHandlerBase``(java.io.ObjectOutput outstream)`<br>Constructs the CXMLHandlerBase using the `ObjectOutput` Stream |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                                                      |
    |------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                     | `characters``(char[] cbuf, int start, int len)`<br>Receive notification of character data inside an element                                                                                                                 |
    | `void`                                                     | `comment``(char[] ch, int start, int length)`<br>Receive notification of comment The parser will invoke this method for each comment found.                                                                                 |
    | `void`                                                     | `comment``(java.lang.String text)`<br>Receive notification of comment The parser will invoke this method for each comment found.                                                                                            |
    | `void`                                                     | `endCDATA``()`<br>Receive notification of end of CDATA                                                                                                                                                                      |
    | `void`                                                     | `endDoctype``()`<br>Receive notification of end of the DTD.                                                                                                                                                                 |
    | `void`                                                     | `endDocument``()`<br>Receive notification of the end of the document.                                                                                                                                                       |
    | `void`                                                     | `endDTD``()`<br>Receive notification of end of DTD declaration                                                                                                                                                              |
    | `void`                                                     | `endElement``(`[`NSName`](../parser/v2/NSName.md)` elem)`<br>Deprecated. <br>this is replaced by endElement(namespace, localName, qname)                                                                                    |
    | `void`                                                     | `endElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName)`<br>Deprecated. <br>this is replaced by endElement(namespace, localName, qname)                                            |
    | `void`                                                     | `endEntity``(java.lang.String name)`<br>Receive notification of end of entity                                                                                                                                               |
    | `void`                                                     | `endPrefixMapping``(java.lang.String prefix)`<br>Receive notification of the end of scope of prefix URI mapping                                                                                                             |
    | [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md) | `getHandler``()`<br>Get the next pipe-line node handler.                                                                                                                                                                    |
    | [`InfosetWriter`](../scalable/InfosetWriter.md)            | `getInfosetWriter``()`<br>Get the CXMLWriter                                                                                                                                                                                |
    | `java.lang.Object`                                         | `getProperty``(java.lang.String name)`<br>Look up the value of a property.                                                                                                                                                  |
    | `void`                                                     | `ignorableWhitespace``(char[] cbuf, int start, int len)`<br>Receive notification of ignorable whitespace in element content                                                                                                 |
    | `void`                                                     | `processingInstruction``(java.lang.String target, java.lang.String data)`<br>Receive notification of a processing instruction                                                                                               |
    | `void`                                                     | `setDoctype``(`[`DTD`](../parser/v2/DTD.md)` dtd)`<br>Receive notification of a DTD (Document Type node).                                                                                                                   |
    | `void`                                                     | `setDocumentLocator``(`[`Locator`](../../../org/xml/sax/Locator.md)` locator)`<br>Receive the Locator object for the document event.                                                                                        |
    | `void`                                                     | `setError``(`[`XMLError`](../parser/v2/XMLError.md)` he)`<br>Receive notification of a XMLError handler.                                                                                                                    |
    | `void`                                                     | `setHandler``(`[`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)` h)`<br>Receive notification of a next pipe-line node handler.                                                                                    |
    | `void`                                                     | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Set the value of a property.                                                                                                                              |
    | `void`                                                     | `setPSVI``(boolean val)`<br>Set flag to store PSVI information                                                                                                                                                              |
    | `void`                                                     | `setTextDecl``(java.lang.String version, java.lang.String encoding)`<br>Receive notification of a Text XML Declaration.                                                                                                     |
    | `void`                                                     | `setXMLSchema``(java.lang.Object s)`<br>Receive notification of a XMLSchema object.                                                                                                                                         |
    | `void`                                                     | `setXSDValidator``(`[`XSDValidator`](../parser/schema/XSDValidator.md)` sv)`<br>Set the XSDValidator used to retrieve PSVI info                                                                                             |
    | `void`                                                     | `startCDATA``()`<br>Receive notification of start of CDATA                                                                                                                                                                  |
    | `void`                                                     | `startDocument``()`<br>Receive notification of the begining of the document.                                                                                                                                                |
    | `void`                                                     | `startDTD``(java.lang.String name, java.lang.String publicId, java.lang.String systemId)`<br>Receive notification of start of DTD declaratoin                                                                               |
    | `void`                                                     | `startElement``(`[`NSName`](../parser/v2/NSName.md)` elem, `[`SAXAttrList`](../parser/v2/SAXAttrList.md)` attributes)`<br>Recieve notification of the begining of an element.                                               |
    | `void`                                                     | `startElement``(java.lang.String namespaceURI, java.lang.String localName, java.lang.String qName, `[`Attributes`](../../../org/xml/sax/Attributes.md)` attributes)`<br>Recieve notification of the begining of an element. |
    | `void`                                                     | `startEntity``(java.lang.String name)`<br>Receive notification of begininning of some internal or external XML entities                                                                                                     |
    | `void`                                                     | `startPrefixMapping``(java.lang.String prefix, java.lang.String uri)`<br>Receive notification of the begin the scope of prefix URI mapping.                                                                                 |

    - ### Methods inherited from class oracle.xml.parser.v2.[DefaultXMLDocumentHandler](../parser/v2/DefaultXMLDocumentHandler.md)

      [`cDATASection`](../parser/v2/DefaultXMLDocumentHandler.md)`, `[`setXMLDecl`](../parser/v2/DefaultXMLDocumentHandler.md)`, `[`skippedEntity`](../parser/v2/DefaultXMLDocumentHandler.md)

    <!-- -->

    - ### Methods inherited from class org.xml.sax.[HandlerBase](../../../org/xml/sax/HandlerBase.md)

      [`endElement`](../../../org/xml/sax/HandlerBase.md)`, `[`error`](../../../org/xml/sax/HandlerBase.md)`, `[`fatalError`](../../../org/xml/sax/HandlerBase.md)`, `[`notationDecl`](../../../org/xml/sax/HandlerBase.md)`, `[`resolveEntity`](../../../org/xml/sax/HandlerBase.md)`, `[`startElement`](../../../org/xml/sax/HandlerBase.md)`, `[`unparsedEntityDecl`](../../../org/xml/sax/HandlerBase.md)`, `[`warning`](../../../org/xml/sax/HandlerBase.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[ContentHandler](../../../org/xml/sax/ContentHandler.md)

      [`skippedEntity`](../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[DocumentHandler](../../../org/xml/sax/DocumentHandler.md)

      [`endElement`](../../../org/xml/sax/DocumentHandler.md)`, `[`startElement`](../../../org/xml/sax/DocumentHandler.md)

<!-- -->

- - ### Constructor Detail

    - #### CXMLHandlerBase

          public CXMLHandlerBase(java.io.ObjectOutput outstream)
                          throws java.io.IOException

      Constructs the CXMLHandlerBase using the `ObjectOutput` Stream
      Parameters:
      `outstream` - - the output stream

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### CXMLHandlerBase

          public CXMLHandlerBase()

      Default Constructor

  <!-- -->

  - ### Method Detail

    - #### getInfosetWriter

          public InfosetWriter getInfosetWriter()

      Get the CXMLWriter

    <!-- -->

    - #### getProperty

          public java.lang.Object getProperty(java.lang.String name)

      Look up the value of a property. The property name is any fully-qualified URI.
      Parameters:
      `name` - The property name, which is a fully-qualified URI.

      Returns:
      The current value of the property.

      See Also:
      `setProperty(java.lang.String, java.lang.Object)`

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String name,
                                  java.lang.Object value)

      Set the value of a property. The property name is any fully-qualified URI.
      Parameters:
      `name` - The property name, which is a fully-qualified URI.

      `value` - The requested value for the property.

    <!-- -->

    - #### setXSDValidator

          public void setXSDValidator(XSDValidator sv)

      Set the XSDValidator used to retrieve PSVI info
      Parameters:
      `sv` - validator

    <!-- -->

    - #### setPSVI

          public void setPSVI(boolean val)

      Set flag to store PSVI information
      Parameters:
      `val` -

    <!-- -->

    - #### setDocumentLocator

          public void setDocumentLocator(Locator locator)

      Receive the Locator object for the document event. By default, do nothing. This method could be overridden by the subclasses events.
      Specified by:
      [`setDocumentLocator`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`setDocumentLocator`](../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`setDocumentLocator`](../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `locator` - The locator for the SAX document events.

      See Also:
      [`ContentHandler.setDocumentLocator(org.xml.sax.Locator)`](../../../org/xml/sax/ContentHandler.md)

    <!-- -->

    - #### startDocument

          public void startDocument()
                             throws SAXException

      Receive notification of the begining of the document. By default, do nothing. This method could be overridden by the subclasses to take specific actions at the begining of a document.
      Specified by:
      [`startDocument`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`startDocument`](../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`startDocument`](../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../org/xml/sax/HandlerBase.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`DocumentHandler.startDocument()`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### endDocument

          public void endDocument()
                           throws SAXException

      Receive notification of the end of the document.
      Specified by:
      [`endDocument`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`endDocument`](../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`endDocument`](../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../org/xml/sax/HandlerBase.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler.endDocument()`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### startPrefixMapping

          public void startPrefixMapping(java.lang.String prefix,
                                         java.lang.String uri)
                                  throws SAXException

      Receive notification of the begin the scope of prefix URI mapping.
      Specified by:
      [`startPrefixMapping`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startPrefixMapping`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `prefix` - The Namespace prefix being declared

      `uri` - The Namespace URI the prefix is mapped to

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DefaultXMLDocumentHandler.endPrefixMapping(java.lang.String)`](../parser/v2/DefaultXMLDocumentHandler.md), [`DefaultXMLDocumentHandler.startElement(oracle.xml.parser.v2.NSName, oracle.xml.parser.v2.SAXAttrList)`](../parser/v2/DefaultXMLDocumentHandler.md)

    <!-- -->

    - #### endPrefixMapping

          public void endPrefixMapping(java.lang.String prefix)
                                throws SAXException

      Receive notification of the end of scope of prefix URI mapping
      Specified by:
      [`endPrefixMapping`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`endPrefixMapping`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `prefix` - The prefix that was being mapped

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DefaultXMLDocumentHandler.startPrefixMapping(java.lang.String, java.lang.String)`](../parser/v2/DefaultXMLDocumentHandler.md), [`DefaultXMLDocumentHandler.endElement(oracle.xml.parser.v2.NSName)`](../parser/v2/DefaultXMLDocumentHandler.md)

    <!-- -->

    - #### startElement

          public void startElement(java.lang.String namespaceURI,
                                   java.lang.String localName,
                                   java.lang.String qName,
                                   Attributes attributes)
                            throws SAXException

      Recieve notification of the begining of an element.
      Specified by:
      [`startElement`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`startElement`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `namespaceURI` - The Namespace URI, or empty string if the element has NamespaceUri

      `localName` - The local name (without prefix)

      `qName` - The qualified name (with prefix)

      `attributes` - The attributes attached to the element. If there are no attributes, then it is an empty Attribute object

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DefaultXMLDocumentHandler.endElement(oracle.xml.parser.v2.NSName)`](../parser/v2/DefaultXMLDocumentHandler.md), [`Attributes`](../../../org/xml/sax/Attributes.md)

    <!-- -->

    - #### endElement

          public void endElement(java.lang.String namespaceURI,
                                 java.lang.String localName,
                                 java.lang.String qName)

      Deprecated. this is replaced by endElement(namespace, localName, qname)
      Receive notification of the end of the element.
      Specified by:
      [`endElement`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Overrides:
      [`endElement`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `namespaceURI` - The namespace URI or empty string if there is no namespace UIR

      `localName` - The local name (without prefix)

      `qName` - The qualified XML 1.0 name (with prefix)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### characters

          public void characters(char[] cbuf,
                                 int start,
                                 int len)
                          throws SAXException

      Receive notification of character data inside an element
      Specified by:
      [`characters`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`characters`](../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`characters`](../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `cbuf` - characters

      `start` - The starting position in the character array

      `len` - The number of characters to use from the character array

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler.characters(char[], int, int)`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### ignorableWhitespace

          public void ignorableWhitespace(char[] cbuf,
                                          int start,
                                          int len)
                                   throws SAXException

      Receive notification of ignorable whitespace in element content
      Specified by:
      [`ignorableWhitespace`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`ignorableWhitespace`](../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`ignorableWhitespace`](../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `cbuf` - The Character from XML docuemnt

      `start` - The start position in the array.

      `len` - The number of characters to read from the array

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler.ignorableWhitespace(char[], int, int)`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### processingInstruction

          public void processingInstruction(java.lang.String target,
                                            java.lang.String data)
                                     throws SAXException

      Receive notification of a processing instruction
      Specified by:
      [`processingInstruction`](../../../org/xml/sax/ContentHandler.md) in interface [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)

      Specified by:
      [`processingInstruction`](../../../org/xml/sax/DocumentHandler.md) in interface [`DocumentHandler`](../../../org/xml/sax/DocumentHandler.md)

      Overrides:
      [`processingInstruction`](../../../org/xml/sax/HandlerBase.md) in class [`HandlerBase`](../../../org/xml/sax/HandlerBase.md)

      Parameters:
      `target` - The processing instruction target

      `data` - The processing instruction data

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler.processingInstruction(java.lang.String, java.lang.String)`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### startDTD

          public void startDTD(java.lang.String name,
                               java.lang.String publicId,
                               java.lang.String systemId)
                        throws SAXException

      Receive notification of start of DTD declaratoin
      Specified by:
      [`startDTD`](../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The document type name

      `publicId` - The declared public identifier for the external DTD subset, or null if none was declared

      `systemId` - The declared system identifier for the externa DTD subset, or null if none was declared

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`LexicalHandler.endDTD()`](../../../org/xml/sax/ext/LexicalHandler.md), [`LexicalHandler.startEntity(java.lang.String)`](../../../org/xml/sax/ext/LexicalHandler.md)

    <!-- -->

    - #### endDTD

          public void endDTD()
                      throws SAXException

      Receive notification of end of DTD declaration
      Specified by:
      [`endDTD`](../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`LexicalHandler.startDTD(java.lang.String, java.lang.String, java.lang.String)`](../../../org/xml/sax/ext/LexicalHandler.md)

    <!-- -->

    - #### startEntity

          public void startEntity(java.lang.String name)
                           throws SAXException

      Receive notification of begininning of some internal or external XML entities
      Specified by:
      [`startEntity`](../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The name of the entity. If it is a parameter entity, the name will begin with '%', and if it is an external DTD subset it will be "\[dtd\]"

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`LexicalHandler.endEntity(java.lang.String)`](../../../org/xml/sax/ext/LexicalHandler.md), [`DeclHandler.internalEntityDecl(java.lang.String, java.lang.String)`](../../../org/xml/sax/ext/DeclHandler.md), [`DeclHandler.externalEntityDecl(java.lang.String, java.lang.String, java.lang.String)`](../../../org/xml/sax/ext/DeclHandler.md)

    <!-- -->

    - #### endEntity

          public void endEntity(java.lang.String name)
                         throws SAXException

      Receive notification of end of entity
      Specified by:
      [`endEntity`](../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `name` - The name of the entity

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`LexicalHandler.startEntity(java.lang.String)`](../../../org/xml/sax/ext/LexicalHandler.md)

    <!-- -->

    - #### startCDATA

          public void startCDATA()
                          throws SAXException

      Receive notification of start of CDATA
      Specified by:
      [`startCDATA`](../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`LexicalHandler.endCDATA()`](../../../org/xml/sax/ext/LexicalHandler.md)

    <!-- -->

    - #### endCDATA

          public void endCDATA()
                        throws SAXException

      Receive notification of end of CDATA
      Specified by:
      [`endCDATA`](../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`LexicalHandler.startCDATA()`](../../../org/xml/sax/ext/LexicalHandler.md)

    <!-- -->

    - #### comment

          public void comment(char[] ch,
                              int start,
                              int length)
                       throws SAXException

      Receive notification of comment
      The parser will invoke this method for each comment found.

      Specified by:
      [`comment`](../../../org/xml/sax/ext/LexicalHandler.md) in interface [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md)

      Parameters:
      `ch` - The comment character data

      `start` - The starting location of the comment

      `length` - The length of the comment character data

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception possibly wrapping another exception

    <!-- -->

    - #### startElement

          public void startElement(NSName elem,
                                   SAXAttrList attributes)
                            throws SAXException

      Recieve notification of the begining of an element.
      Specified by:
      [`startElement`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`startElement`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `elem` - The NSName of the element

      `attributes` - The attributes attached to the element. If there are no attributes, then it is an empty Attribute object

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler.startElement(java.lang.String, org.xml.sax.AttributeList)`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### endElement

          public void endElement(NSName elem)
                          throws SAXException

      Deprecated. this is replaced by endElement(namespace, localName, qname)
      Receive notification of the end of the element.
      Specified by:
      [`endElement`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`endElement`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `elem` - The NSName of the element.

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md)

      See Also:
      [`DocumentHandler.endElement(java.lang.String)`](../../../org/xml/sax/DocumentHandler.md)

    <!-- -->

    - #### setTextDecl

          public void setTextDecl(java.lang.String version,
                                  java.lang.String encoding)
                           throws SAXException

      Receive notification of a Text XML Declaration.
      The Parser will invoke this method once for each text XML Decl

      Specified by:
      [`setTextDecl`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`setTextDecl`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `version` - The version number (or null, if not specified)

      `encoding` - The encoding name

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### comment

          public void comment(java.lang.String text)
                       throws SAXException

      Receive notification of comment
      The parser will invoke this method for each comment found.

      Specified by:
      [`comment`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`comment`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `text` - The comment character data

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception possibly wrapping another exception

    <!-- -->

    - #### setHandler

          public void setHandler(XMLDocumentHandler h)
                          throws SAXException

      Receive notification of a next pipe-line node handler.
      Specified by:
      [`setHandler`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`setHandler`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `h` - The XMLDocumentHandler node

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### getHandler

          public XMLDocumentHandler getHandler()

      Get the next pipe-line node handler.
      Specified by:
      [`getHandler`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`getHandler`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Returns:
      The XMLDocumentHandler node

    <!-- -->

    - #### setError

          public void setError(XMLError he)
                        throws SAXException

      Receive notification of a XMLError handler.
      Specified by:
      [`setError`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`setError`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `he` - The XMLError object

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setXMLSchema

          public void setXMLSchema(java.lang.Object s)
                            throws SAXException

      Receive notification of a XMLSchema object.
      Specified by:
      [`setXMLSchema`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`setXMLSchema`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `s` - The XMLSchema object

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### setDoctype

          public void setDoctype(DTD dtd)
                          throws SAXException

      Receive notification of a DTD (Document Type node).
      The Parser will invoke this method after calling startDocument to register the DTD used.

      Specified by:
      [`setDoctype`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`setDoctype`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Parameters:
      `dtd` - The DTD node

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

    <!-- -->

    - #### endDoctype

          public void endDoctype()
                          throws SAXException

      Receive notification of end of the DTD.
      Specified by:
      [`endDoctype`](../parser/v2/XMLDocumentHandler.md) in interface [`XMLDocumentHandler`](../parser/v2/XMLDocumentHandler.md)

      Overrides:
      [`endDoctype`](../parser/v2/DefaultXMLDocumentHandler.md) in class [`DefaultXMLDocumentHandler`](../parser/v2/DefaultXMLDocumentHandler.md)

      Throws:
      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

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
- **[Next Class](CXMLParser.md)**

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
